
<<<<<<< HEAD
Необходимо найти opid операции:
=======
## Домашнее задание к занятию "6.4. PostgreSQL"

#### Задача 1
```
root@dont-touch:/home/dlebedev/docker-compose# docker ps
CONTAINER ID   IMAGE     COMMAND   CREATED   STATUS    PORTS     NAMES
root@dont-touch:/home/dlebedev/docker-compose# docker run --rm -d --name=postgres-docker -e POSTGRES_PASSWORD=123 postgres:13
Unable to find image 'postgres:13' locally
13: Pulling from library/postgres
8740c948ffd4: Pull complete 
c8dbd2beab50: Pull complete 
05d9dc9d0fbd: Pull complete 
ddd89d5ec714: Pull complete 
f98bb9f03867: Pull complete 
0554611e703f: Pull complete 
64e0a8694477: Pull complete 
8b868a753f47: Pull complete 
29acea527529: Pull complete 
04331b81a289: Pull complete 
faa16d756995: Pull complete 
8992a861a703: Pull complete 
3a0e6483774c: Pull complete 
Digest: sha256:1c36dd0c70477d7f7e472df3cddcdcc1c95526e74ca02b75e4a2c2c4ebd2f1db
Status: Downloaded newer image for postgres:13
319b5a711dc33357ba7556803ceb9a85d1638c826a669ed8cd161aae7684808d
root@dont-touch:/home/dlebedev/docker-compose# docker ps
CONTAINER ID   IMAGE         COMMAND                  CREATED              STATUS          PORTS      NAMES
319b5a711dc3   postgres:13   "docker-entrypoint.s…"   About a minute ago   Up 59 seconds   5432/tcp   postgres-docker
root@dont-touch:/home/dlebedev/docker-compose# docker exec -it postgres-docker bash
root@319b5a711dc3:/# 
root@319b5a711dc3:/# psql -U postgres
psql (13.9 (Debian 13.9-1.pgdg110+1))
Type "help" for help.
postgres=# \l+
List of databases
Name    |  Owner   | Encoding |  Collate   |   Ctype    |   Access privileges   |  Size   | Tablespace |                Description                 
-----------+----------+----------+------------+------------+-----------------------+---------+------------+--------------------------------------------
postgres  | postgres | UTF8     | en_US.utf8 | en_US.utf8 |                       | 7901 kB | pg_default | default administrative connection database
template0 | postgres | UTF8     | en_US.utf8 | en_US.utf8 | =c/postgres          +| 7753 kB | pg_default | unmodifiable empty database
|          |          |            |            | postgres=CTc/postgres |         |            | 
template1 | postgres | UTF8     | en_US.utf8 | en_US.utf8 | =c/postgres          +| 7753 kB | pg_default | default template for new databases
|          |          |            |            | postgres=CTc/postgres |         |            | 
(3 rows)

postgres=#  \conninfo
You are connected to database "postgres" as user "postgres" via socket in "/var/run/postgresql" at port "5432".

postgres=#  \dtS
List of relations
Schema   |          Name           | Type  |  Owner   
------------+-------------------------+-------+----------
pg_catalog | pg_aggregate            | table | postgres
pg_catalog | pg_am                   | table | postgres
pg_catalog | pg_amop                 | table | postgres
pg_catalog | pg_amproc               | table | postgres
pg_catalog | pg_attrdef              | table | postgres
pg_catalog | pg_attribute            | table | postgres
pg_catalog | pg_auth_members         | table | posters
pg_catalog | pg_authid               | table | posters
pg_catalog | pg_cast                 | table | postgres
pg_catalog | pg_class                | table | postgres
pg_catalog | pg_collation            | table | postgres
pg_catalog | pg_constraint           | table | postgres
pg_catalog | pg_conversion           | table | postgres
pg_catalog | pg_database             | table | postgres
pg_catalog | pg_db_role_setting      | table | postgres
pg_catalog | pg_default_acl          | table | postgres
pg_catalog | pg_depend               | table | postgres
pg_catalog | pg_description          | table | postgres
pg_catalog | pg_enum                 | table | postgres
pg_catalog | pg_event_trigger        | table | postgres
pg_catalog | pg_extension            | table | postgres
pg_catalog | pg_foreign_data_wrapper | table | postgres
pg_catalog | pg_foreign_server       | table | postgres
pg_catalog | pg_foreign_table        | table | postgres
pg_catalog | pg_index                | table | postgres
pg_catalog | pg_inherits             | table | postgres
pg_catalog | pg_init_privs           | table | postgres
pg_catalog | pg_language             | table | postgres
pg_catalog | pg_largeobject          | table | postgres
pg_catalog | pg_largeobject_metadata | table | postgres
pg_catalog | pg_namespace            | table | postgres
pg_catalog | pg_opclass              | table | postgres
pg_catalog | pg_operator             | table | postgres
pg_catalog | pg_opfamily             | table | postgres
pg_catalog | pg_partitioned_table    | table | postgres
pg_catalog | pg_policy               | table | postgres
pg_catalog | pg_proc                 | table | postgres
pg_catalog | pg_publication          | table | postgres
pg_catalog | pg_publication_rel      | table | postgres
pg_catalog | pg_range                | table | postgres
pg_catalog | pg_replication_origin   | table | postgres
pg_catalog | pg_rewrite              | table | postgres
pg_catalog | pg_seclabel             | table | postgres
pg_catalog | pg_sequence             | table | postgres
pg_catalog | pg_shdepend             | table | postgres
pg_catalog | pg_shdescription        | table | postgres
pg_catalog | pg_shseclabel           | table | postgres
pg_catalog | pg_statistic            | table | postgres
pg_catalog | pg_statistic_ext        | table | postgres
pg_catalog | pg_statistic_ext_data   | table | postgres
pg_catalog | pg_subscription         | table | postgres
pg_catalog | pg_subscription_rel     | table | postgres
pg_catalog | pg_tablespace           | table | postgres
pg_catalog | pg_transform            | table | postgres
pg_catalog | pg_trigger              | table | postgres
pg_catalog | pg_ts_config            | table | postgres
pg_catalog | pg_ts_config_map        | table | postgres
pg_catalog | pg_ts_dict              | table | postgres
pg_catalog | pg_ts_parser            | table | postgres
pg_catalog | pg_ts_template          | table | postgres
pg_catalog | pg_type                 | table | postgres
pg_catalog | pg_user_mapping         | table | postgres
(62 rows)

postgres=#  \dS+

List of relations
Schema   |              Name               | Type  |  Owner   | Persistence |    Size    | Description 
------------+---------------------------------+-------+----------+-------------+------------+-------------
pg_catalog | pg_aggregate                    | table | postgres | permanent   | 56 kB      | 
pg_catalog | pg_am                           | table | postgres | permanent   | 40 kB      | 
pg_catalog | pg_amop                         | table | postgres | permanent   | 80 kB      | 
pg_catalog | pg_amproc                       | table | postgres | permanent   | 64 kB       
pg_catalog | pg_attrdef                      | table | postgres | permanent   | 8192 bytes | 
pg_catalog | pg_attribute                    | table | postgres | permanent   | 456 kB     | 
pg_catalog | pg_auth_members                 | table | postgres | permanent   | 40 kB      | 
pg_catalog | pg_authid                       | table | postgres | permanent   | 48 kB      | 
pg_catalog | pg_available_extension_versions | view  | postgres | permanent   | 0 bytes    | 
pg_catalog | pg_available_extensions         | view  | postgres | permanent   | 0 bytes    | 
pg_catalog | pg_cast                         | table | postgres | permanent   | 48 kB      | 
pg_catalog | pg_class                        | table | postgres | permanent   | 136 kB     | 
pg_catalog | pg_collation                    | table | postgres | permanent   | 240 kB     | 
pg_catalog | pg_config                       | view  | postgres | permanent   | 0 bytes    | 
pg_catalog | pg_constraint                   | table | postgres | permanent   | 48 kB      | 
pg_catalog | pg_conversion                   | table | postgres | permanent   | 48 kB      | 
pg_catalog | pg_cursors                      | view  | postgres | permanent   | 0 bytes    | 
pg_catalog | pg_database                     | table | postgres | permanent   | 48 kB      | 
pg_catalog | pg_db_role_setting              | table | postgres | permanent   | 8192 bytes | 
pg_catalog | pg_default_acl                  | table | postgres | permanent   | 8192 bytes | 
pg_catalog | pg_depend                       | table | postgres | permanent   | 488 kB     | 
pg_catalog | pg_description                  | table | postgres | permanent   | 376 kB     | 
pg_catalog | pg_enum                         | table | postgres | permanent   | 0 bytes    | 
pg_catalog | pg_event_trigger                | table | postgres | permanent   | 8192 bytes | 
pg_catalog | pg_extension                    | table | postgres | permanent   | 48 kB      | 
pg_catalog | pg_file_settings                | view  | postgres | permanent   | 0 bytes    | 
pg_catalog | pg_foreign_data_wrapper         | table | postgres | permanent   | 8192 bytes | 
pg_catalog | pg_foreign_server               | table | postgres | permanent   | 8192 bytes | 
pg_catalog | pg_foreign_table                | table | postgres | permanent   | 8192 bytes | 
pg_catalog | pg_group                        | view  | postgres | permanent   | 0 bytes    | 
pg_catalog | pg_hba_file_rules               | view  | postgres | permanent   | 0 bytes    | 
pg_catalog | pg_index                        | table | postgres | permanent   | 64 kB      | 
pg_catalog | pg_indexes                      | view  | postgres | permanent   | 0 bytes    | 
pg_catalog | pg_inherits                     | table | postgres | permanent   | 0 bytes    | 
pg_catalog | pg_init_privs                   | table | postgres | permanent   | 56 kB      | 
pg_catalog | pg_language                     | table | postgres | permanent   | 48 kB      | 
pg_catalog | pg_largeobject                  | table | postgres | permanent   | 0 bytes    | 
pg_catalog | pg_largeobject_metadata         | table | postgres | permanent   | 0 bytes    | 
pg_catalog | pg_locks                        | view  | postgres | permanent   | 0 bytes    | 
pg_catalog | pg_matviews                     | view  | postgres | permanent   | 0 bytes    | 
pg_catalog | pg_namespace                    | table | postgres | permanent   | 48 kB      | 
pg_catalog | pg_opclass                      | table | postgres | permanent   | 48 kB      | 
pg_catalog | pg_operator                     | table | postgres | permanent   | 144 kB     | 
pg_catalog | pg_opfamily                     | table | postgres | permanent   | 48 kB      | 
pg_catalog | pg_partitioned_table            | table | postgres | permanent   | 8192 bytes | 
pg_catalog | pg_policies                     | view  | postgres | permanent   | 0 bytes    | 
pg_catalog | pg_policy                       | table | postgres | permanent   | 8192 bytes | 
pg_catalog | pg_prepared_statements          | view  | postgres | permanent   | 0 bytes    | 
pg_catalog | pg_prepared_xacts               | view  | postgres | permanent   | 0 bytes    | 
pg_catalog | pg_proc                         | table | postgres | permanent   | 688 kB     | 
pg_catalog | pg_publication                  | table | postgres | permanent   | 0 bytes    | 
pg_catalog | pg_publication_rel              | table | postgres | permanent   | 0 bytes    | 
pg_catalog | pg_publication_tables           | view  | postgres | permanent   | 0 bytes    | 
pg_catalog | pg_range                        | table | postgres | permanent   | 40 kB      | 
pg_catalog | pg_replication_origin           | table | postgres | permanent   | 8192 bytes | 
pg_catalog | pg_replication_origin_status    | view  | postgres | permanent   | 0 bytes    | 
pg_catalog | pg_replication_slots            | view  | postgres | permanent   | 0 bytes    | 
pg_catalog | pg_rewrite                      | table | postgres | permanent   | 656 kB     | 
pg_catalog | pg_roles                        | view  | postgres | permanent   | 0 bytes    | 
pg_catalog | pg_rules                        | view  | postgres | permanent   | 0 bytes    | 
pg_catalog | pg_seclabel                     | table | postgres | permanent   | 8192 bytes | 
pg_catalog | pg_seclabels                    | view  | postgres | permanent   | 0 bytes    | 
pg_catalog | pg_sequence                     | table | postgres | permanent   | 0 bytes    | 
pg_catalog | pg_sequences                    | view  | postgres | permanent   | 0 bytes    | 
pg_catalog | pg_settings                     | view  | postgres | permanent   | 0 bytes    | 
pg_catalog | pg_shadow                       | view  | postgres | permanent   | 0 bytes    | 
pg_catalog | pg_shdepend                     | table | postgres | permanent   | 40 kB      | 
pg_catalog | pg_shdescription                | table | postgres | permanent   | 48 kB      | 
pg_catalog | pg_shmem_allocations            | view  | postgres | permanent   | 0 bytes    | 
pg_catalog | pg_shseclabel                   | table | postgres | permanent   | 8192 bytes | 
pg_catalog | pg_stat_activity                | view  | postgres | permanent   | 0 bytes    | 
pg_catalog | pg_stat_all_indexes             | view  | postgres | permanent   | 0 bytes    | 
pg_catalog | pg_stat_all_tables              | view  | postgres | permanent   | 0 bytes    | 
pg_catalog | pg_stat_archiver                | view  | postgres | permanent   | 0 bytes    | 
pg_catalog | pg_stat_bgwriter                | view  | postgres | permanent   | 0 bytes    | 
pg_catalog | pg_stat_database                | view  | postgres | permanent   | 0 bytes   | 
pg_catalog | pg_stat_database_conflicts      | view  | postgres | permanent   | 0 bytes    | 
pg_catalog | pg_stat_gssapi                  | view  | postgres | permanent   | 0 bytes    | 
pg_catalog | pg_stat_progress_analyze        | view  | postgres | permanent   | 0 bytes    | 
pg_catalog | pg_stat_progress_basebackup     | view  | postgres | permanent   | 0 bytes    | 
pg_catalog | pg_stat_progress_cluster        | view  | postgres | permanent   | 0 bytes    | 
pg_catalog | pg_stat_progress_create_index   | view  | postgres | permanent   | 0 bytes    | 
pg_catalog | pg_stat_progress_vacuum         | view  | postgres | permanent   | 0 bytes    | 
pg_catalog | pg_stat_replication             | view  | postgres | permanent   | 0 bytes    | 
pg_catalog | pg_stat_slru                    | view  | postgres | permanent   | 0 bytes    | 
pg_catalog | pg_stat_ssl                     | view  | postgres | permanent   | 0 bytes    | 
pg_catalog | pg_stat_subscription            | view  | postgres | permanent   | 0 bytes    | 
pg_catalog | pg_stat_sys_indexes             | view  | postgres | permanent   | 0 bytes    | 
pg_catalog | pg_stat_sys_tables              | view  | postgres | permanent   | 0 bytes    | 
pg_catalog | pg_stat_user_functions          | view  | postgres | permanent   | 0 bytes    | 
pg_catalog | pg_stat_user_indexes            | view  | postgres | permanent   | 0 bytes    | 
pg_catalog | pg_stat_user_tables             | view  | postgres | permanent   | 0 bytes    | 
pg_catalog | pg_stat_wal_receiver            | view  | postgres | permanent   | 0 bytes    | 
pg_catalog | pg_stat_xact_all_tables         | view  | postgres | permanent   | 0 bytes    | 
pg_catalog | pg_stat_xact_sys_tables         | view  | postgres | permanent   | 0 bytes    | 
pg_catalog | pg_stat_xact_user_functions     | view  | postgres | permanent   | 0 bytes    | 
pg_catalog | pg_stat_xact_user_tables        | view  | postgres | permanent   | 0 bytes    | 
pg_catalog | pg_statio_all_indexes           | view  | postgres | permanent   | 0 bytes    | 
pg_catalog | pg_statio_all_sequences         | view  | postgres | permanent   | 0 bytes    | 
pg_catalog | pg_statio_all_tables            | view  | postgres | permanent   | 0 bytes    | 
pg_catalog | pg_statio_sys_indexes           | view  | postgres | permanent   | 0 bytes    | 
pg_catalog | pg_statio_sys_sequences         | view  | postgres | permanent   | 0 bytes    | 
pg_catalog | pg_statio_sys_tables            | view  | postgres | permanent   | 0 bytes    | 
pg_catalog | pg_statio_user_indexes          | view  | postgres | permanent   | 0 bytes    | 
pg_catalog | pg_statio_user_sequences        | view  | postgres | permanent   | 0 bytes    | 
pg_catalog | pg_statio_user_tables           | view  | postgres | permanent   | 0 bytes    | 
pg_catalog | pg_statistic                    | table | postgres | permanent   | 248 kB     | 
pg_catalog | pg_statistic_ext                | table | postgres | permanent   | 8192 bytes | 
pg_catalog | pg_statistic_ext_data           | table | postgres | permanent   | 8192 bytes | 
pg_catalog | pg_stats                        | view  | postgres | permanent   | 0 bytes    | 
pg_catalog | pg_stats_ext                    | view  | postgres | permanent   | 0 bytes    | 
pg_catalog | pg_subscription                 | table | postgres | permanent   | 8192 bytes | 
pg_catalog | pg_subscription_rel             | table | postgres | permanent   | 0 bytes    | 
pg_catalog | pg_tables                       | view  | postgres | permanent   | 0 bytes    | 
pg_catalog | pg_tablespace                   | table | postgres | permanent   | 48 kB      | 
pg_catalog | pg_timezone_abbrevs             | view  | postgres | permanent   | 0 bytes    | 
pg_catalog | pg_timezone_names               | view  | postgres | permanent   | 0 bytes    | 
pg_catalog | pg_transform                    | table | postgres | permanent   | 0 bytes    | 
pg_catalog | pg_trigger                      | table | postgres | permanent   | 8192 bytes | 
pg_catalog | pg_ts_config                    | table | postgres | permanent   | 40 kB      | 
pg_catalog | pg_ts_config_map                | table | postgres | permanent   | 56 kB      | 
pg_catalog | pg_ts_dict                      | table | postgres | permanent   | 48 kB      | 
pg_catalog | pg_ts_parser                    | table | postgres | permanent   | 40 kB      | 
pg_catalog | pg_ts_template                  | table | postgres | permanent   | 40 kB      | 
pg_catalog | pg_type                         | table | postgres | permanent   | 120 kB     | 
pg_catalog | pg_user                         | view  | postgres | permanent   | 0 bytes    | 
pg_catalog | pg_user_mapping                 | table | postgres | permanent   | 8192 bytes | 
pg_catalog | pg_user_mappings                | view  | postgres | permanent   | 0 bytes    | 
pg_catalog | pg_views                        | view  | postgres | permanent   | 0 bytes    | 
(129 rows)


postgres=# \q

root@319b5a711dc3:/# 
```

