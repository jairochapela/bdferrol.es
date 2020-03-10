---
title: 'Actividad: servidor WebDAV'
date: 2020-03-09 12:19:58
tags: UF1466
---
Vamos a configurar un servidor WebDAV que nos permita crear una unidad de almacenamiento en red y compartir archivos y carpetas. Trabajaremos sobre una máquina virtual Debian con el servidor Apache instalado.

Para el proceso de configuración nos podemos guiar por los siguientes enlaces:

* [Instalar WebDAV en Debian 9 con soporte SSL](https://librematica.es/blogs/instalar-webdav-debian-9)
* [Servidor WebDAV - Servidor Debian](https://servidordebian.org/es/squeeze/internet/webdav/apache2_davfs) (desactualizado)

Aunque el primer enlace lo trata, no sería necesario habilitar el soporte SSL.

Para testearlo, podemos utilizar alguna herramienta como **cadaver** y/o el propio explorador de Windows, conectándonos a una unidad de red.

### Compatibilidad con Windows

Es posible acceder al servicio desde el explorador de Windows, conectándose a él como una unidad de red. No obstante, existen unas limitaciones en cuanto a compatibilidad (o, más bien, por seguridad). Para que funcione, debemos cambiar la configuración de WebDAV para que utilice un esquema de autenticación basado en HTTP Digest. Lo activaremos con el comando ``a2enmod auth_digest`` y la configuración queda similar a esto:

```xml
<Location /webdav>
        DAV On
        AuthType Digest
        AuthName "webdav"
        AuthUserFile /etc/apache2/webdav.passwd
        Require valid-user
&lt;/Location>
```

Al utilizar este tipo de autenticación, también debemos generar contraseñas con el comando **htdigest**, del modo siguiente:

```
htdigest -c /etc/apache2/webdav.passwd WebDAV usuario
```


### Si algo va mal...

Para detectar errores o causas de un mal funcionamiento puede ser de utilidad consultar el registro de errores de Apache. Se puede hacer con el comando siguiente:
```
tail -f /var/log/apache2/error.log
```

