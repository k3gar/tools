---
relacionado: "[[Resolución de Nombres de Windows y ataques de SMB]]"
categoria: Tools
---
**Es una herramienta de código abierto escrita en Perl utilizada para enumerar y extraer información de sistemas Windows y Samba mediante el protocolo SMB.** Funciona como un envoltorio que consolida las funcionalidades de otras herramientas de Samba (como 
`smbclient`, `rpclient`, `net` y `nmblookup`) en una interfaz única, ofreciendo capacidades similares a la antigua `enum.exe` de BindView. 

Se emplea principalmente en la fase de reconocimiento de pruebas de penetración y ciberseguridad para recopilar datos sin necesidad de credenciales previas (o usando autenticación nula), operando típicamente en los puertos 139 y 445. Sus características clave incluyen:

- **Enumeración de usuarios y grupos:** Lista cuentas locales y de dominio, incluyendo miembros. 
- **Enumeración de recursos compartidos:** Identifica carpetas y archivos SMB accesibles. 
- **Obtención de políticas de contraseña:** Extrae configuraciones de seguridad como longitud mínima. 
- **Identificación del sistema:** Determina la versión del sistema operativo, el dominio o grupo de trabajo. 
- **RID Cycling:** Técnica de fuerza bruta sobre identificadores relativos (RID) para descubrir usuarios cuando el acceso anónimo está parcialmente restringido.

### Sintaxis:

- **-U:** Busca usuarios configurados.
- **-S:** Obtiene una lista de archivos compartidos.
- **-G:** Obtiene una línea de los grupos y sus miembros.
- **-P:** Enumera las políticas de contraseñas.
- **-i:** Obtiene una lista de impresoras
- **-v:** ver

**Ejemplo:**

```
enum4linux -P 172.17.0.2
```

> Enum4linux tiene una opción que combina las opciones -U, -S, -G, -P, -r, -o, -n, -i en un solo comando. Utilizando el argumento **-a**.

