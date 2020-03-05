---
title: 'Actividad: automatización de backups incrementales con cifrado'
date: 2020-03-04 11:28:50
tags: UF1466
---
La importancia de hacer copias de seguridad es innegable. Tanto empresas como particulares tienen la necesidad de gestionar, de algún modo, la salvaguarda de la información que manejan en su día a día para que, en caso de pérdida o catástrofe, puedan recuperarla.

Partimos de un caso en el que tenemos un servidor GNU/Linux que contiene cuentas de usuario, con sus correspondientes carpetas de trabajo. Nos interesa programar una copia de seguridad que cumpla con los siguientes requerimientos:

* Que sea de tipo incremental.
* Que conserve toda la información de fechas, propietario y permisos.
* Que los datos de la copia de seguridad vayan cifrados.
* Que se pueda automatizar mediante el programador de tareas **cron**.
* Que la copia de seguridad se pueda copiar en la nube y/o en dispositivos externos.

En cuanto a la periodicidad de las copias, se pretende mantener una copia completa semanal y copias incrementales diarias.

## Se pide

Elaborar un documento que describa el procedimiento a seguir, paso a paso, para instalar y configurar el procedimiento de copias de seguridad periódicas. Es importante incluir en dicho documento un apartado que detalle el proceso de recuperación de una copia de seguridad previa. El documento se entregará en formato PDF a través de [este enlace](https://zurdistan.cloud/index.php/s/bdD2n6fmPnxar3x).

## Algo de información

El procedimiento consta de las siguientes partes o tareas:

* Instalar Duplicity.
* Definir una clave para el cifrado de las copias de seguridad.
* Disponer de un servidor remoto, accesible por SSH. En ese servidor tendremos una cuenta de usuario y una carpeta ``backups``.
* Generación en local de un par de claves RSA (sin passphrase) para poder acceder al servidor sin tener que introducir la contraseña.
* Transferir la clave pública RSA al servidor remoto.
* Configurar **cron** para que automatice las copias de seguridad.

A modo de referencia, se proporcionan algunos scripts y configuraciones para realizar este proceso con **Duplicity**, copiando al servidor remoto los backups mediante **rsync**. Pueden consultarse [en este enlace](https://gist.github.com/jairochapela/ee088e8b5d514203302007ee3b51bcb4).