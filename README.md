# Redes1-Practica1
Generación y configuración de una topología de red pequeña formada por 3 vpc, una vm (tiny linux), dos switch capa 2 y un router.

## Topología de Red
La topología implementada consiste en 4 host, dos host conectados a un switch que conforman el segmento de 

![image](https://concepto.de/wp-content/uploads/2015/03/paisaje-e1549600034372.jpg)

## Configuración

### Configuración de host
Para realizar la configuración se debe tener el dispositivo encendido e ingresar por medio de la terminal. 

1. Ejecutar el siguiente comando para verificar la información de red de la computadora.
 ``` show ip ```
2. Con el siguiente comando configurar la IP y la puerta de enlace. 
 ```ip <IP> <GATEWAY>```
3. Guardar la configuración con el comando 
   ```save ```

### Configuración de Router
Para realizar la configuración se debe tener el dispositivo encendido e ingresar por medio de la terminal. 

Verificar el estado de las interfaces del router con el comando 
  ```Sh ip int brief```

1. Ejecutar siguiente comando para etrar al menú de configuración del router
    ```conf t ```
2. Indicar la interfaz a configurar con el comando 
  ```int f0/ <x>```
en donde x es el número identificador de la interfaz

3. Ejecutar el siguiente comando para configurar la IP de la interfaz
  ```ip address <IP> <MASCARA DE RED>```

4. Activar la interfaz con el comando 
  ```no shut```

5. Salir de la configuración de la interfaz 
  ```exit```
6. Salir de la configuración del router con el comando
  ```exit```

7. Guardar la configuración del router con el comando 
  ```wr```

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

