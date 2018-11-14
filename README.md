# Microservices

**El presente repositorio está destinado a recopilar información acerca de microservices, que debes saber;
adicionalmente se intentará dar un ejemplo para su puesta en práctica.**

Definición
---------------
También conocido como arquitectura de microservicios, es un estilo para el desarrollo de software en la que una gran
aplicación se construye como un conjunto de serivicios modulares, pequeños, poco compactos, con versiones
independientes y escalables, que se comunican entre sí a través de protocolos estándar con interfaces bien definidas.
Estos modulos individuales son responsables de tareas concretas y altamente definidas.

Todo esto permite que los servicios puedan ser escritos en lenguajes independientes y administrados por equipos
diferentes.

 La arquitectura de microservicios se centra en la simplificación de la tecnología para crear sistemas complejos con
 componentes optimizados. 
 
 **"bajo acoplamiento - alta cohesión"**

Ventajas:
---------------
- Permite el escalamiento horizontal de forma independiente.
- Eficiente para dar soporte a un sin fin de plataformas y dispositivos (Mobile, Web, IoT ...)
- Permite que cada servicio se implemente, reconstruya, implemente de nuevo y se administre de manera independiente.
- Mejora aislamiento de fallos.
- Otro ventaja poco mencionada es la adopción de hardware básico por encima de costosos equipos de hardware de grandes
  vendors.
- Mejor uso de los recursos de computación.
- El ciclo de vida de desarrollo se desarrolla en términos generales.
- La corrección de errores y nuevas funciones se entregan con mayor rapidez.
- Mantenimiento de componentes más sencillos.

Para la eficaz implementación de estos microservicios se deben considerar las siguientes guías:

* Herramientas de detección y registro de servicios.
* Estándares de empaquetado para aplicaciones en contenedores, y herramientas de orquestación para replicar
  los contenedores a escala.
* Creación de entornos CI.
* Herramientas de resolución de dependencias.
* Herramientas de supervisión de servicios, alertas y eventos.

Cuando se habla de microservicios se introducen nuevos problemas, la comunicación por ejemplo es realizada por http
por lo que necesitarías hacer un balanceo de carga, registrar cada microservicio.

comunicaciones rapidas y seguras:
La encriptación se esta convirtiendo en un estandar.
Las comunicaciones SSL son lentas.
La encriptación es CPU intensive.

si deseas encriptar la data en la capa de transmisión, se introduce significante overhead en terminos de tasas de
conexión y uso de CPU.

Existen tres modelos de arquitectura de Red:
-Proxy Model
    Trafico in-bound es manejado a través de un reverse proxy/ load balancer
    Los servicios se comunican directamente entre sí
    A menudo con una conexión de round-robin para los DNS
    
-Router Mesh Model
    Trafico In-bound a traves de un reverse proxy
    Balanceo de carga centralizado
    Se tiene un balanceador de carga entre los servicios
     
-Fabric Model
    Enrutamiento a nivel de contenedor
    Los servicios se conectar directamente entre ellos
    
Que es una API: Application Programming Interface
--------------------------------------------------

Rest
Arquitectura de aplicaciones basadas en redes, sus siglas significan REpresentational State Transfer.

Restful
Se pudiera decir que son programas basados en REST.

Rest vs Restful
REST es una arquitectura para aplicaciones basadas en redes (como Internet), sus siglas significan REpresentational
State Transfer y por otro lado RESTful web service o RESTful api, son programas basados en REST. Pero muchas veces se
usan como sinónimos (REST y RESTful).

## I. Casos de uso

## I. Estructura de directorios

Estructura
---------------

**Definición de una estructura en el README.md**

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

Métodos de petición HTTP
-------------------------

Métodos:

    GET
    Solicita una representación de un recurso específico. Estas peticiones sólo deben recuperar datos.

    HEAD
    Pide una respuesta idéntica a la de una petición GET, pero sin el cuerpo de la respuesta.
    
    POST
    Se utiliza para enviar una entidad a un recurso específico, causando a menudo un cambio en el estado.
    
    DELETE
    Borra un recurso específico.
    
    CONNECT
    Establece un túnel hacia el servidor identificado por el recurso. 
    
    OPTIONS
    Es utilizado para describir las opciones de comunicación para el recurso de destino.
    
    TRACE
    Realiza una prueba de bucle de retorno de mensaje a lo largo de la ruta al recurso de destino.
    
    PATCH
    Es utilizado para aplicar modificaciones parciales a un recurso.
    
    PUT
    Actualiza un recurso existente, no lo crea si no existe.

Algunos códigos de estados HTTP
---------------------------------
    200 -> Ok. Ejm: operación exitosa.
    201 -> Created. Ejm:  se creo un registro de forma exitosa.
    403 -> Forbidden. Ejm: cuando se intenta acceder a un registro para el que no tenemos acceso.
    404 -> Not Found. Ejm: se intenta acceder a un registro/recurso que no existe.

Anatomía de una URL (Uniform Resource Locator)
----------------------------------------------

http://ejemplo.com/path/index.html?var=int#fragment1
| 1 |       2     |         3     |   4  |    5    |

1: Protocol
2: host
3: path
4: Query String, se usa para pasar datos a una BD o o algún otro tipo de almacenamiento; las variables van separadas
   por "&".
5: Fragment

Otros patrones arquitectonicos
-------------------------------

* Arquitectura orientada al servicio (SOA)
* Arquitectura monolítica

**Iniciativa realizada por [Oswaldo Tedesco](mailto:oter2901@gmail.com) y [Cefranlly Perez](mailto:cefranllyperez@gmail.com)**