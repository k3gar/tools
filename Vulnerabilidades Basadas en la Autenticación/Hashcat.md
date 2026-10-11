---
relacionado: "[[Explotando las Vulnerabilidades Basadas en la Autenticación]]"
---
Hashcat es la herramienta de **recuperación y descifrado de contraseñas más rápida y avanzada** del mundo, diseñada para probar la robustez de las credenciales en auditorías de seguridad y pentesting. Es un software de **código abierto** (licencia MIT) que opera mediante la comparación de hashes calculados contra valores objetivo, aprovechando la potencia de procesamiento masivo de las **GPU** (CUDA, ROCm, OpenCL) y CPUs para ejecutar ataques de fuerza bruta, diccionario y máscaras a alta velocidad.

Soporta más de **450 algoritmos de hashing** (como MD5, NTLM, SHA) y es compatible con **Linux, Windows y macOS**. Su uso es legítimo para auditar la seguridad de sistemas propios, recuperar contraseñas olvidadas o competir en CTFs, aunque su capacidad para romper hashes complejos en minutos también la convierte en una herramienta utilizada con fines maliciosos si se accede a credenciales sin autorización.

### Uso:


```
sudo hashcat -m 0 -a 0 -o cracked.txt my_pw_hashes.txt /usr/share/wordlists/rockyou.txt
```
Este comando genera las contraseñas descifradas en el nuevo archivo **cracked.txt**, utilizando la lista de palabras **rockyou.txt**. La opción -m define el tipo de hash y -a define el modo de ataque.

![[Pasted image 20261003152259.png]]