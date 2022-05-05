1. 
	route-views>show ip route 1.187.64.0/24
                                    ^
% Invalid input detected at '^' marker.

route-views>show ip route 1.187.64.0   
Routing entry for 1.187.64.0/20
  Known via "bgp 6447", distance 20, metric 0
  Tag 6939, type external
  Last update from 64.71.137.241 1w2d ago
  Routing Descriptor Blocks:
  * 64.71.137.241, from 64.71.137.241, 1w2d ago
      Route metric is 0, traffic share count is 1
      AS Hops 4
      Route tag 6939
      MPLS label: none


route-views>show bgp 1.187.64.0     
BGP routing table entry for 1.187.64.0/20, version 2037340792
Paths: (24 available, best #24, table default)
  Not advertised to any peer
  Refresh Epoch 1
  53767 174 55644 45271
    162.251.163.2 from 162.251.163.2 (162.251.162.3)
      Origin IGP, localpref 100, valid, external
      Community: 174:21101 174:22008 53767:5000
      path 7FE103DEFCB8 RPKI State not found
      rx pathid: 0, tx pathid: 0
  Refresh Epoch 1
  20912 3257 174 55644 45271
    212.66.96.126 from 212.66.96.126 (212.66.96.126)
      Origin IGP, localpref 100, valid, external
      Community: 3257:8070 3257:30155 3257:50001 3257:53900 3257:53902 20912:65004
      path 7FE139FF75C8 RPKI State not found
      rx pathid: 0, tx pathid: 0
  Refresh Epoch 1
  3561 209 3356 3491 55644 45271
    206.24.210.80 from 206.24.210.80 (206.24.210.80)
      Origin IGP, localpref 100, valid, external
      path 7FE021DE67F8 RPKI State not found
      rx pathid: 0, tx pathid: 0
  Refresh Epoch 1
  701 1273 55644 45271
    137.39.3.55 from 137.39.3.55 (137.39.3.55)
      Origin IGP, localpref 100, valid, external
      path 7FE03D1BB6A8 RPKI State not found
      rx pathid: 0, tx pathid: 0
  Refresh Epoch 1
  8283 3491 55644 45271
    94.142.247.3 from 94.142.247.3 (94.142.247.3)
      Origin IGP, metric 0, localpref 100, valid, external
      Community: 3491:400 3491:403 3491:9001 3491:9080 3491:9081 3491:9087 3491:62210 3491:62220 8283:1 8283:101
      unknown transitive attribute: flag 0xE0 type 0x20 length 0x18
        value 0000 205B 0000 0000 0000 0001 0000 205B
              0000 0005 0000 0001 
      path 7FE11BBA1FF8 RPKI State not found
      rx pathid: 0, tx pathid: 0
  Refresh Epoch 1
  3549 3356 3491 55644 45271
    208.51.134.254 from 208.51.134.254 (67.16.168.191)
      Origin IGP, metric 0, localpref 100, valid, external
      Community: 3356:3 3356:22 3356:86 3356:575 3356:666 3356:903 3356:2011 3491:400 3491:403 3491:9001 3491:9080 3491:9081 3491:9087 3491:62210 3491:62220 3549:2581 3549:30840
      path 7FE10A3D1C70 RPKI State not found
      rx pathid: 0, tx pathid: 0
  Refresh Epoch 1
  3356 174 55644 45271
    4.68.4.46 from 4.68.4.46 (4.69.184.201)
      Origin IGP, metric 0, localpref 100, valid, external
      Community: 3356:3 3356:22 3356:86 3356:575 3356:666 3356:903 3356:2012
      path 7FE16A008E68 RPKI State not found
      rx pathid: 0, tx pathid: 0
  Refresh Epoch 1
  3267 1299 1273 55644 45271
    194.85.40.15 from 194.85.40.15 (185.141.126.1)
      Origin IGP, metric 0, localpref 100, valid, external
      path 7FE119AF2EE8 RPKI State not found
      rx pathid: 0, tx pathid: 0
  Refresh Epoch 1
  49788 174 55644 45271



2.
	root@DonTtouch:/# ip link add dummy0 type dummy
root@DonTtouch:/# sudo ip addr add 192.168.5.0/24 dev dummy0
root@DonTtouch:/# sudo ip link set dummy0 up
root@DonTtouch:/# ip address
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
7: dummy0: <BROADCAST,NOARP,UP,LOWER_UP> mtu 1500 qdisc noqueue state UNKNOWN group default qlen 1000
    link/ether da:5a:54:c2:61:95 brd ff:ff:ff:ff:ff:ff
    inet 192.168.5.0/24 scope global dummy0
       valid_lft forever preferred_lft forever
    inet6 fe80::d85a:54ff:fec2:6195/64 scope link 
       valid_lft forever preferred_lft forever


root@DonTtouch:/# ip route add 192.168.2.0/24 via 192.168.5.0
root@DonTtouch:/# ip route
default via 192.168.2.57 dev ens18 proto static metric 100 
10.0.0.0/24 dev ens18.5 proto kernel scope link src 10.0.0.9 
169.254.0.0/16 dev ens18 scope link metric 1000 
192.168.2.0/24 via 192.168.5.0 dev dummy0 
192.168.2.0/24 dev ens18 proto kernel scope link src 192.168.2.250 metric 100 
192.168.5.0/24 dev dummy0 proto kernel scope link src 192.168.5.0 



3.
	root@DonTtouch:/# ss -tpan
State            Recv-Q           Send-Q                     Local Address:Port                        Peer Address:Port            Process                                                                 
LISTEN           0                64                               0.0.0.0:45007                            0.0.0.0:*                                                                                       
LISTEN           0                4096                             0.0.0.0:111                              0.0.0.0:*                users:(("rpcbind",pid=203837,fd=4),("systemd",pid=1,fd=263))           
LISTEN           0                4096                             0.0.0.0:49521                            0.0.0.0:*                users:(("rpc.mountd",pid=204478,fd=17))                                
LISTEN           0                4096                       127.0.0.53%lo:53                               0.0.0.0:*                users:(("systemd-resolve",pid=392159,fd=13))                           
LISTEN           0                128                              0.0.0.0:22                               0.0.0.0:*                users:(("sshd",pid=3817,fd=3))                                         
LISTEN           0                5                              127.0.0.1:631                              0.0.0.0:*                users:(("cupsd",pid=894605,fd=7))                                      
LISTEN           0                4096                             0.0.0.0:41435                            0.0.0.0:*                users:(("rpc.mountd",pid=204478,fd=9))                                 
LISTEN           0                4096                             0.0.0.0:34559                            0.0.0.0:*                users:(("rpc.mountd",pid=204478,fd=13))                                
LISTEN           0                64                               0.0.0.0:2049                             0.0.0.0:*                                                                                       
ESTAB            0                36                         192.168.2.250:22                         83.69.192.100:59282            users:(("sshd",pid=908263,fd=4))                                       
LISTEN           0                4096                                [::]:33997                               [::]:*                users:(("rpc.mountd",pid=204478,fd=11))                                
LISTEN           0                4096                                [::]:111                                 [::]:*                users:(("rpcbind",pid=203837,fd=6),("systemd",pid=1,fd=265))           
LISTEN           0                4096                                [::]:43445                               [::]:*                users:(("rpc.mountd",pid=204478,fd=19))                                
LISTEN           0                128                                 [::]:22                                  [::]:*                users:(("sshd",pid=3817,fd=4))                                         
LISTEN           0                5                                  [::1]:631                                 [::]:*                users:(("cupsd",pid=894605,fd=6))                                      
LISTEN           0                64                                  [::]:45279                               [::]:*                                                                                       
LISTEN           0                64                                  [::]:2049                                [::]:*                                                                                       
LISTEN           0                4096                                [::]:59811                               [::]:*                users:(("rpc.mountd",pid=204478,fd=15))     


22-tcp,udp SSH
111-tcp,udp RPC
53-tcp,udp DNS

4.
	root@DonTtouch:/# ss -upan
State            Recv-Q           Send-Q                      Local Address:Port                        Peer Address:Port           Process                                                                 
UNCONN           0                0                                 0.0.0.0:631                              0.0.0.0:*               users:(("cups-browsed",pid=894606,fd=7))                               
UNCONN           0                0                                 0.0.0.0:59053                            0.0.0.0:*               users:(("rpc.mountd",pid=204478,fd=16))                                
UNCONN           0                0                                 0.0.0.0:57122                            0.0.0.0:*               users:(("avahi-daemon",pid=456,fd=14))                                 
UNCONN           0                0                                 0.0.0.0:46903                            0.0.0.0:*                                                                                      
UNCONN           0                0                                 0.0.0.0:2049                             0.0.0.0:*                                                                                      
UNCONN           0                0                           127.0.0.53%lo:53                               0.0.0.0:*               users:(("systemd-resolve",pid=392159,fd=12))                           
UNCONN           0                0                                 0.0.0.0:111                              0.0.0.0:*               users:(("rpcbind",pid=203837,fd=5),("systemd",pid=1,fd=264))           
UNCONN           0                0                                 0.0.0.0:34023                            0.0.0.0:*               users:(("rpc.mountd",pid=204478,fd=12))                                
UNCONN           0                0                                 0.0.0.0:5353                             0.0.0.0:*               users:(("avahi-daemon",pid=456,fd=12))                                 
UNCONN           0                0                                 0.0.0.0:57622                            0.0.0.0:*               users:(("rpc.mountd",pid=204478,fd=8))                                 
UNCONN           0                0                                    [::]:48641                               [::]:*               users:(("rpc.mountd",pid=204478,fd=18))                                
UNCONN           0                0                                    [::]:35329                               [::]:*               users:(("rpc.mountd",pid=204478,fd=10))                                
UNCONN           0                0                                    [::]:35504                               [::]:*               users:(("rpc.mountd",pid=204478,fd=14))                                
UNCONN           0                0                                    [::]:53037                               [::]:*                                                                                      
UNCONN           0                0                                    [::]:2049                                [::]:*                                                                                      
UNCONN           0                0                                    [::]:37957                               [::]:*               users:(("avahi-daemon",pid=456,fd=15))                                 
UNCONN           0                0                                    [::]:111                                 [::]:*               users:(("rpcbind",pid=203837,fd=7),("systemd",pid=1,fd=277))           
UNCONN           0                0                                    [::]:5353                                [::]:*               users:(("avahi-daemon",pid=456,fd=13))                                 


5.
	
