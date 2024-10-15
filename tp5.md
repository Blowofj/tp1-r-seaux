tp 5 
ip configuré :
```
PS C:\Windows\system32> ipconfig

Ethernet adapter Ethernet 3:

   Connection-specific DNS Suffix  . :
   Link-local IPv6 Address . . . . . : fe80::e471:adec:e49a:655c%58
   IPv4 Address. . . . . . . . . . . : 10.5.1.1
   Subnet Mask . . . . . . . . . . . : 255.255.255.0
   Default Gateway . . . . . . . . . :
```
```
[root@Client1 ~]# ip a
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default qlen 1000
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
    inet 127.0.0.1/8 scope host lo
       valid_lft forever preferred_lft forever
    inet6 ::1/128 scope host
       valid_lft forever preferred_lft forever
2: enp0s3: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc fq_codel state UP group default qlen 1000
    link/ether 08:00:27:81:31:d4 brd ff:ff:ff:ff:ff:ff
    inet 10.5.1.11/24 brd 10.5.1.255 scope global noprefixroute enp0s3
       valid_lft forever preferred_lft forever
    inet6 fe80::a00:27ff:fe81:31d4/64 scope link
       valid_lft forever preferred_lft forever

[root@Client2 ~]# ip a
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default qlen 1000
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
    inet 127.0.0.1/8 scope host lo
       valid_lft forever preferred_lft forever
    inet6 ::1/128 scope host
       valid_lft forever preferred_lft forever
2: enp0s3: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc fq_codel state UP group default qlen 1000
    link/ether 08:00:27:b2:20:d8 brd ff:ff:ff:ff:ff:ff
    inet 10.5.1.12/24 brd 10.5.1.255 scope global noprefixroute enp0s3
       valid_lft forever preferred_lft forever
    inet6 fe80::a00:27ff:feb2:20d8/64 scope link
       valid_lft forever preferred_lft forever

[root@routeur ~]# ip a
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default qlen 1000
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
    inet 127.0.0.1/8 scope host lo
       valid_lft forever preferred_lft forever
    inet6 ::1/128 scope host
       valid_lft forever preferred_lft forever
2: enp0s3: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc fq_codel state UP group default qlen 1000
    link/ether 08:00:27:fc:55:2c brd ff:ff:ff:ff:ff:ff
    inet 10.5.1.254/24 brd 10.5.1.255 scope global noprefixroute enp0s3
       valid_lft forever preferred_lft forever
    inet6 fe80::a00:27ff:fefc:552c/64 scope link
       valid_lft forever preferred_lft forever
3: enp0s8: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc fq_codel state UP group default qlen 1000
    link/ether 08:00:27:56:8c:45 brd ff:ff:ff:ff:ff:ff
    inet 10.0.3.15/24 brd 10.0.3.255 scope global dynamic noprefixroute enp0s8
       valid_lft 84763sec preferred_lft 84763sec
    inet6 fe80::d3ec:aa00:308:5d00/64 scope link noprefixroute
       valid_lft forever preferred_lft forever
```
ping :
```
[root@routeur ~]# ping 10.5.1.1
PING 10.5.1.1 (10.5.1.1) 56(84) bytes of data.
64 bytes from 10.5.1.1: icmp_seq=1 ttl=128 time=0.337 ms
64 bytes from 10.5.1.1: icmp_seq=2 ttl=128 time=0.272 ms
64 bytes from 10.5.1.1: icmp_seq=3 ttl=128 time=0.321 ms
64 bytes from 10.5.1.1: icmp_seq=4 ttl=128 time=0.489 ms
64 bytes from 10.5.1.1: icmp_seq=5 ttl=128 time=0.326 ms
64 bytes from 10.5.1.1: icmp_seq=6 ttl=128 time=0.499 ms
64 bytes from 10.5.1.1: icmp_seq=7 ttl=128 time=0.497 ms
^C
--- 10.5.1.1 ping statistics ---
7 packets transmitted, 7 received, 0% packet loss, time 6134ms
rtt min/avg/max/mdev = 0.272/0.391/0.499/0.091 ms
[root@routeur ~]# ping 10.5.1.254
PING 10.5.1.254 (10.5.1.254) 56(84) bytes of data.
64 bytes from 10.5.1.254: icmp_seq=1 ttl=64 time=0.026 ms
64 bytes from 10.5.1.254: icmp_seq=2 ttl=64 time=0.094 ms
64 bytes from 10.5.1.254: icmp_seq=3 ttl=64 time=0.065 ms
^C
--- 10.5.1.254 ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2067ms
rtt min/avg/max/mdev = 0.026/0.061/0.094/0.027 ms
[root@routeur ~]# ping 10.5.1.11
PING 10.5.1.11 (10.5.1.11) 56(84) bytes of data.
64 bytes from 10.5.1.11: icmp_seq=1 ttl=64 time=1.06 ms
64 bytes from 10.5.1.11: icmp_seq=2 ttl=64 time=0.821 ms
64 bytes from 10.5.1.11: icmp_seq=3 ttl=64 time=0.839 ms
^C
--- 10.5.1.11 ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2004ms
rtt min/avg/max/mdev = 0.821/0.906/1.058/0.107 ms
[root@routeur ~]# ping 10.5.1.12
PING 10.5.1.12 (10.5.1.12) 56(84) bytes of data.
64 bytes from 10.5.1.12: icmp_seq=1 ttl=64 time=0.996 ms
64 bytes from 10.5.1.12: icmp_seq=2 ttl=64 time=0.680 ms
64 bytes from 10.5.1.12: icmp_seq=3 ttl=64 time=0.754 ms
^C
--- 10.5.1.12 ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2004ms
rtt min/avg/max/mdev = 0.680/0.810/0.996/0.134 ms
```

