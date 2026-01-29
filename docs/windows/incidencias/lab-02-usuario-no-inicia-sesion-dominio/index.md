# LAB 02 – Usuario no puede iniciar sesión en el dominio

## Descripción del problema
Un usuario del dominio no puede iniciar sesión en un equipo cliente unido al dominio `labs.local`.

## Entorno

### Infraestructura

- **Hypervisor:** VMware Workstation

### Controlador de dominio

- Sistema operativo: Windows Server 2022
- Rol: Active Directory Domain Services (AD DS) y DNS
- Nombre del servidor: SRV-DC01
- Dirección IP: 192.168.56.10

### Equipo cliente

- Sistema operativo: Windows 10
- Nombre del equipo: PC-01
- Dirección IP: 192.168.56.20

### Dominio

- Nombre del dominio: labs.local

## Síntomas
- El equipo cliente no puede iniciar sesión con un usuario del dominio.
- Mensajes de error al intentar unir o autenticar en el dominio.
- Resolución DNS inconsistente.

![Fallo de resolución DNS desde el cliente](img/02-nslookup-fallando.png)


## Diagnóstico

Para identificar la causa del problema se realizaron las siguientes comprobaciones, siguiendo un orden lógico de menor a mayor complejidad:

### Comprobaciones iniciales

- Verificación de la conectividad de red entre el equipo cliente y el servidor.
- Revisión de la configuración IP del equipo cliente.
- Comprobación de que el servidor DNS del cliente apunta al controlador de dominio.

### Comprobaciones en el controlador de dominio

- Verificación del estado del servicio DNS.
- Comprobación de la existencia del usuario en Active Directory.
- Revisión de los registros SRV del dominio para confirmar que el controlador de dominio es localizable.


![Zona DNS labs.local en el servidor](img/03-dns-zona-labs-local.png)

![Registro del controlador de dominio en DNS](img/04-registro-controlador-dominio.png)


## Resolución

Una vez identificada la causa del problema, se aplicaron las siguientes acciones correctivas:

### Corrección de la configuración DNS

- Se verificó que el equipo cliente utilizara como servidor DNS la dirección IP del controlador de dominio.
- Se descartó el uso de servidores DNS externos o configuraciones incorrectas.

![Configuración IP del equipo cliente](img/01-ip-configurada-pc.png)

### Unión correcta del equipo al dominio

- Se realizó nuevamente el proceso de unión del equipo cliente al dominio `labs.local`.
- Se utilizaron las credenciales correctas del administrador del dominio.

![Dominio labs.local creado y operativo](img/05-dominio-creado.png)

### Inicio de sesión con usuario de dominio

- Tras completar la unión al dominio, el equipo cliente se reinició.
- El usuario del dominio pudo iniciar sesión correctamente sin incidencias.

![Inicio de sesión correcto con usuario de dominio](img/06-login-usuario-dominio.png)


## Verificación

Tras aplicar la solución, se realizaron las siguientes comprobaciones para confirmar que la incidencia había quedado resuelta:

- El equipo cliente aparece correctamente unido al dominio `labs.local`.
- El usuario del dominio puede iniciar sesión sin errores.
- El usuario y el equipo son visibles desde Active Directory.

![Usuario del dominio creado en Active Directory](img/07-ad-usuario-creado.png)


- Resolución DNS correcta desde cliente y servidor.

