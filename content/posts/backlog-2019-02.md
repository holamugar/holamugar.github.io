---
title: "Backlog 2019.02"
date: 2019-02-08
categorias: ["Backlog"]
tags: ["backlog","extensiones","magento","open source"]
description: "El viernes 1 de febrero (hace una semana) hicimos nuestro primer hangout abierto para conversar sobre varios temas que estaban a mitad de camino, algunos otros que estaban sin avance y alguna cosa que habíamos hecho no de la mejor manera."
image: images/posts/2019/02/2019-02-08-01.png
---

El viernes 1 de febrero (hace una semana) hicimos nuestro primer hangout abierto para conversar sobre varios temas que estaban a mitad de camino, algunos otros que estaban sin avance y alguna cosa que habíamos hecho no de la mejor manera.

Desde la [meetup de diciembre](/posts//recap-del-metameetup-8-en-buenos-aires/) se viene trabajando en ordenar y facilitar todo lo que sea necesario para que podamos colaborar online.

Se comenzó con una lista de temas que se venían conversando en [Slack](https://mugar.slack.com/) desde hacía varios días. Otros temas surgieron en la reunión.

Lo definido finalmente ha sido lo siguiente:

* Se creó el repositorio templates para guardar los [templates](https://github.com/holamugar/templates) que cada repositorio usará (para PR, issues, Readme, etc, etc).
* Se definió y corrigió cómo se nombran los repositorios y paquetes composer. Editamos la página de Cómo escribimos módulos y cambiamos repositorio y paquete de [Mugar_ArgentinaRegions](https://github.com/holamugar/module-argentina-regions).
* Se arreglaron los nombres de los demás repositorios, que aún son proyectos que no pasaron de la etapa alpha.
* Se definió que mediante estas reuniones, y hasta la próxima que se hará en marzo, se trabajará en una serie de módulos específicos (aunque no es una lista exclusiva).
* Cualquier discusión se llevará adelante o bien mediante issues en los módulos o en el canal #github dentro de Slack.
* Los módulos con los cuales avanzaríamos durante febrero son: [language-es_ar](https://github.com/holamugar/language-es_ar) y el módulo que agrega la posibilidad de indicar tipo y número de documento para un customer y sus subentidades.
* Otra definición que se tomó, luego de ver algunas cuestiones en el ecosistema, es que por lo pronto no haremos forks de los módulos de los gateways de pago.
* Debemos estandarizar la forma en que se configura la IDE para poder validar cuestiones mínimas de formato de código. Para esto vamos a adherir a lo que provee Magento para PHPCS y PHPMD.

La idea es avanzar sobre esta hoja de ruta durante febrero y ver, el mes próximo, en dónde nos encuentra.
