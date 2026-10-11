---
relacionado: "[[Tipos de enumeración]]"
categoria: Tools
---
Es una herramienta de manipulación de paquetes interactiva y flexible escrita en **Python.** Permite esnifar, generar, enviar y analizar tráfico de red, además de realizar escaneos, pruebas de protocolos y creación de herramientas de diagnóstico mediante código Python.
### Características principales:

- **Manipulación de paquetes**: Construcción manual de paquetes capa por capa (IP, TCP, UDP, ICMP, etc.) usando valores predeterminados o personalizados. 
    
- **Sniffing**: Captura de tráfico de red en tiempo real con filtros tipo libpcap. 
    
- **Automatización**: Integrable como librería en scripts de Python para crear utilidades de escaneo (como `nmap` o `hping`) o detección de vulnerabilidades. 
    
- **Multiplataforma**: Compatible con Linux, macOS, BSD y Windows, funcionando en modo interactivo o programático.

##### Ejecución:

- Crea un paquete ICMP simple.
```
>>> send(IP(dst="IP")/ICMP()/"malicious-payload")
```

- Enumera los formatos y protocolos disponibles
```
>>> ls()
```

- Muestra las opciones y campos de un protocolo.
```
>>> ls(*protocolo*)
```

- Para desplazarse por las capas y los protocolos de Scrapy.
```
>>> explore()
```

- Recopila el tráfico mediante la interfaz predeterminada.
```
>>> sniff()
```

- Para guardar la salida anterior en una variable.
```
>>> a = _
```

- Para ver el tráfico capturado.
```
>>> a.summary()
```

- Capturar el tráfico de una interfaz específica.
  Luego, guardamos la salida en variable.
```
>>> sniff(iface="*nombre interfaz*")
```

- Filtra las solicitudes y se detiene al llegar al valor.
```
>>> sniff(iface="*nombre interfaz*", filter="protocol", count=*número*)

Ej:
>>> sniff(iface="br-internal", filter="icmp", count=10) 
```

- Para ver el tráfico con un valor correlativo.
```
>>> a.nsummary()
```

- Para obtener una salida detallada.
```
>>> a[*numero*]
```

- Para guardar los datos en archivo pcap.
```
>>> wrpcap("nombre del archivo.pcap", nombre de variable)
```


##### Crear y enviar un paquete ICMP:

==En una terminal:==
```
>>> sniff(iface="br-internal")
```

==En otra terminal:==
```
>>> scapy
>>> send(IP(dst="10.6.6.23")/ICMP()/"This is a test")
```

##### Crear y enviar un paquete TCP SYN:
> Escuchamos en la interfaz

- Envía un paquete IP al host 10.6.6.23, al puerto TCP 445, con el indicados S (SYN) activado.
```
send(IP(dst="10.6.6.23")/TCP(dport=445, flag="S"))
```

##### Capturar y guardar el tráfico de red:

```
sudo tcpdump -i eth0 -s 0 -w packetdump.pcap
```

- **-i** permite especificar la interfaz en la que se escuchará. Si no se especifica, capturará todo el tráfico.
- **-s** especifica la longitud de la instantánea de cada paquete.
- **-w** se usa para escribir el resultado del comando en un archivo.