# Microservices

**El presente repositorio está destinado a recopilar información acerca de microservices, que debes saber;
adicionalmente se intentará dar un ejemplo para su puesta en práctica.**

Definición
---------------
También conocido como arquitectura de microservicios, es un estilo para el desarrollo de software en la que una gran
aplicación se construye como un conjunto de serivicios modulares, pequeños, con versiones independientes y escalables,
que se comunican entre sí a través de protocolos estándar con interfaces bien definidas.

Todo esto permite que los servicios puedan ser escritos en lenguajes independientes y administrados por equipos
diferentes.

Una de sus mayores ventajas es que permite el escalamiento horizontal.
Eficientes para dar soporte a un sin fin de plataformas y dispositivos (Mobile, Web, IoT ...)

## I. Casos de uso

## I. Estructura de directorios

Estructura
---------------

**Definición de una estructura en el README.md**

    .
    ├── folder_conector_01       # Carpeta para códigos de Conectores
    │   ├── code_conector_02.py                     # ?
    │   ├── library.py                              # ?
    │   └── ...
    ├── folder_conector_02
    │   ├── code_conector_02.py                     # ?
    │   ├── library.py                              # ?
    │   └── ...
    ├── README.md
    └── ...

Referenciando imagenes
----------------------

![](images/arquitectura_amazon.png)

Primeros pasos
---------------

Para el armado de esta arquitectura se va a utilizar contenedores por lo que es necesario tener instalado docker;
adicionalmente se debe contar con el SDK de AWS isntalado para el despliegue de imagenes dockerizadas en el Repositorio
de AWS (ECR).



**Iniciativa realizada por [Oswaldo Tedesco](mailto:oter2901@gmail.com) y [Cefranlly Perez](mailto:cefranllyperez@gmail.com)**