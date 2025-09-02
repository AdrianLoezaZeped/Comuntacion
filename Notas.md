# Configuracion inicial de un switch
Realiza una secuencia de 5 pasos
**Paso 1:** Primero, el switch carga un programa de autodiagnóstico al encender (POST) almacenado en la memoria ROM. El POST verifica el subsistema de la CPU. Este comprueba la CPU, la memoria DRAM y la parte del dispositivo flash que integra el sistema de archivos flash.  
  
**Paso 2:** A continuación, el switch carga el software del cargador de arranque. El cargador de arranque es un pequeño programa almacenado en la memoria ROM que se ejecuta inmediatamente después de que el POST se completa correctamente.  
  
**Paso 3:** El cargador de arranque lleva a cabo la inicialización de la CPU de bajo nivel. Inicializa los registros de la CPU, que controlan dónde está asignada la memoria física, la cantidad de memoria y su velocidad.  
 
**Paso 4:** El cargador de arranque inicia el sistema de archivos flash en la placa del sistema.  
  
**Paso 5:** Por último, el cargador de arranque localiza y carga una imagen de software del sistema operativo de IOS en la memoria y delega el control del switch a IOS.
El sistema esta cargado en la memoria flash
El nombre de la bios te indica las caracterizticas del sistema operativo, por eso nunca hay que modificarlo cada nombre o letra del nombre indica algo.
Los switch mas viejitos tienen leds para dar indicaciones de lo que esta pasando en este momento.
* Sistema
* RPS
* Estadisticas
* DUPLX(HALF-DUPLEX Y FULL-DUPLEX)
* PoE
1,2,3,6(Datos en el cable UTP)
4,5,7,8(Conexion en el cable UTP)

## Acceso a la administracion de los swiches 
Para el acceso a la administración remota de un switch, este se debe configurar con una dirección IP y una máscara de subred.
Tenga en cuenta que para administrar el switch desde una red remota, el switch debe configurarse con una puerta de enlace predeterminada. 
Este es un proceso muy similar a la configuración de la información de dirección IP en los dispositivos host. En la ilustración, se debe asignar una dirección IP a la interfaz 
virtual del switch (SVI) de S1. La SVI es una interfaz virtual, no un puerto físico del switch. Se utiliza un cable de consola para acceder a una PC de modo que el switch puede configurar específicamente.
## Auto-MDIX(MDIX automatico)
Hasta hace poco, se requerían determinados tipos de cable (cruzado o directo) para conectar dispositivos. Las conexiones switch a switch o switch a router requerían el uso de diferentes cables Ethernet. Mediante el uso de la característica automática de conexión cruzada de interfaz dependiente del medio (auto-MDIX) en una interfaz, se elimina este problema. Al habilitar la característica auto-MDIX, la interfaz detecta automáticamente el tipo de conexión de cable requerido (directo o cruzado) y configura la conexión conforme a esa información. Al conectarse a los switches sin la función auto-MDIX, los cables directos deben utilizarse para conectar a dispositivos como servidores, estaciones de trabajo o routers. Los cables cruzados se deben utilizar para conectarse a otros switches o repetidores.

Con la característica auto-MDIX habilitada, se puede usar cualquier tipo de cable para conectarse a otros dispositivos, y la interfaz se ajusta de manera automática para proporcionar comunicaciones satisfactorias. En los switches Cisco más nuevos, el comando mdix auto del modo de configuración de interfaz habilita la función. Al usar auto-MDIX en una interfaz, la velocidad de la interfaz y el dúplex deben configurarse para que la función auto funcione correctamente.
