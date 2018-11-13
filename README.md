# Microservices

**El presente repositorio está destinado a recopilar información acerca de microservices, que debes saber;
adicionalmente se intentará dar un ejemplo para su puesta en práctica.**

Definición
---------------
Toolkit que sirve como interfaz para los servicios de Amazon Cloud y la librería Boto3 de python.


EL objetivo principal de este repo, es la búsqueda de un CD de códigos ordenados y de rápida comprensión por ambas partes (DBI & FOX). A continuación se detallan elementos del CD de códigos que FOX pide a DBI cumplir durante todo el partnership entre ambas partes.

## I. Estructura de directorios


Estructura
---------------
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


![](images/arquitectura_amazon.png)

Primeros pasos
---------------

Para el armado de esta arquitectura se va a utilizar contenedores por lo que es necesario tener instalado docker;
adicionalmente se debe contar con el SDK de AWS isntalado para el despliegue de imagenes dockerizadas en el Repositorio
de AWS (ECR).



**Iniciativa realizada por [Oswaldo Tedesco](mailto:oter2901@gmail.com) y [Cefranlly Perez](mailto:cefranllyperez@gmail.com)**