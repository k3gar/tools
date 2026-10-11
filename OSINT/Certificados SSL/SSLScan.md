---
relacionado: "[[Búsqueda de Info. a partir de certificados SSL]]"
categoria: Tools
---
Es una herramienta de línea de comandos de código abierto diseñada para Linux que escanea servicios habilitados para SSL/TLS (como HTTPS, SMTP, FTP) con el fin de identificar las suites de cifrado soportadas y evaluar la seguridad de la configuración.

-  Consulta los servicios SSL para determinar qué cifrados se admiten

```
sslscan *dominio*
```

- Permite exportar los resultados en un archivo html. (**aha** se debe instalar)

```
sslscan *dominio* | aha > archivo.html
```

##### Código de color en SSLScan

- **Texto de fondo rojos:** Cifrado NULO. No se utilizó cifrado.
- **Rojo:** Cifrado roto (Menor o igual a 40 bits), protocolo vulnerable o roto, como SSLv2 o SSLv3, o algoritmo de firma de certificados como MD5.
- **Amarillo:** Cifrado débil (Menor o igual a 56 bits) o algoritmo de firma débil, como SHA-1.
- **Violeta:** Cifrado anónimo, como ADH o AECDH.