>>>>>>> 204cc5011e65a9c6490936eae5d3a0d1ab5995fd

db.currentOp({ "active" : true, "secs_running" : { "$gt" : 180 }})

<<<<<<< HEAD
{
    "inprog" : [
        {
            //...
            "opid" : 12345,
            "secs_running" : NumberLong(123)
            //...
        }
    ]
}

Завершить принудительно

db.killOp(12345)
=======
## Задача 2

Используя `psql` создайте БД `test_database`.

Изучите [бэкап БД](https://github.com/netology-code/virt-homeworks/tree/virt-11/06-db-04-postgresql/test_data).
>>>>>>> 204cc5011e65a9c6490936eae5d3a0d1ab5995fd

Восстановите бэкап БД в `test_database`.

<<<<<<< HEAD
 Использовать метод maxTimeMS() для установки предела исполнения по времени операций 
 Используя Database Profiler, отловить медленные операции. С помощью executionStats проанализировать. Попробовать
оптимизировать: удалить или добавить индексы, настроить шардинг и т.д.
=======
Перейдите в управляющую консоль `psql` внутри контейнера.
>>>>>>> 204cc5011e65a9c6490936eae5d3a0d1ab5995fd

Подключитесь к восстановленной БД и проведите операцию ANALYZE для сбора статистики по таблице.

Используя таблицу [pg_stats](https://postgrespro.ru/docs/postgresql/12/view-pg-stats), найдите столбец таблицы `orders` 
с наибольшим средним значением размера элементов в байтах.

**Приведите в ответе** команду, которую вы использовали для вычисления и полученный результат.


<<<<<<< HEAD
Возможнo вся память занята истекшими ключами, но еще не удаленными. Redis заблокировался (ACTIVE_EXPIRE_CYCLE_LOOKUPS_PER_LOOP), чтобы вывести из DB удаленные ключи и снизить их количество менее 25%. Т.к. Redis - однопоточное приложение, то все операции блокируются, пока он не выполнит очистку,можно поэксперементировать с hz в redis.conf



3.



Из документации MySQL могут быть три причины
1)Слишком объемные запросы на миллионы строк, рекомендуется увеличение параметра net_read_timeout
2)Малое значение параметра connect_timeout, клиент не успевает установить соединение.
3)Размер сообщения/запроса превышает размер буфера max_allowed_packet на сервере или max_allowed_packet на строне клиента.


