1.

version: '3.6'

volumes:
  data: {}
  backup: {}

services:

  postgres:
    image: postgres:12
    container_name: psql
    ports:
      - "0.0.0.0:5432:5432"
    volumes:
      - data:/var/lib/postgresql/data
      - backup:/media/postgresql/backup
    environment:
      POSTGRES_USER: "user"
      POSTGRES_PASSWORD: "123123"
      POSTGRES_DB: "db"
    restart: always

root@dont-touch:/home/dlebedev/docker-compose# docker-compose up -d
Creating network "docker-compose_default" with the default driver
Creating volume "docker-compose_data" with default driver
Creating volume "docker-compose_backup" with default driver
Pulling postgres (postgres:12)...
12: Pulling from library/postgres
8740c948ffd4: Pull complete
c8dbd2beab50: Pull complete
05d9dc9d0fbd: Pull complete
ddd89d5ec714: Pull complete
f98bb9f03867: Pull complete
0554611e703f: Pull complete
64e0a8694477: Pull complete
8b868a753f47: Pull complete
18bfbb5f850c: Pull complete
5744def07d7d: Pull complete
fe9fb494287c: Pull complete
818b3a4590df: Pull complete
a7343ebe57c4: Pull complete
Digest: sha256:12c7030c6753e64f72601faa81c76a028ba6f0f5afb076ca6be2da57bc1eb93a
Status: Downloaded newer image for postgres:12
Creating psql ... done

root@dont-touch:/home/dlebedev/docker-compose# docker exec -it psql bash
root@2c6e4159f984:/# export PGPASSWORD=123123 && psql -h localhost -U user db
psql (12.13 (Debian 12.13-1.pgdg110+1))
Type "help" for help.

db=# 


2.

db=# CREATE USER "test-admin-user";
CREATE ROLE
db=# CREATE DATABASE test_db;
CREATE DATABASE
db=# CREATE TABLE orders (
db(#     id SERIAL,
    наименование VARCHAR, 
    цена INTEGER,
    PRIMARY KEY (id)
);
CREATE TABLE  
test_db=# CREATE TABLE clients (
    id SERIAL,
    фамилия VARCHAR,
    "страна проживания" VARCHAR, 
    заказ INTEGER,
    PRIMARY KEY (id),
    CONSTRAINT fk_заказ
      FOREIGN KEY(заказ) 
            REFERENCES orders(id)
);
CREATE TABLE

db-# \q
root@2c6e4159f984:/# export PGPASSWORD=123123 && psql -h localhost -U user test_db
psql (12.13 (Debian 12.13-1.pgdg110+1))
Type "help" for help.

test_db=# CREATE TABLE orders (
    id SERIAL,
    наименование VARCHAR, 
    цена INTEGER,
    PRIMARY KEY (id)
);
CREATE TABLE

test_db=# CREATE TABLE clients (
    id SERIAL,
    фамилия VARCHAR,
    "страна проживания" VARCHAR, 
    заказ INTEGER,
    PRIMARY KEY (id),
    CONSTRAINT fk_заказ
      FOREIGN KEY(заказ) 
            REFERENCES orders(id)
);
CREATE TABLE

test_db=# CREATE INDEX ON clients("страна проживания");
CREATE INDEX
test_db=# GRANT ALL ON TABLE orders, clients TO "test-admin-user";
GRANT
test_db=# CREATE USER "test-simple-user" WITH PASSWORD 'netology';
CREATE ROLE
test_db=# GRANT CONNECT ON DATABASE test_db TO "test-simple-user";
GRANT
test_db=# GRANT USAGE ON SCHEMA public TO "test-simple-user";
GRANT
test_db=# GRANT SELECT, INSERT, UPDATE, DELETE ON orders, clients TO "test-simple-user";
GRANT

		

		Список БД
test_db=# \l+
                                                                   List of databases
   Name    | Owner | Encoding |  Collate   |   Ctype    |     Access privileges     |  Size   | Tablespace |                Description                 
-----------+-------+----------+------------+------------+---------------------------+---------+------------+--------------------------------------------
 db        | user  | UTF8     | en_US.utf8 | en_US.utf8 |                           | 8049 kB | pg_default | 
 postgres  | user  | UTF8     | en_US.utf8 | en_US.utf8 |                           | 7969 kB | pg_default | default administrative connection database
 template0 | user  | UTF8     | en_US.utf8 | en_US.utf8 | =c/user                  +| 7825 kB | pg_default | unmodifiable empty database
           |       |          |            |            | user=CTc/user             |         |            | 
 template1 | user  | UTF8     | en_US.utf8 | en_US.utf8 | =c/user                  +| 7825 kB | pg_default | default template for new databases
           |       |          |            |            | user=CTc/user             |         |            | 
 test_db   | user  | UTF8     | en_US.utf8 | en_US.utf8 | =Tc/user                 +| 8121 kB | pg_default | 
           |       |          |            |            | user=CTc/user            +|         |            | 
           |       |          |            |            | "test-simple-user"=c/user |         |            | 
