Después entramos al netplan y editamos:

  ![imatge](img/foto1.png)




INSTALA EL SERVICIO SSH AL UBUNTU
instalamos eln ssh desde ubuntu:

habilitamos el ssh

Miramos que el servicio ssh esté activo:















DOCUMENTA LA PRIMERA CONEXIÓN DÓNDE PREGUNTA POR LA VALIDEZ DEL CERTIFICADO.
Hacemos ip a en ubuntu para ver la ip del adaptador de solo anfitrión:


Ahora si desde la máquina Windows en powershell o terminal comprobamos la conexión haciendo ssh + nombre de la máquina Ubuntu + ip de solo anfitrión de la máquina Ubuntu .Nos pedirá permisos, osea la contraseña y unos cuántos “yes”



























HABILITA EL USUARIO ROOT EN UBUNTU (SE HACE PONIENDO UNA CONTRASEÑA)
Ahora habilitamos el usuario root y lo hacemos poniendo una contraseña. Hacemos sudo passwd root y nos pedirá la contraseña y le asignaremos una contraseña la cuál le he puesto “usuari”


MUESTRA LA CONFIGURACIÓN RELATIVA A LOS USUARIOS EN EL ARCHIVO sshd_config: Habilita solo un usuario para poder acceder remotamente y que otros no puedan conectarse.

Desde la máquina Ubuntu entramos al siguiente archivo:

Dentro del archivo añadimos la última línea que se muestra a continuación:














COMPRUEBA CÓMO EL USUARIO ROOT SI PUEDE HACER LOGIN EN LOCAL PERO NO PUEDE INICIAR SESIÓN REMOTA VÍA SSH
Desde la máquina Ubuntu hacemos login de manera local con el usuario root:

Después desde la máquina Windows intentaremos hacer ssh con el usuario root y veremos qué nos dice que el acceso es denegado. Se hace poniendo ssh + el nombre de usuario que en este caso el root + la ip de la máquina Ubuntu




















DOCUMENTA Y CONFIGURA SSH PARA ACCEDER CON CERTIFICADO CLIENTE EN LUGAR DE USUARIO Y CONTRASEÑA

En la máquina Windows generamos algunos códigos RSA con la comanda siguiente: 
























Ahora lo que vamos hacer es mirar que tengamos los archivos anteriores que necesitamos, lo cuál tenemos que copiar en nuestra máquina Ubuntu es el que acaba en .pub y lo vamos a copiar con la comanda scp

Con la comanda scp lo copiamos a la máquina Ubuntu:















En nuestra máquina ubuntu creamos el siguiente archivo, tiene que estar dentro de la carpeta ssh. Lo creamos con la siguiente comanda:

Ahora copiamos la clave id_rsa.pub dentro del archivo que creamos en la comanda anterior.


Ahora desde la máquina Windows hacemos ssh + nombre de la máquina Ubuntu en mi caso es usuari + ip para comprobar que podemos conectarnos a la máquina ubuntu sin que nos pida la contraseña.












CONFIGURA EN EL EQUIPO WINDOWS 11 EL SERVIDOR OpenSSH

Entramos a la configuración de Windows 11 y entramos a sistemas.




















Dentro de sistemas tenemos que entrar a “ver características” y permitimos que la aplicación haga cambios en el dispositivo.




































Una vez dentro de la aplicación, IMPORTANTE darle a “ver las características disponible”

















Buscamos “OpenSSH”, marcamos la casilla y le damos a agregar.






Una vez agregado seguimos con el siguiente punto.














CONÉCTATE REMOTAMENTE DESDE EL EQUIPO LINUX en mi caso es (UBUNTU)

Para poder conectarnos remotamente primero tenemos que hacer lo siguiente:

-Primero apagamos el Firewall en windows 11, buscamos “Firewall y protección de red” entramos y seguidamente entramos a “Red pública” y la desactivamos.









-Seguidamente ejecutamos el powershell como administrador 


-Una vez iniciado el powershell como administrador encendemos en servicio de server SSH


-Hacemos que cada vez que iniciemos la máquina se active el servicio.



-Por último hacemos ipconfig desde el powershell de la máquina Windows para ver la ip del adaptador de solo anfitrión y que después con esa ip nos conectaremos desde la máquina Ubuntu.






Ahora si que hacemos el ejercicio que es conectarnos remotamente desde la máquina Linux que en mi caso es Ubuntu.
Desde la máquina Ubuntu nos conectamos a la máquina Windows con la ip de la interfície de solo anfitrión de la máquina Windows.
-Primero hacemos un ping desde la máquina Ubuntu para comprobar que se pueden ver entre las dos máquinas. El ping sería ping + ip de solo anfitrión de la máquina Windows.

-Una vez comprobado que las dos máquinas se ven ahora si que nos conectamos desde la máquina Ubuntu a la máquina Windows. Lo vamos hacer haciendo ssh + el nombre de la máquina windows + la ip de solo anfitrión.



CREA UN TÚNEL COMO EL DE LA GUÍA 


Creamos el túnel con la siguiente comanda:





Configuración del tunel proxy en windows:


