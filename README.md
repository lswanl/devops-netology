Задача 1:
1. Опишите своими словами основные преимущества применения на практике IaaC паттернов.
	Ответ:
		1. Ускорение инфраструктуры для процессов разработки и тестирования, что позволяет ускорить процесс производства продука
		2. Устранение дрейфа конфигурации объектов и, как следствие, идентичность конфигураций
		3. Более быстрый процесс разработки за счёт реализации непрерывной сборки продукта.  Уменьшается стоимость исправления дефекта, его можно обнаружить на каждом этапе сборки
2. Какой из принципов IaaC является основополагающим?
	Ответ:
		1. Основополагающим является идемпотентность


Задача 2:
1. Чем Ansible выгодно отличается от других систем управление конфигурациями?
	Ответ:
		1. Ansible прост в использования, не требует установки агента или клиента на целевую систему
2. Какой, на ваш взгляд, метод работы систем конфигурации более надёжный push или pull?
	Ответ:
		1. Pull. Исключает коллизии broadcast. Исключает возможность перхвата конфигурации


Задача 3:
1. Установить на личный компьютер:

    VirtualBox
    Vagrant
    Ansible

Приложить вывод команд установленных версий каждой из программ, оформленный в markdown.

	Ответ:  1. root@DonTtouch:~# vboxmanage --version
		   6.1.34_Ubuntur150636

		2. root@DonTtouch:~# vagrant version
		   Installed Version: 2.2.6

		3. root@DonTtouch:~# ansible --version
		   ansible 2.9.6
		   config file = /etc/ansible/ansible.cfg
		   configured module search path = ['/root/.ansible/plugins/modules', '/usr/share/ansible/plugins/modules']
		   ansible python module location = /usr/lib/python3/dist-packages/ansible
		   executable location = /usr/bin/ansible
		   python version = 3.8.10 (default, Jun 22 2022, 20:18:18) [GCC 9.4.0]


Задача 4:
1.Воспроизвести практическую часть лекции самостоятельно.

    Создать виртуальную машину.
    Зайти внутрь ВМ, убедиться, что Docker установлен с помощью команды

	Ответ:
		1. 
	root@DonTtouch:~# docker ps
	CONTAINER ID   IMAGE                               COMMAND                  CREATED       STATUS       PORTS                                       NAMES
	4ab766469fb5   netboxcommunity/netbox:v3.2-2.1.0   "/usr/bin/tini -- /o…"   5 weeks ago   Up 5 weeks   0.0.0.0:8000->8080/tcp, :::8000->8080/tcp   netbox-docker-netbox-1
	5f6ca39e7b0d   netboxcommunity/netbox:v3.2-2.1.0   "/usr/bin/tini -- /o…"   5 weeks ago   Up 5 weeks                                               netbox-docker-netbox-housekeeping-1
	0a970c0274ab   netboxcommunity/netbox:v3.2-2.1.0   "/usr/bin/tini -- /o…"   5 weeks ago   Up 5 weeks                                               netbox-docker-netbox-worker-1
	d7e747bf25c6   postgres:14-alpine                  "docker-entrypoint.s…"   5 weeks ago   Up 5 weeks   5432/tcp                                    netbox-docker-postgres-1
	9dbbb712f9ab   redis:7-alpine                      "docker-entrypoint.s…"   5 weeks ago   Up 5 weeks   6379/tcp                                    netbox-docker-redis-1
	7c9c9e57e173   redis:7-alpine                      "docker-entrypoint.s…"   5 weeks ago   Up 5 weeks   6379/tcp                                    netbox-docker-redis-cache-1

			(Тетсовая машина для себя была развернута в docker )