(5 rows)


		Список таблиц

test_db=#  \d+ clients
                                                           Table "public.clients"
      Column       |       Type        | Collation | Nullable |               Default               | Storage  | Stats target | Description 
-------------------+-------------------+-----------+----------+-------------------------------------+----------+--------------+-------------
 id                | integer           |           | not null | nextval('clients_id_seq'::regclass) | plain    |              | 
 фамилия           | character varying |           |          |                                     | extended |              | 
 страна проживания | character varying |           |          |                                     | extended |              | 
 заказ             | integer           |           |          |                                     | plain    |              | 
Indexes:
    "clients_pkey" PRIMARY KEY, btree (id)
    "clients_страна проживания_idx" btree ("страна проживания")
Foreign-key constraints:
    "fk_заказ" FOREIGN KEY ("заказ") REFERENCES orders(id)
Access method: heap


test_db=# \d+ orders
                                                        Table "public.orders"
    Column    |       Type        | Collation | Nullable |              Default               | Storage  | Stats target | Description 
--------------+-------------------+-----------+----------+------------------------------------+----------+--------------+-------------
 id           | integer           |           | not null | nextval('orders_id_seq'::regclass) | plain    |              | 
 наименование | character varying |           |          |                                    | extended |              | 
 цена         | integer           |           |          |                                    | plain    |              | 
Indexes:
    "orders_pkey" PRIMARY KEY, btree (id)
Referenced by:
    TABLE "clients" CONSTRAINT "fk_заказ" FOREIGN KEY ("заказ") REFERENCES orders(id)
Access method: heap




		Запрос списка пользователей 

test_db=# SELECT 
    grantee, table_name, privilege_type 
FROM 
    information_schema.table_privileges 
WHERE 
    grantee in ('test-admin-user','test-simple-user')
    and table_name in ('clients','orders')
order by 
    1,2,3;
     grantee      | table_name | privilege_type 
------------------+------------+----------------
 test-admin-user  | clients    | DELETE
 test-admin-user  | clients    | INSERT
 test-admin-user  | clients    | REFERENCES
 test-admin-user  | clients    | SELECT
 test-admin-user  | clients    | TRIGGER
 test-admin-user  | clients    | TRUNCATE
 test-admin-user  | clients    | UPDATE
 test-admin-user  | orders     | DELETE
 test-admin-user  | orders     | INSERT
 test-admin-user  | orders     | REFERENCES
 test-admin-user  | orders     | SELECT
 test-admin-user  | orders     | TRIGGER
 test-admin-user  | orders     | TRUNCATE
 test-admin-user  | orders     | UPDATE
 test-simple-user | clients    | DELETE
 test-simple-user | clients    | INSERT
 test-simple-user | clients    | SELECT
 test-simple-user | clients    | UPDATE
 test-simple-user | orders     | DELETE
 test-simple-user | orders     | INSERT
 test-simple-user | orders     | SELECT
 test-simple-user | orders     | UPDATE
(22 rows)



3.

test_db=# INSERT INTO orders VALUES (1, 'Шоколад', 10), (2, 'Принтер', 3000), (3, 'Книга', 500), (4, 'Монитор', 7000), (5, 'Гитара', 4000);
INSERT 0 5

test_db=# SELECT * FROM orders;
 id | наименование | цена 
----+--------------+------
  1 | Шоколад      |   10
  2 | Принтер      | 3000
  3 | Книга        |  500
  4 | Монитор      | 7000
  5 | Гитара       | 4000
(5 rows)

test_db=# SELECT count(1) FROM orders;
 count 
-------
     5
(1 row)


test_db=# INSERT INTO clients VALUES (1, 'Иванов Иван Иванович', 'USA'), (2, 'Петров Петр Петрович', 'Canada'), (3, 'Иоганн Себастьян Бах', 'Japan'), (4, 'Ронни Джеймс Дио', 'Russia'), (5, 'Ritchie Blackmore', 'Russia');
INSERT 0 5

test_db=# SELECT * FROM clients;
 id |       фамилия        | страна проживания | заказ 
----+----------------------+-------------------+-------
  1 | Иванов Иван Иванович | USA               |      
  2 | Петров Петр Петрович | Canada            |      
  3 | Иоганн Себастьян Бах | Japan             |      
  4 | Ронни Джеймс Дио     | Russia            |      
  5 | Ritchie Blackmore    | Russia            |      
(5 rows)

test_db=# SELECT count(1) FROM clients;
 count 
-------
     5
(1 row)

test_db=# 


4.

