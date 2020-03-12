---
title: HTTPS y autenticación basada en certificados de cliente
date: 2020-03-12 09:54:31
tags: UF1468
---
El procedimiento a seguir consta de los siguientes pasos:

1. Creación de clave y certificado de CA raíz
2. Solicitud de certificados de cliente
3. Generación del certificado


### Generación del certificado raíz

El certificado se genera con este comando:
```
openssl genrsa -des3 -out root-ca.key 1024
```
Pedirá una contraseña o _passphrase_ para cifrar la clave que se va a generar, protegiéndola así de usos indebidos.

Una vez generada la clave, se procede con el autofirmado:

```
openssl req -new -x509 -days 3650 -key root-ca.key -out root-ca.crt
```

### Generación de certificado de host
Ya disponiendo de un certificado raíz, podemos crear certificados de host. Este tipo de certificado es el que nos entrega el servidor cuando accedemos a él, y debiera ir firmado por el certificado raíz (el que generamos anteriormente). Para proceder:

```
openssl req -new -key certificate.key -out certificate.csr
```

Este paso generará una **solicitud** de certificado, no el certificado en sí. Para obtener este último:

```
openssl x509 -req -in certificate.csr -CA root-ca.crt -CAkey root-ca.key -CAcreateserial -out certificate.crt -sha256
```

Podemos indicarle un tiempo de validez en días si además incorporamos la opción ``-days 365`` (para un año, por ejemplo).

Una vez generado el certificado, copiaremos clave y certificado en el servidor, asegurándonos de que el acceso a la clave está protegido. El servidor web ha de configurarse para utilizar el certificado.

```
cp root-ca.crt certificate.crt /etc/ssl/certs
cp root-ca.key certificate.key /etc/ssl/private
```

El certificado recién generado se indicará en la configuración del servidor web (Apache) para que lo utilice. Es necesario reiniciar el servicio.

### Generación de certificados de usuario

Para generar un certificado de usuario comenzamos también con una solicitud:

```
openssl req -newkey rsa:2048 -keyout jairo.key -out jairo.csr
```

A partir de la solicitud se genera el certificado.

```
openssl x509 -req -in jairo.csr -CA root-ca.crt -CAkey root-ca.key -extensions client -out jairo.csr
```

El certificado se empaqueta en formato PKCS12 para poder entregárselo al usuario y que éste lo pueda importar en su equipo:

```
openssl pkcs12 -export -inkey jairo.key -in jairo.crt -out jairo.p12
```

El fichero .p12 resultante está listo para ser importado en el navegador.
