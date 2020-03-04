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