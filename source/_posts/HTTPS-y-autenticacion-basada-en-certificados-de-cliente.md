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


### Generación de certificados de usuario

(TBD)