Пути решения
1)Увеличить на сервере MySQL wait_timeout, max_allowed_packet, net_write_timeout и net_read_timeout
2)В SQLAlchemy уменьшить pool_recycle, wait_timeout
3)При исчезновении ошибки Lost connection to MySQL server during query возвращать по одному параметры в исходное состояние - для локализации проблемы.


4.


Postgres недостаточно памяти


1)По возможности добавить ресурсов RAM, провести отключить или перенести ненужные приложения.
2)Произвести настройку параметров, затрагивающих память в Postgres:
max_connections
shared_buffer
work_mem
effective_cache_size
maintenance_work_mem




=======



```
postgres=# CREATE DATABASE test_database;
CREATE DATABASE

root@dont-touch:/media/postgresql/backup# wget https://github.com/netology-code/virt-homeworks/blob/virt-11/06-db-04-postgresql/test_data/test_dump.sql
--2023-01-13 06:15:19--  https://github.com/netology-code/virt-homeworks/blob/virt-11/06-db-04-postgresql/test_data/test_dump.sql
Resolving github.com (github.com)... 140.82.121.3
Connecting to github.com (github.com)|140.82.121.3|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: unspecified [text/html]
Saving to: ‘test_dump.sql’

test_dump.sql                                        [ <=>                                                                                                 ] 172.34K  --.-KB/s    in 0.1s    

2023-01-13 06:15:20 (1.43 MB/s) - ‘test_dump.sql’ saved [176480]

root@dont-touch:/media/postgresql/backup# docker cp /media/postgresql/backup/test_dump.sql postgres-docker\:tmp
root@dont-touch:/media/postgresql/backup# docker exec -it postgresql-docker bash
root@dont-touch:/media/postgresql/backup#
root@dont-touch:/media/postgresql/backup#
root@319b5a711dc3:/# psql -U postgres -f /tmp/test_dump.sql  test_database
SET
SET
SET
SET
SET
set_config
------------

(1 row)

SET
SET
SET
SET
SET
SET
CREATE TABLE
ALTER TABLE
CREATE SEQUENCE
ALTER TABLE
ALTER SEQUENCE
ALTER TABLE
COPY 8
setval
--------
8
(1 row)

ALTER TABLE


root@319b5a711dc3:/# psql -U postgres
psql (13.6 (Debian 13.6-1.pgdg110+1))
Type "help" for help.
root@319b5a711dc3:/#

postgres=# \c test_database
You are now connected to database "test_database" as user "postgres".
test_database=# \dt
List of relations
Schema |  Name  | Type  |  Owner
--------+--------+-------+----------
public | orders | table | postgres
(1 row)

test_database=# ANALYZE VERBOSE public.orders;
INFO:  analyzing "public.orders"
INFO:  "orders": scanned 1 of 1 pages, containing 8 live rows and 0 dead rows; 8 rows in sample, 8 estimated total rows
ANALYZE

test_database=# SELECT avg_width FROM pg_stats WHERE tablename='orders';
avg_width
-----------
4
16
4
(3 rows)
```




