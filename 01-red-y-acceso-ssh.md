# Día 1: Infraestructura de red y acceso remoto seguro (SSH)

## Objetivos del día
- Reutilizar hardware de red para extender la conectividad del entorno del servidor.
- Establecer acceso remoto por terminal al servidor para su administración (sin monitor ni periféricos).

## Hardware y Software
- **Servidor:** Lenovo ThinkCentre (Ubuntu Server).
- **Red:** Router TP-Link (reconfigurado como repetidor).
- **Protocolo:** SSH (OpenSSH).

## Desarrollo de la jornada

### 1. Reacondicionamiento del Router
Para integrar el router antiguo en la topología de red principal sin causar conflictos, se llevaron a cabo las siguientes configuraciones:
- **Desactivación del servidor DHCP:** Fundamental para que el router principal siga siendo el único que asigne direcciones IP en la red, evitando conflictos de red y bucles.
- **Asignación de IP estática:** Se le asignó al router secundario una IP dentro del rango de la red principal (pero fuera de su pool DHCP) para poder acceder a su panel de administración en el futuro.
- **Configuración inalámbrica/LAN:** Vinculación con la red principal para extender la cobertura hacia la zona del servidor.

### 2. Configuración de acceso SSH
Una vez garantizada la conectividad física y de red, el siguiente paso fue habilitar la administración remota del servidor. 
- Comprobación de la interfaz de red del servidor para identificar su IP local ("ip a").
- Verificación del servicio `sshd` en Ubuntu Server.
- Conexión exitosa desde el equipo cliente mediante la terminal:
  
  ```bash
  ssh usuario@ip_del_servidor
