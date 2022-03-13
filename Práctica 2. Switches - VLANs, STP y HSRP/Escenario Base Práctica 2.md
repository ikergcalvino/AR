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

! config

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

! config

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

! config

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

! config

end
wr
reload
```
