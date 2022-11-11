## En el Servidor: 

### Crea un usuario nuevo:

$ sudo useradd nombreUsuario

### Activa servidor SSH: 

$ sudo systemctl start ssh
$ sudo ufw allow 22

$ sudo cp /etc/sshd_config{,.back}  
> Y para editarlo si hace falta  
> $ sudo nano /etc/sshd_config  
> - Port 22  
> - HostKey /etc/ssh/ssh_host_rsa_key  
  HostKey /etc/ssh/ssh_host_dsa_key  
  HostKey /etc/ssh/ssh_host_ecdsa_key  
> - SyslogFacility AUTH  
  LogLevel INFO  
> - LoginGraceTime 120  
  PermitRootLogin yes  
  StrictModes yes
  
```  
$ sudo systemctl reload ssh
```  

### Busca la ip del ordenador:
```  
$ ifconfig (inet 192.168.0.XXX)
```  

## En el Cliente: 

### Para entrar dentro del otro ordenador: 
```  
$ ssh ejerciciossh@192.168.0.XXX
```  
### Instalacion Apache en el servidor:  
[Paso a paso de como Instalar Apache.](https://github.com/PauMadu/Tema-3/blob/main/MemoriasApache.md)

### Pasa una web a algún lugar del servidor: 
sudo chmod +777 ./ejercicio

Primero crearemos un documento.html en el escritorio del cliente y para pasarlo al servidor solo tendremos que ejecutar:
``` 
$ scp ./Escritorio/hola.html ejerciciossh@192.168.0.XXX:/var/www/ejercicio
``` 

sudo nano /etc/apache2/sites-available/ejerciciossh.conf

sudo gedit /etc/hosts
Y poner la ip junto el nombre www.ejerciciossh.com

sudo a2dissite ejerciciossh.conf

systemctl reload apache2

sudo a2ensite ejerciciossh.conf

systemctl reload apache2


### Crea un virtualhost: 

Creamos un directorio:  
```  
$ sudo mkdir /var/www/your_domain 
```  
Le damos permisos al directorio:  
``` 
sudo chmod -R 755 /var/www/your_domain  
``` 
Y creamos la pagina:
``` 
sudo nano /var/www/your_domain/index.html
``` 
Y dentro del editor agregaremos:  
``` 
<html>
    <head>
        <title>Welcome to Your_domain!</title>
    </head>
    <body>
        <h1>Success!  The your_domain virtual host is working!</h1>
    </body>
</html>
``` 
Guardamos y cerramos.

### Modifica los host del local para que con la dirección elegida vaya a la ip del servidor: 

```sudo gedit /etc/hosts```
Donde se nos habrirá un Gedit y deberemos modificar lo siguiente.  
![Modificación](https://github.com/PauMadu/Tema-4/blob/main/hosts.png)

### Comprueba que puedes conectarte a la página: 
![Comprobación](https://github.com/PauMadu/Tema-4/blob/main/Comprobacion.png)

### Abre en el servidor un browser a la página: 
