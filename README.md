1. системный вызов команды CD -> chdir("/tmp")

2. [root@localhost devops-netology]# file /dev/tty
/dev/tty: character special
[root@localhost devops-netology]# file /dev/sda
/dev/sda: block special
[root@localhost devops-netology]# file /bin/bash
/bin/bash: ELF 64-bit LSB executable, x86-64, version 1 (SYSV), dynamically linked (uses shared libs), for GNU/Linux 2.6.32

[root@localhost devops-netology]# strace file
execve("/usr/bin/file", ["file"], 0x7ffe799be3e0 /* 25 vars */) = 0
open("/usr/lib64/tls/x86_64/libmagic.so.1", O_RDONLY|O_CLOEXEC) = -1 
stat("/usr/lib64/tls/x86_64", 0x7ffe18a09e20) = -1 ENOENT 
open("/usr/lib64/tls/libmagic.so.1", O_RDONLY|O_CLOEXEC) = -1 ENOENT (
stat("/usr/lib64/tls", {st_mode=S_IFDIR|0555, st_size=6, ...}) = 0
open("/usr/lib64/x86_64/libmagic.so.1", O_RDONLY|O_CLOEXEC) = -1 ENOENT 
stat("/usr/lib64/x86_64", 0x7ffe18a09e20) = -1 ENOENT 
open("/usr/lib64/libmagic.so.1", O_RDONLY|O_CLOEXEC) = 3

3. [root@localhost devops-netology]# ps aux | grep nano
root      1724  0.0  0.0 112832   972 pts/0    R+   16:28   0:00 grep --color=auto nano

[root@localhost devops-netology]# lsof -p 1724

[root@localhost devops-netology]# echo '' >/proc/1724

4. Зомби" процессы освобождают свои ресурсы, но не освобождают запись в таблице процессов. Запись освободиться при вызове wait()

5. [root@localhost devops-netology]#~sudo -i
[root@localhost devops-netology]## dpkg -L bpfcc-tools | grep sbin/opensnoop
/usr/sbin/opensnoop-bpfcc
[root@localhost devops-netology]# /usr/sbin/opensnoop-bpfcc
PID    COMM               FD ERR PATH
766    vminfo              6   0 /var/run/utmp
562    dbus-daemon        -1   2 /usr/local/share/dbus-1/system-services
562    dbus-daemon        18   0 /usr/share/dbus-1/system-services
562    dbus-daemon        -1   2 /lib/dbus-1/system-services
562    dbus-daemon        18   0 /var/lib/snapd/dbus-1/system-services/

6.
системный вызов uname()
Part of the utsname information is also accessible  via  /proc/sys/ker‐
       nel/{ostype, hostname, osrelease, version, domainname}.

7.
[root@localhost devops-netology]# test -d /tmp/some_dir; echo Hi
Hi
[root@localhost devops-netology]# test -d /tmp/some_dir && echo Hi
[root@localhost devops-netology]#


&& -  условный оператор, 
а ;  - разделитель последовательных команд

test -d /tmp/some_dir && echo Hi - в данном случае echo  отработает только при успешном заверщении команды test

set -e - прерывает сессию при любом ненулевом значении исполняемых команд в конвеере кроме последней.
в случае &&  вместе с set -e- вероятно не имеет смысла, так как при ошибке , выполнение команд прекратиться


8.
-e прерывает выполнение исполнения при ошибке любой команды кроме последней в последовательности 
-x вывод трейса простых команд 
-u неустановленные/не заданные параметры и переменные считаются как ошибки, с выводом в stderr текста ошибки и выполнит завершение неинтерактивного вызова
-o pipefail возвращает код возврата набора/последовательности команд, ненулевой при последней команды или 0 для успешного выполнения команд.

9.
Самые частые (описание топроное, но по руссски :) ):
S*(S,S+,Ss,Ssl,Ss+) - Процессы ожидающие завершения (спящие с прерыванием "сна")
I*(I,I<) - фоновые(бездействующие) процессы ядра
доп символы это доп характеристики, например приоритет.
