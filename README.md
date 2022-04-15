1.
1.
windows : ipconfig /all

linux: 

root@DonTtouch:~# ip a
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default qlen 1000
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
    inet 127.0.0.1/8 scope host lo
       valid_lft forever preferred_lft forever
    inet6 ::1/128 scope host 
       valid_lft forever preferred_lft forever
2: ens18: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc fq_codel state UP group default qlen 1000
    link/ether ee:0b:4b:48:c9:c3 brd ff:ff:ff:ff:ff:ff
    altname enp0s18
    inet 192.168.2.250/24 brd 192.168.2.255 scope global noprefixroute ens18
       valid_lft forever preferred_lft forever
    inet6 fe80::1551:c2b3:1d86:809a/64 scope link noprefixroute 
       valid_lft forever preferred_lft forever


2.
команда lldpctl из пакета lldpd


3.
root@DonTtouch:~# modprobe 8021q
root@DonTtouch:~# apt-get install vlan -y
Чтение списков пакетов… Готово
Построение дерева зависимостей       
Чтение информации о состоянии… Готово
Уже установлен пакет vlan самой новой версии (2.0.4ubuntu1.20.04.1).
Следующий пакет устанавливался автоматически и больше не требуется:
  libfwupdplugin1
Для его удаления используйте «apt autoremove».
Обновлено 0 пакетов, установлено 0 новых пакетов, для удаления отмечено 0 пакетов, и 4 пакетов не обновлено.
root@DonTtouch:~# vconfig add ens18 5

Warning: vconfig is deprecated and might be removed in the future, please migrate to ip(route2) as soon as possible!

root@DonTtouch:~# ip addr add 10.0.0.9/24 dev ens18.5
root@DonTtouch:~# ip link set up ens18.5
root@DonTtouch:~# ip a
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default qlen 1000
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
    inet 127.0.0.1/8 scope host lo
       valid_lft forever preferred_lft forever
    inet6 ::1/128 scope host 
       valid_lft forever preferred_lft forever
2: ens18: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc fq_codel state UP group default qlen 1000
    link/ether ee:0b:4b:48:c9:c3 brd ff:ff:ff:ff:ff:ff
    altname enp0s18
    inet 192.168.2.250/24 brd 192.168.2.255 scope global noprefixroute ens18
       valid_lft forever preferred_lft forever
    inet6 fe80::1551:c2b3:1d86:809a/64 scope link noprefixroute 
       valid_lft forever preferred_lft forever
3: ens18.6@ens18: <BROADCAST,MULTICAST> mtu 1500 qdisc noop state DOWN group default qlen 1000
    link/ether ee:0b:4b:48:c9:c3 brd ff:ff:ff:ff:ff:ff
4: ens18.9@ens18: <BROADCAST,MULTICAST> mtu 1500 qdisc noop state DOWN group default qlen 1000
    link/ether ee:0b:4b:48:c9:c3 brd ff:ff:ff:ff:ff:ff
    inet 10.0.0.9/24 scope global ens18.9
       valid_lft forever preferred_lft forever
5: ens18.1@ens18: <BROADCAST,MULTICAST> mtu 1500 qdisc noop state DOWN group default qlen 1000
    link/ether ee:0b:4b:48:c9:c3 brd ff:ff:ff:ff:ff:ff
6: ens18.5@ens18: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc noqueue state UP group default qlen 1000
    link/ether ee:0b:4b:48:c9:c3 brd ff:ff:ff:ff:ff:ff
    inet 10.0.0.9/24 scope global ens18.5
       valid_lft forever preferred_lft forever
    inet6 fe80::ec0b:4bff:fe48:c9c3/64 scope link 
       valid_lft forever preferred_lft forever


4.
Типы агрегации (объединения) интерфейсов в Linux
mode=0 (balance-rr)
Этот режим используется по-умолчанию, если в настройках не указано другое. balance-rr обеспечивает балансировку нагрузки и отказоустойчивость. В данном режиме пакеты отправляются "по кругу" от 
первого интерфейса к последнему и сначала. Если выходит из строя один из интерфейсов, пакеты отправляются на остальные оставшиеся.При подключении портов к разным коммутаторам, требует их настройки.

