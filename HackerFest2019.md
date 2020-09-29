# HackerFest2019 - Walkthrough



`nmap -sC -sV 192.168.153.32 -o nmap-scan`

**Escaneo de Puertos**

![](images/hackerfest2019/nmap1.png)

![](/images/hackerfest2019/nmap2.png)

Dentro de los archivos que existen dentro de FTP esta wp-config.php

**Extraccion de archivo de configuracion de wordpress**

![](/images/hackerfest2019/accesoftp.png)

**Revision del contenido de wp-config.php**

![](/images/hackerfest2019/wp-config.png)

No se puede acceder con estas credenciales ni via SSH ni en wp-admin. Otro vector de ataque seria utilizando un exploit para webmin

**Exploits sugeridos para Webmin**

![](/images/hackerfest2019/searchsploit.png)

![](/images/hackerfest2019/webmin.png)

**Configuracion en Rapid7**

![](/images/hackerfest2019/rapid7.png)

Se ingresa a metasploit los datos que se solicitan para el exploit.

+ RHOST 192.168.153.32
+ LHOST 192.168.49.153
+ LPORT 443
+ exploit target 0 
+ SSL true
+ forceexploit true

**Exploit**

![](/images/hackerfest2019/exploit.png)

**Flag{92bf511a#######################}**  proof.txt
**Flag{d1d8bcfa########################}** local.txt

## Referencias

+ **Pasos para ejecutar el exploit** https://www.rapid7.com/db/modules/exploit/linux/http/webmin_backdoor
+ **Exploit Webmin 1.920 -Remote Code Execution** https://www.exploit-db.com/exploits/47293
