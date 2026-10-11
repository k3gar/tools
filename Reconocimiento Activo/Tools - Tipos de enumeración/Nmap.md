---
relacionado: "[[Reconocimiento Activo]]"
categoria: Tools
---
- Respuestas del escaneo SYN en Nmap

| Estado   | Tipo                                     | Descripción                                  |
| -------- | ---------------------------------------- | -------------------------------------------- |
| Abierto  | TCP SYN-ACK                              | El servidor está escuchando en el puerto.    |
| Cerrado  | TCP RST                                  | El servidor no está escuchando en el puerto. |
| Filtrado | Sin Respuesta o destino ICMP inaccesible | El puerto está protegido con costafuegos.    |

### Tipos de análisis Nmap

- #### Escaneo de conexión TCP (-sT)
	Establece una conexión TCP completa con el dispositivo de destino. Como crea una conexión completa, crea más tráfico (por lo tanto, tarda más).
	
	Es el escaneo por defecto. Se debe de usar solo cuando el escaneo SYN no es opción.
	
	**Respuestas:**

| Estado   | Tipo                                     | Descripción                                  |
| -------- | ---------------------------------------- | -------------------------------------------- |
| Abierto  | TCP SYN-ACK                              | El servidor está escuchando en el puerto.    |
| Cerrado  | TCP RST                                  | El servidor no está escuchando en el puerto. |
| Filtrado | Sin Respuesta o destino ICMP inaccesible | El puerto está protegido con costafuegos.    |
> Un escaneo TCP envía un paquete adicional por escaneo, lo que aumenta el ruido en la red y puede activar alarmas que un escaneo medio abierto no activaría.
![[Escaneo de conexion TCP.png]]
- #### Escaneo UDP (-sU)
	
	La mayoría de casos se buscará puertos TCP, sin embargo, puede haber casos en los que deba buscarse puertos UDP, por ejemplo, si se busca enumerar un servidor DNS, SNMP o DHCP.
	
	**Respuestas:**

| Estado           | Tipo                              | Descripción                                 |
| ---------------- | --------------------------------- | ------------------------------------------- |
| Abierto          | Datos devueltos por el puerto     | Se esta escuchando en el puerto             |
| Cerrado          | Mensaje de error de ICMP recibido | El servicio no está escuchando              |
| Abierto/Filtrado | Sin respuesta de ICMP             | El puerto está protegido o venció el tiempo |
![[Escaneo UDP.png]]

- #### Escaneo FIN de TCP (-sF)
	Un filtro de red o Firewalls pueden detectar un escaneo de sincronización. 
	En tal caso, empleamos un escaneo diferente. Con el escaneo TCP FIN, se envía un paquete FIN al puerto de destino.
	
	Si el puerto está cerrado, el sistema de destino devuelve un paquete RST. Si no se recibe nada del destino, se puede considerar al puerto abierto, porque el comportamiento normal sería el paquete FIN.
	
> Un escaneo FIN de TCP no es útil en sistemas basados en Windows, ya que responden con paquetes RST, sin importar el estado del puerto.

	

| Estado           | Tipo                                     | Descripción                              |
| ---------------- | ---------------------------------------- | ---------------------------------------- |
| Filtrado         | Se recibió un error de ICMP inalcanzable | El puerto cerrado debe responder con RST |
| Cerrado          | Paquete RST recibido                     | El puerto cerrado debe responder con RST |
| Abierto/Filtrado | No se recibió respuesta                  | El puerto abierto debe descartar el FIN  |

![[Escaneo FIN de TCP.png]]

- #### Escaneo de detección de host (-sn)
	Es uno de los tipos de escaneo más comunes, usados para enumerar hosts en una red, porque puede usar diferentes tipos de mensajes ICMP.
	
> 	El valor predeterminado para la operación de escaneo -sn es enviar un paquete eco ICMP al destino, un TCP SYN al puerto 443, un TCP ACK al puerto 80 y una solicitud de marca de tiempo ICMP

- #### Opciones de sincronización (-T0-5)
	Permiten determinar cuán agresivo será un escaneo, mientras deja que Nmap elija los valores de sincronización exactos.
	
	**-T0 (Paranoico):** Muy lento, se usa para la evasión de IDS.
	**-T1 (Furtivo):** Bastante lento, se usa para la evasión de IDS.
	**-T2 (Educado):** Se ralentiza para consumir menos ancho de banda, se ejecuta aprox. 10  veces más lento que el valor predeterminado.
	**-T3 (Normal):** Predeterminado, un módulo de tiempo dinámico.
	**-T4 (Agresivo):** Supone una red rápida y confiable, y puede abrumar al objetivo.
	**-T5 (Demente):**  Muy agresivo, probablemente abrumará o perderá los puertos abiertos.


#### Nmap opciones de comando.

- **`-sC`**: Equivale a `--script=default`; ejecuta un conjunto seguro y útil de scripts para detectar vulnerabilidades básicas, metadatos de servicios y configuraciones por defecto.

- **`-sV`**: Sonda los puertos abiertos para determinar el nombre y la versión exacta del servicio (por ejemplo, identificar si es Apache 2.4.66 o OpenSSH 8.9), lo cual es crucial para buscar vulnerabilidades específicas.

- **`-oN`** en **Nmap** se utiliza para guardar la salida del escaneo en un **formato normal** (similar a la visualización en pantalla) dentro de un archivo de texto.