# Práctica 1. Ejercicio 3

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

network 172.16.1.0
network 192.168.2.0
network 192.168.5.0

no auto-summary
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

router rip
version 2

network 172.16.3.0
network 172.16.4.0
network 192.168.2.0
network 192.168.6.0

no auto-summary
passive-interface g0/1
passive-interface g0/2
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
