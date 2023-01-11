#   NGINX
## CASOS PRÁCTICOS

Veremos la versión instalada de nginx

`nginx -v`

![image](https://user-images.githubusercontent.com/91204696/211743585-37d0df5b-c54a-4e62-a4f1-338046f95ec7.png)

Nos metemos en `sites-enable`, para ver su fichero de configuración.

![image](https://user-images.githubusercontent.com/91204696/211751768-c66c9701-0739-4692-8554-4ceac5b75c69.png)

Lo que esta subrayado en la siguiente imagen, es el orden de carga que tiene nginx, para visualizar una página.

![image](https://user-images.githubusercontent.com/91204696/211751743-531c0dad-f943-4193-871f-d9e287d9cd96.png)

Ahora configuramos el balanceo de carga.

Primero de todo borramos el `default` de `/etc/nginx/sites-enable`

![image](https://user-images.githubusercontent.com/91204696/211753449-61409722-837f-47d8-9f59-ad776d592bb1.png)

Creamos el fichero `load-balacing-conf` y pegamos lo siguiente

    upstream backend {
        server 192.168.10.11;
        server 192.168.10.12;
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

![image](https://user-images.githubusercontent.com/91204696/211755401-1c6dff53-28d8-43cf-87a0-58da48fece65.png)

_________________________________________________________________________________________________________________

#### LICENCIA

<a rel="license" href="http://creativecommons.org/licenses/by-sa/4.0/"><img alt="Licencia de Creative Commons" style="border-width:0" src="https://i.creativecommons.org/l/by-sa/4.0/88x31.png" /></a><br />Este obra está bajo una <a rel="license" href="http://creativecommons.org/licenses/by-sa/4.0/">licencia de Creative Commons Reconocimiento-CompartirIgual 4.0 Internacional</a>.
