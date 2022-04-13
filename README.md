1. Прочитал про тип файлов, не знал о них ранее.

2. Жесткая ссылка это по сути зеркальная копия объекта, наследующая его права, владельца и группу. Имеет тот же inode что и оригинальный файл.
Поэтому разных владельцев и разные права оригинал и хардлинк иметь не могут.

3.  У меня не установлен Vagrant так virtual box  не поддерживается М1 пока что, добавил ещё один диск в свою виртальную машину дальнейшие задания по разделам буду проивоить с ним.

4. root@DonTtouch:/home/dlebedev/GIT/devops-netology# fdisk -l
Диск /dev/loop0: 4 KiB, 4096 байт, 8 секторов
Единицы: секторов по 1 * 512 = 512 байт
Размер сектора (логический/физический): 512 байт / 512 байт
Размер I/O (минимальный/оптимальный): 512 байт / 512 байт


Диск /dev/loop1: 61,93 MiB, 64917504 байт, 126792 секторов
Единицы: секторов по 1 * 512 = 512 байт
Размер сектора (логический/физический): 512 байт / 512 байт
Размер I/O (минимальный/оптимальный): 512 байт / 512 байт


Диск /dev/loop2: 54,24 MiB, 56872960 байт, 111080 секторов
Единицы: секторов по 1 * 512 = 512 байт
Размер сектора (логический/физический): 512 байт / 512 байт
Размер I/O (минимальный/оптимальный): 512 байт / 512 байт


Диск /dev/loop3: 248,78 MiB, 260841472 байт, 509456 секторов
Единицы: секторов по 1 * 512 = 512 байт
Размер сектора (логический/физический): 512 байт / 512 байт
Размер I/O (минимальный/оптимальный): 512 байт / 512 байт


Диск /dev/loop4: 65,22 MiB, 68378624 байт, 133552 секторов
Единицы: секторов по 1 * 512 = 512 байт
Размер сектора (логический/физический): 512 байт / 512 байт
Размер I/O (минимальный/оптимальный): 512 байт / 512 байт


Диск /dev/loop5: 43,6 MiB, 45703168 байт, 89264 секторов
Единицы: секторов по 1 * 512 = 512 байт
Размер сектора (логический/физический): 512 байт / 512 байт
Размер I/O (минимальный/оптимальный): 512 байт / 512 байт


Диск /dev/loop6: 61,92 MiB, 64901120 байт, 126760 секторов
Единицы: секторов по 1 * 512 = 512 байт
Размер сектора (логический/физический): 512 байт / 512 байт
Размер I/O (минимальный/оптимальный): 512 байт / 512 байт


Диск /dev/loop7: 43,64 MiB, 45748224 байт, 89352 секторов
Единицы: секторов по 1 * 512 = 512 байт
Размер сектора (логический/физический): 512 байт / 512 байт
Размер I/O (минимальный/оптимальный): 512 байт / 512 байт


Диск /dev/sda: 13 GiB, 13958643712 байт, 27262976 секторов
Disk model: QEMU HARDDISK   
Единицы: секторов по 1 * 512 = 512 байт
Размер сектора (логический/физический): 512 байт / 512 байт
Размер I/O (минимальный/оптимальный): 512 байт / 512 байт
Тип метки диска: dos
Идентификатор диска: 0x64e6f3ac

Устр-во    Загрузочный  начало    Конец  Секторы Размер Идентификатор Тип
/dev/sda1  *              2048  1050623  1048576   512M             b W95 FAT32
/dev/sda2              1052670 27260927 26208258  12,5G             5 Расширенный
/dev/sda5              1052672 27260927 26208256  12,5G            83 Linux


Диск /dev/sdb: 10 GiB, 10737418240 байт, 20971520 секторов
Disk model: QEMU HARDDISK   
Единицы: секторов по 1 * 512 = 512 байт
Размер сектора (логический/физический): 512 байт / 512 байт
Размер I/O (минимальный/оптимальный): 512 байт / 512 байт

