---
title: "Modificando el fondo de esta página"
date: 2022-11-10T19:42:20-06:00
draft: false
---

Este blog utiliza el framework Hugo con la plantilla PaperMod, por lo que todo es ampliamente configurable. Ahora vamos a modificar el fondo de la página por algo más interesasnte.

La página [addy codes](https://toolkit.addy.codes/) recopila muchisimas otras páginas con contenido para diseño web, de ahí encontré un [generador de patrones](https://app.haikei.app/?utm_source=toolkit.addy.codes). El cual elegí el diseño actual ajustando parámetros.

### Integrar el fondo al tema

El tema de PaperMod tiene una sección dónde especifica como extender la funcionalidad del mismo usando css propio en [este](https://discourse.gohugo.io/t/papermod-theme-how-to-add-custom-css/30165/3) artículo, pero a pesar de dicha función que viene implementada el buscador no pudo encontrar los archivos por más que los colocara en el sitio correcto.

Terminé poniendolos en la carpeta de contenido de los posts. Y editando el archivo de css en la carpeta extend (usada para extender el contenido css)

```
    .dark.list,.dark{
    background-image: url("../../posts/images/polygon-scatter-haikei.svg");
    background-repeat:repeat;
    /* background-image: url("../../posts/images/wave-haikei.svg"); */
    }
```

### Modificar el fondo de los posts

Ya que se aplicó al listado y a los posts, tuve que crear un fondo para los posts dónde tenga un contraste para poder leerse correctamente, así como un padding y un border radius.

```
    .post-single{
        background-color: rgb(46, 46, 51);
        padding: 1em;
        border-radius: 10px;
        -webkit-border-radius: 10px;
        -moz-border-radius: 10px;
        -ms-border-radius: 10px;
        -o-border-radius: 10px;
    }
```

Y con esto modifiqué la página para verse de mejor manera.