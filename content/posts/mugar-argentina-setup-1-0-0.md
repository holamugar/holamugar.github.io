---
title: "Mugar Argentina Setup 1.0.0"
date: 2020-06-18
categories: ["Extensiones"]
tags: ["extensiones","mugar-argentina-regions","mugar-argentina-setup","mugar-language-es_ar","open source"]
description: "En la semana se estuvo trabajando en adecuar el metapaquete que intenta ser una ayuda inicial al momento de adaptar Magento a nuestro país."
image: images/posts/2020/06/2020-06-18-01.png
---

En la semana se estuvo trabajando en adecuar el metapaquete que intenta ser una ayuda inicial al momento de adaptar Magento a nuestro país.

A diferencia de la versión anterior, hemos añadido el módulo de [traducción a español es_AR](https://github.com/holamugar/language-es_ar). Además, con nueva versión de [Mugar_ArgentinaRegions](https://github.com/holamugar/module-argentina-regions).

La lista total de cambios sería:

* Se arregló y creó el paquete Mugar_Language-es_AR 1.0.0.
* Se normalizó estructura de Mugar_Language-es_AR y se llegó a versión 2.0.1.
* Se dio compatibilidad con PHP 7.1, 7.2, 7.3 y 7.4 únicamente a Mugar_Language-es_AR.
* Se cambió el instalador de Mugar_ArgentinaRegions a data patch.
* Se dio compatibilidad con PHP 7.2, 7.3 y 7.4 únicamente a Mugar_ArgentinaRegions y a Mugar_ArgentinaSetup.
* Se incluyó en el metapaquete el módulo de idioma.
* Se agregaron instrucciones de instalación (aunque quedó un error que agregamos como issue para quien quiera participar con correcciones sencillas)

Los pasos para instalar son:

```shell
composer require mugar/argentina-setup
```

Una vez descargado nos tocará habilitar el módulo de provincias primero.

```shell
bin/magento module:enable Mugar_ArgentinaRegions
```

Luego actualizamos la base de datos para instalar.

```shell
bin/magento setup:upgrade
```

Lo siguiente será aplicar las traducciones.

```shell
bin/magento i18n:pack --mode=replace -d vendor/mugar/language-es_ar/es_AR.csv es_AR
```

Esto agregará para cada módulo el archivo de traducción en nuestro locale.

Finalmente hacemos el deploy.

```shell
bin/magento setup:static-content:deploy es_AR
```

Antes de terminar, por el terma de las provincias, limpiamos cache.

```shell
bin/magento cache:clean
```

Y ahora si, ya deberías tener las traducciones y las provincias de Argentina funcionando.

Ambos paquetes pueden también ser instalados de forma independiente.

Si te interesa participar para mejorar o corregir (o incluso proponer) módulos que simplifiquen el proceso de regionalización de la tienda, podés participar en el canal #github que tenemos en [Slack](https://join.slack.com/t/mugar/shared_invite/enQtNjUwNzExMzgyMjQ1LWM2Zjk3NThiYWVlYjMzNDcwOWRhZDliMmIxNGY5MDBkMDU1ZWJkNjEyM2U1NTU3NTE1ZDdlNTZmOWJlNGFhYzg).