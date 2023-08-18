# Redes1_Tarea3_G1
Tarea No.3 del Laboratorio de Redes de Computadoras 1 Sección O
# Manual de Configuración de VPN
# Integrantes del Grupo
* Luis David Garcia Alay - 201612511
* María Julissa García Morán - 201602805
* Christopher Alexander Acajabon Gudiel - 201404278
* Luis Alfredo Vejo Mendoza - 201212527
# Herramientas Necesarias
 * Equipo
   * 4 estudiantes con PC con sistema operativo libre.
 * Software
   * Administrador de VPN's (OpenVPN)
 * Plataforma Utilizada
   * Google Cloud Platform (GCP)
# Pasos a seguir para la configuración de la VPN
1. Crear la maquina virtual
   * Para la creacion de la maquina virtual se debe contar con una cuenta de google si se desea utilizar GCP, procedemos a ir hacia el area de Compute Engine y luego en Virtual Machine en esta area le damos en          Crear Instancia, y nos saldra la siguiente imagen en donde podremos configurar nuestra instancia de VM, aqui podemos escoger las propiedades que necesitemos para nuestra maquina virtual, para la practica se        utilizaron las siguientes:
      * SO: Ubuntu
      * Maquina virtual de 2 nucleos y 8gb de ram
      * Acceso predeterinado
      * Trafico http y https

2. Iniciar la maquina virtual:
    * En este paso solamente debemos seleccionar la maquina virtual que creamos, hacer click derecho e iniciar maquina virtual.

3. Selecciona la opción SSH para abrir la consola del sistema operativo elegido.

4. Actualiza las librerías del sistema operativo con el comando:

       sudo apt-get update

5. Instalación del paquete WGET:

   * Verifica si WGET está instalado:

         sudo wget -v

   * Si no está instalado:

         sudo apt-get install wget

6. Verifica si WGET está correctamente instalado:

       sudo -i
   
       wget -v

8. Instalación de OpenVPN:
    - Para poder instalar la herramienta que nos permitira crear una red vpn debemos ingresar el siguiente comando:

          sudo wget https://cubaelectronica.com/OpenVPN/openvpn-install.sh
      
          sudo bash openvpn-install.sh

9. Ingresa la dirección IP pública de la máquina virtual.
  
    - Despues del paso anterior el programa nos pedira nuestra ip publica, para poder saber cual es nuestra ip publica, nos dirigimos a nuestro navegador y en la consola de google cloud donde nos muestra nuestras        maquinas virutal buscamos la maquina virtual que estamos utlizando actualmente y buscamos el apartado de ip public, copiamos el numero que se nos otorga y lo pegamos en nuestra consola.
 
10. Escoge el protocolo UDP para las conexiones VPN.

    - Luego de realizar el paso anterior, el programa nos pedira que escojamos el tipo de protocolo que queremos para nuestras conexiones, en este caso escojeremos el UDP ya que este es el protocolo que nos              interesa, para esto solo debemos ingresar el numero que corresponde al protocolo que queremos y le damos enter.

11. Define el puerto de escucha y el DNS de la red VPN.

    - Como siguiente paso debemos de ingresar el puerto de escucha de nuestra red vpn, en este caso se escogio el 1194.
    - Luego de ingresar nuestro puerto vamos a ingresar nuestro DNS, este nos indica en que zona de autoridad nos queremos ubicar, en este caso usaremos el DNS de google, para esto ingresamos el numero                  correspondiente a google.

12. Crea el certificado del cliente (puede tardar unos minutos).

    - Despues de realizar lo anterior nos pedira que ingresemos el nombre del certificado de nuestro cliente, con esto podremos identificar a nuestra manera a que cliente le estamos asignando el certicado que           estamos creando, para esto solo debemos ingresar el nombre que queremos con las especificaciones que nos pide OpenVPN.

13. Creación de reglas de Firewall:

    - Ve a Red de VPC en el menú y crea dos reglas: entrada-vpn para entrada y salida-vpn para salida.

    - Configura las propiedades de la regla: destino, filtro de origen, rango de IP y protocolos/puertos.
        * Para los destinos seleccionaremos todas las instancias de red.
        * Filtros de origen usaremos: Rangos de IP
        * Definiremos nuestros rangos de IP permitidos
        * Rango permitidos: 0.0.0.0/0
        * Filtro de origen ninguno
        * Protocolos y puertos, escogeremos protocolos y puertos especificados
        * Utilizaremos el protocolo UPD, con el puerto 1194

14. Descarga el perfil de cliente desde la consola.

15. Descarga el archivo desde la opción de descarga en la esquina superior derecha.

16. Prueba de Perfiles:

    - Instala OpenVPN en tu máquina física.

       - https://openvpn.net/vpn-client/

    - Carga el archivo de perfil en la aplicación.

    - Conecta y verifica la conexión exitosa.

17. Comprobación de la conexión externa y de la dirección IP.

18. Comprobación de la conexión desde el servidor VPN a tu máquina física usando 'ping'.

    * Para poder determinar que nuestra conexion fue exitosa, debemos abrir la consola de nuestra computadora fisica e ingresa el siguiente comando.
      - ipconfig

19. Creación de nuevos Perfiles:

    Ejecuta de nuevo el comando:

        sudo bash openvpn-install.sh

20. Pruebas de conexión al nuevo cliente usando 'ping'.
