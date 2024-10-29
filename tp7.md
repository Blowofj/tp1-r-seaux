Lister les ports en écoute sur la machine
```
[root@webLan ~]# sudo ss -lnpt | grep 80
LISTEN 0      511          0.0.0.0:80        0.0.0.0:*    users:(("nginx",pid=1580,fd=6),("nginx",pid=1579,fd=6))
LISTEN 0      511             [::]:80           [::]:*    users:(("nginx",pid=1580,fd=7),("nginx",pid=1579,fd=7))
```

 Ouvrir le port dans le firewall de la machine
```
[root@webLan ~]# firewall-cmd --permanent --add-port=80/tcp
success
[root@webLan ~]# sudo firewall-cmd --reload
success
[root@webLan ~]# sudo firewall-cmd --list-all
public (active)
  target: default
  icmp-block-inversion: no
  interfaces: enp0s3
  sources:
  services: cockpit dhcpv6-client ssh
  ports: 80/tcp
  protocols:
  forward: yes
  masquerade: no
  forward-ports:
  source-ports:
  icmp-blocks:
  rich rules:
```

Vérifier que ça a pris effet
```
[root@webLan ~]# ping sitedefou.tp7.b1
PING sitedefou.tp7.b1 (10.7.1.11) 56(84) bytes of data.
64 bytes from sitedefou.tp7.b1 (10.7.1.11): icmp_seq=1 ttl=64 time=0.037 ms
64 bytes from sitedefou.tp7.b1 (10.7.1.11): icmp_seq=2 ttl=64 time=0.069 ms
64 bytes from sitedefou.tp7.b1 (10.7.1.11): icmp_seq=3 ttl=64 time=0.078 ms
^C
--- sitedefou.tp7.b1 ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2084ms
rtt min/avg/max/mdev = 0.037/0.061/0.078/0.017 ms
[root@webLan ~]# curl sitedefou.tp7.b1
meow !
```

 Capture tcp_http.pcap : bon bah voir la capture fichier tcp_http.pcap

 Voir la connexion établie

 ```
PS C:\Windows\system32> netstat -a -n -b

Active Connections

   TCP    10.7.1.1:57879         10.7.1.11:80           ESTABLISHED
 [firefox.exe]
 ```

 Lister les ports en écoute sur la machine
```
[root@webLan /]# ss -lnpt | grep 443
LISTEN 0      511        10.7.1.11:443       0.0.0.0:*    users:(("nginx",pid=1624,fd=6),("nginx",pid=1623,fd=6))
```

Gérer le firewall
```
[root@webLan /]# firewall-cmd --permanent --remove-port=80/tcp
success
[root@webLan /]# firewall-cmd --permanent --add-port=443/tcp
success
[root@webLan /]# firewall-cmd --reload
success
[root@webLan /]# firewall-cmd --list-all
public (active)
  target: default
  icmp-block-inversion: no
  interfaces: enp0s3
  sources:
  services: cockpit dhcpv6-client ssh
  ports: 443/tcp
  protocols:
  forward: yes
  masquerade: no
  forward-ports:
  source-ports:
  icmp-blocks:
  rich rules:
```

Capture tcp_https.pcap : voir fichier tcp_https

Prouvez que vous avez bien une nouvelle carte réseau wg0

```
[root@VPN ~]# ip a
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default qlen 1000
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
    inet 127.0.0.1/8 scope host lo
       valid_lft forever preferred_lft forever
    inet6 ::1/128 scope host
       valid_lft forever preferred_lft forever
2: enp0s3: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc fq_codel state UP group default qlen 1000
    link/ether 08:00:27:4f:2a:4a brd ff:ff:ff:ff:ff:ff
    inet 10.7.1.111/24 brd 10.7.1.255 scope global noprefixroute enp0s3
       valid_lft forever preferred_lft forever
    inet6 fe80::a00:27ff:fe4f:2a4a/64 scope link
       valid_lft forever preferred_lft forever
3: enp0s8: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc fq_codel state UP group default qlen 1000
    link/ether 08:00:27:fc:96:1e brd ff:ff:ff:ff:ff:ff
    inet 10.7.2.111/24 brd 10.7.2.255 scope global noprefixroute enp0s8
       valid_lft forever preferred_lft forever
    inet6 fe80::a00:27ff:fefc:961e/64 scope link
       valid_lft forever preferred_lft forever
4: wg0: <POINTOPOINT,NOARP,UP,LOWER_UP> mtu 1420 qdisc noqueue state UNKNOWN group default qlen 1000
    link/none
    inet 10.7.200.1/24 scope global wg0
       valid_lft forever preferred_lft forever
```

 Déterminer sur quel port écoute Wireguard

 ```
 [root@VPN ~]# ss -lun
State    Recv-Q    Send-Q       Local Address:Port        Peer Address:Port   Process
UNCONN   0         0                127.0.0.1:323              0.0.0.0:*
UNCONN   0         0                  0.0.0.0:51820            0.0.0.0:*
UNCONN   0         0                    [::1]:323                 [::]:*
UNCONN   0         0                     [::]:51820               [::]:*
 ```

  Ouvrez ce port dans le firewall
  ```
  [root@VPN ~]# firewall-cmd --permanent --add-port=51820/tcp
success
[root@VPN ~]# firewall-cmd --reload
success
[root@VPN ~]# firewall-cmd --list-all
public (active)
  target: default
  icmp-block-inversion: no
  interfaces: enp0s3 enp0s8
  sources:
  services: cockpit dhcpv6-client ssh
  ports: 22/tcp 51820/ucp
  protocols:
  forward: yes
  masquerade: no
  forward-ports:
  source-ports:
  icmp-blocks:
  rich rules:
  ```

   Ping ping ping !
   ```
   [root@Client1 ~]# ping 10.7.200.1
PING 10.7.200.1 (10.7.200.1) 56(84) bytes of data.
64 bytes from 10.7.200.1: icmp_seq=1 ttl=64 time=2.71 ms
64 bytes from 10.7.200.1: icmp_seq=2 ttl=64 time=2.39 ms
64 bytes from 10.7.200.1: icmp_seq=3 ttl=64 time=2.66 ms
64 bytes from 10.7.200.1: icmp_seq=4 ttl=64 time=2.94 ms
^C
--- 10.7.200.1 ping statistics ---
4 packets transmitted, 4 received, 0% packet loss, time 3008ms
rtt min/avg/max/mdev = 2.394/2.675/2.941/0.194 ms
   ```

Capture ping1_vpn.pcap

Capture ping2_vpn.pcap

Prouvez que vous avez toujours un accès internet
```
[root@Client1 ~]# traceroute 1.1.1.1
traceroute to 1.1.1.1 (1.1.1.1), 30 hops max, 60 byte packets
 1  _gateway (10.7.200.1)  3.784 ms  18.806 ms  20.098 ms
 2  * * *
 3  10.0.3.2 (10.0.3.2)  38.049 ms  48.738 ms  48.731 ms
 4  10.0.3.2 (10.0.3.2)  48.706 ms  48.695 ms  48.664 ms
```

Visitez le service Web à travers le VPN
```
[root@Client1 ~]# curl -k https://sitedefou.tp7.b1
meow !
```