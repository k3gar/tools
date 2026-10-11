---
relacionado: "[[Vulnerabilidades Basadas en Aplicaciones]]"
categoria: Tools
---
**Greenbone Vulnerability Management (GVM)**, anteriormente conocido como **OpenVAS**, es un escáner de vulnerabilidades de código abierto integrado en **Kali Linux** diseñado para detectar fallos de seguridad en redes y sistemas.

- **Función principal:** Realiza auditorías de seguridad automatizadas mediante pruebas de vulnerabilidades de red (NVTs) actualizadas diariamente.
    
- **Arquitectura:** Es un marco de trabajo que integra el motor de escaneo, el daemon de gestión (**gvmd**) y una interfaz web (**Greenbone Security Assistant**) para la gestión completa de vulnerabilidades.
    
- **Origen:** Proviene de una bifurcación del proyecto **Nessus** y se consolidó tras la rebranding de OpenVAS para ofrecer una solución profesional y gratuita.
    
- **Instalación en Kali:** Se instala fácilmente mediante el gestor de paquetes con `sudo apt install gvm` y se inicializa con `sudo gvm-setup`, que configura la base de datos PostgreSQL y descarga los feeds de vulnerabilidades.
![[Pasted image 20260915152809.png]]


#### Inicializarlo:

`sudo gvm-start`

> **Nota**: Es posible que reciba el mensaje “**Los servicios de GVM ya se están ejecutando**”. Si el navegador no se abre automáticamente, inícielo manualmente y vaya a https://127.0.0.1:9392. Aparecerá la pantalla de inicio de sesión de Greenbone Security Assistant en el navegador.

### Escanear un host.

En este paso, escaneará el host vulnerable Metasploitable con el escáner de GVM. Este análisis puede llevar algún tiempo, así que esté preparado para esperar al menos 20 minutos o más hasta que finalice.

1. La GUI de la aplicación GVM Scanner debe abrirse en el navegador. Seleccione **Scans -> Tasks** en la barra de menús. En la parte superior izquierda de la ventana **Tasks** aparecen tres iconos. Seleccione el icono **Task Wizard** que parece una varita mágica. Elija **Advanced Task Wizard** en el menú desplegable.
2. En la ventana del Advanced Task Wizard, introduzca **Metasploitable** como nombre del análisis. En el campo Target Host(s), ingrese la dirección IP de Metasploitable, **172.17.0.2**. Deje el resto de la configuración sin cambios y haga clic en **Create** para crear la tarea e iniciar el análisis.
3. La ventana Task indica que la tarea se está ejecutando. En la parte inferior de la ventana, aparece la tarea Metasploitable y la barra de estado muestra el porcentaje completado. Espere hasta que el estado muestre Listo (100% completado). Esto puede demorar 30 minutos o más.
4. Haga clic en el número **1** en la columna Reports (Informes) de la fila Metasploitable, junto al indicador de estado. La lista de informes se abre con una entrada para el día y la hora actuales y la tarea denominada Metasploitable.


![[Pasted image 20260915170731.png]]

> Puede copiar los archivos /etc/passwd y /etc/shadow para obtener los nombres de usuario y las contraseñas con hash (cifradas).

