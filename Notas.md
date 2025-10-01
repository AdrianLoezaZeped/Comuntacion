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

## VLANS
VLAN(Red de area local virtual)- Son redes locales virtuales para dividir la red en diferentes partes a partir de la capa 2, ya que solo se pueden comunicar con redes de su mismo VLAN
Puerto de acceso- A donde se conectan dispositivos finales, se le asigna es una VLAN con la que va trabajar
Puerto Trocal - Por donde pasa trafico de mas de una VLAN, pasan de todas las VLANS del switch
Por medio de un ruteador te comunicas con dispositivos finales, que se encuentran en una red ajena a la que estas conectado

-Tipos de VLANS
* VLAN #1 - Ya existe por default y no se puede borrar, todos los puertos por default pertenecen a la VLAN 1 , pero si se puede  cambiar los puertos a otro puerto distinto
* VLAN de Datos - Es la utilzada para separar el trafico generado por el usuario(Dispositivos Finales)
* VLAN Nativa - Todo el trafico que generes se etiqueta con el ID de la VLAN que esta configurada, para poder mandar por un enlace troncal de switch a switch debe tener la etiqueta de la VLAN que viene, cuando se genera sin una etiqueta de VLAN automáticamente se etiqueta y se convierte en VLAN Nativa por default lo pone en la VLAN 1 eso se puede cambiar
* VLAN de Administración - Se le asigna una IP para poder trabajar por medio de una interfaz remota 
* VLAN de voz - Se necesita una VLAN separada para admitir la tecnología de voz sobre IP (VoIP).

Puertos Troncales (Switch con Switch o Switch con un router)
Subneteo va de la mano con la creación de las vlans para que la capa 2 y 3 queden configuradas

### Configuracion de puertos de acceso 
```
enable
configure terminal
int f0/0 ;Eso depende de la interface que se este configurando
switchport mode access ;Para activar el puerto de acceso
switchport access vlan 10 ; Aqui se asigna la vlan que tendra la inteface
```
<img width="581" height="306" alt="Captura de pantalla 2025-09-17 180244" src="https://github.com/user-attachments/assets/85f0115f-8779-43f1-89f7-a51122aeb776" />

Ejemplo de los comandos utilizados

### Configuracion de puertos troncales
```
enable
configure terminal
int g0/0 ;Eso depende de la interface que se este configurando
switchport mode trunk ;Para activar el puerto truncal
```

<img width="515" height="98" alt="image" src="https://github.com/user-attachments/assets/3efacb46-3275-4382-b660-3a319b71b515" />

Ejemplo de los comandos utilizados


### Prueba realizada de la configuracion
<img width="1916" height="841" alt="Captura de pantalla 2025-09-17 180446" src="https://github.com/user-attachments/assets/9638c1ff-5eb1-4471-b882-f2f68e672142" />
Se realiza la prueba una vez configuradas todos las VLANS de puerto de acceso y Tambien la VLAN Troncal

## Practica VLANS Subinterfaces
<img width="1068" height="378" alt="image" src="https://github.com/user-attachments/assets/51965c2b-c371-4746-a253-94bebb69ac6a" />

Topologia Utilizada

Objetivo configurar todos dispositivos tengas conexion entre ellos 
* Configurar las puertos troncales y puertos de acceso dependiendo del que se ocupe
<img width="367" height="86" alt="image" src="https://github.com/user-attachments/assets/a5aa15f1-73b6-4bf0-a645-45081ff8a090" />
<img width="365" height="146" alt="image" src="https://github.com/user-attachments/assets/722ccd85-2d86-47ee-8b83-ba8b62e94eab" />

* Configuracion del enrutador para poder realizar conectar todas las VLANS
<img width="798" height="424" alt="image" src="https://github.com/user-attachments/assets/b10d8763-7e6f-4b6f-ac33-7f7c281dc8b7" />

Primero se prende el puerto del router por defecto esta apagado

Se proceden a crear una subiterfaz de VLAN

Por medio del encapsulation se pone a trabajar el router de manera troncal seria con la opcion de dot1Q y la vlan que se la asignara despues se le asiganara la gateway con la que trabaja la vlan de esa manera ya permite la conexion por con las demas vlan ya que esta vlan trabajara de manera troncal se crean las 3 vlans necesarias para la topologia

<img width="436" height="91" alt="image" src="https://github.com/user-attachments/assets/74957e91-5c9d-45b2-abd9-30b6d7e42ea8" />

Un switch no tiene la VLAN 20 y requiere el conocerla para poder trabajar el puerto de manera troncal si no conoce el puerto no permitira el trafico por ese puerto troncal asi que se crea una vlan 20 vacia con la cual se permitira el paso por ese puero troncal

<img width="675" height="226" alt="image" src="https://github.com/user-attachments/assets/bcb79347-8be4-45b9-b69f-d94eb8758c7c" />