mode=1 (active-backup)
При active-backup один интерфейс работает в активном режиме, остальные в ожидающем. Если активный падает, управление передается одному из ожидающих. Не требует поддержки данной функциональности от 
коммутатора.

mode=2 (balance-xor)
Передача пакетов распределяется между объединенными интерфейсами по формуле ((MAC-адрес источника) XOR (MAC-адрес получателя)) % число интерфейсов. Один и тот же интерфейс работает с определённым 
получателем. Режим даёт балансировку нагрузки и отказоустойчивость.

mode=3 (broadcast)
Происходит передача во все объединенные интерфейсы, обеспечивая отказоустойчивость.

mode=4 (802.3ad)
Это динамическое объединение портов. В данном режиме можно получить значительное увеличение пропускной способности как входящего так и исходящего трафика, используя все объединенные интерфейсы. 
Требует поддержки режима от коммутатора, а так же (иногда) дополнительную настройку коммутатора.

mode=5 (balance-tlb)
Адаптивная балансировка нагрузки. При balance-tlb входящий трафик получается только активным интерфейсом, исходящий - распределяется в зависимости от текущей загрузки каждого интерфейса. 
Обеспечивается отказоустойчивость и распределение нагрузки исходящего трафика. Не требует специальной поддержки коммутатора.

mode=6 (balance-alb)
Адаптивная балансировка нагрузки (более совершенная). Обеспечивает балансировку нагрузки как исходящего (TLB, transmit load balancing), так и входящего трафика (для IPv4 через ARP). Не требует 
специальной поддержки коммутатором, но требует возможности изменять MAC-адрес устройства.


bonds:
    bond0:
      dhcp4: no
      interfaces: [ens18, ens19]
      parameters: 
        mode: 802.3ad
        mii-monitor-interval: 1

5.

root@DonTtouch:/# apt install ipcalc -y
Чтение списков пакетов… Готово
Построение дерева зависимостей       
Чтение информации о состоянии… Готово
Следующий пакет устанавливался автоматически и больше не требуется:
  libfwupdplugin1
Для его удаления используйте «apt autoremove».
Следующие НОВЫЕ пакеты будут установлены:
  ipcalc
Обновлено 0 пакетов, установлено 1 новых пакетов, для удаления отмечено 0 пакетов, и 4 пакетов не обновлено.
Необходимо скачать 25,9 kB архивов.
После данной операции объём занятого дискового пространства возрастёт на 64,5 kB.
Пол:1 http://ru.archive.ubuntu.com/ubuntu focal/universe amd64 ipcalc all 0.41-5 [25,9 kB]
Получено 25,9 kB за 0с (313 kB/s)
Выбор ранее не выбранного пакета ipcalc.
(Чтение базы данных … на данный момент установлено 171914 файлов и каталогов.)
Подготовка к распаковке …/archives/ipcalc_0.41-5_all.deb …
Распаковывается ipcalc (0.41-5) …
Настраивается пакет ipcalc (0.41-5) …
Обрабатываются триггеры для man-db (2.9.1-1) …


root@DonTtouch:/# ipcalc 10.10.10.0/29
Address:   10.10.10.0           00001010.00001010.00001010.00000 000
Netmask:   255.255.255.248 = 29 11111111.11111111.11111111.11111 000
Wildcard:  0.0.0.7              00000000.00000000.00000000.00000 111
=>
Network:   10.10.10.0/29        00001010.00001010.00001010.00000 000
HostMin:   10.10.10.1           00001010.00001010.00001010.00000 001
HostMax:   10.10.10.6           00001010.00001010.00001010.00000 110
Broadcast: 10.10.10.7           00001010.00001010.00001010.00000 111
Hosts/Net: 6                     Class A, Private Internet


8 адресов, включая адрес подсети и бродкаст. На хосты остается 6 адресов


