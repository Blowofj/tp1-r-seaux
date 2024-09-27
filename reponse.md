Adresses IP de ta machine

```
PS C:\Users\saade> ipconfig
    Wireless LAN adapter Wi-Fi:

    Connection-specific DNS Suffix  . :
    Link-local IPv6 Address . . . . . : fe80::350f:de16:1eb4:4fc2%18
    IPv4 Address. . . . . . . . . . . : 10.33.78.239
    Subnet Mask . . . . . . . . . . . : 255.255.240.0
    Default Gateway . . . . . . . . . : 10.33.79.254

    Ethernet adapter Ethernet 2:

   Connection-specific DNS Suffix  . :
   Link-local IPv6 Address . . . . . : fe80::3da9:45c2:45af:d017%3
   IPv4 Address. . . . . . . . . . . : 192.168.56.1
   Subnet Mask . . . . . . . . . . . : 255.255.255.0
   Default Gateway . . . . . . . . . :
```

Si t'as un accès internet normal, d'autres infos sont forcément dispos...

```
Wireless LAN adapter Wi-Fi:

   Connection-specific DNS Suffix  . :
   Description . . . . . . . . . . . : Intel(R) Wi-Fi 6E AX211 160MHz
   Physical Address. . . . . . . . . : C8-8A-9A-E6-33-1D
   DHCP Enabled. . . . . . . . . . . : Yes
   Autoconfiguration Enabled . . . . : Yes
   Link-local IPv6 Address . . . . . : fe80::350f:de16:1eb4:4fc2%18(Preferred)
   IPv4 Address. . . . . . . . . . . : 10.33.78.239(Preferred)
   Subnet Mask . . . . . . . . . . . : 255.255.240.0
   Lease Obtained. . . . . . . . . . : Friday, September 27, 2024 12:11:37 PM
   Lease Expires . . . . . . . . . . : Saturday, September 28, 2024 12:03:44 PM
   Default Gateway . . . . . . . . . : 10.33.79.254
   DHCP Server . . . . . . . . . . . : 10.33.79.254
   DHCPv6 IAID . . . . . . . . . . . : 164137626
   DHCPv6 Client DUID. . . . . . . . : 00-01-00-01-2D-62-53-4D-10-7C-61-70-C8-EB
   DNS Servers . . . . . . . . . . . : 8.8.8.8
                                       1.1.1.1
   NetBIOS over Tcpip. . . . . . . . : Enabled
```
 Envoie un ping vers...

 ```
PS C:\Users\saade> ping 10.33.78.239

Pinging 10.33.78.239 with 32 bytes of data:
Reply from 10.33.78.239: bytes=32 time<1ms TTL=128
Reply from 10.33.78.239: bytes=32 time<1ms TTL=128
Reply from 10.33.78.239: bytes=32 time<1ms TTL=128
Reply from 10.33.78.239: bytes=32 time<1ms TTL=128

Ping statistics for 10.33.78.239:
    Packets: Sent = 4, Received = 4, Lost = 0 (0% loss),
Approximate round trip times in milli-seconds:
    Minimum = 0ms, Maximum = 0ms, Average = 0ms
 ```

```
PS C:\Users\saade> ping 127.0.0.1

Pinging 127.0.0.1 with 32 bytes of data:
Reply from 127.0.0.1: bytes=32 time<1ms TTL=128
Reply from 127.0.0.1: bytes=32 time<1ms TTL=128
Reply from 127.0.0.1: bytes=32 time<1ms TTL=128
Reply from 127.0.0.1: bytes=32 time<1ms TTL=128

Ping statistics for 127.0.0.1:
    Packets: Sent = 4, Received = 4, Lost = 0 (0% loss),
Approximate round trip times in milli-seconds:
    Minimum = 0ms, Maximum = 0ms, Average = 0ms
```

On continue avec ping. Envoie un ping vers...

```
PS C:\Users\saade> ping 10.33.79.254

Pinging 10.33.79.254 with 32 bytes of data:
Request timed out.
Request timed out.
Request timed out.
Request timed out.

Ping statistics for 10.33.79.254:
    Packets: Sent = 4, Received = 0, Lost = 4 (100% loss),
```

```
PS C:\Users\saade> ping 10.33.66.78

Pinging 10.33.66.78 with 32 bytes of data:
Reply from 10.33.66.78: bytes=32 time=17ms TTL=64
Reply from 10.33.66.78: bytes=32 time=36ms TTL=64
Reply from 10.33.66.78: bytes=32 time=44ms TTL=64
Reply from 10.33.66.78: bytes=32 time=55ms TTL=64

Ping statistics for 10.33.66.78:
    Packets: Sent = 4, Received = 4, Lost = 0 (0% loss),
Approximate round trip times in milli-seconds:
    Minimum = 17ms, Maximum = 55ms, Average = 38ms
```

