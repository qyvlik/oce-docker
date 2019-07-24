# oce-fast-up

1. **`oce-fast-up` does not set docker volumes**
2. make sure you have install `docker` and `docker-compose`
3. copy [.env.example](./.env.example) to [`.env`](./.env)
4. define the env var in the [`.env`](./.env) file
5. `docker-compose pull`
6. `docker-compose up -d`

## cn

1. **`oce-fast-up`没有特意设置数据卷**
2. 确认安装好 `docker`, `docker-compose`
3. 将 [.env.example](./.env.example) 拷贝到同目录下，并命名为 [`.env`](./.env)，[`.env`](./.env) 是给 `docker-compose` 使用的
    - [`.env`](./.env) 有若干环境变量
4. 返回项目根路径，然后拉取 `docker` 镜像：`docker-compose pull`
5. 启动项目：`docker-compose up -d`
6. 如果需要重启项目，可以直接 `docker-compose restart`

