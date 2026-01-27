# Incidencia: Usuario no puede iniciar sesión en el dominio

## 1. Descripción de la incidencia

El usuario contacta con el servicio de soporte indicando que no puede iniciar sesión en su equipo con su cuenta de dominio.

El mensaje aparece al introducir las credenciales y le impide acceder a su entorno de trabajo con normalidad.

Se procede a revisar la incidencia para identificar la causa del problema y aplicar la solución correspondiente.

## 2. Entorno del laboratorio

La incidencia se produce en un entorno de pruebas que simula una red corporativa básica con Active Directory.

El entorno está compuesto por los siguientes equipos:

 **Controlador de Dominio (DC)**  
  - Sistema operativo: Windows Server  
  - Rol: Active Directory Domain Services  
  - Función: Autenticación de usuarios y gestión del dominio


 **Equipo cliente**  
  - Sistema operativo: Windows 10 Pro  
  - Rol: Equipo unido al dominio  
  - Usuario afectado: Usuario del dominio

Ambos equipos se encuentran en la misma red y se comunican correctamente a nivel de red.

## 3. Preparación del entorno

Antes de reproducir la incidencia, se prepara el entorno de Active Directory para simular un escenario real.

### 3.1 Configuración del dominio

Se dispone de un controlador de dominio con Active Directory correctamente configurado y operativo.

- Dominio configurado
- Servicios de Active Directory funcionando correctamente
- El controlador de dominio responde a las peticiones de autenticación

### 3.2 Creación del usuario de dominio

Se crea un usuario de dominio que será el afectado por la incidencia.

- Usuario creado en Active Directory
- Usuario habilitado
- Usuario sin incidencias aparentes en el dominio

### 3.3 Equipo cliente unido al dominio

El equipo cliente se encuentra correctamente unido al dominio.

- El equipo aparece en Active Directory
- El usuario puede iniciar sesión correctamente en condiciones normales
- No existen problemas de conectividad entre el cliente y el controlador de dominio

## 4. Reproducción de la incidencia

Una vez preparado el entorno, se procede a reproducir la incidencia para observar el comportamiento del sistema.

### 4.1 Bloqueo del usuario en Active Directory

Desde el controlador de dominio, se accede a Active Directory Users and Computers y se bloquea manualmente la cuenta del usuario afectado.

Esta acción simula una situación habitual, como múltiples intentos fallidos de inicio de sesión.

### 4.2 Intento de inicio de sesión en el equipo cliente

El usuario intenta iniciar sesión en el equipo cliente utilizando sus credenciales de dominio.

Al introducir el nombre de usuario y la contraseña, el sistema muestra un mensaje de error indicando que no es posible iniciar sesión.

El usuario no puede acceder a su entorno de trabajo con normalidad.

## 5. Diagnóstico de la incidencia

Tras reproducir la incidencia, se procede a realizar el diagnóstico para identificar la causa del problema.

### 5.1 Verificación del estado del usuario

Desde el controlador de dominio, se revisa el estado de la cuenta del usuario en Active Directory.

Se observa que la cuenta del usuario se encuentra **bloqueada**, lo que impide el inicio de sesión en el dominio.

Este bloqueo suele producirse tras varios intentos fallidos de autenticación.

### 5.2 Comprobaciones adicionales

Como parte del proceso de diagnóstico, se realizan comprobaciones adicionales para descartar otros posibles problemas:

- El equipo cliente sigue unido correctamente al dominio
- No existen problemas de conectividad entre el cliente y el controlador de dominio
- No hay incidencias con los servicios de Active Directory

Tras estas comprobaciones, se confirma que la causa de la incidencia es el **bloqueo de la cuenta del usuario**.

## 6. Resolución de la incidencia

Una vez identificada la causa de la incidencia, se procede a aplicar la solución correspondiente.

### 6.1 Desbloqueo de la cuenta de usuario

Desde el controlador de dominio, se accede a Active Directory Users and Computers y se desbloquea la cuenta del usuario afectado.

Esta acción permite restablecer la capacidad del usuario para autenticarse en el dominio.

### 6.2 Restablecimiento de la contraseña (si aplica)

En caso de que sea necesario, se procede al restablecimiento de la contraseña del usuario, asignando una nueva contraseña temporal.

Se informa al usuario de la nueva contraseña y se le indica que deberá cambiarla en el próximo inicio de sesión.

## 7. Verificación y cierre de la incidencia

Tras aplicar la solución, se realiza una verificación para confirmar que la incidencia ha quedado resuelta.

### 7.1 Verificación del inicio de sesión

El usuario intenta nuevamente iniciar sesión en el equipo cliente utilizando sus credenciales de dominio.

El inicio de sesión se realiza correctamente y el usuario puede acceder a su entorno de trabajo sin incidencias.

### 7.2 Cierre de la incidencia

Una vez confirmado el correcto funcionamiento, la incidencia se da por resuelta y se procede a su cierre.

## 8. Conclusiones y lecciones aprendidas

Esta incidencia pone de manifiesto la importancia de verificar el estado de las cuentas de usuario en Active Directory antes de realizar cambios más complejos en el sistema.

Durante la resolución de la incidencia se ha aprendido que:

- Un usuario bloqueado es una causa frecuente de problemas de inicio de sesión
- Es importante revisar primero el estado de la cuenta antes de asumir errores de red o de sistema
- Seguir un proceso ordenado de diagnóstico evita aplicar soluciones innecesarias
- La verificación final es clave antes de cerrar cualquier incidencia

Este tipo de incidencias son habituales en entornos corporativos y su correcta gestión mejora la experiencia del usuario y la eficiencia del soporte técnico.