```
PS C:\Users\saade> ping www.thinkerview.com

Pinging www.thinkerview.com [188.114.97.7] with 32 bytes of data:
Reply from 188.114.97.7: bytes=32 time=18ms TTL=55
Reply from 188.114.97.7: bytes=32 time=15ms TTL=55
Reply from 188.114.97.7: bytes=32 time=16ms TTL=55
Reply from 188.114.97.7: bytes=32 time=15ms TTL=55

Ping statistics for 188.114.97.7:
    Packets: Sent = 4, Received = 4, Lost = 0 (0% loss),
Approximate round trip times in milli-seconds:
    Minimum = 15ms, Maximum = 18ms, Average = 16ms
```

Faire une requête DNS à la main

```
PS C:\Users\saade> nslookup www.thinkerview.com
Server:  dns.google
Address:  8.8.8.8

Non-authoritative answer:
Name:    www.thinkerview.com
Addresses:  2a06:98c1:3121::7
          2a06:98c1:3120::7
          188.114.96.7
          188.114.97.7

PS C:\Users\saade> nslookup www.wikileaks.org
Server:  dns.google
Address:  8.8.8.8

Non-authoritative answer:
Name:    wikileaks.org
Addresses:  51.159.197.136
          80.81.248.21
Aliases:  www.wikileaks.org

PS C:\Users\saade> nslookup www.torproject.org
Server:  dns.google
Address:  8.8.8.8

Non-authoritative answer:
Name:    www.torproject.org
Addresses:  2620:7:6002:0:466:39ff:fe7f:1826
          2a01:4f8:fff0:4f:266:37ff:feae:3bbc
          2a01:4f9:c010:19eb::1
          2a01:4f8:fff0:4f:266:37ff:fe2c:5d19
          2620:7:6002:0:466:39ff:fe32:e3dd
          95.216.163.36
          116.202.120.166
          116.202.120.165
          204.8.99.146
          204.8.99.144
```

Effectue un scan du réseau auquel tu es connecté

```
PS C:\Users\saade> nmap.exe -sn -PR 10.33.64.0/20
    Starting Nmap 7.95 ( https://nmap.org ) at 2024-09-27 17:32 Romance Daylight Time
    Stats: 0:03:49 elapsed; 0 hosts completed (0 up), 4095 undergoing ARP Ping Scan
    ARP Ping Scan Timing: About 31.73% done; ETC: 17:44 (0:08:15 remaining)
    Packet Tracing disabled.
    Nmap scan report for 10.33.66.78
    Host is up (0.070s latency).
    MAC Address: E4:B3:18:48:36:68 (Intel Corporate)
    Nmap scan report for 10.33.69.82
    Host is up (0.010s latency).
    MAC Address: 58:96:71:9C:C7:6E (Wistron Neweb)
    Nmap scan report for 10.33.79.254
    Host is up (0.0030s latency).
    MAC Address: 7C:5A:1C:D3:D8:76 (Sophos)
    Nmap scan report for 10.33.78.239
    Host is up.
    Nmap done: 4096 IP addresses (149 hosts up) scanned in 331.06 seconds
```

Changer d'adresse IP

```
Wireless LAN adapter Wi-Fi:

   Connection-specific DNS Suffix  . :
   Description . . . . . . . . . . . : Intel(R) Wi-Fi 6E AX211 160MHz
   Physical Address. . . . . . . . . : C8-8A-9A-E6-33-1D
   DHCP Enabled. . . . . . . . . . . : No
   Autoconfiguration Enabled . . . . : Yes
   Link-local IPv6 Address . . . . . : fe80::350f:de16:1eb4:4fc2%18(Preferred)
   IPv4 Address. . . . . . . . . . . : 10.33.73.8(Preferred)
   Subnet Mask . . . . . . . . . . . : 255.255.240.0
   Default Gateway . . . . . . . . . : 10.33.79.254
   DHCPv6 IAID . . . . . . . . . . . : 164137626
   DHCPv6 Client DUID. . . . . . . . : 00-01-00-01-2D-62-53-4D-10-7C-61-70-C8-EB
   DNS Servers . . . . . . . . . . . : 8.8.8.8
                                       1.1.1.1
   NetBIOS over Tcpip. . . . . . . . : Enabled
```