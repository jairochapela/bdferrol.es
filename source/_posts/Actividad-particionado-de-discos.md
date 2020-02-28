---
title: 'Actividad: particionado de discos'
date: 2020-02-28 11:19:54
tags: UF1466
---
En este ejercicio trabajamos con particiones y su creación durante el proceso de instalación del sistema operativo.

Crearemos una máquina virtual con las suguientes características:
- S.O. Linux Debian de 64 bits
- 1024 MB de RAM
- Disco duro virtual de 8 GB, dinámicamente alojado

Sobre esta máquina virtual instalamos el sistema operativo a partir de la ISO de instalación en red de Debian. La configuraremos para que tenga las siguientes particiones:
- Una partición de 3 GB para el sistema raíz (/)
- Una partición de 4 GB para las carpetas de usuarios (/home)
- Una partición de 1 GB para la memoria de intercambio o swap

Las particiones tendrán un sistema de archivos de tipo Ext4; a excepción de la swap, que tendrá el formato propio.

Para formalizar la entrega, se pide un documento en el que se enumeren las particiones creadas y sus respectivos puntos de montaje. Acompáñese la enumeración con capturas de los comandos ``cat /proc/partitions`` y ``mount``. Indicar también cómo está configurada la swap, con la correspondiente captura del comando ``free``. La entrega se hará de forma individual, en un documento PDF, a través de [este enlace](https://zurdistan.cloud/index.php/s/qsQ7xxm34qKYGTd).