Con esa creacion ya permitira el trafico de la vlan 20 tambien

## Configuracion de Switch de capa 3
<img width="1401" height="422" alt="image" src="https://github.com/user-attachments/assets/9433c4e0-47b4-4d81-b6f5-4a6757b84431" />

Se realizara la conexion de un dispositivo final a otro dispositivo final por medio de dos switch de capa 3, en la cual unos fungira como como ruteador 

### Puertos De acceso y puertos troncales

<img width="247" height="76" alt="image" src="https://github.com/user-attachments/assets/d7f10745-706d-44c1-be14-0e98c43f078c" />

Primero se realiza la conexion con los puertos de acceso de fastethernet como en las practicas pasadas se llegaba a realizar

<img width="336" height="69" alt="image" src="https://github.com/user-attachments/assets/f5fc3686-f36b-4b2c-8f63-d0f8cf36d544" />

Se procede a realizar la configuracion de los puertos troncales los cuales trabajan por lenguaje dot1q

### Configuracion de ruteador en el switch capa 3

<img width="367" height="140" alt="image" src="https://github.com/user-attachments/assets/7fbbf3e5-893e-40a0-ba60-53d163d6e56e" />

Se agregan las IP de los dispositivos en los cuale configuraremos como ruteador 

<img width="365" height="151" alt="image" src="https://github.com/user-attachments/assets/45fda570-1de2-43e0-9aaf-53a7dd6d8f9c" />

Una vez agregadas debemos revisar que todos los switches conozcan todas las vlans que hay de lo contrario no lo habra comunicacion

<img width="791" height="628" alt="image" src="https://github.com/user-attachments/assets/18ac6744-8b2c-43db-afc0-d0b0a3df3e13" />

En caso de que no lo conozca debemos agregarla aunque no haya ningun dispositivo en esa vlan ya que los enlaces troncales solo dejan pasar el trafico de las vlans que conocen

<img width="804" height="474" alt="image" src="https://github.com/user-attachments/assets/823f78cb-84bd-4a99-836f-e52a4178f368" />

De esta manera se agregarian las VLAN

<img width="1919" height="907" alt="image" src="https://github.com/user-attachments/assets/1656904f-1d21-4dc7-93f7-097ba5d71e07" />

Ahora si ya habria conexion en las entre los dos dispositivos finales

## VTP
Modos y Comandos de VTP (VLAN Trunking Protocol)

**VTP** es un protocolo de capa 2 de Cisco que permite a los *switches* compartir y sincronizar la información de configuración de VLAN en un dominio.

### Modos de Operación de VTP

| Modo | Descripción | Creación/Modificación de VLAN | Propagación de Anuncios | Sincronización con Anuncios |
| :--- | :--- | :--- | :--- | :--- |
| **Servidor** | Es el punto central de gestión. Modo por defecto en switches Cisco. | **SÍ** | **SÍ** (Envía y reenvía) | **SÍ** (Si la revisión es mayor) |
| **Cliente** | El switch recibe y aplica la configuración de VLAN del servidor. | **NO** | **SÍ** (Reenvía) | **SÍ** (Si la revisión es mayor) |
| **Transparente** | El switch no participa en el dominio VTP, pero reenvía los anuncios VTP que recibe. | **SÍ** (Solo localmente, no se propaga) | **SÍ** (Reenvía) | **NO** |
| **Off** (VTPv3) | Deshabilita VTP por completo. No reenvía anuncios. | **SÍ** (Solo localmente) | **NO** (No reenvía) | **NO** |

### Comandos de Configuración de VTP (Modo de Configuración Global)

| Comando | Descripción | Ejemplo |
| :--- | :--- | :--- |
| `vtp mode` | Establece el modo de operación del VTP. | `vtp mode server` <br> `vtp mode client` <br> `vtp mode transparent` |
| `vtp domain` | Asigna el nombre de dominio VTP (debe ser el mismo en todos los switches). | `vtp domain MI_RED` |
| `vtp password` | Configura una contraseña para el dominio VTP. | `vtp password cisco123` |
| `vtp version` | Define la versión del protocolo (1, 2 o 3). | `vtp version 3` |

### Comandos de Verificación de VTP (Modo Privilegiado)

| Comando | Descripción |
| :--- | :--- |
| `show vtp status` | Muestra el estado del VTP, incluyendo el modo de operación, el nombre de dominio y el número de revisión de la configuración. |
| `show vlan brief` | Muestra un resumen de las VLANs configuradas en el switch. |

Funciona por medio de revisiones el numero mayor de revisiones en un switch se actualizan todos los switchs al que tenga el mayor numero de revisiones por eso hay que tener cuidado cuando se agrega un switch al dominio, se debe tener la preacupacion de tener un numero menor de revisiones que los demas switches conectados
### Practca de VTP

