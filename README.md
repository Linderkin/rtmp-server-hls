# rtmp-server-hls

## Español

[**Docker**](https://www.docker.com/) Imagen basada en Debian12-slim con [**Nginx**](http://nginx.org/en/) usando el modulo_ [**nginx-rtmp-module**](https://github.com/arut/nginx-rtmp-module)  para video en streaming con un reproductor.

## Descripción

Esta [**Docker**](https://www.docker.com/) imagen es para montar un servidor RTMP para multimedia / video stream, las principales caracteristicas de esta imagen son:

[**Basado en Debian12-slim**](http://debian.org)

[**Nginx v1.25.1**](http://nginx.org/en/) 

[**Modulo RTMP Nginx v1.2.2**](https://github.com/arut/nginx-rtmp-module)


**Imagen de Docker Hub**: <[https://hub.docker.com/repository/docker/linderkin/rtmp-hls-server](https://hub.docker.com/repository/docker/linderkin/rtmp-hls-server)>

## Detalles

## Como usar

* Puede simplemente ejecutar el siguiente comando en docker (se puede modificar luego los ficheros por nano)

```bash
docker run -d -p 1935:1935 -p 8080:8080 linderkin/rtmp-hls-server
```

## Cómo hacerlo funcionar con OBS Studio y VLC

* Ejecute el contenedor con el comando anterior

#OBS
* Abre el [OBS Studio](https://obsproject.com/)
* Hacemos click  en el botón "Ajustes" => "Emision" o en "Archivo" => "Ajustes" => "Emision"
* En "Servicio" seleccionamos "Personalizado"
* En "Servidor" ponemos: `rtmp://<IP_Servidor>/live` cambiando `<IP_Servidor>` con la ip donde se está ejecutando el contenedor. Por ejemplo: `rtmp://192.168.1.162/live`
* En "Clave de retransmision" usar `stream` (esto se puede cambiar editando el archivo index.html en `/srv/www/`
* Hacemos click en el botón Aceptar
* Hacemos click en el botón Start Streaming

#VLC Player
* Abrir  [VLC](http://www.videolan.org/vlc/index.html) player
* Hacemos click en la opción "Medio"  del menu de navegación
* Click en "Abrir ubicación de red"
* Ponemos la url de arriba como `rtmp://<IP_Servidor>/live/<key>` cambiando `<IP_Servidor>` con la ip donde se está ejecutando el contenedor y cambiamos `<key>`  por la clave de transmision que tengamos en el codigo del index.html. Por ejemplo: `rtmp://192.168.1.162/live/stream`
* Click en "Reproducir"
* Ahora VLC, se pondrá a reproducir lo que esteas emitiendo por OBS u otro programa.

#Navegador
* Abre un navegador (Chrome, Firefox, Safari, Edge)
* Escribe la siguiente url y pulsa enter `http://<IP_Servidor>:8080/index.html` (esto puedes cambiarlo en tu router, para que cuando alguien entre por el puerto 80 vaya al 8080 en local asi solo tendria que poner `http://<IP_Servidor>`
* El reproductor debería comenzar a emitir la transmisión
* Ten en cuenta que de forma predeterminada el archio index.html intenta abrir el archivo `stream.m3u8` por la clave `stream` que puedes cambiar.

## Licencia

Este proyecto está licenciado bajo los términos de la Licencia MIT.


## English

[**Docker**](https://www.docker.com/) image based on Debian12-slim with [**Nginx**](http://nginx.org/en/) using the [**nginx-rtmp-module**](https://github.com/arut/nginx-rtmp-module) module for live video streaming with hls player

## Description

This [**Docker**](https://www.docker.com/) image can be used to create an RTMP server for multimedia / video streaming using [**Nginx**](http://nginx.org/en/) and [**nginx-rtmp-module**](https://github.com/arut/nginx-rtmp-module), built from the current latest sources (Nginx 1.25.1 and nginx-rtmp-module 1.2.2).

This was inspired by other similar previous images from [tiangolo](https://hub.docker.com/r/tiangolo/nginx-rtmp/)

**Docker Hub image**: <[https://hub.docker.com/repository/docker/linderkin/rtmp-hls-server](https://hub.docker.com/repository/docker/linderkin/rtmp-hls-server)>

## Details

## How to use

* For the simplest case, just run a container with this image:

```bash
docker run -d -p 1935:1935 -p 8080:8080 linderkin/rtmp-hls-server
```

## How to test with OBS Studio and VLC

* Run a container with the command above


* Open [OBS Studio](https://obsproject.com/)
* Click the "Settings" button
* Go to the "Stream" section
* In "Stream Type" select "Custom Streaming Server"
* In the "URL" enter the `rtmp://<ip_of_host>/live` replacing `<ip_of_host>` with the IP of the host in which the container is running. For example: `rtmp://192.168.0.30/live`
* In the "Stream key" use `stream`
* Click the "OK" button
* In the section "Sources" click the "Add" button (`+`) and select a source (for example "Screen Capture") and configure it as you need
* Click the "Start Streaming" button


* Open a [VLC](http://www.videolan.org/vlc/index.html) player
* Click in the "Media" menu
* Click in "Open Network Stream"
* Enter the URL from above as `rtmp://<ip_of_host>/live/<key>` replacing `<ip_of_host>` with the IP of the host in which the container is running and `<key>` with the key you created in OBS Studio. For example: `rtmp://192.168.0.30/live/stream`
* Click "Play"
* Now VLC should start playing whatever you are transmitting from OBS Studio


* Open an internet Browser
* in the address bar, enter `http://<ip_of_host>:8080/index.html`
* the hls player should start playing the stream
* Note that by default, index.html try to open stream.m3u8 for the key `stream`
* to enable more stream keys, duplicate /srv/www/index.html and modify line 16 to match your key


## License

This project is licensed under the terms of the MIT License.
