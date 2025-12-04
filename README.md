📄 Resumen de la Guía de Instalación y
Configuración de VPN en OpenStack

Este proyecto documenta el proceso completo para desplegar un servicio VPN con WireGuard dentro de un entorno OpenStack 
utilizando MicroStack como plataforma de nube privada. La guía cubre desde la instalación del entorno hasta la conexión
final del cliente a través de la VPN.

🔧 1. Preparación del Entorno

Se instala VirtualBox y se crea una máquina virtual con Ubuntu, la cual servirá como host para la instalación de MicroStack.
También se descargan imágenes necesarias (como Ubuntu Server Cloud).

☁️ 2. Instalación de MicroStack (OpenStack)

Se instala MicroStack mediante Snap y se inicializan sus servicios (redes, Keystone, Horizon, cómputo, etc.).
Luego se accede al panel web Horizon con el usuario admin.

🌐 3. Configuración de Redes en OpenStack

Desde Horizon se realizan configuraciones fundamentales:

- Creación de key pairs para acceso vía SSH

- Creación de red interna, subred y router

- Asociación con red externa

- Configuración de security groups, incluyendo el puerto UDP 51820 para WireGuard

🖼️ 4. Creación de Imágenes e Instancias

Se sube una imagen de Ubuntu Cloud, se lanza una instancia en la red creada y se agrega:

- Una llave SSH

- Un script cloud-init para configurar el usuario

- Una Floating IP para acceso externo

 🔐 5. Acceso por SSH

Desde una máquina externa se accede a la instancia con la llave privada descargada, tras asignarle permisos adecuados.

🛡️ 6. Configuración del Servidor WireGuard

En la instancia se realiza:

- Habilitación del reenvío de IP

- Creación de claves del servidor

- Configuración del archivo wg0.conf

- Activación del servicio WireGuard

💻 7. Configuración del Cliente WireGuard

En el cliente (host externo):

- Se generan claves del cliente

- Se crea el archivo client.conf con datos del servidor

- Se instala WireGuard

- Se levanta la interfaz VPN para conectar con el servidor

🧪 8. Pruebas Finales

Se verifica la conexión mediante ping a la IP(10.8.0.1). 

