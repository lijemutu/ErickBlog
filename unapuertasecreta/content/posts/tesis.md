---
title: "Simulaciones y enfermedades craneales (Tésis de Licenciatura)"
date: 2022-09-08T14:25:35-05:00
# draft: true
---


En el desarrollo de personas o animales un punto crucial es la generación de huesos, específicamente el craneo. Las células que producen y generan el hueso son reguladas por señales externas que les indican dónde, cómo y cuánto producir de hueso, estas señales son mandadas por otras células usando proteínas.

![Gif de crecimiento craneal](../images/og.gif)

Existen proteínas para el aumento y la disminución de la producción de hueso, las cuales deben de coexistir en balance para que no ocurran malformaciones, la interacción de estas proteínas entre si se pueden representar por conjuntos de ecuaciones (específicamente ecuaciones diferenciales parciales acopladas no lineales, que largo nombre...) que se pueden resolver a través de métodos numéricos usando programas computacionales.

El trabajo que desarrollé fue una ampliación a un trabajo actual, el cual modela el desarrollo de los huesos de craneos de ratones desde etapas previas al nacimiento. Agruegué términos adicionales a las ecuaciones para poder representar nuevas células y el proceso de muerte celular o apoptósis.

![Imágen de cambios agregados al nuevo modelo](../images/edoref.png)
*A) Modelo previo, B) Modelo modificado sin apoptosis, C) Modelo modificado con apoptosis*

No solamente hubo cambios visuales sobre la forma de los huesos, sino también se encontraron enfermedades craneales al variar los parámetros de las ecuaciones como la craneosinostosis.


![Tabla de ecuaciones modificadas junto con su malformacion craneal](../images/tabla_de_mutaciones.png)

Si quieres puedes leer mi tesis en este [enlace](../images/Tésis9junio2022confechaconagradconportada.pdf).

