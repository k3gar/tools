---
relacionado: "[[Resolución de Nombres de Windows y ataques de SMB]]"
categoria: Tools
---
**smbclient** es una herramienta de línea de comandos del paquete **Samba** que permite a sistemas Linux interactuar con recursos compartidos de archivos y carpetas en servidores **Windows** o Samba utilizando el protocolo **SMB/CIFS**. 

Su funcionamiento es similar al de un cliente **FTP**, ofreciendo comandos para listar directorios, navegar entre carpetas, y **subir o descargar archivos** de forma interactiva o mediante scripts.  Se utiliza comúnmente para:

- **Enumerar recursos:** Listar las carpetas compartidas disponibles en un servidor remoto. 
- **Transferencia de archivos:** Copiar archivos locales al servidor o descargarlos desde él. 
- **Pruebas de seguridad:** Verificar permisos, accesos anónimos o vulnerabilidades en configuraciones SMB durante auditorías. 
    
Por defecto, se conecta a través del **puerto TCP 139** (o 445 en versiones modernas de Windows sin NetBIOS).  En distribuciones como **Kali Linux**, suele estar pre-instalado para facilitar tareas de reconocimiento de red.

**Ejemplos:**

```
smbclient --help
```

- Enumerar los recursos compartidos en un host.
```
smbclient -L //172.17.0.2/
```

- Conectarse a un recurso compartido.
```
smbclient //*ip*/*recurso*
```

- Cargar un archivo a un servidor de destino:
```
put *local_file_name* *remote_file_name*
```

- Ver el contenido del recurso compartido:
```
dir
```

