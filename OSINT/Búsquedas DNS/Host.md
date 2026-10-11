---
relacionado: "[[Búsquedas DNS]]"
categoria: Tools
---
- Se usa para conocer la IP de un host o el nombre de host de una IP
```
host *IP*

host *Nombre de Host Conocido*
```


- Utilizar el comando host con más detalles
```
host -v *IP/Host*
```

- Especificar el tipo de consulta
```
host -t txt *IP/Host*

host -t SOA *IP/Host*

host -t ns *IP/Host*
```
