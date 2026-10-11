---
relacionado: "[[Explotando las Vulnerabilidades Basadas en la Autenticación]]"
---
RainbowCrack es una herramienta de código abierto desarrollada por **Zhu Shuanglei** que genera y utiliza **tablas rainbow** (tablas de arcoíris) para el descifrado de contraseñas mediante el ataque de **compensación de tiempo-memoria** (time-memory trade-off).

A diferencia de los crackeadores por fuerza bruta que calculan los hashes en tiempo real, **RainbowCrack** realiza una costosa precomputación de combinaciones de texto plano y sus hashes, almacenándolos en archivos masivos. Una vez generadas las tablas, el proceso de descifrado es **cientos de veces más rápido**, permitiendo recuperar contraseñas de algoritmos como **LM, NTLM, MD5, SHA1 y SHA256** en segundos o minutos, siempre que las tablas cubran el espacio de caracteres y longitud de la contraseña objetivo.

- **Funcionamiento**: Utiliza cadenas de hashes con funciones de reducción variables para minimizar colisiones y optimizar el uso de memoria.
    
- **Rendimiento**: Soporta aceleración por **GPU** (CUDA para NVIDIA, OpenCL para AMD) y computación multinúcleo para acelerar las búsquedas en tablas grandes.
    
- **Limitaciones**: Su eficacia disminuye significativamente contra contraseñas con **salt** (sal) o algoritmos de hash muy largos y complejos, ya que el tamaño de las tablas requerido se vuelve imprácticamente grande.
    
- **Uso ético**: Se emplea principalmente en **pruebas de penetración**, auditorías de seguridad y forense digital para evaluar la fortaleza de las contraseñas almacenadas, requiriendo autorización explícita para su uso.

## Uso:

```
sudo apt install rainbowcrack
```
Para instalar RainbowCrack

```
sudo rtgen md5 loweralpha 1 3 0 1000 1000 0

cd /usr/share/rainbowcrack

```
Este comando crea una tabla de arcoíris que puede descifrar contraseñas de tres caracteres y solo letras minúsculas. La aplicación creó un archivo con 1000 entradas. La creación de tablas de arcoíris más complejas puede llevar mucho tiempo y consumir muchos recursos.

*La tabla de arcoíris recién creada debe estar en el directorio como un archivo **.rt**.*

### Ordene la tabla del arcoíris

```
sudo rtsort .
```
Ordena las tablas de Arcoiris

```
echo -n 'dog' | md5sum | awk '{print $1}'
```
Este comando genera un hash para una contraseña simple de 3 caracteres que luego pueda descifrarse.

```
rcrack . -h 06d80eb0c50b49a509b492424e8c805
```
Descifra el hash con la tabla arcoíris usando RainbowCrack. RainbowCrack debería descifrar el hash y revelar la contraseña **dog**.


```
rcrack . -l ~/my_rainbow_hashes.txt
```
La opción **-l** le dice a rcrack que use un archivo de lista hash como entrada.

![[Pasted image 20261003170620.png]]