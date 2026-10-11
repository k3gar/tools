---
relacionado: "[[Ataques de ruta (MITM)]]"
categoria: Tools
---
Ettercap se usa para realizar ataques en ruta (MITM). El objetivo de un ataque en ruta es interceptar el tráfico entre dispositivos para obtener información que pueda utilizarse para hacerse pasar por el objetivo o alterar los datos que se transmiten. El atacante se encuentra ”entre” dos hosts en comunicación. En los ataques en ruta, el hacker no necesita comprometer el dispositivo objetivo, sino que solo puede "olfatear" o rastrear el tráfico que va y viene entre el objetivo y el destino. Ettercap se utiliza como herramienta en ruta y la máquina de ataque está en la misma red IP que la víctima.

###  Configuración de un ataque de suplantación de ARP

1. Visualizamos los vecinos arp con el comando ``ip neighbor`` 
2. Se ejecuta el comando ``ettercap -h``  
3. Inicie la interfaz gráfica de usuario de Ettercap GTK+ con el comando ``sudo ettercap -G`` 
4. Cambie la interfaz de detección a **br-internal**, que es la interfaz configurada en la red virtual 10.6.6.0/24, cambiando el valor en la lista desplegable **Setup> Primary** **Interface**.
5. Haga clic en el icono de la **casilla de verificación** en la parte superior derecha de la pantalla de Ettercap para continuar. Aparece un mensaje en la parte inferior de la pantalla que indica que se ha iniciado el rastreo unificado.
6. En la ventana GUI de Ettercap, abra la ventana Hosts List haciendo clic en el menú de Ettercap (icono de tres puntos). Seleccione la entrada **Hosts** y luego **Hosts List**. Haga clic en el icono **Scan for hosts** (lupa) en la parte superior izquierda de la barra de menús para buscar hosts vecinos. Aparece una lista de los hosts detectados en la red 10.6.6.0/24 en la ventana Host List (Lista de hosts).
7. Defina los dispositivos de origen y destino del ataque. Para ello, haga clic en la dirección IP **10.6.6.23** en la ventana para resaltar el host del usuario de destino. Haga clic en el botón **Add to Target 1** en la parte inferior de la ventana Host List (Lista de hosts). Esto define el host del usuario como Target 1 (Objetivo 1).
8. Haga clic en la dirección IP del servidor web de destino en **10.6.6.13** para resaltar la línea. Haga clic en el botón **Add to Target 2** en la parte inferior de la ventana del host.

Cualquier dirección IP/MAC especificada como Target 1 tendrá todo su tráfico desviado a través de la computadora atacante que ejecuta Ettercap. En esta práctica de laboratorio, la computadora atacante es la máquina Kali Linux en 10.6.6.1. Todas las demás computadoras de la subred, excepto los destinos, se comunicarán normalmente.

9. Haga clic en el icono de MITM en la barra de menús (el primer icono circular en la parte superior derecha). Seleccione **ARP Poisoning...** en el menú desplegable. Verifique que **Sniff remote connections** (Rastrear conexiones remotas) esté seleccionado. Haga clic en **OK**.
10. Se inicia la explotación MITM. Si la detección no se inicia inmediatamente, haga clic en la opción **Start** (botón de reproducción) a la izquierda en el menú superior.

### Paso 2: Realizar el ataque de suplantación de ARP.

1. Regrese a la ventana de terminal que ejecuta la sesión SSH con el host del usuario de destino en 10.6.6.23. Repita el ping a 10.6.6.13.

labuser@3fb0515ea2f7:/$ **ping -c 5 10.6.6.13**

2. Utilice el comando **ip neighbor** para ver la tabla ARP en 10.6.6.23 nuevamente. Tenga en cuenta la dirección MAC enumerada para 10.6.6.13.

## Parte 3: Usar Wireshark para observar el ataque de suplantación de ARP

### Paso 1: Seleccionar los dispositivos de destino y realizar el ataque MITM con la CLI

1. El comando **ettercap -T** ejecuta Ettercap en modo texto, en lugar de utilizar la interfaz gráfica de usuario. La sintaxis para iniciar Ettercap y especificar los destinos es: **sudo ettercap -T [_opciones_] -q -i [_interfaz_] -- write [_nombre de archivo_] -- mitm arp /[_target 1_]// / [_target 2_] //**

Ejemplo:

> **sudo** **ettercap -T -q -i br-internal --write mitm-saved.pcap --mitm arp /10.6.6.23// /10.6.6.13//**

