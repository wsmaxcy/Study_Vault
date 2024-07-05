Network commands relavent to networkinging

`ip a` - new way of doing it. output is colorful
output:
```bash
➜  ~ ip a 
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default qlen 1000
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
    inet 127.0.0.1/8 scope host lo
       valid_lft forever preferred_lft forever
2: eth0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc fq_codel state UP group 57841 qlen 1000
    link/ether d4:5d:64:d4:4a:6f brd ff:ff:ff:ff:ff:ff
    inet 192.168.1.220/24 brd 192.168.1.255 scope global noprefixroute eth0
       valid_lft forever preferred_lft forever
3: docker0: <NO-CARRIER,BROADCAST,MULTICAST,UP> mtu 1500 qdisc noqueue state DOWN group default 
    link/ether 02:42:43:ae:72:b7 brd ff:ff:ff:ff:ff:ff
    inet 172.17.0.1/16 brd 172.17.255.255 scope global docker0
       valid_lft forever preferred_lft forever
4: nordlynx: <POINTOPOINT,UP,LOWER_UP> mtu 1420 qdisc noqueue state UNKNOWN group default qlen 1000
    link/none 
    inet 10.5.0.2/32 scope global nordlynx
       valid_lft forever preferred_lft forever
```

`ifconfig` - old way of doing it. still works and mostly what i use
output:
```bash
➜  ~ ifconfig
docker0: flags=4099<UP,BROADCAST,MULTICAST>  mtu 1500
        inet 172.17.0.1  netmask 255.255.0.0  broadcast 172.17.255.255
        ether 02:42:43:ae:72:b7  txqueuelen 0  (Ethernet)
        RX packets 0  bytes 0 (0.0 B)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 0  bytes 0 (0.0 B)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

eth0: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        inet 192.168.1.220  netmask 255.255.255.0  broadcast 192.168.1.255
        ether d4:5d:64:d4:4a:6f  txqueuelen 1000  (Ethernet)
        RX packets 167429  bytes 200638260 (191.3 MiB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 92072  bytes 26045848 (24.8 MiB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

lo: flags=73<UP,LOOPBACK,RUNNING>  mtu 65536
        inet 127.0.0.1  netmask 255.0.0.0
        loop  txqueuelen 1000  (Local Loopback)
        RX packets 78  bytes 6116 (5.9 KiB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 78  bytes 6116 (5.9 KiB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

nordlynx: flags=81<UP,POINTOPOINT,RUNNING>  mtu 1420
        inet 10.5.0.2  netmask 255.255.255.255  destination 10.5.0.2
        unspec 00-00-00-00-00-00-00-00-00-00-00-00-00-00-00-00  txqueuelen 1000  (UNSPEC)
        RX packets 165319  bytes 193372156 (184.4 MiB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 90189  bytes 21840300 (20.8 MiB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0
```

`ip n` - n stands for neighbor
output:
```bash
➜  ~ ip n    
192.168.1.120 dev eth0 FAILED 
192.168.1.143 dev eth0 lladdr 00:e0:4c:68:01:47 STALE 
192.168.1.1 dev eth0 lladdr c0:06:c3:c8:26:d4 REACHABLE 
192.168.1.112 dev eth0 lladdr 00:60:e0:80:44:69 STALE 
```
asks what IP address is associated with what MAC address
`ip` command is a little be prettier

`ip r` and `route` are the same thing
```bash
➜  ~ ip r
default via 192.168.1.1 dev eth0 proto dhcp src 192.168.1.220 metric 100 
172.17.0.0/16 dev docker0 proto kernel scope link src 172.17.0.1 linkdown 
192.168.1.0/24 dev eth0 proto kernel scope link src 192.168.1.220 metric 100 
➜  ~ route       
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
default         _gateway        0.0.0.0         UG    100    0        0 eth0
172.17.0.0      0.0.0.0         255.255.0.0     U     0      0        0 docker0
192.168.1.0     0.0.0.0         255.255.255.0   U     100    0        0 eth0
```
both of these are looking at the routing table, aka, where our traffic is routing through.

# Go over this section again. This is confusing for me

`ping` - basically asks "Hey are you still alive?"
Might wont work. ICMP could be disabled and that could be the reason that it is off, or the host might be down. Just takes more troubleshooting to figure that out.