---
relacionado: "[[Scaners OSINT]]"
categoria: Tools
---
Es un marco OSINT similar al marco de Metaexploit. Consta de una serie de módulos que se pueden ejecutar en sus propios workspaces. Los módulos se pueden configurar con ajustes específicos del módulo.

## Commandos:

- Inicializa el entorno. Se trabaja dentro de su propio marco.
```
recon-ng
```


- Commandos para listar, eliminar, crear o cargar un workspace.
```
worwspaces list

workspaces remove

workspaces create

workspaces load
```

- Marketplace
  
```
marketplace info *modulo*  #Obtener inf. de un módulo

marketplace install *nombre módulo* 

marketplace search   #Permite mostrar módulos disponibles o buscar agregando una                       palabra clave al final
```

- Modules
  
```
modules load *modulo*    #Cargar un módulo

modules search           #Muestra los módulos instalados

modules reload           #Recargar, limpiar y reindexar los módulos instalados.
```


>  **Luego de cargar un módulo**

```
options list                     # Lista los parámetros configurables del módulo

options set *parametro* *valor*  # Establece un valor al parámetro

options unset *parametro*        # Cambia el valor de ese parámetro a None

show *parametro*                 # Muestra datos de categorías específicas. Por                                     ejemplo, show hosts, muestra los hosts                                           encontrados
```

```
run          # Ejecuta el módulo

dashboard    # Proporciona un resumen de la información recopilada
```


> **¡En otra terminal!**

```
recon-web      # Lanza una interfaz web para explorar los datos
```

### Recon-ng

![[Recon-ng.png]]

### Recon-web

![[Recon-web.png]]
