---
title: "Mugar_ArgentinaRegions 1.2.0"
date: 2019-02-04
categorias: ["Extensiones"]
tags: ["extensiones","mugar-argentina-regions","open source"]
description: "Durante el mes de enero se estuvo trabajando en algunos de los tickets que teníamos creados para el módulo, y el viernes, luego de nuestra primera grooming (de la cual tendremos post resúmen), se decidió hacer algunos ajustes para respetar cuestiones de forma."
image: images/posts/2019/02/2019-02-04-01.png
---

Durante el mes de enero se estuvo trabajando en algunos de los [tickets](https://github.com/holamugar/module-argentina-regions/issues) que teníamos creados para el módulo, y el viernes, luego de nuestra primera grooming (de la cual tendremos post resúmen), se decidió hacer algunos ajustes para respetar cuestiones de forma.

Los cambios hechos en el módulo fueron:

1. Se asignó el código ISO 3166-2 a cada provincia. ([Ver en GitHub](https://github.com/holamugar/module-argentina-regions/issues/1))
2. Se creó un readme.md base para usar como modelo en los otros módulos. ([Ver en GitHub](https://github.com/holamugar/module-argentina-regions/issues/2))
3. Se creó script de desinstalación. ([Ver en GitHub](https://github.com/holamugar/module-argentina-regions/issues/6))
4. Se cambió el nombre del repositorio y el nombre del paquete. ([Ver en GitHub](https://github.com/holamugar/module-argentina-regions/issues/8))

Sobre el último punto, hemos corregido el documento Cómo escribimos módulos, ya que el nombre del paquete debería ser como se ha definido ahora (separando con guión cada palabra).

Desde ahora, para instalar el módulo, usaremos:

```shell
composer require mugar/module-argentina-regions
```

Luego, lo activamos como ya se hacía.

```shell
bin/magento module:enable Mugar_ArgentinaRegions
```

Actualizamos la base de datos.

```shell
bin/magento setup:upgrade
```

Y finalmente limpiamos cache.

```shell
bin/magento cache:clean
```

Como se indica en el readme del módulo, si necesitáramos desinstalar el módulo, ejecutaremos:

```shell
bin/magento module:uninstall Mugar_ArgentinaRegions
```

Desde ahora, el módulo se encuentra en el repositorio:

[https://github.com/holamugar/module-argentina-regions](https://github.com/holamugar/module-argentina-regions)

Y en Packagist en:

[https://packagist.org/packages/mugar/module-argentina-regions](https://packagist.org/packages/mugar/module-argentina-regions)