## Задача 3

Архитектор и администратор БД выяснили, что ваша таблица orders разрослась до невиданных размеров и
поиск по ней занимает долгое время. Вам, как успешному выпускнику курсов DevOps в нетологии предложили
провести разбиение таблицы на 2 (шардировать на orders_1 - price>499 и orders_2 - price<=499).

Предложите SQL-транзакцию для проведения данной операции.

Можно ли было изначально исключить "ручное" разбиение при проектировании таблицы orders?




```
test_database=# CREATE TABLE orders_more_499_price (CHECK (price > 499)) INHERITS (orders);
CREATE TABLE
test_database=# INSERT INTO orders_more_499_price SELECT * FROM orders WHERE price > 499;
INSERT 0 3
test_database=# CREATE TABLE orders_less_499_price (CHECK (price <= 499)) INHERITS (orders);
CREATE TABLE
test_database=# INSERT INTO orders_LESS_499_price SELECT * FROM orders WHERE price <= 499;
INSERT 0 5
test_database=# DELETE FROM ONLY orders;
DELETE 8
test_database=# \dt
List of relations
Schema |         Name          | Type  |  Owner
--------+-----------------------+-------+----------
public | orders                | table | postgres
public | orders_less_499_price | table | postgres
public | orders_more_499_price | table | postgres
(3 rows)


CREATE RULE orders_insert_to_more AS ON INSERT TO orders WHERE ( price > 499 ) DO INSTEAD INSERT INTO orders_more_499_price VALUES (NEW.*);
CREATE RULE orders_insert_to_less AS ON INSERT TO orders WHERE ( price <= 499 ) DO INSTEAD INSERT INTO orders_less_499_price VALUES (NEW.*);
```


## Задача 4

Используя утилиту `pg_dump` создайте бекап БД `test_database`.

Как бы вы доработали бэкап-файл, чтобы добавить уникальность значения столбца `title` для таблиц `test_database`?


```

export PGPASSWORD=123 && pg_dump -h localhost -U postgres test_database > /tmp/test_database_backup.sql

title character varying(80) NOT NULL UNIQUE,
```
>>>>>>> 204cc5011e65a9c6490936eae5d3a0d1ab5995fd
