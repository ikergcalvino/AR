# Práctica 1. Ejercicio 4

## R1

```
en
conf t
hostname R1
no ip domain-lookup

line console 0
logging synchronous
exit

router rip
version 2

network 192.168.1.0
network 192.168.2.0
network 192.168.5.0

auto-summary
passive-interface g0/0
exit

end
wr
reload
```

## R2

```
en
conf t
hostname R2
no ip domain-lookup

line console 0
logging synchronous
exit

ip route 0.0.0.0 0.0.0.0 192.0.2.2

router rip
version 2

network 192.0.2.0
network 192.168.2.0
network 192.168.3.0
network 192.168.4.0
network 192.168.6.0

no auto-summary
passive-interface g0/0
passive-interface g0/1
passive-interface g0/2
redistribute static
exit

end
wr
reload
```

## R3

```
en
conf t
hostname R3
no ip domain-lookup

line console 0
logging synchronous
exit

router rip
version 2

network 192.168.5.0
network 192.168.6.0

auto-summary
exit

end
wr
reload
```
