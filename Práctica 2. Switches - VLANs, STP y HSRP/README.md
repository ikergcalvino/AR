# Práctica 2. Switches - VLANs, STP y HSRP

## Configuración de VLANs

### Configuración de VLANs adicionales

```
Switch(config)# vlan <nº vlan>
Switch(config-vlan)# name <nombre>
```

### Cambio de VLAN a la que está asignada un puerto de un switch

```
Switch(config)# interface <tipo de interfaz> <módulo/slot/tarjeta>
Switch(config-if)# switchport mode access
Switch(config-if)# switchport access vlan <nº vlan>
```

```
Switch(config)# interface range <Tipo> <slot>/<puerto inicial> - <puerto final>
Switch(config-if)# switchport mode access
Switch(config-if)# switchport access vlan <nº vlan>
```

### Eliminar una VLAN

```
Switch(config)# no vlan <nº vlan>
```

## Verificación y prueba

### Comandos de diagnóstico VLAN

```
Switch> show vlan
Switch> show interfaces switchport
```
