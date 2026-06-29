

# Red Empresarial Multisucursal | Cisco Packet Tracer

Simulación de una infraestructura de red empresarial con tres sucursales interconectadas mediante enlaces WAN, implementando segmentación de red, enrutamiento dinámico y políticas de seguridad utilizando Cisco Packet Tracer.

---

## Descripción

Este proyecto simula la infraestructura de una empresa con presencia en tres sucursales:

* CDMX (Matriz)
* Norte
* Sur

Cada sede cuenta con redes independientes para sus departamentos, mientras que la comunicación entre sucursales se realiza mediante enlaces WAN punto a punto y el protocolo de enrutamiento dinámico OSPF.

La solución implementa un diseño escalable basado en buenas prácticas de administración de redes, incluyendo segmentación mediante VLAN, enrutamiento entre VLANs, asignación automática de direcciones IP y control de acceso mediante listas ACL.

---

## Objetivos

* Diseñar una red empresarial multisucursal.
* Implementar segmentación lógica mediante VLAN.
* Configurar Router-on-a-Stick para el enrutamiento entre VLANs.
* Implementar enrutamiento dinámico utilizando OSPF.
* Automatizar la asignación de direcciones IP mediante DHCP.
* Restringir el acceso entre departamentos utilizando ACL.
* Validar la conectividad entre todas las sucursales.

---

## Arquitectura de la red

La infraestructura está compuesta por:

| Componente                   | Cantidad |
| ---------------------------- | -------: |
| Routers Cisco                |        3 |
| Switches Cisco Catalyst 2960 |        3 |
| Servidor                     |        1 |
| Equipos cliente              |       13 |
| VLANs                        |        7 |
| Enlaces WAN Serial           |        2 |

---

## Topología

```
                    MATRIZ (CDMX)

        PCs Ventas / Admin / TI
                 |
             SW-CDMX
                 |
           Router R-CDMX
                 |
          WAN Serial (R1-R2)
                 |
            Router R-NORTE
                 |
             SW-NORTE
                 |
          PCs Ventas / Admin
                 |
          WAN Serial (R2-R3)
                 |
             Router R-SUR
                 |
              SW-SUR
                 |
          PCs Ventas / Admin
```
---

## Tecnologías implementadas

| Tecnología          | Descripción                             |
| ------------------- | --------------------------------------- |
| Cisco Packet Tracer | Simulación de la infraestructura        |
| Cisco IOS           | Configuración de dispositivos           |
| VLAN                | Segmentación de la red                  |
| IEEE 802.1Q         | Trunking entre switch y router          |
| Router-on-a-Stick   | Enrutamiento entre VLANs                |
| OSPF                | Enrutamiento dinámico                   |
| DHCP                | Asignación automática de direcciones IP |
| ACL                 | Control de acceso entre departamentos   |
| WAN Serial          | Comunicación entre sucursales           |

---

## Plan de direccionamiento

### Sucursal CDMX

| VLAN | Departamento   | Red             | Gateway      |
| ---- | -------------- | --------------- | ------------ |
| 10   | Ventas         | 192.168.10.0/24 | 192.168.10.1 |
| 20   | Administración | 192.168.20.0/24 | 192.168.20.1 |
| 30   | TI             | 192.168.30.0/24 | 192.168.30.1 |

### Sucursal Norte

| VLAN | Departamento   | Red             | Gateway      |
| ---- | -------------- | --------------- | ------------ |
| 10   | Ventas         | 192.168.40.0/24 | 192.168.40.1 |
| 20   | Administración | 192.168.50.0/24 | 192.168.50.1 |

### Sucursal Sur

| VLAN | Departamento   | Red             | Gateway      |
| ---- | -------------- | --------------- | ------------ |
| 10   | Ventas         | 192.168.60.0/24 | 192.168.60.1 |
| 20   | Administración | 192.168.70.0/24 | 192.168.70.1 |

### Enlaces WAN

| Enlace           | Red           |
| ---------------- | ------------- |
| R-CDMX ↔ R-NORTE | 10.10.10.0/30 |
| R-NORTE ↔ R-SUR  | 10.10.10.4/30 |

---

## Funcionalidades implementadas

* Segmentación mediante VLAN.
* Enrutamiento entre VLANs utilizando Router-on-a-Stick.
* Comunicación entre sucursales mediante enlaces WAN.
* Enrutamiento dinámico con OSPF (Área 0).
* Asignación automática de direcciones IP mediante DHCP.
* Políticas de seguridad utilizando ACL.
* Comunicación extremo a extremo entre todas las sucursales.

---

## Validación

Se verificó el correcto funcionamiento mediante:

* Comunicación entre equipos de distintas sucursales.
* Conectividad entre VLANs autorizadas.
* Propagación automática de rutas OSPF.
* Asignación automática de direcciones IP.
* Restricción de acceso hacia la VLAN de TI mediante ACL.
* Verificación de tablas de enrutamiento y vecinos OSPF.

Comandos utilizados:

```bash
show vlan brief
show interfaces trunk
show ip interface brief
show ip route
show ip ospf neighbor
show access-lists
```

---

## Estructura del repositorio

```
.
├── Red_Multisucursal.pkt
├── README.md
├── capturas/
│   ├── topologia.png
│   ├── ospf.png
│   ├── dhcp.png
│   └── acl.png
└── docs/
    └── configuracion.txt
```

---

## Ejecución

1. Abrir el archivo `Red_Multisucursal.pkt` con Cisco Packet Tracer.
2. Esperar a que todos los dispositivos inicialicen.
3. Acceder a la CLI de routers y switches para revisar la configuración.
4. Ejecutar pruebas de conectividad mediante `ping`.
5. Verificar el funcionamiento de OSPF, DHCP y ACL.

---

## Resultados

La infraestructura permite:

* Comunicación entre las tres sucursales.
* Segmentación lógica mediante VLAN.
* Enrutamiento dinámico automático.
* Administración centralizada del direccionamiento IP.
* Aplicación de políticas de seguridad entre departamentos.

---

## Autor

**Mauricio Escobar Sanchez**

GitHub: https://github.com/Mau12701

Correo: mauriescobar127@outlook.com

---

Este proyecto fue desarrollado con fines académicos y de aprendizaje.
