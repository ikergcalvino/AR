# Práctica 1. Ejercicio 2

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

network 192.168.2.0
network 192.168.3.0
network 192.168.4.0
network 192.168.6.0

auto-summary
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
