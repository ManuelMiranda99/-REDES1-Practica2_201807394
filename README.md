
# Practica 2

**Universidad de San Carlos de Guatemala**

**Facultad de Ingeniería**

**Escuela de Ciencias y Sistemas**

**Redes de Computadoras 1**

**Ing. Pedro Pablo Hernandez Ramirez**

**Aux. Andrés Alejandro Montufar Cordero**

**Angel Manuel Miranda Asturias 201807394**

# Manual de Configuración

## Configuración de la topología de red en GNS3

La topología de red que se nos presento para realizar la práctica es la siguiente (Agregadas las IPs correspondientes):
![alt-text](https://github.com/ManuelMiranda99/-REDES1-Practica2_201807394/blob/master/Imgs/Topologia.png "Topología de Red")
Para la configuración de la red se hizo uso de GNS3 para su simulación. Se conectaron Router, Switches, VPCS y la máquina virtual de TinyCoreLinux dentro de la interfaz de GNS3.
Para determinar las IPs y máscaras de red se realizó un análisis del enunciado.

### Router

El router nos proporciona conectividad entre los 3 sectores que están divididos. La imagen de router que tenemos solo nos brinda la posibilidad de tener 2 puertos. Pero estos se pueden configurar en GNS3. Damos doble click al router mientras esta apagado (o click derecho -> Configuración). Esto nos mostrará una ventana emergente. En esta seleccionamos el menú Slots.

![alt-text](https://github.com/ManuelMiranda99/-REDES1-Practica2_201807394/blob/master/Imgs/ConfigRouter/Slots.png "Slots Iniciales")

Luego de este seleccionamos cualquiera de los slots y los asignamos al valor NM-1FE-TX de la siguiente manera:

![alt-text](https://github.com/ManuelMiranda99/-REDES1-Practica2_201807394/blob/master/Imgs/ConfigRouter/addSlot.png "Seleccionar Slot")

Aplicamos los cambios y ya contamos con más slots en el router.

#### Configuración de Slots

La configuración del router se muestra en el siguiente screenshot.

![alt-text](https://github.com/ManuelMiranda99/-REDES1-Practica2_201807394/blob/master/Imgs/ConfigRouter/InterfacesConfig.png "Realizar Configuración")

Luego de esto guardamos los cambios con el comando:

```
wr
```

Y confirmamos con:

```
sh run
```

![alt-text](https://github.com/ManuelMiranda99/-REDES1-Practica2_201807394/blob/master/Imgs/ConfigRouter/SaveAndCheck.png "Guardar y Confirmar 1")

![alt-text](https://github.com/ManuelMiranda99/-REDES1-Practica2_201807394/blob/master/Imgs/ConfigRouter/SaveAndCheck1.png "Guardar y Confirmar 2")

### VPCS

La configuración de las VPCS se siguió como en la práctica 1. Por eso solo mostraré screenshots del procedimiento y no detallar los comandos.

#### VPCS 1 (Finanzas)

![alt-text](https://github.com/ManuelMiranda99/-REDES1-Practica2_201807394/blob/master/Imgs/VPCS/Finanzas1.png "Finanzas 1")

#### VPCS 2 (Finanzas)

![alt-text](https://github.com/ManuelMiranda99/-REDES1-Practica2_201807394/blob/master/Imgs/VPCS/Finanzas2.png "Finanzas 2")

#### VPCS 3 (Ventas)

![alt-text](https://github.com/ManuelMiranda99/-REDES1-Practica2_201807394/blob/master/Imgs/VPCS/Ventas1.png "Ventas 1")

#### VPCS 4 (Ventas)

![alt-text](https://github.com/ManuelMiranda99/-REDES1-Practica2_201807394/blob/master/Imgs/VPCS/Ventas2.png "Ventas 2")

#### VPCS 5 (Ventas)

![alt-text](https://github.com/ManuelMiranda99/-REDES1-Practica2_201807394/blob/master/Imgs/VPCS/Ventas3.png "Ventas 3")

### Máquina Virtual

Al igual que con las VPCS, se siguió el mismo procededimiento que en la práctica 1. Con la diferencia de que se cambio la IP de broadcast que te coloca la configuración de red automáticamente.

![alt-text](https://github.com/ManuelMiranda99/-REDES1-Practica2_201807394/blob/master/Imgs/VPCS/Informatica.png "Máquina Virtual")

# Manual de Reportes

## Cálculos de Dominios

Para la realización de los cálculos de dominio de broadcast y de colisión se utilizaron las siguientes "reglas" que nos brindo el ingeniero durante las clases:

### Dominios Router

Por cada interfaz conectada el router cuenta con:

* 1 dominio de colisión
* 1 dominio de broadcast

### Dominios HUB

El HUB se puede decir que es el más sencillo de realizar los cálculos de todos. Debido a que es un dispositivo "tonto". Este cuenta con

* 1 dominio de colisión
* 1 dominio de broadcast

Nótese que a diferencia del router, este es simplemente 1 de cada uno por dispositivo, no 1 de cada uno por interfaz conectada.

### Dominios Switch

El switch al ser un dispositivo inteligente cuenta con unas "reglas" o características distintas al HUB. Este tiene:

* N dominios de colisión (Siendo N el número de puertos conectados)
* 1 dominio de broadcast

Es necesario mencionar que los dominios se "comparten" entre dispositivos. Con la imagen que detalla los cálculos se entenderá mejor.

![alt-text](https://github.com/ManuelMiranda99/-REDES1-Practica2_201807394/blob/development/Imgs/CalculoDominios.png "Cálculo de dominios")

## Capturas de paquetes

Para la captura de paquetes se utilizó el software Wireshark y la opción de capturar paquetes que nos brinda GNS3. El procedimiento se detalla a continuación.

### Ping extendido

Primero se realizó un ping extendido en la máquina virtual. Es importante hacerla en esta, ya que las VPCS solo mandan 5 paquetes y terminan los envíos. La máquina virtual realiza envíos hasta que se le da Ctrl+C.

![alt-text](https://github.com/ManuelMiranda99/-REDES1-Practica2_201807394/blob/master/Imgs/Captura_Paquetes/PingExt.png "Ping extendido")

### Entrar a capturar paquetes desde GNS3

Para la captura de paquetes se debe de tener presente que todos los dispositivos estén iniciados. Se da click derecho en alguno de los cables y se le da a la opción de _Start capture_.

![alt-text](https://github.com/ManuelMiranda99/-REDES1-Practica2_201807394/blob/master/Imgs/Captura_Paquetes/GetOptPaq.png "Start Capture")

Luego de darle click nos mostrará una ventana emergente a la que daremos click en _OK_.

![alt-text](https://github.com/ManuelMiranda99/-REDES1-Practica2_201807394/blob/master/Imgs/Captura_Paquetes/PackCapture.png "OK")

Esto nos abrira Wireshark si lo instalamos durante el proceso de instalación de GNS3.

![alt-text](https://github.com/ManuelMiranda99/-REDES1-Practica2_201807394/blob/master/Imgs/Captura_Paquetes/StartCapture.png "Wireshark")

### En Wireshark

Este software nos muestra como se estan enviando paquetes en todos lados. No solo se encuentran los pings que hemos realizado, sino que también algunas comunicaciones entre otros dispositivos. Para ver los paquetes que estamos enviando desde nuestro ping extendido debemos de aplicar un filtro a los paquetes. En la parte superior de Wireshark, hay una caja de texto que dice **_Apply a display filter ..._**, ahí escribiremos icmp para ver solo los paquetes de los ping que realizamos.

![alt-text](https://github.com/ManuelMiranda99/-REDES1-Practica2_201807394/blob/master/Imgs/Captura_Paquetes/FilterPa.png "Apply filter")

Como se puede observar los datos de nuestra _Source_ y nuestro _Destination_ coinciden con el ping extendido que realizamos. Además que muestra el tiempo en que se contesto y se puede dar doble click en algún paquete para ver este.

![alt-text](https://github.com/ManuelMiranda99/-REDES1-Practica2_201807394/blob/master/Imgs/Captura_Paquetes/infoPacket.png "Check package")
