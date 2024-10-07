Prouvez que votre configuration est effective :

```
PS C:\Users\saade\Desktop\netcat-1.11> Get-NetIPAddress -InterfaceAlias "Ethernet"


IPAddress         : fe80::1125:98bc:1a8a:86a6%8
InterfaceIndex    : 8
InterfaceAlias    : Ethernet
AddressFamily     : IPv6
Type              : Unicast
PrefixLength      : 64
PrefixOrigin      : WellKnown
SuffixOrigin      : Link
AddressState      : Preferred
ValidLifetime     :
PreferredLifetime :
SkipAsSource      : False
PolicyStore       : ActiveStore

IPAddress         : 10.255.255.200
InterfaceIndex    : 8
InterfaceAlias    : Ethernet
AddressFamily     : IPv4
Type              : Unicast
PrefixLength      : 24
PrefixOrigin      : Manual
SuffixOrigin      : Manual
AddressState      : Preferred
ValidLifetime     :
PreferredLifetime :
SkipAsSource      : False
PolicyStore       : ActiveStore
```