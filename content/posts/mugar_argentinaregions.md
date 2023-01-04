---
title: "Mugar_ArgentinaRegions"
date: 2018-12-27
categories: ["Extensiones"]
tags: ["extensiones","mugar-argentina-regions","open source"]
description: "Tal como definiéramos en el hackatón de junio, y a pesar de haber ido más lento de lo deseado, podemos decir que tenemos un primer módulo oficial."
image: images/posts/2018/12/2018-12-27-01.png
---

Tal como definiéramos en el [hackatón de junio](/posts/recap-del-meetup-3-en-buenos-aires/), y a pesar de haber ido más lento de lo deseado, podemos decir que tenemos un primer módulo oficial.

El módulo se forkeó de [Barbanet_ArgentinaRegions 1.0.0](https://www.damianculotta.com.ar/magento/barbanet_argentinaregions-1-0-0/), el cual será deprecado.

El código está [disponible en Github](https://github.com/holamugar/module-argentinaregions) y se puede [instalar por Composer desde Packagist](https://packagist.org/packages/mugar/module-argentinaregions).

Para instalarlo, usaremos composer:

```shell
composer require mugar/module-argentina-regions
```

Una vez que se haya instalado, deberemos activarlo.

```shell
bin/magento module:enable Mugar_ArgentinaRegions
```

Y ahora si, actualizar.

```shell
bin/magento setup:upgrade
```

No olvidarse de limpiar cache ya que estos datos se cachean siempre.

```shell
bin/magento cache:clean
```

Ahora si, al intentar, por ejemplo, cotizar un envío, tendríamos que tener las provincias cargadas.

![Módulo](/images/posts/2018/12/2018-12-27-02.png#center)

Además de proveer de la lista de provincias argentinas para Magento 2, con este módulo estamos buscando comenzar a contribuir más allá de los encuentros mensuales.

Es por eso que si miran en [https://github.com/holamugar/module-argentinaregions/issues](https://github.com/holamugar/module-argentinaregions/issues) van a ver que hay dos issues creados. Intentaremos marcar aquellos issues que consideremos pueden ayudar a quien se está iniciando o duda en cómo colaborar, pueda hacerlo.

Actualmente, para este módulo, tenemos dos issues que se pueden revisar:

* [Definir el código a usar para cada Provincia](https://github.com/holamugar/module-argentinaregions/issues/1)
* [reparar readme.md y dejarlo como modelo para otros módulos MugAr](https://github.com/holamugar/module-argentinaregions/issues/2)

Si hubieran dudas, siempre podemos llevar la discusión en los issues específicos o en [Slack](https://mugar.slack.com/).
