---
relacionado: "[[Scaners OSINT]]"
categoria: Tools
---
Es un scanner OSINT Automatizado. Puede realizar escaneos con: dominios, ip, sub-red, ASN, Correos, Número de teléfono y Nombres.

Sus casos de uso son:

> **ALL:** Para obtener toda la información posible.
> 
> **Footprint:** Para obtener la información que el objetivo expone.
> 
> **Investigate:** Para investigar objetivos con comportamiento malicioso.
> 
> **Passive:** Cuando no se desea que el objetivo sospeche que se está analizando.
> 

```
spiderfoot -l 127.0.0.1:5001

# Inicializa la app en la IP y puerto indicado
```

![[spiderfoot - 1.png]]

- Para exportar los resultados a un fichero

```
exitfool *archivo o ruta para todo un fichero* > *archivo*
```

