# Configurando integración continua para nuestra app

- Necesitaremos crear dentro de nuestro [proyecto](https://github.com/XDavid1999/PacketService) un archivo [.travis.yml](https://github.com/XDavid1999/PacketService/blob/master/.travis.yml) que proporcione a travis información acerca de aspectos relevantes de nuestro proyecto. Lo que travis hará, por defecto, será pasar los [test](https://github.com/XDavid1999/PacketService/blob/master/test/packetServiceTest.js) que tengamos hechos.
- En este archivo especificaremos nuestro lenguaje, en nuestro caso *node_js*,con el tag **language**.
- Probaremos distintas versiones de nuestro lenguaje, en este caso: *10.19.0, 12.19.0 y 15.1.0*. Para ello solo deberemos poner el tag **node_js** y debajo las versiones a testear.
- Los paquetes a instalar, en este caso nuestro *taskrunner*, con **before_install**.
- Instalaremos las dependencias, en este caso con npm install, ya que tras varias horas de búsqueda no encontramos como hacerlo corrrectamente con nuestro *taskrunner*, con **install**
- La orden que ejecutará travis, que en este caso será correr los test con nuestro *taskrunner*, con **script**.

En este caso no usamos docker, si lo hicieramos, no sería necesario especificar ni el lenguaje que utilizaremos ni la versión del mismo ya que los test correrán dentro de nuestro contenedor, que ya tiene todo lo necesario.

## Script

~~~
language: node_js
node_js:
  - 10.19.0 # Versión en mi PC
  - 12.19.0 # La de mi contenedor
  - 15.1.0  # Última versión del lenguaje

before_install:
  - npm install -g gulp

install:
 - npm install

script:  
 - gulp test
~~~

## Script para testear con docker

~~~
# No construiremos el contenedor de nuevo ya que lo tenemos, 
# subido a DockerHub,así que simplemente le haremos pull
before_install:
    docker pull xdavid1999/packetservice1999:latest

# Haremos que corran los test en el contenedor que acabamos de
# descargar
script:
    docker run -t -v `pwd`:/test xdavid1999/packetservice1999

~~~

## Último build correcto
![travisCorrecto](images/im1.png)