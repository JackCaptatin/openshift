FROM ubuntu:20.04

# 设置环境变量
ENV PG_VERSION 12
ENV PGDATA /var/lib/postgresql/data
ENV PATH $PATH:/usr/lib/postgresql/$PG_VERSION/bin
ENV DEBIAN_FRONTEND=noninteractive  #这行是为了防止 debconf 交互

# 安装PostgreSQL
RUN apt-get update && \
    apt-get install -y postgresql-$PG_VERSION && \
    apt-get clean && \
    rm -rf /var/lib/apt/lists/* && \
    mkdir -p /var/run/postgresql && chown -R postgres:postgres /var/run/postgresql && \
    chmod 2777 /var/run/postgresql

# 设置数据目录
RUN mkdir -p "$PGDATA" && chown -R postgres:postgres "$PGDATA" && chmod 777 "$PGDATA"

USER postgres

# 初始化数据库
RUN initdb

EXPOSE 5432

CMD ["postgres"]
