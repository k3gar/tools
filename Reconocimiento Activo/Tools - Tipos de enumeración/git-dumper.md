---
relacionado: "[[Tipos de enumeración]]"
categoria: Tools
---
**Git-dumper** es una herramienta de código abierto utilizada en pruebas de penetración y seguridad informática para **volcar o extraer el contenido de un repositorio Git** (.git) que ha sido expuesto accidentalmente en un servidor web.

Su funcionamiento principal consiste en:

- **Reconstruir el repositorio**: Descarga los archivos ocultos del directorio `.git` (como objetos, referencias y registros) para recrear localmente el código fuente y el historial de versiones del sitio.

> **Instalación:**
> 
> pipx install git-dumper


**Uso:**

`git-dumper http://10.64.187.19:8080/.git loot`
