# Escenario Base Práctica 2

## AL-SW1

```
en
conf t
hostname AL-SW1
no ip domain-lookup

line console 0
logging synchronous
exit

vlan 10
name BLUE
exit

int range f0/1 - 6
switchport mode access
switchport access vlan 10
exit

vlan 20
name RED
exit

int range f0/7 - 12
switchport mode access
switchport access vlan 20
exit

vlan 30
name GREEN
exit

int range f0/13 - 18
switchport mode access
switchport access vlan 30
exit

vlan 40
name YELLOW
exit

int range f0/19 - 24
switchport mode access
switchport access vlan 40
exit

int g0/1
switchport mode trunk

int g0/2
switchport mode trunk

exit

spanning-tree portfast default

end
wr
reload
```

## AL-SW2

```
en
conf t
hostname AL-SW2
no ip domain-lookup

line console 0
logging synchronous
exit

vlan 10
name BLUE
exit

int range f0/1 - 6
switchport mode access
switchport access vlan 10
exit

vlan 20
name RED
exit

int range f0/7 - 12
switchport mode access
switchport access vlan 20
exit

vlan 30
name GREEN
exit

int range f0/13 - 18
switchport mode access
switchport access vlan 30
exit

vlan 40
name YELLOW
exit

int range f0/19 - 24
switchport mode access
switchport access vlan 40
exit

int g0/1
switchport mode trunk

int g0/2
switchport mode trunk

exit

spanning-tree portfast default

end
wr
reload
```

## DL-SW1

```
en
conf t
hostname DL-SW1
no ip domain-lookup

line console 0
logging synchronous
exit

vlan 10
name BLUE
exit

vlan 20
name RED
exit

vlan 30
name GREEN
exit

vlan 40
name YELLOW
exit

int g1/0/1
switchport mode trunk

int g1/0/2
switchport mode trunk

int g1/0/3
switchport mode trunk

exit

spanning-tree vlan 10 priority 4096
spanning-tree vlan 20 priority 4096
spanning-tree vlan 30 priority 8192
spanning-tree vlan 40 priority 8192

int vlan 10
ip add 10.1.1.253 255.255.255.0

standby 10 ip 10.1.1.1
standby 10 priority 110
standby 10 preempt
standby 10 track g1/0/4
standby 10 track g1/0/5

no shutdown

int vlan 20
ip add 10.1.2.253 255.255.255.0

standby 20 ip 10.1.2.1
standby 20 priority 110
standby 20 preempt
standby 20 track g1/0/4
standby 20 track g1/0/5

no shutdown

int vlan 30
ip add 10.1.3.253 255.255.255.0

standby 30 ip 10.1.3.1
standby 30 priority 100
standby 30 preempt
standby 30 track g1/0/4
standby 30 track g1/0/5

no shutdown

int vlan 40
ip add 10.1.4.253 255.255.255.0

standby 40 ip 10.1.4.1
standby 40 priority 100
standby 40 preempt
standby 40 track g1/0/4
standby 40 track g1/0/5

no shutdown

int g1/0/4
no switchport
ip add 10.0.13.3 255.255.255.0

int g1/0/5
no switchport
ip add 10.0.23.3 255.255.255.0

router rip
version 2
network 10.0.0.0

end
wr
reload
```

## DL-SW2

```
en
conf t
hostname DL-SW2
no ip domain-lookup

line console 0
logging synchronous
exit

vlan 10
name BLUE
exit

vlan 20
name RED
exit

vlan 30
name GREEN
exit

vlan 40
name YELLOW
exit

int g1/0/1
switchport mode trunk

int g1/0/2
switchport mode trunk

int g1/0/3
switchport mode trunk

exit

spanning-tree vlan 10 priority 8192
spanning-tree vlan 20 priority 8192
spanning-tree vlan 30 priority 4096
spanning-tree vlan 40 priority 4096

int vlan 10
ip add 10.1.1.254 255.255.255.0

standby 10 ip 10.1.1.1
standby 10 priority 100
standby 10 preempt
standby 10 track g1/0/4
standby 10 track g1/0/5

no shutdown

int vlan 20
ip add 10.1.2.254 255.255.255.0

standby 20 ip 10.1.2.1
standby 20 priority 100
standby 20 preempt
standby 20 track g1/0/4
standby 20 track g1/0/5

no shutdown

int vlan 30
ip add 10.1.3.254 255.255.255.0

standby 30 ip 10.1.3.1
standby 30 priority 110
standby 30 preempt
standby 30 track g1/0/4
standby 30 track g1/0/5

no shutdown

int vlan 40
ip add 10.1.4.254 255.255.255.0

standby 40 ip 10.1.4.1
standby 40 priority 110
standby 40 preempt
standby 40 track g1/0/4
standby 40 track g1/0/5

no shutdown

int g1/0/4
no switchport
ip add 10.0.14.4 255.255.255.0

int g1/0/5
no switchport
ip add 10.0.24.4 255.255.255.0

router rip
version 2
network 10.0.0.0

end
wr
reload
```
