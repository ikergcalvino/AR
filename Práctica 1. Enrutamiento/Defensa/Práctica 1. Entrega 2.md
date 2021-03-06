# Práctica 1. Entrega 2

## ISP1

```
en
conf t
hostname ISP1
no ip domain-lookup

line console 0
logging synchronous
exit

int g0/0
ip add 192.0.2.1 255.255.255.252
no shut

int g0/1
ip add 192.0.2.10 255.255.255.252
no shut

int s0/0/0
ip add 192.0.2.17 255.255.255.240
no shut

ip route 10.0.0.0 255.0.0.0 192.0.2.18
ip route 172.16.0.0 255.255.0.0 192.0.2.18

router rip
version 2

network 192.0.2.0
network 192.0.2.8
network 192.0.2.16

no auto-summary
passive-interface s0/0/0
redistribute static
exit

end
wr
reload
```

## ISP2

```
en
conf t
hostname ISP2
no ip domain-lookup

line console 0
logging synchronous
exit

int g0/0
ip add 192.0.2.5 255.255.255.252
no shut

int g0/1
ip add 192.0.2.2 255.255.255.252
no shut

router rip
version 2

network 192.0.2.0
network 192.0.2.4

auto-summary
exit

end
wr
reload
```

## ISP3

```
en
conf t
hostname ISP3
no ip domain-lookup

line console 0
logging synchronous
exit

int g0/0
ip add 192.0.2.9 255.255.255.252
no shut

int g0/1
ip add 192.0.2.6 255.255.255.252
no shut

int s0/0/0
ip add 192.0.2.33 255.255.255.240
no shut

ip route 192.168.1.0 255.255.255.0 192.0.2.34

router rip
version 2

network 192.0.2.4
network 192.0.2.8
network 192.0.2.32

no auto-summary
passive-interface s0/0/0
redistribute static
exit

end
wr
reload
```

## HQ-R1

```
en
conf t
hostname HQ-R1
no ip domain-lookup

line console 0
logging synchronous
exit

int g0/0
ip add 172.16.12.1 255.255.255.0
no shut

int g0/1
ip add 10.1.17.1 255.255.255.0
no shut

int g0/0/0
ip add 10.0.0.1 255.255.255.252
no shut

int g0/1/0
ip add 10.0.0.10 255.255.255.252
no shut

router rip
version 2

network 10.0.0.0
network 10.0.0.8
network 172.16.12.0
network 10.1.17.0

no auto-summary
passive-interface g0/0
passive-interface g0/1
exit

end
wr
reload
```

## HQ-R2

```
en
conf t
hostname HQ-R2
no ip domain-lookup

line console 0
logging synchronous
exit

int g0/0
ip add 172.16.13.1 255.255.255.0
no shut

int g0/1
ip add 10.1.19.1 255.255.255.0
no shut

int g0/0/0
ip add 10.0.0.5 255.255.255.252
no shut

int g0/1/0
ip add 10.0.0.2 255.255.255.252
no shut

router rip
version 2

network 10.0.0.0
network 10.0.0.4
network 172.16.13.0
network 10.1.19.0

no auto-summary
passive-interface g0/0
passive-interface g0/1
exit

end
wr
reload
```

## HQ-R3

```
en
conf t
hostname HQ-R3
no ip domain-lookup

line console 0
logging synchronous
exit

int g0/0
ip add 10.254.1.1 255.255.255.0
no shut

int g0/0/0
ip add 10.0.0.9 255.255.255.252
no shut

int g0/1/0
ip add 10.0.0.6 255.255.255.252
no shut

int s0/2/0
ip add 192.0.2.18 255.255.255.240
no shut

ip route 0.0.0.0 0.0.0.0 192.0.2.17

router rip
version 2

network 10.0.0.4
network 10.0.0.8
network 10.254.1.0
network 192.0.2.16

no auto-summary
passive-interface g0/0
passive-interface s0/2/0
redistribute static
exit

end
wr
reload
```

## BR-1

```
en
conf t
hostname BR-1
no ip domain-lookup

line console 0
logging synchronous
exit

int s0/0/0
ip add 192.0.2.34 255.255.255.240
no shut

int g0/0
ip add 192.168.1.1 255.255.255.128
no shut

int g0/1
ip add 192.168.1.129 255.255.255.128
no shut

ip route 0.0.0.0 0.0.0.0 192.0.2.33

end
wr
reload
```
