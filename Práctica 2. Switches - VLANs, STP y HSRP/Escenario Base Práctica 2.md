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

end
wr
reload
```