root@DonTtouch:/# ipcalc 10.10.10.0/24
Address:   10.10.10.0           00001010.00001010.00001010. 00000000
Netmask:   255.255.255.0 = 24   11111111.11111111.11111111. 00000000
Wildcard:  0.0.0.255            00000000.00000000.00000000. 11111111
=>
Network:   10.10.10.0/24        00001010.00001010.00001010. 00000000
HostMin:   10.10.10.1           00001010.00001010.00001010. 00000001
HostMax:   10.10.10.254         00001010.00001010.00001010. 11111110
Broadcast: 10.10.10.255         00001010.00001010.00001010. 11111111
Hosts/Net: 254                   Class A, Private Internet


В /24 подсети 256 адресов, подсеть 10.10.10.0/24 можно разделить на 32 подсети 10.10.10.0/29
Network: 10.10.10.0/29 Network: 10.10.10.8/29
Network: 10.10.10.16/29 до Network: 10.10.10.248/29


6.

диапазон 100.64.0.0 — 100.127.255.255 с маской 255.192.0.0 (/10)

root@DonTtouch:/# ipcalc 100.64.0.0/10 -s 50
Address:   100.64.0.0           01100100.01 000000.00000000.00000000
Netmask:   255.192.0.0 = 10     11111111.11 000000.00000000.00000000
Wildcard:  0.63.255.255         00000000.00 111111.11111111.11111111
=>
Network:   100.64.0.0/10        01100100.01 000000.00000000.00000000
HostMin:   100.64.0.1           01100100.01 000000.00000000.00000001
HostMax:   100.127.255.254      01100100.01 111111.11111111.11111110
Broadcast: 100.127.255.255      01100100.01 111111.11111111.11111111
Hosts/Net: 4194302               Class A

1. Requested size: 50 hosts
Netmask:   255.255.255.192 = 26 11111111.11111111.11111111.11 000000
Network:   100.64.0.0/26        01100100.01000000.00000000.00 000000
HostMin:   100.64.0.1           01100100.01000000.00000000.00 000001
HostMax:   100.64.0.62          01100100.01000000.00000000.00 111110
Broadcast: 100.64.0.63          01100100.01000000.00000000.00 111111
Hosts/Net: 62                    Class A

Needed size:  64 addresses.
Used network: 100.64.0.0/26
Unused:
100.64.0.64/26
100.64.0.128/25
100.64.1.0/24
100.64.2.0/23
100.64.4.0/22
100.64.8.0/21
100.64.16.0/20
100.64.32.0/19
100.64.64.0/18
100.64.128.0/17
100.65.0.0/16
100.66.0.0/15
100.68.0.0/14
100.72.0.0/13
100.80.0.0/12
100.96.0.0/11


7.

apr -a для Windows 
в  Linux arp входит в пакет net-tools

root@DonTtouch:/# apt install net-tools -y
Чтение списков пакетов… Готово
Построение дерева зависимостей       
Чтение информации о состоянии… Готово
Следующий пакет устанавливался автоматически и больше не требуется:
  libfwupdplugin1
Для его удаления используйте «apt autoremove».
Следующие НОВЫЕ пакеты будут установлены:
  net-tools
Обновлено 0 пакетов, установлено 1 новых пакетов, для удаления отмечено 0 пакетов, и 4 пакетов не обновлено.
Необходимо скачать 196 kB архивов.
После данной операции объём занятого дискового пространства возрастёт на 864 kB.
Пол:1 http://ru.archive.ubuntu.com/ubuntu focal/main amd64 net-tools amd64 1.60+git20180626.aebd88e-1ubuntu1 [196 kB]
Получено 196 kB за 0с (2 219 kB/s)
Выбор ранее не выбранного пакета net-tools.
(Чтение базы данных … на данный момент установлено 171926 файлов и каталогов.)
Подготовка к распаковке …/net-tools_1.60+git20180626.aebd88e-1ubuntu1_amd64.deb …
Распаковывается net-tools (1.60+git20180626.aebd88e-1ubuntu1) …
Настраивается пакет net-tools (1.60+git20180626.aebd88e-1ubuntu1) …
Обрабатываются триггеры для man-db (2.9.1-1) …

root@DonTtouch:/# arp
Адрес HW-тип HW-адрес Флаги Маска Интерфейс
_gateway                 ether   00:26:55:80:e2:e3   C                     ens18


все записи можно удалить командой ip neigh flush all
один адрес удалить командой arp -d "ip address"
