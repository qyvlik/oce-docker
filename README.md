# oce-docker

## [oce-fast-up](./oce-fast-up/README.md)

Fast up a **oce** use by a single machine. The machine only 2CPU 4G RAM, 20G disk space (such as aws ec2 t2.medium or higher).

## [oce-std](./oce-std/README.md)

Start up a **oce** by standard mode. The machine at less 4CPU8G, 200G disk space(such as aws ec2 c5.xlarge or higher).










before
```text
mysql> show status like  'Innodb_buffer_pool_%';
+---------------------------------------+-------------+
| Variable_name                         | Value       |
+---------------------------------------+-------------+
| Innodb_buffer_pool_dump_status        | not started |
| Innodb_buffer_pool_load_status        | not started |
| Innodb_buffer_pool_pages_data         | 15858       |
| Innodb_buffer_pool_bytes_data         | 332857344   |
| Innodb_buffer_pool_pages_dirty        | 454         |
| Innodb_buffer_pool_bytes_dirty        | 7184384     |
| Innodb_buffer_pool_pages_flushed      | 216886      |
| Innodb_buffer_pool_pages_free         | 110353      |
| Innodb_buffer_pool_pages_misc         | 4861        |
| Innodb_buffer_pool_pages_total        | 131072      |
| Innodb_buffer_pool_read_ahead_rnd     | 0           |
| Innodb_buffer_pool_read_ahead         | 0           |
| Innodb_buffer_pool_read_ahead_evicted | 0           |
| Innodb_buffer_pool_read_requests      | 175454044   |
| Innodb_buffer_pool_reads              | 1307        |
| Innodb_buffer_pool_wait_free          | 0           |
| Innodb_buffer_pool_write_requests     | 15932029    |
+---------------------------------------+-------------+
```






after
```text
mysql> show status like  'Innodb_buffer_pool_%';
+---------------------------------------+-------------+
| Variable_name                         | Value       |
+---------------------------------------+-------------+
| Innodb_buffer_pool_dump_status        | not started |
| Innodb_buffer_pool_load_status        | not started |
| Innodb_buffer_pool_pages_data         | 16464       |
| Innodb_buffer_pool_bytes_data         | 345858048   |
| Innodb_buffer_pool_pages_dirty        | 812         |
| Innodb_buffer_pool_bytes_dirty        | 12337152    |
| Innodb_buffer_pool_pages_flushed      | 256726      |
| Innodb_buffer_pool_pages_free         | 109542      |
| Innodb_buffer_pool_pages_misc         | 5066        |
| Innodb_buffer_pool_pages_total        | 131072      |
| Innodb_buffer_pool_read_ahead_rnd     | 0           |
| Innodb_buffer_pool_read_ahead         | 0           |
| Innodb_buffer_pool_read_ahead_evicted | 0           |
| Innodb_buffer_pool_read_requests      | 182682966   |
| Innodb_buffer_pool_reads              | 1312        |
| Innodb_buffer_pool_wait_free          | 0           |
| Innodb_buffer_pool_write_requests     | 16589670    |
+---------------------------------------+-------------+
```
















