# Web infrastructure design
Es la planificación y configuración de los componentes necesarios para alojar y poner en funcionamiento un sitio web. Incluye la selección y configuración de servidores, la implementación de servicios de red, la configuración de la seguridad y el almacenamiento de datos, entre otros aspectos.

### What is a server?
A server is a physical device or virtual instance that provides functionality and services to other programs or devices, known as "clients."

### El servidor puede ser fisico o virtual
Un servidor físico es un equipo de hardware dedicado que funciona como un servidor completo. Tiene todos los componentes necesarios para ejecutar aplicaciones y servicios en una red, como procesadores, memoria y discos duros.

Un servidor virtual es una instancia lógica creada mediante software de virtualización. Se divide y comparte los recursos de un servidor físico entre varios servidores virtuales, cada uno con su propio sistema operativo y configuraciones.

### El Servidor ejecuta un sistema operativo
El sistema operativo es esencial para el funcionamiento de un servidor, ya que administra los recursos, interactúa con el hardware, administra servicios y aplicaciones, brinda control y seguridad, permite la programación y automatización de tareas en el servidor.

### Contenido dinamico y estatico
El contenido dinámico se refiere a la generación de contenido web en tiempo real, basado en la interacción del usuario, los datos almacenados en una base de datos u otras variables. A diferencia del contenido estático, que se muestra de la misma manera para todos los usuarios, el contenido dinámico se adapta y cambia según diferentes condiciones y eventos.
El contenido dinámico permite personalizar la experiencia del usuario y proporcionar información relevante y actualizada.
EL contenido estatico se crea previamente y se almacena en un servidor, y su presentación no varía, a menos que se realicen cambios manuales en el servidor.

### What is a web server?
A web server is a software that serves web pages to clients upon their request, it does this over the protocol HTTP.

### Protocol HTTP
HTTP (Hypertext Transfer Protocol) es un protocolo de comunicación utilizado para transferir información en la web. Es el protocolo principal que permite que los clientes (como navegadores web) y servidores (como servidores web) se comuniquen entre sí.
El protocolo HTTP opera en un modelo de solicitud-respuesta, donde un cliente envía una solicitud HTTP a un servidor y el servidor responde con una respuesta HTTP correspondiente. Estas solicitudes y respuestas están compuestas por una serie de mensajes estructurados y definidos por reglas específicas.

### What is HTTPS?
A version of HTTP that secure the traffic between your browser and the website by encrypting it.

### Qué es un protocolo de red?
Un protocolo de red es un conjunto de reglas establecidas que especifican cómo formatear, enviar y recibir datos para que los puntos finales de la red informática, incluidos ordenadores, servidores, enrutadores y máquinas virtuales, puedan comunicarse a pesar de las diferencias en sus infraestructuras, diseños o estándares subyacentes.

### What is a codebase?
Is the collection of source code that is used to build a software system.

### What is a database?
Is a collection of information that is stored and organized so that it can be easily accessed, updated and managed.

### What is the role of the domain name?
Actúa como una etiqueta legible por humanos que se asigna a una dirección IP numérica única para facilitar la navegación y la localización de los sitios web y otros servicios en línea.
Main functions of the domain name: identification, accessibility, organization, brand and reputation.

### What is a DNS?
A system to translate domain names into IP addresses. The A (Address Record) record is one of the most common types of DNS records and is used to establish a direct correspondence between a domain name and an IP address.

### What is TCP/IP?
Transmission Control Protocol/Internet Protocol, is a suite of communications protocols used to interconnect network devices on the Internet or any private network.

### Qué tipo de registro DNS es www en www.foobar.com?
El tipo de registro DNS para "www" en "www.foobar.com" es un registro de tipo CNAME (Canonical Name). El registro CNAME se utiliza para asociar un subdominio, en este caso "www", con el nombre de dominio principal "foobar.com". Al utilizar un registro CNAME, el subdominio "www" redirige a la misma dirección IP que el dominio principal "foobar.com". Esto permite que los usuarios accedan al sitio web utilizando tanto "www.foobar.com" como "foobar.com" y sean redirigidos al mismo destino.


