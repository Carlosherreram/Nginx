### Instalación y configuración de servidor web Nginx.

## Carlos Herrera Martín

# Instalación
Lo primero que deberemos hacer es instalar Nginx.
En este caso realizaremos el trabajo con una máquina Ubuntu por lo que la instalación la realizaremos mediante los comandos `sudo apt update` y después `sudo apt install nginx`.

![2](https://user-images.githubusercontent.com/91744455/167165224-ce01107d-1184-4afb-a492-296b6507e798.png)


# Prueba
Ahora para comprobar que la instalación ha salido bien escribiremos en nuestro navegador `localhost`.
![3](https://user-images.githubusercontent.com/91744455/167165443-dd1f08e6-8c67-4e38-b779-811269165d0a.png)

#Configuración 
Si accedemos a la carpeta `/etc/nginx/sites-available` y ejecutamos `cat default` podemos echar un vistazo al puerto que se utiliza, la ruta del archivo y el URL.
![4](https://user-images.githubusercontent.com/91744455/167166842-d73cac7c-3d2a-4fa3-9a33-99714772f593.png)

Si accedemos a `/var/www/html` y ejecutamos `cat index.nginx-debian.html` podemos ver el archivo html que se nos mostró en el navegador.
![5](https://user-images.githubusercontent.com/91744455/167167186-a570cbf9-3746-43b5-bc3a-1c7a158af885.png)


Ahora debemos añadir los archivos html de las dos páginas que queremos implementar en nuestro servidor Nginx.
Para eso crearemos dos carpetas dentro de `var/www` a una la llamremos *clock* y a la otra *fireworks*.
Después copiaremos dentro de cada carpeta sus respectivos archivos *index.html*.
![6](https://user-images.githubusercontent.com/91744455/167167840-5d40d792-6b9c-4d4f-ae7c-e20fd1a59789.png)

Lo siguiente que debemos hacer es volver a la ruta `/etc/nginx/sites-available`  y crear dos copias del archivo default renombrandolas, en este caso se llamarán *fireworks.cherrera.com* y *clock.cherrera.com*.
Debemos modificar el contenido de estos archivos eliminando la opción *default_server* de *listen* escribiendo la nueva ruta en *root* y cambiando el nombre del dominio en server_name.
![7](https://user-images.githubusercontent.com/91744455/167168581-43210857-4ea5-4055-9101-2fda633faecb.png)
![8](https://user-images.githubusercontent.com/91744455/167168706-ed370775-4f8f-439d-af52-ddc0d5c23afc.png)
Ahora accederemos a `/etc/nginx/sites-enabled` y los activaremos mediante el comando `sudo ln -s /sites-available/xxxx.cherrera.com` 

A continuación modificaremos el archivo *hosts* que se encuentra en `/etc` y añadiremos en *127.0.1.1* los dominios de nuestras páginas.
![9](https://user-images.githubusercontent.com/91744455/167168971-dd7be808-ff71-4646-b414-e8736fa69ea3.png)
Deberemos reiniciar Nginx para que se realicen los cambios mediante el comando `sudo nginx -s reload`.
![10](https://user-images.githubusercontent.com/91744455/167169586-f182c74d-b62e-426a-8b86-16046c60a9de.png)


#Comprobación 
En este punto sólo queda comprobar que todo ha salido correctamente y para ello escribiremos en nuestro navegador las URL que les hemos dado a los archivos .html.
![11](https://user-images.githubusercontent.com/91744455/167169775-df75a4de-3248-40a5-a4d9-a1a1168222af.png)
![12](https://user-images.githubusercontent.com/91744455/167169816-ae2b6fa4-4dbd-44ac-b606-03b5491cc82c.png)











