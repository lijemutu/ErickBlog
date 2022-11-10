---
title: "Nameorigin o el origen de los altos puestos"
date: 2022-09-15T14:38:12-05:00
draft: false
---

### ¿Por qué es normal escuchar a nuestros gobernantes y funcionarios con apellidos no tan comunes?

Esta pregunta me llamó la atención, nombres y apellidos como Sheinbaum (CDMX), Cosío (BCS), Vizcaíno (Colima) [entre otros](https://www.conago.org.mx/gobernadores). Han ocupado los puestos de gobernantes de nuestro país por decadas, es raro aunque no imposible encontrarnos a un alto funcionario con apellidos dentro de la [lista de los más comunes](https://politica.expansion.mx/mexico/2022/08/11/estos-son-los-apellidos-mas-comunes-en-mexico):
* Hernández
* García
* Martínez
* González
* López
* Rodríguez

Entre otros, por otra parte este comportamiento es visto en entornos empresariales, siendo los dueños de las grandes empresas mexicanas poseedores de apellidos no tan comunes:

* Carlos **Slim Helú**
* Carlos Slim **Domit**
* Germán **Larrea** Mota Velasco
* Daniel **Servitje Montull**
* Alejandro **Baillères Gual**
* Carlos **Hank** González
* Armando Garza **Sada**
* Antonio Valle **Perochena**

Al parecer hay una clara relación entre el poder y apellidos no tan comunes, o dicho de otra manera, el poder heredado debido del colonialismo.

Esta aplicación que realicé muestra un mapa de los gobernantes de los estados de México y el origen de sus apellidos, para observar de forma gráfica los estados y el origen de los apellidos de sus gobernantes. También incluye una sección dónde podrás ingresar algun nombre o apellido de alguna persona y buscar su origen.

### Detalles técnicos

Esta aplicación fue realizada con el lenguaje python como backend, utilizando el framework flask y algunas librerias para renderizar y manipular información geoespacial. Para la persistencia se utilizó una base de dato llamada PostgreSQL.

Se desplegó en una máquina virtual ec2 de AWS, a través de docker compose para manejar el servicio de la aplicación y la base de datos dentro del mismo entorno. Lo cual si bien fue la forma más barata de tener una aplicación ejecutandose no la más sencilla.

Para crear y destruir las instancias de ec2 se utilizó el programa de Pulumi que es una apalicación de IaC o (Infraestructure as code), dónde no solamente gestiona los gateways de red y los grupos de seguridad sino también el script inicial que ejecuta la máquina virtual. Descargar, instalar, configurar y ejecutar fueron las tareas que realiza dicho script. Nuevamente al no usar servicios manejados (abaratando costo) se tuvo que desarrollar todo esto.

Al estar en linea con una IP pública se encontró un reto muy importante de caídas en el sitio, los buscadores de puertos, que buscan aleatoriamente direcciones ip, con el puerto http (80) abierto para intentar por fuerza bruta obtener algún acceso o información del sistema. Comunmente dirigido a sitios de wordpress

Por lo que otra aplicación tuvo que ser utilizada para poder mitigar estos intrusos, fail2ban fue instalada y configurada para bloquear ips con comportamientos extraños.

### Conclusión

Se nota el trabajo que conlleva usar bare metal para desplegar alguna aplicación, y no es para nada poco lo que los servicios administrados ofrecen, porque en unos pocos clics se realiza toda esta ejecución que fue trabajo de varias semanas. Todo conlleva un precio, tanto monetario como en horas hombre.






