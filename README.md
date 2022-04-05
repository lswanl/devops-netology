1.  Добавляю его в автозагрузку: sudo systemctl enable node_exporter

systemctl status node_exporter
● node_exporter.service - Prometheus exporter for hardware and OS metrics
     Loaded: loaded (/etc/systemd/system/node_exporter.service; enabled; vendor preset: enabled)
     Active: active (running) since Sat 2021-11-27 16:09:43 UTC; 21h ago
       Docs: https://github.com/prometheus/node_exporter/blob/master/README.md
   Main PID: 1341 (node_exporter)
      Tasks: 4 (limit: 1112)
     Memory: 2.3M
     CGroup: /system.slice/node_exporter.service
             └─1341 /home/vagrant/node_exporter-1.3.0.linux-amd64/node_exporter

2.
process_cpu_seconds_total
node_schedstat_waiting_seconds_total
node_pressure_cpu_waiting_seconds_total 
node_memory_Percpu_bytes
node_softnet_dropped_total
node_softnet_processed_total
node_memory_MemAvailable_bytes  
node_memory_MemFree_bytes  
node_memory_MemTotal_bytes
node_memory_SwapCached_bytes  
node_memory_SwapFree_bytes 
node_memory_SwapTotal_bytes  
node_netstat_Tcp_ActiveOpens
node_netstat_Tcp_CurrEstab
node_netstat_Tcp_PassiveOpens
node_network_flags
node_network_iface_id
node_network_iface_link
node_network_mtu_bytes
node_network_receive_bytes_total
node_network_speed_bytes
node_network_transmit_bytes_total
node_network_up
node_disk_io_time_seconds_total
node_disk_read_bytes_total
node_disk_read_time_seconds_total
node_disk_reads_completed_total
node_disk_write_time_seconds_total
node_disk_writes_completed_total
node_disk_written_bytes_total

3.  Установил пакет netdata, apt-install netdata -y
внес изменения в файл /etc/netdata/netdata.conf 

NetData Configuration

# The current full configuration can be retrieved from the running
# server at the URL
#
#   http://localhost:19999/netdata.conf
#
# for example:
#
#   wget -O /etc/netdata/netdata.conf http://localhost:19999/netdata.conf
#

[global]
        run as user = netdata
        web files owner = root
        web files group = root
        # Netdata is not designed to be exposed to potentially hostile
        # networks. See https://github.com/netdata/netdata/issues/164
        bind socket to IP = 0.0.0.0


4.  dmesg > dmesg && cat dmesg | grep virtual*

5.  /sbin/sysctl -n fs.nr_open

