# Ejercicio 2. Escenario Base

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
ip add 172.16.32.1 255.255.240.0
no shut

int s0/0/0
ip add 192.168.2.1 255.255.255.0
no shut

int s0/0/1
ip add 192.168.5.1 255.255.255.0
no shut

router rip
version 2

network 172.16.32.0
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

int g0/1
ip add 172.16.0.1 255.255.240.0
no shut

int g0/2
ip add 171.16.16.1 255.255.240.0
no shut

int s0/0/0
ip add 192.168.6.2 255.255.255.0
no shut

int s0/0/1
ip add 192.168.2.2 255.255.255.0
no shut

router rip
version 2

network 172.16.0.0
network 172.16.16.0
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

int s0/0/0
ip add 192.168.5.2 255.255.255.0
no shut

int s0/0/1
ip add 192.168.6.1 255.255.255.0
no shut

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
