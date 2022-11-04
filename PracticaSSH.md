## En el Servidor: 

### Crea un usuario nuevo:

$ sudo useradd nombreUsuario

### Activa servidor SSH: 

$ sudo systemctl start ssh

$ sudo cp /etc/sshd_config{,.back}
> Y para editarlo si hace falta
> $ sudo nano /etc/sshd_config
> - Port 22
> - HostKey /etc/ssh/ssh_host_rsa_key
  HostKey /etc/ssh/ssh_host_dsa_key
  HostKey /etc/ssh/ssh_host_ecdsa_key
- SyslogFacility AUTH
  LogLevel INFO
- LoginGraceTime 120
  PermitRootLogin yes
  StrictModes yes
  
$ sudo systemctl reload ssh

### Busca la ip del ordenador:

$ ifconfig (inet 192.168.0.XXX)

## En el Cliente: 

### Para entrar dentro del otro ordenador: 
- $ ssh ejercicio@192.135.0.XXX

### Instalacion Apache en el servidor:  
[Paso a paso de como Instalar Apache.](https://github.com/PauMadu/Tema-3/blob/main/MemoriasApache.md)

### Pasa una web a algún lugar del servidor: 

### Crea un virtualhost: 

### Modifica los host del local para que con la dirección elegida vaya a la ip del servidor: 

### Comprueba que puedes conectarte a la página: 

### Abre en el servidor un browser a la página: 
