---
relacionado: "[[Reputación de la empresa y postura de seguridad]]"
categoria: Tools
---
H8mail es una herramienta de código abierto escrita en Python diseñada para realizar OSINT (Inteligencia de Fuentes Abiertas) y buscar contraseñas comprometidas en filtraciones de datos.  Su función principal es verificar si una dirección de correo electrónico (o usuario/IP) ha aparecido en bases de datos de brechas de seguridad conocidas. 

La herramienta opera consultando múltiples fuentes simultáneamente:

**APIs remotas:** Integra servicios como Have I Been Pwned, Hunter.io, Snusbase, Dehashed y Leak-Lookup, que requieren claves API para acceder a datos completos.

**Archivos locales:** Permite buscar en compilaciones de brechas descargadas, como la Breach Compilation o la Collection #1, utilizando multiprocesamiento para agilizar el análisis de archivos grandes. 

Es utilizada principalmente por profesionales de ciberseguridad, investigadores OSINT y testers de penetración para:

**Respuesta a incidentes:** Verificar rápidamente si credenciales corporativas han sido expuestas. 

**Auditorías de seguridad:** Identificar usuarios con contraseñas comprometidas para forzar cambios o implementar MFA.

**Pruebas de penetración:** Simular ataques de credential stuffing para evaluar la exposición de una organización. 

Además de buscar compromisos, h8mail incluye funciones avanzadas como perseguir correos relacionados (para mapear estructuras organizacionales) y extraer direcciones de correo desde URLs o texto no estructurado mediante expresiones regulares.  Los resultados pueden exportarse en formatos CSV o JSON para su integración en sistemas de gestión de seguridad. 

https://github.com/khast3x/h8mail

```
pip3 install h8mail
```
