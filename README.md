# Balanceador con NGINX 

## Aprovisionamiento

### Creamos los scripts de aprovisionamiento para las máquinas según su requerimiento, el script del nginx se compartirá para las dos máquinas.
![](Imagenes/2Scriptsql.png)

![](Imagenes/3scriptnginx.png)

![](Imagenes/4scriptbalanceador.png)

## VagrantFile
![](Imagenes/1vagrantfile.png)

## Mysql
### En el servidor de SQL lo primero que tendremos que hacer es editar el archivo 50-server.cnf y poner la IP de la máquina.
![](Imagenes/5mysqsl.png)

### Luego entraremos en MySQL y le daremos un usuario para ambas máquinas Nginx en la base de datos lamp_db
![](Imagenes/6mysql.png)

### Ahora clonamos la base de datos de la práctica de josejuansanchez, para borrar las 3 líneas de configuración que trae por defecto
![](Imagenes/6.5mysql.png)
![](Imagenes/7mysql.png)


### A continuación, importamos la base de datos de la práctica de josejuan, y comprobamos que se ha importado correctamente. Tras esto, podremos borrar la carpeta de la práctica, ya que hemos cogido lo que necesitamos de ella
![](Imagenes/8mysql.png)


## Nginx

### Lo primero a hacer en las maquinas Nginx, es crear una carpeta con permisos para www-data y clonar la práctica y descomprimirla
![](Imagenes/9nginx.png)

### Introducimos la IP del servidor SQL, y el usuario y la contraseña con los que vamos a acceder, que son los que creamos antes para estas máquinas nginx
![](Imagenes/10nginx.png)

### También editamos el archivo conf, e indicamos que va a escuchar por el puerto 9000 en la 127.0.0.1
![](Imagenes/11nginx.png)

### Ahora copiamos el sitio default de sites available, y editamos el nginx para indicarle que vamos a usar un sitio tipo php
![](Imagenes/12nginx.png)

### Y también descomentamos las líneas que nos van a servir para utilizar el PHP y escuchar en su puerto
![](Imagenes/13nginx.png)

### Lo último que haremos en los nginx, será hacer un ln para tener un enlace en los sitios activos, y borrar el default.
![](Imagenes/14nginx.png)

## Balanceador

### En el balanceador indicamos la ip de los servidores, y podremos acceder a la base de datos con la IP pública del balanceador
![](Imagenes/15balanceador.png)
