#   NGINX
## CASOS PRÁCTICOS

Veremos la versión instalada de nginx

`nginx -v`

![image](https://user-images.githubusercontent.com/91204696/211743585-37d0df5b-c54a-4e62-a4f1-338046f95ec7.png)

Nos metemos en `sites-enable`, para ver su fichero de configuración.

![image](https://user-images.githubusercontent.com/91204696/211751768-c66c9701-0739-4692-8554-4ceac5b75c69.png)

Lo que esta subrayado en la siguiente imagen, es el orden de carga que tiene nginx, para visualizar una página.

![image](https://user-images.githubusercontent.com/91204696/211751743-531c0dad-f943-4193-871f-d9e287d9cd96.png)

Le pondremos una red interna y una ip.

![image](https://user-images.githubusercontent.com/91204696/211765100-7ae3b93e-508b-40a2-a513-3c04d2ae20f4.png)


Ahora configuramos el balanceo de carga.

Necesitaremos 3 máquinas: La principal que es donde estará el balanceo de carga, el servidor 1 y el servidor 2.

Primero de todo borramos el `default` de `/etc/nginx/sites-enable`

![image](https://user-images.githubusercontent.com/91204696/211763462-365f7cf3-0cea-4a8d-ab1e-a5aa72aeeb5d.png)

Creamos el fichero `load-balacing-conf` y pegamos lo siguiente

    upstream backend {
    	ip_hash;
        server 172.26.0.123;
        erver 172.26.0.124;
    }
    
    server {
        listen      80;
        server_name loadbalancing.example.com;

        location / {
	        proxy_redirect      off;
	        proxy_set_header    X-Real-IP $remote_addr;
	        proxy_set_header    X-Forwarded-For $proxy_add_x_forwarded_for;
	        proxy_set_header    Host $http_host;
		proxy_pass http://backend;
	    }
     }

![image](https://user-images.githubusercontent.com/91204696/211764319-ae383a3d-2ea6-499a-9433-5c95fa5d1c42.png)

Comprobamos la sintaxis.

![image](https://user-images.githubusercontent.com/91204696/211755564-b3c2a483-399a-4d22-bc2c-f9941e373c2f.png)

Y reiniciamos el servicio.

![image](https://user-images.githubusercontent.com/91204696/211755684-883c5d41-58a9-438c-ae18-bb7b445f4f67.png)

Configuramos los otros dos servidores.
Les ponemos las ips:

***Servidor 1***

![image](https://user-images.githubusercontent.com/91204696/211766241-f234da03-b034-4026-acb5-9cd41e2e13bd.png)


***Servidor 2***

![image](https://user-images.githubusercontent.com/91204696/211766658-4a474ddb-6b3f-4e24-9253-331dc2eb109e.png)

En ambos servidores vamos a crear un index.html personalizado.

***Servidor 1***

![image](https://user-images.githubusercontent.com/91204696/211767938-324f6a03-a449-4d46-98b3-13ad381ea259.png)


***Servidor 2***

![image](https://user-images.githubusercontent.com/91204696/211768858-d9e60fb9-5c68-4350-9c2c-d041a77f56c8.png)


_________________________________________________________________________________________________________________

#### LICENCIA

<a rel="license" href="http://creativecommons.org/licenses/by-sa/4.0/"><img alt="Licencia de Creative Commons" style="border-width:0" src="https://i.creativecommons.org/l/by-sa/4.0/88x31.png" /></a><br />Este obra está bajo una <a rel="license" href="http://creativecommons.org/licenses/by-sa/4.0/">licencia de Creative Commons Reconocimiento-CompartirIgual 4.0 Internacional</a>.
