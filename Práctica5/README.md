#  Virtual NetWork

**Objetivo**
Aprender a implementar una red virtual de Azure así como el proceso para interconectarlas.

**Requesitos**
* Cuenta de Azure
* Suscripcion

**Desarrollo**
1. Creación de un Grupo de recursos.

![Resource Group ej. Sesion 5](../Pr%C3%A1ctica5/Images/Resource%20Group.png)

2. Implementación de dos Azure Virtual NetWorks.
![Virtual NetWorks ej VN1](../Pr%C3%A1ctica5/Images/Virtual%20Networks.png)
Al crear estos dos recursos, debemos tener en mente la regió donde se hospedarán las VMs, ya que de los contraio no se podrá conseguir el objetivo de la práctica.

3. Implementación de 2 Azure Virtual Machines.
![Virtual Machine1](../Pr%C3%A1ctica5/Images/VM1.png)

*Instancias*

Al implemetar la VM, se tomaron cuatro consideraciones: 
* La región señeccionada (Austria Center) se tomo debido a que al momento de la práctica ningun otra región nos permitia su implementación.
* Se opto por una imagen de Linux para conocer otros sistemas.
* En el apartado de redes debemos elegir alguna de las dos redes creadas (de preferencia optar por estandarizar VM1 con Virtual Network1).
* En el apartado de *Administration Account* debemos seleccionar "password", donde deberemos dar un user name y un password.
![](../Pr%C3%A1ctica5/Images/Administration%20Account.png)
---------

*Implementación*

Una vez creadas las VMs nos enfocamos en una, en este caso VM1; nos dirigimos al el apartado *"connection"*, seleccionamos SSH y comipamos el siguiente texto:

![](../Pr%C3%A1ctica5/Images/Connection.png)

Posteriormente seleccionamos el simbolo de terminal que se encuentra en la parte superior derecha, para entrar al Azure Cloud Shell.

![](../Pr%C3%A1ctica5/Images/Cloud%20Shell.png)

Ahora debemos acceder a nuestra VM1 mediante las siguientes lineas de código:

```
$ ssh diego@20.70.17.41 (aqui va el texto copiado al inicio de este apartado)
```
Esto desplegara unas lineas de texto donde te pedira tu contraseña registrada al crear el recurso de vm1, tal como se muestra a continuación:
````
diego@Azure:~$ ssh diego@20.70.17.41
The authenticity of host '20.70.17.41 (20.70.17.41)' can't be established.
ECDSA key fingerprint is SHA256:u1Ap8ccpV1APfx+f48Nli9rRGFc/JXW81Z0bAIvsISw.
Are you sure you want to continue connecting (yes/no)? yes 
Warning: Permanently added '20.70.17.41' (ECDSA) to the list of known hosts.
diego@20.70.17.41's password: 
Welcome to Ubuntu 20.04.4 LTS (GNU/Linux 5.13.0-1031-azure x86_64)
...
diego@vm1:~$
````

4. Agregar un Peering en alguna de las VMs.
Ahora debemos crear un Peering desde alguna de nuestras Virtual NetWorks, para lo cual nos vamos a la Virtual Network1 y en la barra de la parte inferior de la izquierda seleccionamos "perring" y posteriormente le damos en "+".

Por estandarizar al nombre seguimos la siguiente nomenclatura:
![](../Pr%C3%A1ctica5/Images/Perring.png)

y la Virtual Network con la cual la vamos a emparejar, en este caso virtualnetwork2.
![](../Pr%C3%A1ctica5/Images/Peering%20connection.png)

Finalmente al crearla debemos esperar hasta que se conecte para ir de nuevo al Cloud Shell y escribir:

```
$ ping 10.2.0.4
```
donde ```10.2.0.4``` es Private IP address de la VM2, dato que sacamos del Network interface.
![](../Pr%C3%A1ctica5/Images/Network%20Interface.png) 

Una vez hecho lo anterior podremos ver que todo se ha hecho correctamente porque comenzaremos a ver lo siguiente:


https://user-images.githubusercontent.com/72471180/174392139-f82d61fc-f7bf-40d5-9d80-f8e1546823af.mp4