## Task 0
![Diagram](https://i.imgur.com/mvbqBIY.png)


### Que es un Load Balancer?
Es un componente de infraestructura utilizado en entornos de red y servidores para distribuir de manera eficiente la carga de trabajo o tráfico entrante entre múltiples servidores o nodos de backend. Su objetivo principal es mejorar el rendimiento, la escalabilidad y la disponibilidad de las aplicaciones o sitios web al garantizar una distribución equitativa de las solicitudes de los clientes.

### Configuración activa-activa: 
En este modo, todos los balanceadores de carga están activos y reciben tráfico de los clientes. El tráfico se distribuye entre los servidores de backend de manera equitativa y los balanceadores de carga comparten la carga de trabajo. Si uno de los balanceadores de carga falla, los demás continúan gestionando el tráfico.

### Configuración activa-pasiva:
En este modo, solo un balanceador de carga está activo y recibe el tráfico de los clientes, mientras que los demás balanceadores de carga permanecen en un estado pasivo. El balanceador de carga activo maneja todas las solicitudes y distribuye el tráfico a los servidores de backend. Si el balanceador de carga activo falla, otro balanceador de carga pasivo toma el control y asume el papel de balanceador de carga activo.

### The MySQL Master-Replica cluster
Utiliza la replicación para mantener los datos sincronizados entre el nodo principal (Master) y los nodos secundarios (Replicas). La replicación es un proceso en el que se copian y aplican automáticamente los cambios realizados en el nodo principal a los nodos secundarios.

### The load balancer is still a single point of failure
Si el balanceador de carga falla, todos los clientes que intenten acceder al sitio web o la aplicación no podrán ser dirigidos correctamente a los servidores de backend y no podrán recibir una respuesta.

## Task 1
![Distributed](https://i.imgur.com/A5JYfb3.png)

### Firewall
Es una medida de seguridad que actúa como una barrera entre una red privada y una red externa. Su objetivo principal es controlar y filtrar el tráfico de red con el fin de proteger los sistemas y datos de posibles amenazas y ataques.
El firewall examina el tráfico que entra y sale de la red según un conjunto de reglas predefinidas. Estas reglas determinan qué tipo de tráfico se permite o se bloquea, basándose en diversos criterios, como las direcciones IP, los puertos, los protocolos y otros atributos del tráfico de red.
Al establecer estas reglas, un firewall puede bloquear el acceso no autorizado desde el exterior de la red, como intentos de intrusión o ataques maliciosos.

### 3 Cortafuegos:
El primer cortafuegos comprueba las reglas después de recibir las solicitudes y podría denegar las siguientes solicitudes. El segundo cortafuegos está trabajando en el servidor para evitar que alguien piratee según las solicitudes, y el tercer cortafuegos actúa como cortafuegos a nivel de circuito, inspeccionando la transacción de la información.

### SSL - Secure Sockets Layer
Es un protocolo de seguridad utilizado para establecer una conexión segura y cifrada entre un servidor web y un navegador web. La función principal es garantizar la confidencialidad, integridad y autenticidad de los datos transmitidos a través de Internet. Cuando se establece una conexión SSL, la información que se transmite entre el servidor y el navegador se cifra, lo que significa que solo el servidor y el cliente pueden entenderla. Esto ayuda a prevenir que los datos sean interceptados y leídos por personas no autorizadas.

### Monitoreo
Es una práctica utilizada para el control de calidad. “Lo que no se puede medir, no se puede mejorar”. Entonces, el monitoreo no solo ayuda a asegurar el mantenimiento de altos niveles de calidad, manteniendo los estándares establecidos y la consistencia, sino también para ayudar en la mejora continua del desempeño de los recursos.

## Task 2
![Segura](https://i.imgur.com/yguietk.png)
