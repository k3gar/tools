---
relacionado: "[[Explotando las Vulnerabilidades Basadas en la Autenticación]]"
---
**John the Ripper** es una herramienta de código abierto y multiplataforma diseñada para la **recuperación y auditoría de contraseñas**, ampliamente utilizada por profesionales de ciberseguridad y administradores de sistemas. Lanzada originalmente en **1996** bajo la licencia **GPLv2+**, su función principal es detectar contraseñas débiles mediante **ataques de diccionario** y **fuerza bruta** para descifrar hashes criptográficos (como MD5, SHA-1, DES y NTLM).

La herramienta destaca por su capacidad para **autodetectar el tipo de cifrado** y su optimización para diferentes arquitecturas de procesadores, funcionando en sistemas Unix, Linux (incluyendo Kali Linux), Windows y macOS. Además de ser un estándar en pruebas de penetración, se emplea para verificar la robustez de las claves de usuario, permitiendo a los administradores identificar vulnerabilidades antes de que sean explotadas.

### Uso:


```
john -h              -----> para ver el archivo de ayuda de John the Ripper
```

```
john --format=raw-md5 my_pw_hashes.txt
```
En este caso, John usa una lista mínima de palabras de contraseña de manera predeterminada para descifrar rápidamente las contraseñas comunes.

Si deja que John continúe ejecutándose el tiempo suficiente, eventualmente descifrará las contraseñas restantes. (Tenga en cuenta que esto puede demorar entre 10 y 20 minutos). Presione **Ctrl-C** o **q** para cancelar en cualquier momento después de haber descifrado algunas contraseñas, si lo desea.


```
john --wordlist=/usr/share/wordlists/rockyou.txt --format=raw-md5 my_pw_hashes.txt
```
Utilice el siguiente comando para indicarle a John the Ripper que utilice la lista de palabras rockyou.txt.

## **Fuerza Bruta**

```
john --incremental my_pw_hashes.txt
```

El **modo incremental** de John the Ripper es un ataque de **fuerza bruta** que intenta descifrar contraseñas probando sistemáticamente **todas las combinaciones posibles** de caracteres dentro de un conjunto definido.

A diferencia del modo de diccionario, que usa listas predefinidas, el modo incremental genera contraseñas sobre la marcha y prioriza las combinaciones más probables basándose en **frecuencias de trigrafos** (estadísticas de letras y posiciones extraídas de contraseñas previamente descifradas).

### Características principales:

- **Configuración:** Se activa con el parámetro `--incremental[=MODE]` (ej. `--incremental:ASCII` o `--incremental:Alpha`).
    
- **Conjuntos de caracteres:** Permite limitar la búsqueda a categorías específicas como **dígitos**, **letras minúsculas**, **alphanuméricas** o **ASCII completo** para reducir el tiempo de cálculo.
    
- **Eficiencia:** Es extremadamente lento para contraseñas largas o complejas, pero muy efectivo para contraseñas cortas o simples si se restringe el espacio de búsqueda.
    
- **Persistencia:** Las contraseñas ya descifradas se guardan en el archivo `john.pot`, por lo que el modo incremental las omitirá en ejecuciones posteriores para no repetirlas.

Se limita de varias formas, todas a través del archivo de configuración `john.conf`:

### 1. Usar modos predefinidos

Cada modo ya tiene un conjunto fijo de caracteres:

|   |   |
|---|---|
|Modo|Caracteres|
|`Digits`|0-9 (10)|
|`Lower`|a-z (26)|
|`Alpha`|a-z A-Z (52)|
|`Alnum`|a-z A-Z 0-9 (62)|
|`ASCII`|95 imprimibles|

```
john --incremental=Alpha passwd.txt
```

### 2. Definir un modo personalizado en `john.conf`

Añade una sección `[Incremental:NOMBRE]` con estos parámetros:

```
[Incremental:MiModo]
File = $JOHN/alpha.chr      # archivo .chr con los caracteres y frecuencias
MinLen = 5                  # longitud mínima
MaxLen = 8                  # longitud máxima
CharCount = 26              # nº máx. de caracteres a usar (limita aún más)
Extra = 1234567890          # caracteres extra no incluidos en el .chr
```

Luego se invoca con `john --incremental=MiModo passwd.txt`.

- **`File`**: apunta al archivo `.chr` que define _qué_ caracteres y en _qué orden/frecuencia_ se prueban.
    
- **`CharCount`**: si el `.chr` tiene 95 caracteres pero pones `CharCount = 25`, John solo usará los 25 más frecuentes.
    
- **`Extra`**: añade caracteres que no están en el `.chr` (se consideran los menos probables).

## Muestre sus contraseñas descifradas.

```
john --show --format=raw-md5 my_pw_hashes.txt
```

![[Pasted image 20261003153707.png]]

![[Pasted image 20261003153726.png]]