---
relacionado: "[[Vulnerabilidades Basadas en Aplicaciones]]"
categoria: Tools
---
Nikto es un **escáner de vulnerabilidades de servidores web** de código abierto, diseñado para profesionales de la seguridad, pentesters y administradores de sistemas. Su función principal es realizar pruebas automatizadas contra servidores HTTP/HTTPS para identificar **más de 8.000** archivos potencialmente peligrosos, programas inseguros, **versiones desactualizadas** de software y **configuraciones erróneas** comunes.

La herramienta funciona enviando múltiples peticiones HTTP al objetivo y comparando las respuestas con una base de datos actualizada de vulnerabilidades conocidas. Es importante destacar que **Nikto no explota** las vulnerabilidades encontradas, sino que se limita a **identificarlas** y generar informes detallados, actuando como una capa inicial de reconocimiento dentro de una auditoría de seguridad web.

### Comandos:

**nikto -h scanme.nmap.org**

**nikto -h https://nmap.org -ssl**                 (Para escanear dominios con HTTPS habilitado)

**nikto -h IP_list.txt**                                        (Para escanear listas)

**nikto -h 172.17.0.2 -o scan_results.htm**   (Para exportarlo de forma más legible en un archivo htm)

**nikto -h 172.17.0.2 -o scan_results.txt -Format csv**       (Para especificar un formato de salida, en este caso, csv)