root@DonTtouch:/home/dlebedev/GIT/devops-netology# fdisk /dev/sdb

Добро пожаловать в fdisk (util-linux 2.34).
Изменения останутся только в памяти до тех пор, пока вы не решите записать их.
Будьте внимательны, используя команду write.

Устройство не содержит стандартной таблицы разделов.
Создана новая метка DOS с идентификатором 0x7daa0c9c.

Команда (m для справки): n
Тип раздела
   p   основной (0 первичный, 0 расширеный, 4 свободно)
   e   расширенный (контейнер для логических разделов)
Выберите (по умолчанию - p): p
Номер раздела (1-4, по умолчанию 1): 1
Первый сектор (2048-20971519, по умолчанию 2048): 5G
Значение за пределами диапазона.
Первый сектор (2048-20971519, по умолчанию 2048): 
Last sector, +/-sectors or +/-size{K,M,G,T,P} (2048-20971519, по умолчанию 20971519): +2G

Создан новый раздел 1 с типом 'Linux' и размером 2 GiB.

Команда (m для справки): n
Тип раздела
   p   основной (1 первичный, 0 расширеный, 3 свободно)
   e   расширенный (контейнер для логических разделов)
Выберите (по умолчанию - p): p
Номер раздела (2-4, по умолчанию 2): 2
Первый сектор (4196352-20971519, по умолчанию 4196352): 
Last sector, +/-sectors or +/-size{K,M,G,T,P} (4196352-20971519, по умолчанию 20971519): +2G

Создан новый раздел 2 с типом 'Linux' и размером 2 GiB.

Команда (m для справки): w
Таблица разделов была изменена.
Вызывается ioctl() для перечитывания таблицы разделов.
Синхронизируются диски.

Добро пожаловать в sfdisk (util-linux 2.34).
Изменения останутся только в памяти до тех пор, пока вы не решите записать их.
Будьте внимательны, используя команду write.

Проверяется, чтобы сейчас никто не использовал этот диск... ОК

Резервные файлы:
         MBR (смещение     0, размер   512): /root/sfdisk-sdb-0x00000000.bak

Диск /dev/sdb: 10 GiB, 10737418240 байт, 20971520 секторов
Disk model: QEMU HARDDISK   
Единицы: секторов по 1 * 512 = 512 байт
Размер сектора (логический/физический): 512 байт / 512 байт
Размер I/O (минимальный/оптимальный): 512 байт / 512 байт
Тип метки диска: dos
Идентификатор диска: 0x7daa0c9c

Старая ситуация:

Устр-во    Загрузочный  начало   Конец Секторы Размер Идентификатор Тип
/dev/sdb1                 2048 4196351 4194304     2G            83 Linux
/dev/sdb2              4196352 8390655 4194304     2G            83 Linux

