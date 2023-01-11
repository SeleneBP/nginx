# NGINX
## INSTALACIÓN
Lo primero que haremos es actualizar nuestra máquina en mi caso Debian 11.

`apt update`

Ahora instalaremos el siguiente paquete

`apt install -y nginx`

![image](https://user-images.githubusercontent.com/91204696/211600496-81848b6c-b641-4efc-9727-762420d9ead7.png)

Vemos el estado.

![image](https://user-images.githubusercontent.com/91204696/211750455-8271c6f5-ae5d-4e8b-9bb6-3f26f4f91193.png)

Habilitamos el puerto ***http*** y ***https***
Primero instalamos el comando `ufw` y habilitamos el puerto `ufw allow http` / `ufw allow https`

![image](https://user-images.githubusercontent.com/91204696/211745024-a03a64f0-4283-4e03-945a-266ee7ce66c0.png)

![image](https://user-images.githubusercontent.com/91204696/211745171-a873c7c8-2ded-4c05-b9f0-c54317c4ce57.png)

Vamos al navegador y ponemos `localhost` para ver si se ha instalado correctamente.

![image](https://user-images.githubusercontent.com/91204696/211750068-7cd6babe-9c9c-4485-9652-21cd45efd3b4.png)

Personalizamos la página de nginx. Creamos un `index.html` apartir del que viene por defecto.

![image](https://user-images.githubusercontent.com/91204696/211751244-32f83c39-1da5-407f-afa5-5435320f6746.png)


#### LICENCIA

<a rel="license" href="http://creativecommons.org/licenses/by-sa/4.0/"><img alt="Licencia de Creative Commons" style="border-width:0" src="https://i.creativecommons.org/l/by-sa/4.0/88x31.png" /></a><br />Este obra está bajo una <a rel="license" href="http://creativecommons.org/licenses/by-sa/4.0/">licencia de Creative Commons Reconocimiento-CompartirIgual 4.0 Internacional</a>.
