## Miniproyecto Sistemas Operativos

**Universidad ICESI**  
**Curso:** Sistemas Operativos  
**Estudiante:** Juan Sebastián Prada.  
**Tema:**  Servicios web  
**Correo:** juan.prada1 at correo.icesi.edu.co

## Objetivos
* Desplegar una aplicación en un servidor que ejecuta el sistema operativo Linux
* Realizar los ajustes y depuración necesarios para desplegar una
aplicación en Linux
* Realizar aplicaciones para obtener información del sistema operativo

## Descripción
Para el despliegue de una aplicación en un servidor se requiere conocer los procedimientos necesarios relacionados con la configuracion de las interfaces de red, ajustes de seguridad, instalación de dependencias, usuarios y herramientas de depuracíon del sistema operativo.

El siguiente proyecto consiste en el despliegue de una aplicación web para obtener información del sistema operativo (La aplicación debe permitir consulta uso de CPU, memoria y espacio en disco). Para este propósito se debe emplear el sistema operativo Ubuntu Server 16.04, el microframework flask y ambientes virtuales.

<p align="center">
  <img src="images/vista-despliegue.png" alt="webservice architecture"/>
</p>

## Actividades
* Nombre y código de todos los integrantes del grupo (máximo 3) (5%)
* Ortografía y redacción (5%)
* Descripción breve de los pasos para cumplir con lo solicitado
  * Sistema operativo Ubuntu Server 16.04 (10%)
  * Configuración de interfaces de red (10%)
  * Configuración de puertos (10%)
  * Instalación de dependencias (10%)
  * Creación de ambientes virtuales (10%)
  * Aplicación en Python (10%)
  * Validación de la ejecución del servicio (netstat) (10%)
* Pruebas de la solución a través de capturas de pantalla. Puede emplear si lo desea una herramienta de captura de pantalla a formato .gif (10%)
* El informe debe ser entregado en formato pdf a través del moodle y el informe en formato README.md debe ser subido a un repositorio de github. El repositorio de github debe ser un fork de https://github.com/ICESI-Training/so-project y para la entrega deberá hacer un Pull Request (PR) respetando la estructura definida. El código fuente y la url de github deben incluirse en el informe (10%).


## Desarrollo

**Sistema operativo:**

![][1]

**Configuracion de interfaces de red:**

``
sudo vi /etc/network/interfaces
``

El campo auto indica que inician junto con el sistema
Para este caso se tienen 3 adaptadores, NAT, Solo-anftrión, Puente
Cada uno se configura mediante el dhcp.

![][2]

**Configuración de puertos:**

El firewall de ubuntu viene desactivado por defecto, lo primero es activarlo

```
sudo ufw enable
```

Para agregar las dependencias se utiliza

```
sudo ufw allow *puerto*/*protocolo*
sudo ufw deny *puerto*/*protocolo*
```

Verificamos el estado del firewall con 

```
sudo ufw status verbose
```

Estado del firewall con los puertos activos:

![][3]

**Instalación dependencias:**

ejecutamos los comandos para actualizar los paquetes presentes en el sistema operativo


```
sudo apt-get update
sudo apte-get -y upgrade
```
Python viene por defecto en ubuntu para verificar su versión utilizamos
Como vamos a utilizar ambientes virtuales usaremos python 2.7

```
python -V
```

Para instalar el manejador de paquetes de python pip utilizamos

```
sudo apt-get install -y python-pip
```

Una vez instalado pip instalaremos los ambientes virtuales:

```
pip install virtualenv
pip install --user virtualenvwrapper
```

Los configuramos:

```
$ vi ~/.bashrc
export WORKON_HOME=~/.virtualenvs
source /home/operativos/.local/bin/virtualenvwrapper.sh
$ source ~/.bashrc
```

Para poder que todo funcione necesitamos copiar los archivos de python
y virtual env a la carpeta /usr/local/bin:

```
cp /user/bin/python /user/local/bin
cp /home/operativos/.local/bin/virtualenv /user/local/bin
```

Ya con esto podemos utilizar los entornos virtuales.

![][4]

**Aplicación en python:**

Para la aplicación en python se utilizo un script en bash para actualizar
la información obtenida por los comandos en archivos .txt que fueron posterior mente
leidos para el retorno de la información.

codigo del script

![][7]

codigo python

![][5]
![][6]

**Funcionamiento:**

https://media.giphy.com/media/26ghbOzgibLYYAtSo/giphy.gif

**Servicio:**

![][8]

![][9]

![][10]




## Referencias
* https://www.ubuntu.com/download/ser
* https://www.cyberciti.biz/faq/how-to-open-firewall-port-on-ubuntu-linux-12-04-14-04-lts/
* https://www.digitalocean.com/community/tutorials/how-to-install-python-3-and-set-up-a-local-programming-environment-on-ubuntu-16-04
* https://github.com/ICESI/so-microservices-python/blob/master/01_virtualenvs/README.md

[1]: images/Screenshot_1.png
[2]: images/Screenshot_2.png
[3]: images/Screenshot_3.png
[4]: images/Screenshot_4.png
[5]: images/Screenshot_5.png
[6]: images/Screenshot_6.png
[7]: images/Screenshot_7.png
[8]: images/Screenshot_8.png
[9]: images/Screenshot_9.png
[10]: images/Screenshot_10.png