️Déjà, prouvez que le routeur a un accès internet

```
[root@routeur ~]# ip a
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default qlen 1000
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
    inet 127.0.0.1/8 scope host lo
       valid_lft forever preferred_lft forever
    inet6 ::1/128 scope host
       valid_lft forever preferred_lft forever
2: enp0s3: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc fq_codel state UP group default qlen 1000
    link/ether 08:00:27:fc:55:2c brd ff:ff:ff:ff:ff:ff
    inet 10.5.1.254/24 brd 10.5.1.255 scope global noprefixroute enp0s3
       valid_lft forever preferred_lft forever
    inet6 fe80::a00:27ff:fefc:552c/64 scope link
       valid_lft forever preferred_lft forever
3: enp0s8: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc fq_codel state UP group default qlen 1000
    link/ether 08:00:27:56:8c:45 brd ff:ff:ff:ff:ff:ff
    inet 10.0.3.15/24 brd 10.0.3.255 scope global dynamic noprefixroute enp0s8
       valid_lft 85677sec preferred_lft 85677sec
    inet6 fe80::d3ec:aa00:308:5d00/64 scope link noprefixroute
       valid_lft forever preferred_lft forever
```
Activez le routage

```
[root@routeur ~]# sudo firewall-cmd --add-masquerade --permanent
success
[root@routeur ~]# sudo firewall-cmd --reload
success
```

️Prouvez que les clients ont un accès internet
```
PS C:\Users\saade> ssh root@10.5.1.12
root@10.5.1.12's password:
Last login: Tue Oct 15 16:40:39 2024 from 10.5.1.1
[root@Client2 ~]# ping google.com
PING google.com (216.58.215.46) 56(84) bytes of data.
64 bytes from par21s17-in-f14.1e100.net (216.58.215.46): icmp_seq=1 ttl=109 time=38.4 ms
64 bytes from par21s17-in-f14.1e100.net (216.58.215.46): icmp_seq=2 ttl=109 time=249 ms64 bytes from par21s17-in-f14.1e100.net (216.58.215.46): icmp_seq=3 ttl=109 time=86.5 ms
64 bytes from par21s17-in-f14.1e100.net (216.58.215.46): icmp_seq=4 ttl=109 time=39.1 ms
^C
--- google.com ping statistics ---
4 packets transmitted, 4 received, 0% packet loss, time 3004ms
rtt min/avg/max/mdev = 38.376/103.157/248.685/86.253 ms
```

Montrez-moi le contenu final du fichier de configuration de l'interface réseau
```
[root@Client2 ~]# cat /etc/sysconfig/network-scripts/ifcfg-enp0s3
DEVICE=enp0s3
NAME=Lan

ONBOOT=yes
BOOTPROTO=static

IPADDR=10.5.1.12
NETMASK=255.255.255.0
GATEWAY=10.5.1.254
DNS1=1.1.1.1
```

Sur routeur.tp5.b1, déterminer sur quel port écoute le serveur SSH
```
[root@routeur ~]# sudo ss -lnpt | grep 22
LISTEN 0      128          0.0.0.0:22        0.0.0.0:*    users:(("sshd",pid=702,fd=3))
LISTEN 0      128             [::]:22           [::]:*    users:(("sshd",pid=702,fd=4))
```

Sur routeur.tp5.b1, vérifier que ce port est bien ouvert
```
[root@routeur ~]# sudo firewall-cmd --list-all
public (active)
  target: default
  icmp-block-inversion: no
  interfaces: enp0s3 enp0s8
  sources:
  services: cockpit dhcpv6-client ssh
  ports:
  protocols:
  forward: yes
  masquerade: yes
  forward-ports:
  source-ports:
  icmp-blocks:
  rich rules:
```

