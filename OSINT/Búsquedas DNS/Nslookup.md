---
relacionado: "[[Búsquedas DNS]]"
categoria: Tools
---
- Establece el tipo de registro a consultar

```
nslookup
> set type=AAAA
> *domino/host*
```

- Sirve para resolver el nombre de dominio desde un DNS específico

```
nslookup *dominio* 8.8.8.8
```

- El tipo **any** sirve para traer todos los registros

```
nslookup -type=any netacad.com 8.8.8.8
```

