---
title: Máquina virtual para pruebas
date: 2020-03-23 08:39:17
tags: Recursos
---
Pongo a vuestra disposición una imagen de una máquina virtual con la que podréis practicar algunas cosas. Se trata de una Debian de 64 bits con Apache y MariaDB instalados, con lo que podréis utilizarla para cargar ahí bases de datos SQL y probar a hacer consultas sobre éstas. La he dotado de lo siguiente:

* Apache2
* MariaDB
* Adminer
* OpenSSH

Para utilizarla necesitáis VirtualBox instalado en vuestro ordenador. Desde el gestor gráfico de VirtualBox podéis importar el OVA y arrancáis la máquina recién creada. La red se configura sola por DHCP. Tiene ya creado un usuario llamado ``ricky`` con password ``maria123``.

El archivo OVA lo podéis descargar de este enlace: [Maria.ova](https://assets.bdferrol.es/Maria.ova).