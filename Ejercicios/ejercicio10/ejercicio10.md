# Configurando integración continua para nuestra app

- Necesitaremos crear dentro de nuestro [proyecto](https://github.com/XDavid1999/PacketService) un archivo [.travis.yml](https://github.com/XDavid1999/PacketService/blob/master/.travis.yml) que proporcione a travis información acerca de aspectos relevantes de nuestro proyecto. Lo que travis hará, por defecto, será pasar los [test](https://github.com/XDavid1999/PacketService/blob/master/test/packetServiceTest.js) que tengamos hechos.
- En este archivo especificaremos nuestro lenguaje, en nuestro caso *node_js*,con el tag **language**.
- La versión de este que usaremos, *v10.19.0*, en nuestro caso con **node_js**.
- El objetivo a realizar previo a la instalación, en nuestro caso construir nuestro contenedor, con **before_install**.
- La orden que ejecutará travis, que será correr los test dentro del contenedor, con **script**.

En este caso, al usar docker, no sería necesario especificar ni el lenguaje que utilizaremos ni la versión del mismo ya que los test correrán dentro de nuestro contenedor, que ya tiene todo lo necesario.

## Script

~~~
before_install:
  docker build -t xdavid1999/packetservice .

script:
  docker run -t -v `pwd`:/test xdavid1999/packetservice
~~~

## Último build correcto
![travisCorrecto](images/im1.png)