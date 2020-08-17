# Redes1-Practica1
Generación y configuración de una topología de red pequeña simulada en GNS3.

## Topología de Red
La topología implementada consiste en:
- Tres host simulados 
- Una vitrualización de la distribución del sistema operativo linux llamado Tiny Linux Core en su versión 8.2.1
- Dos switch capa 2
- Un router c3725

Estos dispositivos se dividen en dos segmentos de red, uno correspondiente a la direccióń 192.168.14.0 y otro a la dirección 192.168.19.0.


![image](https://github.com/EmmGarci4/Redes1-Practica1_201610649/blob/master/images-readme/project.png)

## Configuración

### Configuración de Host Simulados
Para realizar la configuración se debe tener el dispositivo encendido e ingresar por medio de la terminal. 

1. Ejecutar el siguiente comando para verificar la información de red de la computadora: `show ip`

   ![image](https://github.com/EmmGarci4/Redes1-Practica1_201610649/blob/master/images-readme/host-config/host-step-1.png)

2. Con el siguiente comando configurar la IP y la puerta de enlace:`ip <IP> <GATEWAY>`. 

   En este caso configuraremos el host simulado con ip 192.168.19.15

   ![image](https://github.com/EmmGarci4/Redes1-Practica1_201610649/blob/master/images-readme/host-config/host-step-2.png)
 
3. Guardar la configuración con el comando `save `

   ![image](https://github.com/EmmGarci4/Redes1-Practica1_201610649/blob/master/images-readme/host-config/host-step-3.png)


Seguir los pasos indicados para configurar los dos host faltantes.

#### Host con IP 192.168.19.15

![image](https://github.com/EmmGarci4/Redes1-Practica1_201610649/blob/master/images-readme/host-config/host2.png)

#### Host con IP 192.168.19.30

![image](https://github.com/EmmGarci4/Redes1-Practica1_201610649/blob/master/images-readme/host-config/host3.png)


### Configuración de Host Virtualizado
1. Descargar la imagen ISO del sistema operativo [Tiny Linux](http://tinycorelinux.net/). Para el caso de esta práctica se ha utilizado la versión 8.2.1 

2. Crear una máquina virtual con la imagen descargada.

3. En GNS3, ir al panel de preferencias 

4. En el panel de preferencias, seleccionar la sección de virtualbox VMs y dar clic en 'New'

5. GNS3 listará las máquinas virtuales disponibles, seleccionar la máquina creada en el paso dos

6. Seleccionar 'Apply' para guardar la configuración y luego 'Ok'

Y listo, encontrará la maquina virtual en el panel de hosts.

### Configuración de Router
Para realizar la configuración se debe tener el dispositivo encendido e ingresar por medio de la terminal. 

1. Verificar el estado de las interfaces del router con el comando: `sh ip int brief`

   ![image](https://github.com/EmmGarci4/Redes1-Practica1_201610649/blob/master/images-readme/router-config/router-step-1.png)
  
2. Ejecutar siguiente comando para etrar al menú de configuración del router:
    ```conf t ```
    
    ![image](https://github.com/EmmGarci4/Redes1-Practica1_201610649/blob/master/images-readme/router-config/router-step-2.png)
        
3. Indicar la interfaz a configurar con el comando 
  ```int f0/ <x>```
en donde x es el número identificador de la interfaz.
En este caso configuraremos la interfaz f0/0 para el segmento de red 192.168.19.0

   ![image](https://github.com/EmmGarci4/Redes1-Practica1_201610649/blob/master/images-readme/router-config/router-step-3.png)
   
4. Ejecutar el siguiente comando para configurar la IP de la interfaz:
  ```ip address <IP> <MASCARA DE RED>```

   ![image](https://github.com/EmmGarci4/Redes1-Practica1_201610649/blob/master/images-readme/router-config/router-step-4.png)
   
5. Activar la interfaz con el comando 
  ```no shut```

   ![image](https://github.com/EmmGarci4/Redes1-Practica1_201610649/blob/master/images-readme/router-config/router-step-5.png)

6. Salir de la configuración de la interfaz con el comando  `exit`

   ![image](https://github.com/EmmGarci4/Redes1-Practica1_201610649/blob/master/images-readme/router-config/router-step-6.png)
  
7. Configurar la interfaz f0/1 para el segmento de red 192.168.14.0 siguiendo los pasos anteriores

   ![image](https://github.com/EmmGarci4/Redes1-Practica1_201610649/blob/master/images-readme/router-config/router-step-7.png)

  
8. Guardar la configuración del router con el comando 
  ```wr```
   
   ![image](https://github.com/EmmGarci4/Redes1-Practica1_201610649/blob/master/images-readme/router-config/router-step-8.png)
  
Finalmente al ejecutar el comando `sh ip int brief` se puede observar el cambio de la configuración del router

![image](https://github.com/EmmGarci4/Redes1-Practica1_201610649/blob/master/images-readme/router-config/router-step-final.png)


### Agregar Imagen de Dispositivo Router a GNS3

1. Descargar imagen de dispositivo

2. Acceder al panel de preferencias

3. En el panel de preferencias, seleccionar la sección de IOS Router y dar clic en 'New'

4. Buscar la imagen descargada en el paso uno y dar clic en 'siguiente'

5. En esta sección aparecerá la iformación del dispositivo. Dar clic en 'Siguiente'

6. En esta sección se le asigna una cantidad de RAM, en este se dejará la cantidad de memoria sugerida.

      Dar clic en 'Siguiente'

7. En esta sección se configuran los adaptadores de red, en este caso se dejarán las configuraciones por defecto. 

      Dar clic en 'Siguiente'

8. En esta sección se configuran los modulos WIC, en este caso se dejarán las configuraciones por defecto. 

      Dar clic en 'Siguiente'

9. En esta sección aparece el identificador asignado por GNS3. 

      Dar clic en 'Siguiente'
      
10. Seleccionar 'Apply' para guardar la configuración y luego 'Ok'

Y listo, encontrará el dispositivo en el panel de routers.


### Pruebas
Para probar la comunicación entre los cuatro host se utiliza el comando [ping](https://linux.die.net/man/8/ping), el cual utiliza el protocolo ICMP para enviar paquetes con el objetivo de verificar la conectividad.
A continuación se muestra la respuesta de la red al hacer ping desde cada uno de los host a todos los demás.


#### Host con IP 192.168.19.30

#### Host con IP 192.168.19.15

#### Host con IP 192.168.14.15

#### Host con IP 192.168.14.30


####
      
## Glosario

###### Red
La red informática nombra al conjunto de computadoras y otros equipos interconectados, que comparten información, recursos y servicios. Puede a su vez dividirse en diversas categorías, según su alcance, su método de conexión o su relación funcional, entre otras.

###### Host
Un host o anfitrión es un dispositivo que funciona como el punto de inicio y final de las transferencias de datos. 

###### Switch
Un switch o conmutador es un dispositivo de interconexión utilizado para conectar equipos en red formando lo que se conoce como una red de área local (LAN) y cuyas especificaciones técnicas siguen el estándar conocido como Ethernet (IEEE 802.3). En la actualidad las redes locales cableadas siguen el estándar Ethernet donde se utiliza una topología en estrella y donde el switch es el elemento central de dicha topología.

###### Router
Es un dispositivo que permite interconectar computadoras que funcionan en el marco de una red. Su función es de establecer la ruta que destinará a cada paquete de datos dentro de una red informática. 

###### Dirección IP
IP son las siglas de**Internet Protocol** que, si lo traducimos al español, significa Protocolo de Internet. Este protocolo, al igual que otros muchos se encarga de establecer las comunicaciones en la mayoría de nuestras redes. Para ello, asigna una dirección única e irrepetible a cada dispositivo que trata de comunicarse en Internet. 
La dirección IP es en realidad un conjunto de números que identifica, de manera lógica y jerárquica, a un dispositivo en la red.

No existe dispositivo en el mundo que pueda comunicarse con otro sin tener una IP. Las direcciones IP son los nombres numéricos que se asignan a un dispositivo a modo de matrícula para que pueda ser llamado por otros dispositivos. Existen dos tipos de IP: las direcciones IP públicas y las direcciones IP privadas.

Tanto las direcciones IP públicas como las privadas están construidas en cuatro bloques numéricos. Cada bloque es un número del 0 al 255 y está separado por un punto. Por ejemplo, una dirección IP pública podría ser 63.45.12.34 y una dirección IP privada, 192.168.0.11.

###### Dirección MAC
La dirección MAC es un identificador único que cada fabricante le asigna a la tarjeta de red de sus dispositivos conectados, desde un ordenador o móvil hasta routers, impresoras u otros dispositivos. Sus siglas vienen del inglés, y significan Media Access Control. Como hay dispositivos con diferentes tarjetas de red, como una para WiFi y otra para Ethernet, algunos pueden tener diferentes direcciones MAC dependiendo de por dónde se conecten.

Las direcciones MAC están formadas por 48 bits representados generalmente por dígitos hexadecimales. Como cada hexadecimal equivale a cuatro binarios (48:4=12), la dirección acaba siendo formada por 12 dígitos agrupados en seis parejas separadas.

###### Termino 
Pellentesque ut dignissim sapien. Nam vulputate, enim eget ornare lobortis, risus erat vehicula tortor, at iaculis massa velit in tortor. Vivamus iaculis risus nec sem porta, posuere auctor massa dapibus. Ut hendrerit facilisis volutpat. Pellentesque habitant morbi tristique senectus et netus et malesuada fames ac turpis egestas. Phasellus porttitor ex at lectus sollicitudin ultricies. Sed mauris elit, lobortis at sapien ac, faucibus facilisis elit. Vivamus a ligula at nunc facilisis aliquet. 
###### Termino
Pellentesque ut dignissim sapien. Nam vulputate, enim eget ornare lobortis, risus erat vehicula tortor, at iaculis massa velit in tortor. Vivamus iaculis risus nec sem porta, posuere auctor massa dapibus. Ut hendrerit facilisis volutpat. Pellentesque habitant morbi tristique senectus et netus et malesuada fames ac turpis egestas. Phasellus porttitor ex at lectus sollicitudin ultricies. Sed mauris elit, lobortis at sapien ac, faucibus facilisis elit. Vivamus a ligula at nunc facilisis aliquet. 
###### Termino
Pellentesque ut dignissim sapien. Nam vulputate, enim eget ornare lobortis, risus erat vehicula tortor, at iaculis massa velit in tortor. Vivamus iaculis risus nec sem porta, posuere auctor massa dapibus. Ut hendrerit facilisis volutpat. Pellentesque habitant morbi tristique senectus et netus et malesuada fames ac turpis egestas. Phasellus porttitor ex at lectus sollicitudin ultricies. Sed mauris elit, lobortis at sapien ac, faucibus facilisis elit. Vivamus a ligula at nunc facilisis aliquet. 