Введите `help' для получения дополнительной информации.

>>> write

Новая ситуация:
Тип метки диска: dos
Идентификатор диска: 0x7daa0c9c

Устр-во    Загрузочный  начало   Конец Секторы Размер Идентификатор Тип
/dev/sdb1                 2048 4196351 4194304     2G            83 Linux
/dev/sdb2              4196352 8390655 4194304     2G            83 Linux

Таблица разделов была изменена
Вызывается ioctl() для перечитывания таблицы разделов.
Синхронизируются диски.


root@DonTtouch:/home/dlebedev/GIT/devops-netology# mdadm --create --verbose /dev/md0 -l 1 -n 2 /dev/sd{b1,c1}
mdadm: Note: this array has metadata at the start and
    may not be suitable as a boot device.  If you plan to
    store '/boot' on this device please ensure that
    your boot-loader understands md/v1.x metadata, or use
    --metadata=0.90
mdadm: size set to 2094080K
Continue creating array? yes
mdadm: Defaulting to version 1.2 metadata
mdadm: array /dev/md0 started.
root@DonTtouch:/home/dlebedev/GIT/devops-netology# mdadm --create --verbose /dev/md0 -l 1 -n 2 /dev/sd{b2,c2}
mdadm: Note: this array has metadata at the start and
    may not be suitable as a boot device.  If you plan to
    store '/boot' on this device please ensure that
    your boot-loader understands md/v1.x metadata, or use
    --metadata=0.90
mdadm: size set to 1046528K
Continue creating array? yes
mdadm: Fail create md0 when using /sys/module/md_mod/parameters/new_array
mdadm: /dev/md0 is already in use.
root@DonTtouch:/home/dlebedev/GIT/devops-netology# lsblk
NAME    MAJ:MIN RM   SIZE RO TYPE  MOUNTPOINT
loop0     7:0    0     4K  1 loop  /snap/bare/5
loop1     7:1    0  61,9M  1 loop  /snap/core20/1328
loop2     7:2    0  54,2M  1 loop  /snap/snap-store/558
loop3     7:3    0 248,8M  1 loop  /snap/gnome-3-38-2004/99
loop4     7:4    0  65,2M  1 loop  /snap/gtk-common-themes/1519
loop5     7:5    0  43,6M  1 loop  /snap/snapd/14978
loop6     7:6    0  61,9M  1 loop  /snap/core20/1405
loop7     7:7    0  43,6M  1 loop  /snap/snapd/15177
sda       8:0    0    13G  0 disk  
├─sda1    8:1    0   512M  0 part  /boot/efi
├─sda2    8:2    0     1K  0 part  
└─sda5    8:5    0  12,5G  0 part  /
sdb       8:16   0     5G  0 disk  
├─sdb1    8:17   0     2G  0 part  
│ └─md0   9:0    0     2G  0 raid1 
└─sdb2    8:18   0     1G  0 part  
  └─md1   9:1    0  1022M  0 raid1 
sdc       8:32   0     5G  0 disk  
├─sdc1    8:33   0     2G  0 part  
│ └─md0   9:0    0     2G  0 raid1 
└─sdc2    8:34   0     1G  0 part  
  └─md1   9:1    0  1022M  0 raid1 


root@DonTtouch:/home/dlebedev/GIT/devops-netology# pvcreate /dev/md0 /dev/md1
  Physical volume "/dev/md0" successfully created.
  Physical volume "/dev/md1" successfully created.
root@DonTtouch:/home/dlebedev/GIT/devops-netology# 

root@DonTtouch:/home/dlebedev/GIT/devops-netology# vgcreate vol_group1 /dev/md0 /dev/md1
  Volume group "vol_group1" successfully created
root@DonTtouch:/home/dlebedev/GIT/devops-netology# pvdisplay
  --- Physical volume ---
  PV Name               /dev/md0
  VG Name               vol_group1
  PV Size               <2,00 GiB / not usable 0   
  Allocatable           yes 
  PE Size               4,00 MiB
  Total PE              511
  Free PE               511
  Allocated PE          0
  PV UUID               CWny4G-GfW4-CmuN-8Rpg-1LXG-cqk7-5IQos5
   
  --- Physical volume ---
  PV Name               /dev/md1
  VG Name               vol_group1
  PV Size               1022,00 MiB / not usable 2,00 MiB
  Allocatable           yes 
  PE Size               4,00 MiB
  Total PE              255
  Free PE               255
  Allocated PE          0
  PV UUID               Qml14b-xsbf-Xekw-CX99-llnO-Xc3w-e3jOOE


root@DonTtouch:/home/dlebedev/GIT/devops-netology# lvcreate -L 100M -n logical_vol1 vol_group1 /dev/md1
  Logical volume "logical_vol1" created.
root@DonTtouch:/home/dlebedev/GIT/devops-netology# lvdisplay
  --- Logical volume ---
  LV Path                /dev/vol_group1/logical_vol1
  LV Name                logical_vol1
  VG Name                vol_group1
  LV UUID                EyAXSv-00r0-sksG-chIt-9s2J-Y9s0-pbqLlK
  LV Write Access        read/write
  LV Creation host, time DonTtouch, 2022-04-13 10:33:33 +0300
  LV Status              available
  # open                 0
  LV Size                100,00 MiB
  Current LE             25
  Segments               1
  Allocation             inherit
  Read ahead sectors     auto
  - currently set to     256
  Block device           253:0


root@DonTtouch:/home/dlebedev/GIT/devops-netology# mkfs.ext4 /dev/vol_group1/logical_vol1
mke2fs 1.45.5 (07-Jan-2020)
Discarding device blocks: done                            
Creating filesystem with 25600 4k blocks and 25600 inodes

Allocating group tables: done                            
Сохранение таблицы inod'ов: done                            
Создание журнала (1024 блоков): готово
Writing superblocks and filesystem accounting information: готово


root@DonTtouch:/home/dlebedev/GIT/devops-netology# lsblk -o NAME,PATH,SIZE,FSTYPE
NAME                          PATH                                  SIZE FSTYPE
loop0                         /dev/loop0                              4K squashfs
loop1                         /dev/loop1                           61,9M squashfs
loop2                         /dev/loop2                           54,2M squashfs
loop3                         /dev/loop3                          248,8M squashfs
loop4                         /dev/loop4                           65,2M squashfs
loop5                         /dev/loop5                           43,6M squashfs
loop6                         /dev/loop6                           61,9M squashfs
loop7                         /dev/loop7                           43,6M squashfs
sda                           /dev/sda                               13G 
├─sda1                        /dev/sda1                             512M vfat
├─sda2                        /dev/sda2                               1K 
└─sda5                        /dev/sda5                            12,5G ext4
sdb                           /dev/sdb                                5G 
├─sdb1                        /dev/sdb1                               2G linux_raid_member
│ └─md0                       /dev/md0                                2G LVM2_member
└─sdb2                        /dev/sdb2                               1G linux_raid_member
  └─md1                       /dev/md1                             1022M LVM2_member
    └─vol_group1-logical_vol1 /dev/mapper/vol_group1-logical_vol1   100M ext4
sdc                           /dev/sdc                                5G 
├─sdc1                        /dev/sdc1                               2G linux_raid_member
│ └─md0                       /dev/md0                                2G LVM2_member
└─sdc2                        /dev/sdc2                               1G linux_raid_member
  └─md1                       /dev/md1                             1022M LVM2_member
    └─vol_group1-logical_vol1 /dev/mapper/vol_group1-logical_vol1   100M ext4


root@DonTtouch:/home/dlebedev/GIT/devops-netology# mkdir /tmp/new
root@DonTtouch:/home/dlebedev/GIT/devops-netology# mount /dev/vol_group1/logical_vol1 /tmp/new/


root@DonTtouch:/home/dlebedev/GIT/devops-netology# wget https://mirror.yandex.ru/ubuntu/ls-lR.gz -O /tmp/new/test.gz.
--2022-04-13 10:38:09--  https://mirror.yandex.ru/ubuntu/ls-lR.gz
Распознаётся mirror.yandex.ru (mirror.yandex.ru)… 213.180.204.183, 2a02:6b8::183
Подключение к mirror.yandex.ru (mirror.yandex.ru)|213.180.204.183|:443... соединение установлено.
HTTP-запрос отправлен. Ожидание ответа… 200 OK
Длина: 22395158 (21M) [application/octet-stream]
Сохранение в: «/tmp/new/test.gz.»

/tmp/new/test.gz.                                  100%[================================================================================================================>]  21,36M  3,42MB/s    за 6,3s    

2022-04-13 10:38:17 (3,42 MB/s) - «/tmp/new/test.gz.» сохранён [22395158/22395158]


oot@DonTtouch:/home/dlebedev/GIT/devops-netology# lsblk
NAME                          MAJ:MIN RM   SIZE RO TYPE  MOUNTPOINT
loop0                           7:0    0     4K  1 loop  /snap/bare/5
loop1                           7:1    0  61,9M  1 loop  /snap/core20/1328
loop2                           7:2    0  54,2M  1 loop  /snap/snap-store/558
loop3                           7:3    0 248,8M  1 loop  /snap/gnome-3-38-2004/99
loop4                           7:4    0  65,2M  1 loop  /snap/gtk-common-themes/1519
loop5                           7:5    0  43,6M  1 loop  /snap/snapd/14978
loop6                           7:6    0  61,9M  1 loop  /snap/core20/1405
loop7                           7:7    0  43,6M  1 loop  /snap/snapd/15177
sda                             8:0    0    13G  0 disk  
├─sda1                          8:1    0   512M  0 part  /boot/efi
├─sda2                          8:2    0     1K  0 part  
└─sda5                          8:5    0  12,5G  0 part  /
sdb                             8:16   0     5G  0 disk  
├─sdb1                          8:17   0     2G  0 part  
│ └─md0                         9:0    0     2G  0 raid1 
└─sdb2                          8:18   0     1G  0 part  
  └─md1                         9:1    0  1022M  0 raid1 
    └─vol_group1-logical_vol1 253:0    0   100M  0 lvm   /tmp/new
sdc                             8:32   0     5G  0 disk  
├─sdc1                          8:33   0     2G  0 part  
│ └─md0                         9:0    0     2G  0 raid1 
└─sdc2                          8:34   0     1G  0 part  
  └─md1                         9:1    0  1022M  0 raid1 
    └─vol_group1-logical_vol1 253:0    0   100M  0 lvm   /tmp/new


root@DonTtouch:/home/dlebedev/GIT/devops-netology# gzip -t /tmp/new/test.gz.
root@DonTtouch:/home/dlebedev/GIT/devops-netology# echo $?
0


root@DonTtouch:/home/dlebedev/GIT/devops-netology# pvmove -n /dev/vol_group1/logical_vol1 /dev/md1 /dev/md0
  /dev/md1: Moved: 8,00%
  /dev/md1: Moved: 100,00%


root@DonTtouch:/home/dlebedev/GIT/devops-netology# mdadm /dev/md0 -f /dev/sdc1
mdadm: set /dev/sdc1 faulty in /dev/md0
root@DonTtouch:/home/dlebedev/GIT/devops-netology# mdadm --detail /dev/md0
/dev/md0:
           Version : 1.2
     Creation Time : Wed Apr 13 10:24:37 2022
        Raid Level : raid1
        Array Size : 2094080 (2045.00 MiB 2144.34 MB)
     Used Dev Size : 2094080 (2045.00 MiB 2144.34 MB)
      Raid Devices : 2
     Total Devices : 2
       Persistence : Superblock is persistent

       Update Time : Wed Apr 13 10:43:46 2022
             State : clean, degraded 
    Active Devices : 1
   Working Devices : 1
    Failed Devices : 1
     Spare Devices : 0

Consistency Policy : resync

              Name : DonTtouch:0  (local to host DonTtouch)
              UUID : 4f16712b:0e4440df:301e897b:79e6d643
            Events : 19

    Number   Major   Minor   RaidDevice State
       0       8       17        0      active sync   /dev/sdb1
       -       0        0        1      removed

       1       8       33        -      faulty   /dev/sdc1


md/raid1:md0: Disk failure on sdc1, disabling device.
                md/raid1:md0: Operation continuing on 1 devices.


root@DonTtouch:/home/dlebedev/GIT/devops-netology# gzip -t /tmp/new/test.gz.
root@DonTtouch:/home/dlebedev/GIT/devops-netology# echo $?
0