6.   root@211273:~# unshare -f --pid --mount-proc sleep 1h
^Z
[1]+  Stopped                 unshare -f --pid --mount-proc sleep 1h
root@211273:~# ps aux
USER         PID %CPU %MEM    VSZ   RSS TTY      STAT START   TIME COMMAND
root           1  0.1  1.0 167080 10884 ?        Ss   09:48   0:01 /sbin/init
root           2  0.0  0.0      0     0 ?        S    09:48   0:00 [kthreadd]
root           3  0.0  0.0      0     0 ?        I<   09:48   0:00 [rcu_gp]
root           4  0.0  0.0      0     0 ?        I<   09:48   0:00 [rcu_par_gp]
root           5  0.0  0.0      0     0 ?        I    09:48   0:00 [kworker/0:0-cgroup_destroy]
root           6  0.0  0.0      0     0 ?        I<   09:48   0:00 [kworker/0:0H-kblockd]
root           8  0.0  0.0      0     0 ?        I<   09:48   0:00 [mm_percpu_wq]
root           9  0.0  0.0      0     0 ?        S    09:48   0:00 [ksoftirqd/0]
root          10  0.0  0.0      0     0 ?        I    09:48   0:00 [rcu_sched]
root          11  0.0  0.0      0     0 ?        S    09:48   0:00 [migration/0]
root          12  0.0  0.0      0     0 ?        S    09:48   0:00 [idle_inject/0]
root          14  0.0  0.0      0     0 ?        S    09:48   0:00 [cpuhp/0]
root          15  0.0  0.0      0     0 ?        S    09:48   0:00 [kdevtmpfs]
root          16  0.0  0.0      0     0 ?        I<   09:48   0:00 [netns]
root          17  0.0  0.0      0     0 ?        S    09:48   0:00 [rcu_tasks_kthre]
root          18  0.0  0.0      0     0 ?        S    09:48   0:00 [kauditd]
root          19  0.0  0.0      0     0 ?        S    09:48   0:00 [khungtaskd]
root          20  0.0  0.0      0     0 ?        S    09:48   0:00 [oom_reaper]
root          21  0.0  0.0      0     0 ?        I<   09:48   0:00 [writeback]
root          22  0.0  0.0      0     0 ?        S    09:48   0:00 [kcompactd0]
root          23  0.0  0.0      0     0 ?        SN   09:48   0:00 [ksmd]
root          24  0.0  0.0      0     0 ?        SN   09:48   0:00 [khugepaged]
root          70  0.0  0.0      0     0 ?        I<   09:48   0:00 [kintegrityd]
root          71  0.0  0.0      0     0 ?        I<   09:48   0:00 [kblockd]
root          72  0.0  0.0      0     0 ?        I<   09:48   0:00 [blkcg_punt_bio]
root          73  0.0  0.0      0     0 ?        I<   09:48   0:00 [tpm_dev_wq]
root          74  0.0  0.0      0     0 ?        I<   09:48   0:00 [ata_sff]
root          75  0.0  0.0      0     0 ?        I<   09:48   0:00 [md]
root          76  0.0  0.0      0     0 ?        I<   09:48   0:00 [edac-poller]
root          77  0.0  0.0      0     0 ?        I<   09:48   0:00 [devfreq_wq]
root          78  0.0  0.0      0     0 ?        S    09:48   0:00 [watchdogd]
root          80  0.0  0.0      0     0 ?        S    09:48   0:00 [kswapd0]
root          81  0.0  0.0      0     0 ?        S    09:48   0:00 [ecryptfs-kthrea]
root          83  0.0  0.0      0     0 ?        I<   09:48   0:00 [kthrotld]
root          84  0.0  0.0      0     0 ?        I<   09:48   0:00 [acpi_thermal_pm]
root          85  0.0  0.0      0     0 ?        S    09:48   0:00 [scsi_eh_0]
root          86  0.0  0.0      0     0 ?        I<   09:48   0:00 [scsi_tmf_0]
root          87  0.0  0.0      0     0 ?        S    09:48   0:00 [scsi_eh_1]
root          88  0.0  0.0      0     0 ?        I<   09:48   0:00 [scsi_tmf_1]
root          90  0.0  0.0      0     0 ?        I<   09:48   0:00 [vfio-irqfd-clea]
root          91  0.0  0.0      0     0 ?        I    09:48   0:00 [kworker/u2:3-events_power_efficient]
root          92  0.0  0.0      0     0 ?        I<   09:48   0:00 [ipv6_addrconf]
root         101  0.0  0.0      0     0 ?        I<   09:48   0:00 [kstrp]
root         104  0.0  0.0      0     0 ?        I<   09:48   0:00 [kworker/u3:0]
root         114  0.0  0.0      0     0 ?        I<   09:48   0:00 [kworker/0:1H-kblockd]
root         118  0.0  0.0      0     0 ?        I<   09:48   0:00 [charger_manager]
root         172  0.0  0.0      0     0 ?        I<   09:48   0:00 [ttm_swap]
root         194  0.0  0.0      0     0 ?        I<   09:48   0:00 [raid5wq]
root         237  0.0  0.0      0     0 ?        S    09:48   0:00 [jbd2/vda1-8]
root         238  0.0  0.0      0     0 ?        I<   09:48   0:00 [ext4-rsv-conver]
root         292  0.0  2.7  84216 27152 ?        S<s  09:49   0:00 /lib/systemd/systemd-journald
root         311  0.0  0.0   2488   516 ?        S    09:49   0:00 bpfilter_umh
root         324  0.0  0.0      0     0 ?        I<   09:49   0:00 [ipmi-msghandler]
root         345  0.0  0.5  21520  5400 ?        Ss   09:49   0:00 /lib/systemd/systemd-udevd
root         486  0.0  0.0      0     0 ?        I<   09:49   0:00 [kaluad]
root         487  0.0  0.0      0     0 ?        I<   09:49   0:00 [kmpath_rdacd]
root         488  0.0  0.0      0     0 ?        I<   09:49   0:00 [kmpathd]
root         489  0.0  0.0      0     0 ?        I<   09:49   0:00 [kmpath_handlerd]
root         490  0.0  1.7 214660 17996 ?        SLsl 09:49   0:00 /sbin/multipathd -d -s
systemd+     512  0.0  0.6  90188  6004 ?        Ssl  09:49   0:00 /lib/systemd/systemd-timesyncd
root         539  0.0  0.7 235560  7296 ?        Ssl  09:49   0:00 /usr/lib/accountsservice/accounts-daemon
message+     540  0.0  0.4   7504  4404 ?        Ss   09:49   0:00 /usr/bin/dbus-daemon --system --address=systemd: --nofork --nopidfile --systemd-activation --syslog-only
root         545  0.0  0.6 232712  6696 ?        Ssl  09:49   0:00 /usr/lib/policykit-1/polkitd --no-debug
root         546  0.0  0.3  80176  3380 ?        Ssl  09:49   0:00 /usr/sbin/qemu-ga
syslog       548  0.0  0.4 224316  4752 ?        Ssl  09:49   0:00 /usr/sbin/rsyslogd -n -iNONE
root         549  0.0  0.7  16616  7512 ?        Ss   09:49   0:00 /lib/systemd/systemd-logind
root         550  0.0  1.1 392360 11964 ?        Ssl  09:49   0:00 /usr/lib/udisks2/udisksd
root         574  0.0  1.0 314460 10852 ?        Ssl  09:49   0:00 /usr/sbin/ModemManager
netdata      716  0.9  3.1 185956 31160 ?        Ssl  09:49   0:12 /usr/sbin/netdata -D
root         721  0.0  0.2   6812  2952 ?        Ss   09:49   0:00 /usr/sbin/cron -f
root         724  0.0  2.0 107904 20352 ?        Ssl  09:49   0:00 /usr/bin/python3 /usr/share/unattended-upgrades/unattended-upgrade-shutdown --wait-for-signal
daemon       726  0.0  0.2   3792  2292 ?        Ss   09:49   0:00 /usr/sbin/atd -f
root         727  0.0  4.3 1270148 43244 ?       Ssl  09:49   0:01 /usr/bin/containerd
root         730  0.0  0.2   5600  2176 ttyS0    Ss+  09:49   0:00 /sbin/agetty -n -l /bin/bash -h -w -L ttyS0 115200 vt100
root         734  0.0  0.1   5828  1668 tty1     Ss+  09:49   0:00 /sbin/agetty -o -p -- \u --noclear tty1 linux
root         739  0.0  0.7  12172  7332 ?        Ss   09:49   0:00 sshd: /usr/sbin/sshd -D [listener] 0 of 10-100 startups
root         755  0.0  7.7 1381512 77060 ?       Ssl  09:49   0:00 /usr/bin/dockerd -H fd:// --containerd=/run/containerd/containerd.sock
root         932  0.0  0.8 711024  8560 ?        Sl   09:49   0:00 /usr/bin/containerd-shim-runc-v2 -namespace moby -id c48e35b35d520f95b83936e07b5561c6403523588b5f9bfec5a065df289c2edb -address 
/run/conta
root         954  0.0  1.4 717088 14132 ?        Ssl  09:49   0:00 /watchtower --cleanup --label-enable --tlsverify --interval 3600
root         969  0.0  0.8 711024  8120 ?        Sl   09:49   0:00 /usr/bin/containerd-shim-runc-v2 -namespace moby -id 14fbfa2311f97431e17f006a3338e53e566197a1d879ad70324cf4017e39343b -address 
/run/conta
netdata      985  0.0  0.3   4028  3028 ?        S    09:49   0:00 bash /usr/lib/netdata/plugins.d/tc-qos-helper.sh 1
netdata     1001  0.0  0.0   4608   696 ?        S    09:49   0:00 /usr/lib/netdata/plugins.d/nfacct.plugin 1
netdata     1002  0.8  0.3  53184  3196 ?        S    09:49   0:10 /usr/lib/netdata/plugins.d/apps.plugin 1
root        1008  0.0  0.0   1572     4 ?        Ss   09:49   0:00 /bin/sh /cmd.sh
root        1080  0.0  0.0   1572    44 ?        Ss   09:49   0:00 crond
root        1081  0.0  4.9 272236 49916 ?        Sl   09:49   0:00 node app/main.js
root        1149  0.0  7.2 768604 72380 ?        SLl  09:49   0:01 /opt/outline-server/bin/prometheus --config.file /opt/outline/persisted-state/prometheus/config.yml --web.enable-admin-api 
--storage.tsdb
root        1280  0.0  0.0      0     0 ?        I<   09:49   0:00 [cfg80211]
root        1329  0.1  1.3 718280 13640 ?        SLl  09:49   0:01 /opt/outline-server/bin/outline-ss-server -config /opt/outline/persisted-state/outline-ss-server/config.yml -metrics 127.0.0.1:9092 
-ip_c
root        1469  0.0  0.8  13892  8780 ?        Ss   09:50   0:00 sshd: root@pts/0
root        1478  0.0  0.9  18236  9332 ?        Ss   09:50   0:00 /lib/systemd/systemd --user
root        1484  0.0  0.3 168436  3120 ?        S    09:50   0:00 (sd-pam)
root        1584  0.0  0.4   8176  4960 pts/0    Ss   09:50   0:00 -bash
root        1683  0.0  0.4   9408  4704 pts/0    S    09:59   0:00 sudo -i
root        1685  0.0  0.4   8260  4992 pts/0    S    09:59   0:00 -bash
root        1695  0.0  0.0   5476   584 pts/0    S    09:59   0:00 sleep 1h
root        1712  0.0  0.0      0     0 ?        I    10:02   0:00 [kworker/u2:0-events_power_efficient]
root        1734  0.0  0.0      0     0 ?        I    10:04   0:00 [kworker/0:1-events]
root        1793  0.0  0.0      0     0 ?        I    10:08   0:00 [kworker/u2:1-events_unbound]
root        1804  0.0  0.0   5480   516 pts/0    T    10:09   0:00 unshare -f --pid --mount-proc sleep 1h
root        1805  0.0  0.0   5476   580 pts/0    S    10:09   0:00 sleep 1h
root        1813  0.0  0.3   8888  3260 pts/0    R+   10:10   0:00 ps aux

root@211273:~# ps aux | grep sleep
root        1695  0.0  0.0   5476   584 pts/0    S    09:59   0:00 sleep 1h
root        1804  0.0  0.0   5480   516 pts/0    T    10:09   0:00 unshare -f --pid --mount-proc sleep 1h
root        1805  0.0  0.0   5476   580 pts/0    S    10:09   0:00 sleep 1h
root        1823  0.0  0.0   6432   720 pts/0    S+   10:12   0:00 grep --color=auto sleep

root@211273:~# nsenter -t 1805 -p -m
root@211273:/# ps
    PID TTY          TIME CMD
      1 pts/0    00:00:00 sleep
      2 pts/0    00:00:00 bash
     11 pts/0    00:00:00 ps


7.  Это т.называемая fork bomb - функция fork рекурсивно вызывающая сама себя до тех пор пока не забьёт все ресурсы системы


