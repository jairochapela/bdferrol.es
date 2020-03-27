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

Para utilizarla necesitáis VirtualBox instalado en vuestro ordenador. Desde el gestor gráfico de VirtualBox podéis importar el OVA y arrancáis la máquina recién creada. La red se configura sola por DHCP. Tiene ya creado un usuario llamado ``ricky`` con password ``maria123``. Téngase en cuenta que el usuario del que hablamos es un usuario del sistema, no de la base de datos; para acceder a esta última, utilizar el usuario ``root`` con la misma contraseña.

El archivo OVA lo podéis descargar de estos enlaces: 
* [Versión de 64 bits](https://assets.bdferrol.es/Maria.ova)
* [Versión de 32 bits](https://assets.bdferrol.es/Maria32.ova)