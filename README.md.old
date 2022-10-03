Задание 1.

root@DonTtouch:~# docker login -u ldywa
Password: 
WARNING! Your password will be stored unencrypted in /root/.docker/config.json.
Configure a credential helper to remove this warning. See
https://docs.docker.com/engine/reference/commandline/login/#credentials-store

Login Succeeded
root@DonTtouch:~# docker pull ldywa
Using default tag: latest
Error response from daemon: pull access denied for ldywa, repository does not exist or may require 'docker login': denied: requested access to the resource is denied
root@DonTtouch:~# docker pull nginx:stable-alpine
stable-alpine: Pulling from library/nginx
213ec9aee27d: Pull complete 
c343366a9d25: Pull complete 
0425b57a482e: Pull complete 
02c28787ed93: Pull complete 
5a1f79310b77: Pull complete 
ed5101eac832: Pull complete 
Digest: sha256:98a1e37840fdf90f57df595dae8e27a198278170323744e13464b7f3a927562e
Status: Downloaded newer image for nginx:stable-alpine
docker.io/library/nginx:stable-alpine

root@DonTtouch:~# docker images
REPOSITORY                      TAG             IMAGE ID       CREATED         SIZE
nginx                           latest          2d389e545974   2 weeks ago     142MB
nginx                           stable-alpine   075b447b534f   7 weeks ago     23.5MB
netboxcommunity/netbox          v3.2-2.1.0      4e68daaf4e99   2 months ago    499MB
postgres                        14-alpine       41cd24e8c51b   2 months ago    216MB
redis                           7-alpine        d30e0f8484bb   2 months ago    28.4MB
ubuntu                          latest          27941809078c   3 months ago    77.8MB
runout/ntdevops53-task1-nginx   latest          9739b065962f   11 months ago   133MB
hello-world                     latest          feb5d9fea6a5   12 months ago   13.3kB


root@DonTtouch:~/Files# docker build -f dockerfile.txt -t ldywa/nginx:1.1 .
Sending build context to Docker daemon  2.048kB
Step 1/2 : FROM nginx
 ---> 2d389e545974
Step 2/2 : RUN echo '<html><head>Hey, Netology</head><body><h1>I am DevOps Engineer!</h1></body></html>' > /usr/share/nginx/html/index.html
 ---> Running in c637ea4e88b5
Removing intermediate container c637ea4e88b5
 ---> 475f6dfd58ec
Successfully built 475f6dfd58ec
Successfully tagged ldywa/nginx:1.1
root@DonTtouch:~/Files# docker push ldywa/nginx:1.1
The push refers to repository [docker.io/ldywa/nginx]
7caaadc4e8fb: Pushed 
36665e416ec8: Mounted from library/nginx 
31192a8593ec: Mounted from library/nginx 
7ee9bf58503c: Mounted from library/nginx 
a064c1703bfd: Mounted from library/nginx 
9388548487b1: Mounted from library/nginx 
b45078e74ec9: Mounted from library/nginx 
1.1: digest: sha256:bee48d013055012889b6147542d36529cc0367276871b4a725c441b249898e95 size: 1777
root@DonTtouch:~/Files# docker run -d -p 8080:80 ldywa/nginx:1.1
0fcf368ca84d0d601bd6db9a8853583aa666730b6c2da75396be0a319a6e51e7


