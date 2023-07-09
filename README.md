# rtmp-server-hls

Español / Spanish

Para hacerlo funcionar solo tienes que editar el fichero index.html que está ubicado en /srv/www/index.html 
y modificar "stream.m3u8" cambiando "stream" por la clave de stream que se desea, no se admite caracteres especiales.

Luego puedes acceder a el por http://{IP_SERVIDOR}/index.html

En el programa de emisión (OBS, VMIX, Etc..), en servidor poner: rtmp://{IP_SERVIDOR}/live/{Clave_Stream}


Ingles / English

To make it work you just have to edit the file index.html which is located in /srv/www/index.html
and modify "stream.m3u8" by changing "stream" to the desired stream key, special characters are not allowed.

Then you can access it by http://{SERVER_IP}/index.html

In the broadcast program (OBS, VMIX, Etc..), on the server put: rtmp://{SERVER_IP}/live/{Stream_Key}