test_db=# UPDATE clients SET "заказ" = (SELECT id FROM orders WHERE "наименование"='Книга') WHERE "фамилия"='Иванов Иван Иванович';
UPDATE 1
test_db=# UPDATE clients SET "заказ" = (SELECT id FROM orders WHERE "наименование"='Монитор') WHERE "фамилия"='Петров Петр Петрович';
UPDATE 1
test_db=# UPDATE clients SET "заказ" = (SELECT id FROM orders WHERE "наименование"='Гитара') WHERE "фамилия"='Иоганн Себастьян Бах';
UPDATE 1

test_db=# SELECT c.* FROM clients c JOIN orders o ON c.заказ = o.id;
 id |       фамилия        | страна проживания | заказ 
----+----------------------+-------------------+-------
  1 | Иванов Иван Иванович | USA               |     3
  2 | Петров Петр Петрович | Canada            |     4
  3 | Иоганн Себастьян Бах | Japan             |     5
(3 rows)


5.

test_db=# SELECT c.* FROM clients c JOIN orders o ON c.заказ = o.id;
 id |       фамилия        | страна проживания | заказ 
----+----------------------+-------------------+-------
  1 | Иванов Иван Иванович | USA               |     3
  2 | Петров Петр Петрович | Canada            |     4
  3 | Иоганн Себастьян Бах | Japan             |     5
(3 rows)

test_db=# EXPLAIN SELECT c.* FROM clients c JOIN orders o ON c.заказ = o.id;
                               QUERY PLAN                               
------------------------------------------------------------------------
 Hash Join  (cost=37.00..57.24 rows=810 width=72)
   Hash Cond: (c."заказ" = o.id)
   ->  Seq Scan on clients c  (cost=0.00..18.10 rows=810 width=72)
   ->  Hash  (cost=22.00..22.00 rows=1200 width=4)
         ->  Seq Scan on orders o  (cost=0.00..22.00 rows=1200 width=4)
(5 rows)



1. Построчно прочитана таблица orders
2. Создан кеш по полю id для таблицы orders
3. Прочитана таблица clients
4. Для каждой строки по полю "заказ" будет проверено, соответствует ли она чему-то в кеше orders
- если соответствия нет - строка будет пропущена
- если соответствие есть, то на основе этой строки и всех подходящих строках кеша СУБД сформирует вывод

При запуске просто explain, Postgres напишет только примерный план выполнения запроса и для каждой операции предположит:
- сколько процессорного времени уйдёт на поиск первой записи и сбор всей выборки: cost=первая_запись..вся_выборка
- сколько примерно будет строк: rows
- какой будет средняя длина строки в байтах: width
Postgres делает предположения на основе статистики, которую собирает периодический выполня analyze запросы на выборку данных из служебных таблиц.
Если запустить explain analyze, то запрос будет выполнен и к плану добавятся уже точные данные по времени и объёму данных.
explain verbose и explain analyze verbose - для каждой операции выборки будут написаны поля таблиц, которые в выборку попали.



6.


root@2c6e4159f984:/# export PGPASSWORD=123123 && pg_dumpall -h localhost -U user > /media/postgresql/backup/test_db.sql
root@2c6e4159f984:/# ls /media/postgresql/backup/
test_db.sql
root@2c6e4159f984:/# exit
exit

root@dont-touch:/home/dlebedev/docker-compose# docker-compose stop
Stopping psql ... done

root@dont-touch:/home/dlebedev/docker-compose# docker ps -a
CONTAINER ID   IMAGE         COMMAND                  CREATED          STATUS                      PORTS     NAMES
2c6e4159f984   postgres:12   "docker-entrypoint.s…"   33 minutes ago   Exited (0) 23 seconds ago             psql


root@dont-touch:/home/dlebedev/docker-compose# docker run --rm -d -e POSTGRES_USER=user -e POSTGRES_PASSWORD=123123 -e POSTGRES_DB=test_db -v dont-touch:/media/postgresql/backup --name psql2 postgres:12
0d78d02f0eff85876e03030a6d2f8c5bfcfeeac756a559e3c21400910609435c
root@dont-touch:/home/dlebedev/docker-compose# docker ps -a
CONTAINER ID   IMAGE         COMMAND                  CREATED          STATUS                     PORTS      NAMES
0d78d02f0eff   postgres:12   "docker-entrypoint.s…"   40 seconds ago   Up 39 seconds              5432/tcp   psql2
2c6e4159f984   postgres:12   "docker-entrypoint.s…"   36 minutes ago   Exited (0) 3 minutes ago              psql

root@dont-touch:/home/dlebedev/docker-compose# docker exec -it psql2  bash
root@0d78d02f0eff:ls /media/postgresql/backup/
test_db.sql
root@0d78d02f0eff:/# export PGPASSWORD=123123 && psql -h localhost -U user -f /media/postgresql/backup/test_db.sql test_db
root@0d78d02f0eff:/# psql -h localhost -U user test_db
psql (12.10 (Debian 12.10-1.pgdg110+1))
Type "help" for help.

test_db=#
