# Ejercicio 1

etcd es un almacén de clave-valor distribuido de gran coherencia que proporciona una forma fiable de almacenar datos a los que debe acceder un sistema distribuido o un grupo de máquinas. Maneja con elegancia las elecciones de líderes durante las particiones de red y puede tolerar fallas de la máquina, incluso en el nodo líder.

## Instalando y almacenando claves con etcd3

### Instalación

En este caso para comenzar instalaremos el mismo en nuestro sistema con npm y --save-dev para poder utilizarlo en nuestro proyecto:

~~~
npm install --save-dev etcd3
~~~

### Almacenamiento

Para almacenar una de nuestras claves simplemente tendremos que ejecutar el siguiente comando:

~~~
export ETCDCTL_API=3
etcdctl put nuevaClave claveSecreta
~~~

Ejecutando un programa basado en el ejemplo podremos ver como efectivamente se ha almacenado.

~~~
const { Etcd3 } = require('etcd3');
const cliente = new Etcd3();

(async () => {
  const clave = await cliente.get('nuevaClave').string();
  console.log("La clave que se almacenó es: ", clave);

  await cliente.delete().all()
})();
~~~