root@DonTtouch:~/Files# curl -v http://localhost:8080
*   Trying 127.0.0.1:8080...
* TCP_NODELAY set
* Connected to localhost (127.0.0.1) port 8080 (#0)
> GET / HTTP/1.1
> Host: localhost:8080
> User-Agent: curl/7.68.0
> Accept: */*
> 
* Mark bundle as not supporting multiuse
< HTTP/1.1 200 OK
< Server: nginx/1.23.1
< Date: Mon, 03 Oct 2022 15:08:59 GMT
< Content-Type: text/html
< Content-Length: 83
< Last-Modified: Mon, 03 Oct 2022 15:04:24 GMT
< Connection: keep-alive
< ETag: "633af9f8-53"
< Accept-Ranges: bytes
< 
<html><head>Hey, Netology</head><body><h1>I am DevOps Engineer!</h1></body></html>
* Connection #0 to host localhost left intact
root@DonTtouch:~/Files# 



Задание 2.


    Высоконагруженное монолитное java веб-приложение;

	    Физическая машина, чтобы не расходовать ресурсы на виртуализацию и из-за монолитности не будет проблем с разворачиванием на разных машинах.

    Nodejs веб-приложение;

	    Docker, для более простого воспроизведения зависимостей в рабочих средах

    Мобильное приложение c версиями для Android и iOS;

	    Виртуальные машины, проще для тестирования, размещения на одной хостовой машине

    Шина данных на базе Apache Kafka;

	    Docker, есть готовые образы для apache kafka, на руку изолированность приложений, а также легкий откат на стабильные версии в случае обнаружения багов в продакшене

    Elasticsearch кластер для реализации логирования продуктивного веб-приложения - три ноды elasticsearch, два logstash и две ноды kibana;

	    Docker, Elasticsearch доступен для установки как образ docker, проще удалять логи, удобнее при кластеризации - меньше времени на запуск контейнеров.

    Мониторинг-стек на базе Prometheus и Grafana;

	    Docker. Есть готовые образы, приложения не хранят данные, что удобно при контейниризации, удобно масштабировать и быстро разворачивать.

    MongoDB, как основное хранилище данных для java-приложения;

	    Физическая машина как наиболее надежное, отказоустойчивое решение. Либо виртуальный сервер.

    Gitlab сервер для реализации CI/CD процессов и приватный (закрытый) Docker Registry

	    Могут быть применены все варианты, в зависимости от наличия соответствующих ресурсов. Но для большей изолированности лучше использовать docker.



Задание 3.


root@DonTtouch:~/Files# docker run -v /data:/data --name centos-container -d -t centos
Unable to find image 'centos:latest' locally
latest: Pulling from library/centos
a1d0c7532777: Pull complete 
Digest: sha256:a27fd8080b517143cbbbab9dfb7c8571c40d67d534bbdee55bd6c473f432b177
Status: Downloaded newer image for centos:latest
67798b4e81d62f472be0c58f97ef155825932bc4817df2aa8bd78a87c9b1cbde
root@DonTtouch:~/Files# 
root@DonTtouch:~/Files# docker run -v /data:/data --name debian-container -d -t debian
Unable to find image 'debian:latest' locally
latest: Pulling from library/debian
23858da423a6: Pull complete 
Digest: sha256:3e82b1af33607aebaeb3641b75d6e80fd28d36e17993ef13708e9493e30e8ff9
Status: Downloaded newer image for debian:latest
e1e7b46907d2ad9c6a9d6095e0ad0fa740e1bde5a8591444a47c280bfc8a116e
root@DonTtouch:~/Files# docker ps
CONTAINER ID   IMAGE                               COMMAND                  CREATED              STATUS              PORTS                                       NAMES
e1e7b46907d2   debian                              "bash"                   33 seconds ago       Up 32 seconds                                                   debian-container
67798b4e81d6   centos                              "/bin/bash"              About a minute ago   Up About a minute                                               centos-container
0fcf368ca84d   ldywa/nginx:1.1                     "/docker-entrypoint.…"   11 minutes ago       Up 11 minutes       0.0.0.0:8080->80/tcp, :::8080->80/tcp       elated_bartik
f62acb0565de   nginx                               "/docker-entrypoint.…"   4 hours ago          Up 4 hours          80/tcp                                      zen_noyce
4ab766469fb5   netboxcommunity/netbox:v3.2-2.1.0   "/usr/bin/tini -- /o…"   2 months ago         Up 8 weeks          0.0.0.0:8000->8080/tcp, :::8000->8080/tcp   netbox-docker-netbox-1
5f6ca39e7b0d   netboxcommunity/netbox:v3.2-2.1.0   "/usr/bin/tini -- /o…"   2 months ago         Up 8 weeks                                                      netbox-docker-netbox-housekeeping-1
0a970c0274ab   netboxcommunity/netbox:v3.2-2.1.0   "/usr/bin/tini -- /o…"   2 months ago         Up 8 weeks                                                      netbox-docker-netbox-worker-1
d7e747bf25c6   postgres:14-alpine                  "docker-entrypoint.s…"   2 months ago         Up 8 weeks          5432/tcp                                    netbox-docker-postgres-1
9dbbb712f9ab   redis:7-alpine                      "docker-entrypoint.s…"   2 months ago         Up 8 weeks          6379/tcp                                    netbox-docker-redis-1
7c9c9e57e173   redis:7-alpine                      "docker-entrypoint.s…"   2 months ago         Up 8 weeks          6379/tcp                                    netbox-docker-redis-cache-1
root@DonTtouch:~/Files# 
root@DonTtouch:~/Files# docker exec centos-container /bin/bash -c "echo test_message>/data/readme.md"
root@DonTtouch:~/Files# sudo touch /data/readme_host.md
root@DonTtouch:~/Files# nano /data/readme_host.md
root@DonTtouch:~/Files# docker exec -it debian-container /bin/bash
root@e1e7b46907d2:/#  cd /data
root@e1e7b46907d2:/data# ls -l
total 8
-rw-r--r-- 1 root root 13 Oct  3 15:19 readme.md
-rw-r--r-- 1 root root 16 Oct  3 15:22 readme_host.md
