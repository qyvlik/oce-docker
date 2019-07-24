# mysql

## show table size

```sql
SELECT 
    table_name AS `Table`, 
    round(((data_length + index_length) / 1024 / 1024), 2) `Size in MB` 
FROM information_schema.TABLES 
WHERE table_schema = "201904-exchange"
    AND table_name like "tb_order_%"
ORDER BY 2 DESC;
```

```sql
SELECT 
    table_name AS `Table`, 
    round(((data_length + index_length) / 1024 / 1024), 2) `Size in MB` 
FROM information_schema.TABLES 
WHERE table_schema = "201904-exchange"
    AND table_name like "tb_user_%"
ORDER BY 2 DESC; 
```

```sql
SELECT 
    table_name AS `Table`, 
    round(((data_length + index_length) / 1024 / 1024), 2) `Size in MB` 
FROM information_schema.TABLES 
WHERE table_schema = "201904-exchange"
    AND table_name like "tb_%"
ORDER BY 2 DESC;
```

## show table index size

```sql
SELECT database_name, table_name, index_name, 
round(stat_value*@@innodb_page_size/1024/1024, 2) size_in_mb
FROM mysql.innodb_index_stats
WHERE stat_name = 'size' AND index_name != 'PRIMARY'
ORDER BY 4 DESC;
```

## qps&tps

```bash
#!/bin/bash
docker exec -it  oce-std_oce-mysql_1 mysqladmin extended-status -h127.0.0.1 -p'root' -i1 \
|awk '
    BEGIN {
        local_switch=0;
        print "QPS   Commit Rollback   TPS    Threads_con Threads_run \n------------------------------------------------------- ";
    }
    $2 ~ /Queries$/            {q=$4-lq;lq=$4;}
    $2 ~ /Com_commit$/         {c=$4-lc;lc=$4;}
    $2 ~ /Com_rollback$/       {r=$4-lr;lr=$4;}
    $2 ~ /Threads_connected$/  {tc=$4;}
    $2 ~ /Threads_running$/    {tr=$4;
    if(local_switch==0) {
        local_switch=1;
        count=0
    } else {
        if(count > 10) { 
            count=0;
            print "-------------------------------------------------------\nQPS   Commit Rollback   TPS    Threads_con Threads_run \n------------------------------------------------------- ";
        } else { 
            count+=1;
            printf " %-6d %-8d %-7d %-8d %-10d %d \n", q,c,r,c+r,tc,tr;
        }
    }
}' > mysql-qps-tps.txt
```