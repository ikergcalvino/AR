# Práctica 1. Enrutamiento

## Configuración básica de router

### Modo usuario

```
Router>
```

### Modo privilegiado

```
Router> enable
Router# disable
Router>
```

### Modo de configuración

```
Router# conf t
Router(config)#
```

### Configuración del nombre del dispositivo

```
Router(config)# hostname <nombre>
Router(config)# no hostname
```

### Configuración de las interfaces de un router

```
Router(config)# interface <tipo de interfaz> <módulo/slot/tarjeta>
Router(config-if)# no shutdown
Router(config-if)# shutdown
```

### Salir del modo de configuración

```
Router(config)# exit
Router#
```

## Enrutamiento Estático

### Configuración de ruta estática

```
Router> enable
Router# configure terminal
Router(config)# ip route <red-destino> <máscara> <ip-siguiente-salto>
```

### Rutas predeterminadas o por defecto (default-gateway)

```
Router> enable
Router# configure terminal
Router(config)# ip route 0.0.0.0 0.0.0.0 <ip-siguiente-salto>
```

## Enrutamiento Dinámico

### Configuración de RIPv2

```
Router(config)# router rip
Router(config)# version 2
Router(config-router)# network [network address]
```

### Función de sumarización automática

```
Router(config-router)# no auto-summary
```

### Actualizaciones RIP por broadcast o multicast

```
Router(config-router)# passive-interface <interface-type> <interface-num>
```

```
Router(config-router)# passive-interface default
Router(config-router)# no passive-interface <int-type> <int-num>
```

### Inyectar información adicional en el protocolo de enrutamiento

```
Router(config-router)# redistribute <protocolo/static>
```
