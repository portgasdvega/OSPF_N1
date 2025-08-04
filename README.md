# Laboratorio OSPF Multiarea en Packet Tracer (Nivel 1)

Este proyecto simula una red corporativa básica utilizando el protocolo de enrutamiento dinámico **OSPF** con segmentación por áreas, implementado en **Cisco Packet Tracer**.

---

## Objetivos

- Configurar un entorno de red segmentado en múltiples áreas OSPF.
- Establecer conectividad completa entre sucursales a través del área backbone (Área 0).
- Verificar la propagación de rutas y la convergencia OSPF.
- Comprobar conectividad mediante pruebas ICMP entre terminales finales.

---

## Topología
````
        [R1-Core-Área 0]
         /           \
   Área 10(R2)       Área 20(R3)
    /                     \
[PC-A]                   [PC-B]

````

- **R1** (Cisco 2911): Backbone (Área 0)
- **R2**: Sucursal A (Área 10)
- **R3**: Sucursal B (Área 20)
- **PC-A**: 192.168.10.2
- **PC-B**: 192.168.20.2

---

## Herramientas utilizadas

- Cisco Packet Tracer 8.X
- Routers Cisco 2911
- PCs finales
- Protocolo OSPFv2
- Sistema de direccionamiento IPv4

---

## Configuraciones clave

### R1 – Área 0

```bash
interface Gig0/1
 ip address 192.168.0.1 255.255.255.252
 no shutdown
interface Gig0/2
 ip address 192.168.0.6 255.255.255.252
 no shutdown
router ospf 1
 router-id 1.1.1.1
 network 192.168.0.0 0.0.0.3 area 0
 network 192.168.0.4 0.0.0.3 area 0
````

### R2 – Área 10

```bash
interface Gig0/0
 ip address 192.168.10.1 255.255.255.0
 no shutdown
interface Gig0/1
 ip address 192.168.0.2 255.255.255.252
 no shutdown
router ospf 1
 router-id 2.2.2.2
 network 192.168.10.0 0.0.0.255 area 10
 network 192.168.0.0 0.0.0.3 area 0
```

### R3 – Área 20

```bash
interface Gig0/0
 ip address 192.168.20.1 255.255.255.0
 no shutdown
interface Gig0/2
 ip address 192.168.0.5 255.255.255.252
 no shutdown
router ospf 1
 router-id 3.3.3.3
 network 192.168.20.0 0.0.0.255 area 20
 network 192.168.0.4 0.0.0.3 area 0
```

---

## Resultados

Se logró conectividad entre las redes LAN de ambas sucursales a través de OSPF.

---

## Archivos incluidos

* `ospf-n1.pkt`: Archivo del proyecto en Packet Tracer.
* `capturas`: Imágenes de verificación de conectividad.
* `README.md`: Documento explicativo del laboratorio.

---

## Aprendizajes clave

* Implementación básica de OSPF con múltiples áreas.
* Uso de máscara wildcard en configuración.
* Importancia del área backbone (Área 0) en OSPF.
* Pruebas de verificación de tabla de enrutamiento y vecinos.

---

## Autor

Emiliano Martínez Vega
Ingeniero en Comunicaciones y Electrónica – IPN
GitHub: [@portgasdvega](https://github.com/portgasdvega)

---

## Licencia

Este proyecto está bajo la licencia MIT.
