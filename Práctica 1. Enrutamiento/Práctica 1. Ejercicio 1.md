# Práctica 1. Ejercicio 1

## R1

```
en
conf t
hostname R1
no ip domain-lookup

line console 0
logging synchronous
exit

int g0/0
ip add 192.168.1.1 255.255.255.0
no shut

int g0/1
ip add 192.168.2.1 255.255.255.0
no shut

ip route 192.168.3.0 255.255.255.0 192.168.2.2
ip route 192.168.4.0 255.255.255.0 192.168.2.2

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

int g0/0
ip add 192.168.2.2 255.255.255.0
no shut

int g0/1
ip add 192.168.3.1 255.255.255.0
no shut

int g0/2
ip add 192.168.4.1 255.255.255.0
no shut

ip route 192.168.1.0 255.255.255.0 192.168.2.1

end
wr
reload
```
