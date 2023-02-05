---
title: "Mugar Argentina Setup"
date: 2019-03-25
categorias: ["Extensiones"]
tags: ["extensiones","mugar-argentina-regions","mugar-argentina-setup","open source"]
description: "Siguiendo con la idea de armar un paquete de módulos que sirvan para configurar y adaptar la tienda a las necesidades y usos de Argentina, hemos creado la primera versión del metapaquete Mugar Argentina Setup."
image: images/posts/2019/03/2019-03-25-01.png
---

Siguiendo con la idea de armar un paquete de módulos que sirvan para configurar y adaptar la tienda a las necesidades y usos de Argentina, hemos creado la primera versión del metapaquete Mugar Argentina Setup.

A diferencia de los módulos, los metapaquetes se utilizan para poder instalar múltiples extensiones. Además, no son un módulo ni contienen código por si mismos.

Por el momento, el metapaquete contiene únicamente el módulo [Mugar_ArgentinaRegions](https://github.com/holamugar/module-argentina-regions) La idea es ir agregando los otros módulos definidos en el roadmap, a medida que vayan alcanzando estabilidad.

Para hacer uso del módulo, como (creemos) bien se indica en el readme, lo instalamos vía Composer.

```shell
composer require mugar/argentina-setup
```

Luego, necesitamos activar el módulo incluido (como dijimos antes, a medida que se agreguen más módulos, esta lista aumentará).

```shell
bin/magento module:enable Mugar_ArgentinaRegions
```

Una vez activado el módulo, necesitaremos actualizar base de datos.

```shell
bin/magento setup:upgrade
```

Y finalmente, limpiar cache.

```shell
bin/magento cache:clean
```

Como hemos instalado el módulo con Composer, podremos también desinstalarlo si lo necesitarámos.

Para esto, ejecutaremos primero:

```shell
bin/magento module:uninstall Mugar_ArgentinaRegions
```

De esta manera, el módulo se desactivará y borrará los datos en base de datos que insertó al instalarse.

Finalmente, ejecutamos:

```shell
composer remove mugar/argentina-setup
```

De esta forma el código descargado se eliminará.
