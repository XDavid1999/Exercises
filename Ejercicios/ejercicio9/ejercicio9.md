# Integración continua con Travis

- Darse de alta en la página de [Travis](https://travis-ci.com) y crear una cuenta en la misma.
- Vincular GitHub con travis. Para ello simplemente le daremos permiso, nos pedirá nuestra contraseña de GitHub, etc.
- En mi caso se ha configurado travis, con ayuda de las instrucciones en la página de la herramienta, para que, al asociar mi cuenta de GitHub y mi cuenta de Travis, me añada automáticamente todos los repositorios de mi cuenta de GitHub a este CI y poder decidir cuales tendrán integración y cuales no.

### Con integración continua

![conIntegracion](images/im1.png)

### Sin integración continua aún

![sinIntegracion](images/im2.png)

- Al añadir la integración continua añadimos un webhook entre GitHub y travis.

### Qué es un WebHook

Un webhook es una forma de que unas aplicaciones proporcionen información en tiempo real a otras. Los webhook entregan datos a otras aplicaciones cada vez que un evento ocurre, lo que significa que obtiene datos de inmediato.