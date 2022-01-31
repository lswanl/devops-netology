1. Это команда встройенная, меняет указатель на текущую дерикторию внутренней функцией
можно сделать CD внешней программой, но после смены деректории необходимо вызвать bash, но тогда мы получим новый shell.

2.
root@Mytest:/home/ldywa# cat test
123123
123123123
123123123123
123123123123123
1231231231231231
qwe

root@Mytest:/home/ldywa# grep qwe test -c
1
root@Mytest:/home/ldywa# grep qwe test -c |wc -l
1

3.  systemd

systemd(1)─┬─agetty(350)
           ├─cron(327)
           ├─dbus-daemon(331)
           ├─dhclient(330)
           ├─exim4(27447)
           ├─rpc.idmapd(27127)
           ├─rpc.mountd(27128)
           ├─rpcbind(26516)
           ├─rsyslogd(337)─┬─{rsyslogd}(342)
           │               ├─{rsyslogd}(343)
           │               └─{rsyslogd}(346)
           ├─sshd(356)───sshd(19728)───sshd(19748)───bash(19749)───su(19752)───bash(19753)───pstree(19971)
           ├─systemd(19732)───(sd-pam)(19733)
           ├─systemd-journal(201)
           ├─systemd-logind(336)
           ├─systemd-timesyn(260)───{systemd-timesyn}(316)
           └─systemd-udevd(218)


4. ls -l \root 2>/dev/pts/1

5.
root@Mytest:/home/ldywa# cat test
123123
123123123
123123123123
123123123123123
1231231231231231
qwe
111111
new line
root@Mytest:/home/ldywa# cat test_out
root@Mytest:/home/ldywa# cat <tst >test_out
bash: tst: Нет такого файла или каталога
root@Mytest:/home/ldywa# cat <test >test_out
root@Mytest:/home/ldywa# cat test_out
123123
123123123
123123123123
123123123123123
1231231231231231
qwe
111111
new line

root@Mytest:/home/ldywa#


6.Вывести полуится при использовании перенаправлении вывода, но наблюдать в графическом режиме не получиться.

7. 
bash 5>&1 - Создаст дескриптор с 5 и перенатправит его в stdout
echo netology > /proc/$$/fd/5 - выведет в дескриптор "5", который был пернеаправлен в stdout

8.

ls -l /root 9>&2 2>&1 1>&9 |grep denied -c
1


9.

переменные окружения

printenv
env

10.


/proc/<PID>/cmdline - полный путь до исполняемого файла процесса [PID]
/proc/<PID>/exe - содержит ссылку до файла запущенного для процесса [PID]

11.

SSE 4.2

12.

при подключении ожидается пользователь, а не другой процесс
добавить -t - , команда исполняется c принудительным созданием псевдотерминала

13.

заначения  kernel.yama.ptrace_scope = 0

14.

tee делает вывод одновременно и в файл, указаный в качестве параметра, и в stdout
команда получает вывод из stdin, перенаправленный через pipe от stdout команды echo
так как команда запущена от sudo , то имеет права на запись в файл
