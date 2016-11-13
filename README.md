# arduino-ros-examples
Set of examples of to learn the interface between ROS and Arduino

## Dependecies
To run the examples you need both the [Arduino](https://www.arduino.cc) and [ROS Kinetic](http://wiki.ros.org/kinetic/Installation/Ubuntu), as well as two extra packages not shipped with the ROS Desktop-full installation:
```shell 
$ sudo apt-get install ros-kinetic-rosserial-arduino
$ sudo apt-get install ros-kinetic-rosserial-python
```
*Note: Examples also run correctly with ROS Indigo*

## Setting Up
The first time you need to call a python script that will generate the necessary code for the Arduino. 
```shell 
$ cd your-arduino-sketchbook/libraries
$ rosrun rosserial_arduino make_libraries.py .
```

*Note: In case you later generate (and install!) a new custom ROS message, or you install a new package with new messages, you will need to run again this script.*

## Running
1. Complie and Load The Arduino code to your board with the Arduino IDE
2. Execute the launch file: 
```shell 
$ roslaunch arduino_ros_examples oscillator.launch
```

# Exercici modificació frecuència del sinus
En aquesta part, em modificat el codi del fitxer oscillator.ino i l'hem guardat amb el nom oscillator_receiving_frequency.ino.
Aquest codi, a diferència de l'altre el que fa és mostrar el sinus a una frequència 20 per defecte però llegir constantment per si rep un altre valor. Per executar aquest codi farem el següent:

1- Compilar i carregar el codi al Arduino fent servir Arduino IDE
2- Executar el fitxer launch: 
```shell 
$ roslaunch arduino_ros_examples oscillator.launch
```

3- Al executar aquest codi sen's obre una finestra on es mostra el plot del sinus, si no ens mostra la variable per defecte, a la casella topic escribir:
```shell 
$ /wave/data
```

4- En una nova terminal:
```shell 
$ rostopic pub /freq std_msgs/UInt16 20
```
On 20 será el número que volguem pasar-li com a frecuència.

Si observem ara el plot veiem com canvia la frecuència del sinus.