Installez et configurez un serveur DHCP sur la machine
```
[root@routeur ~]# dnf -y install dhcp-server
[root@routeur ~]# nano /etc/dhcp/dhcpd.conf
[root@routeur ~]# systemctl enable --now dhcpd
[root@routeur ~]# firewall-cmd --add-service=dhcp
success
[root@routeur ~]# firewall-cmd --runtime-to-permanent
success
```

Créez une nouvelle machine client 


(Lors de la création de mon serveur DHCP j'ai initialisé la range de ma machine entre 10.5.1.13 et 10.5.1.200 c'est pourquoi ma machine s'est connecté en 10.5.1.14 (car j'ai fait un teste aussi avant qui as donc pris 10.5.1.13))
```
[root@Client3 ~]# ping google.com
PING google.com (142.250.200.206) 56(84) bytes of data.
64 bytes from mrs09s10-in-f14.1e100.net (142.250.200.206): icmp_seq=1 ttl=109 time=38.4 ms
64 bytes from muc11s13-in-f14.1e100.net (142.250.200.206): icmp_seq=2 ttl=109 time=249 ms
64 bytes from muc11s13-in-f14.1e100.net (142.250.200.206): icmp_seq=4 ttl=109 time=39.1 ms
^C
--- google.com ping statistics ---
4 packets transmitted, 4 received, 0% packet loss, time 3004ms
rtt min/avg/max/mdev = 38.376/103.157/248.685/86.253 ms
```

Consultez le bail DHCP qui a été créé pour notre client
```
[root@routeur ~]# systemctl status dhcpd
● dhcpd.service - DHCPv4 Server Daemon
     Loaded: loaded (/usr/lib/systemd/system/dhcpd.service; enabled; preset: disabled)
     Active: active (running) since Tue 2024-10-15 17:24:26 CEST; 13min ago
       Docs: man:dhcpd(8)
             man:dhcpd.conf(5)
   Main PID: 1797 (dhcpd)
     Status: "Dispatching packets..."
      Tasks: 1 (limit: 11099)
     Memory: 4.6M
        CPU: 22ms
     CGroup: /system.slice/dhcpd.service
             └─1797 /usr/sbin/dhcpd -f -cf /etc/dhcp/dhcpd.conf -user dhcpd -group dhcpd --no-pid

Oct 15 17:28:24 routeur dhcpd[1797]: DHCPDISCOVER from 08:00:27:e3:0b:44 via enp0s3
Oct 15 17:28:25 routeur dhcpd[1797]: DHCPOFFER on 10.5.1.13 to 08:00:27:e3:0b:44 via enp0s3
Oct 15 17:28:25 routeur dhcpd[1797]: DHCPREQUEST for 10.5.1.13 (10.5.1.254) from 08:00:27:e3:0b:44 via enp0s3
Oct 15 17:28:25 routeur dhcpd[1797]: DHCPACK on 10.5.1.13 to 08:00:27:e3:0b:44 via enp0s3
Oct 15 17:36:28 routeur dhcpd[1797]: DHCPREQUEST for 10.0.2.15 from 08:00:27:d2:a8:15 via enp0s3: wrong network.
Oct 15 17:36:28 routeur dhcpd[1797]: DHCPNAK on 10.0.2.15 to 08:00:27:d2:a8:15 via enp0s3
Oct 15 17:36:28 routeur dhcpd[1797]: DHCPDISCOVER from 08:00:27:d2:a8:15 via enp0s3
Oct 15 17:36:29 routeur dhcpd[1797]: DHCPOFFER on 10.5.1.14 to 08:00:27:d2:a8:15 via enp0s3
Oct 15 17:36:29 routeur dhcpd[1797]: DHCPREQUEST for 10.5.1.14 (10.5.1.254) from 08:00:27:d2:a8:15 via enp0s3
Oct 15 17:36:29 routeur dhcpd[1797]: DHCPACK on 10.5.1.14 to 08:00:27:d2:a8:15 via enp0s3
```

Confirmez qu'il s'agit bien de la bonne adresse MAC

```
[root@Client3 ~]# ip a
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default qlen 1000
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
    inet 127.0.0.1/8 scope host lo
       valid_lft forever preferred_lft forever
    inet6 ::1/128 scope host
       valid_lft forever preferred_lft forever
2: enp0s3: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc fq_codel state UP group default qlen 1000
    link/ether 08:00:27:22:20:k6 brd ff:ff:ff:ff:ff:ff
    inet 10.5.1.14/24 brd 10.5.1.255 scope global noprefixroute enp0s3
       valid_lft 2591160 preferred_lft 2591160
    inet6 fe80::a00:27ff:fed2:a815/64 scope link
       valid_lft forever preferred_lft forever
```