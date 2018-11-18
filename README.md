# Microservices

**El presente repositorio está destinado a recopilar información acerca de microservices, que debes saber;
adicionalmente se intentará dar un ejemplo para su puesta en práctica.**

## Definición

También conocido como arquitectura de microservicios, es un estilo para el desarrollo de software en la que una gran
aplicación se construye como un conjunto de serivicios modulares, pequeños, poco compactos, con versiones
independientes y escalables, que se comunican entre sí a través de protocolos estándar con interfaces bien definidas.
Estos modulos individuales son responsables de tareas concretas y altamente definidas.

Todo esto permite que los servicios puedan ser escritos en lenguajes independientes y administrados por equipos
diferentes.

La arquitectura de microservicios se centra en la simplificación de la tecnología para crear sistemas complejos con
componentes optimizados.

**"bajo acoplamiento - alta cohesión"**
Alta cohesión: Cada componente en la medida de lo posible debe realizar una sola función.
Bajo acoplamiento: Cada componente debe ser independiente, es decir, un cambio en un componente no debe
afectar/involucrar otro componente. Los componentes deben estar lo menos ligado posibles.

## Ventajas:

- Permite la [escalabilidad](##-Principios-de-escalabilidad-y-desempeño) horizontal de forma independiente.
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

- Herramientas de detección y registro de servicios.
- Estándares de empaquetado para aplicaciones en contenedores, y herramientas de orquestación para replicar
  los contenedores a escala.
- Creación de entornos CI.
- Herramientas de resolución de dependencias.
- Herramientas de supervisión de servicios, alertas y eventos.

Cuando se habla de microservicios se introducen nuevos problemas, la comunicación por ejemplo es realizada por http
por lo que necesitarías hacer un balanceo de carga, registrar cada microservicio.

comunicaciones rapidas y seguras:
La encriptación se esta convirtiendo en un estandar.
Las comunicaciones SSL son lentas.
La encriptación es CPU intensive.

Si deseas encriptar la data en la capa de transmisión, se introduce significante overhead en terminos de tasas de
conexión y uso de CPU.

Existen tres modelos de arquitectura de Red:
-Proxy Model
Trafico in-bound es manejado a través de un reverse proxy/load balancer
Los servicios se comunican directamente entre sí
A menudo con una conexión de round-robin para los DNS

-Router Mesh Model
Trafico In-bound a traves de un reverse proxy
Balanceo de carga centralizado
Se tiene un balanceador de carga entre los servicios

-Fabric Model
Enrutamiento a nivel de contenedor
Los servicios se conectar directamente entre ellos

## Desventajas

- El desarrollo de un sistema distribuido puede ser complejo, desde el momento en que todo es un servicio independiente, se debe tener cuidado al manejar las solicitudes entre modulos, en muchos casos se debe escribir codigo extra para evitar la corrupcion de las mismas.

- El manejo de diferentes bases de datos y transacciones puede ser complicado

- Testear una aplicacion orientada a servicios puede convertirse en una continua ejecucion de pasos, en una solucion monolitica solo necesitamos ejecutar nuestra aplicacion en un servidor, y asegurarnos de su conectividad con la base de datos. Con microservicios, cada servicio dependiente necesita ser confirmado antes de que se pueda testear toda la solucion

- Desplegar microservicios puede llegar a ser complejo, estos deben estar coordinados con multiples servicios, lo cual no necesariamente es tan sencillo como desplegar una aplicacion monolitica

## Principios de escalabilidad y desempeño

Eficiencia es de las cosas más importantes en el mundo de hoy.
Para construir una aplicación escalable, tenemos que considerar en el diseño dos aspectos: concurrencia y
particionamiento. La concurrencia permite que cada tarea sea dividida en piezas más pequeñas, mientras que el
particionamiento es esencial para permitir que estas piezas más pequeñas sean procesadas en paralelo.
Dicho esto podemos inferir que la escalabilidad esta relacionada en como dividimos y ejecutamos el procesamiento de
tareas; y el desempeño es la medida de cuan eficientemente la aplicación procesa estas tareas.

Debemos utilizar nuestros recursos de hardware de forma eficiente, ser concientes de los cuellos de botella y
requerimientos, para así hacer una planificación de capacidad.

Entender el crecimiento escalable de tu servicio conlleva dos puntos importantes: el primero es entender donde encaja
el servicio en todo el ecosistema y que métrica de negocio se puede ver afectada; la segunda es la comprensión bien
definida, medible y cuantitativa del tráfico que un microservicio puede manejar.
Una medida de crecimiento de escala sería determinar la cantidad requests per seconds (RPS) o queries per seconds (QPS)
que un servicio puede manejar, luego se debe estimar cuantas RPS/QPS va a manejar en el futuro. Una técnica podría ser
utilizar pruebas de carga, junto al analisis del historial de trafico. El otro paso viene del entendimiento del negocio,
es decir, luego de un análisis de crecimiento de negocio se puede identificar a nivel técnico que servicios estan
involucrados y medir el impacto a nivel cualitativo. La medida cuantitativa de crecimiento esta estrechamente
relacionada con la medida cualitativa, transformando esta apreciación a algo medible en terminos de

Uso eficiente de los recursos: CPU, memoria, almacenamiento de datos y la red son los recursos que tenemos y necesitamos
para poner en marcha nuestra aplicación. El primer paso sería catalogar la importancia y priorización de los servicios
claves del negocio para darle mayor cantidad de recursos. Ejm: se puede asignar un host por servicio con hardware
dedicado pero esto podría ser un uso ineficiente del hardware y un tanto costoso. En la mayoría de los casos se podrían
asignar diversos servicios siempre y cuando se asegure su aislamiento en cuanto a sus servicios vecinos -aquí entraría
una tecnología como Docker. Una de las prácticas más eficientes es abstraer completamente la noción de un host y
reemplazarlo con recursos de hardware utilizando tecnologías de extracción de recursos como Apache Mesos.

Otro paso importante para que los recursos sean eficientemente asignados y distribuidos es identificar los cuellos de
botella y los requerimientos de recursos. Por lo general estos recursos se refieren a CPU y RAM, y en ambientes
multihilos los threads pasan a ser el tercer componente esencial.

Otro punto a identificar son los cuellos de botella que puedan limitar el cremiento de nuestros servicios. Ejm: el
número de conexiones que puede manejar una Base de Datos. Otro ejemplo sería cuando tu servicio solo puede crecer de
forma vertical

Otro aspecto importante que influye en la arquitectura de los servicios es el lenguaje de programación utilizado, si se
utiliza python por ejemplo, existen muchas maneras para procesar varias tareas apoyado en frameworks asyncronos como
tornado, otra forma sería utilizar tecnologías de colas como RabbitMQ (Aunque no es muy recomendado).
Para esta elección el equipo debe hacerse preguntas como: - Como el servicio procesará las tareas. - Cuan eficientemente estos servicios procesan las tareas. - Y que eficiencia tendrá el servicio a medida que el número de tareas se incremente.

Como se ha mencionado anteriormente el servicio debe ser pensando en terminos de concurrencia y particionamiento.
Concurrencia: que el procesamiento de tareas se haga en paralelo en piezas de código menores.

## Que es una API: Application Programming Interface

Rest
Arquitectura de aplicaciones basadas en redes, sus siglas significan **RE**presentational **S**tate **T**ransfer.

Restful
Se pudiera decir que son programas basados en REST.

Rest vs Restful
REST es una arquitectura para aplicaciones basadas en redes (como Internet), sus siglas significan **RE**presentational
**S**tate **T**ransfer y por otro lado RESTful web service o RESTful api, son programas basados en REST. Pero muchas
veces se usan como sinónimos (REST y RESTful).

## I. Casos de uso

## I. Estructura de directorios

## Stateful vs stateless

Stateful es por ejemplo cuando se debe implementar una lógica donde la información de un usuario deba ser guardada en
alguna memoria.

## Estructura

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

## Referenciando imagenes

![](images/arquitectura_amazon.png)

## Métodos de petición HTTP

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

## Algunos códigos de estados HTTP

    200 -> Ok. Ejm: operación exitosa.
    201 -> Created. Ejm:  se creo un registro de forma exitosa.
    403 -> Forbidden. Ejm: cuando se intenta acceder a un registro para el que no tenemos acceso.
    404 -> Not Found. Ejm: se intenta acceder a un registro/recurso que no existe.

## Anatomía de una URL (Uniform Resource Locator)

http://ejemplo.com/path/index.html?var=int#fragment1

| 1 | 2 | 3 | 4 | 5 |

1: Protocol
2: Host
3: Path
4: Query String, se usa para pasar datos a una BD o o algún otro tipo de almacenamiento; las variables van separadas
por "&".
5: Fragment

JSON Web Token (JWT)

## Otros patrones arquitectonicos

- Arquitectura orientada al servicio (SOA)
- Arquitectura monolítica

**Iniciativa realizada por [Oswaldo Tedesco](mailto:oter2901@gmail.com) y [Cefranlly Perez](mailto:cefranllyperez@gmail.com)**
