---
title: "Backlog 2019.12"
date: 2019-12-09
categories: ["Backlog"]
tags: ["backlog","buenos aires","extensiones","magento","meetup","rosario"]
description: "Retomamos esto que mal llamamos Backlog (si alguien tiene una sugerencia superadora, bienvenida sea)."
image: images/posts/2019/12/2019-12-09-01.png
---

Retomamos esto que mal llamamos Backlog (si alguien tiene una sugerencia superadora, bienvenida sea).

El viernes pasado tuvimos nuestra grooming mensual y se acordaron varias acciones.

El eje central estuvo en [Github](https://github.com/holamugar) y en los módulos que siempre decimos que quisiéramos escribir para simplificar la configuración y uso de Magento en Argentina.

Finalmente, luego de tener publicados [Mugar_ArgentinaRegions](https://github.com/holamugar/module-argentina-regions) y el meta-paquete [Mugar_ArgentinaSetup](https://github.com/holamugar/argentina-setup), retomamos un plan a corto plazo.

Se repasó la discusión sobre por qué es necesario un tipo y número de documento tanto para el Billing como para el Shipping. Una vez aclarado el motivo (es necesario para las facturas y puede ser necesario para algunas empresas de logística) Oliverio nos mostró una demo funcional de su [PoC](https://es.wikipedia.org/wiki/Prueba_de_concepto).

Este módulo guarda estrecha relación con otro que está en el roadmap, [Mugar_Afip](https://github.com/holamugar/module-afip). Este módulo debería permitir generar facturas electrónicas y así ayudar a las tiendas con esa tarea también.

Cuando llegamos hasta aquí, estuvimos de acuerdo en que vamos a crear el módulo Mugar_Taxes y que servirá para cargar/instalar impuestos (inicialmente IVA) para las tiendas.

Ese módulo, dado que es sencillo en términos de programación, sería usado para volver a insistir con la participación en Github, más allá del nivel de conocimiento técnico de quien quiera participar.

De esta manera, el roadmap actual se definió así:

1) Oliverio hará un PR a [Mugar_CustomerIdentificationDocument](https://github.com/holamugar/module-customer-identification-document) con su PoC. Sobre eso, [Federico](https://ar.linkedin.com/in/federicorivollier) ayudará con la creación de tickets e issues para avanzar con el desarrollo.
2) Se creará el módulo Mugar_Taxes para que se trabaje en un módulo con reglas de impuestos, que se necesitará en un futuro para el módulo de creación de facturas electrónicas.
3) Una vez que esos módulos estén listos y funcionando, se comenzará con la creación de la factura electrónica, no antes. Para eso [Matías](https://ar.linkedin.com/in/matiasanoniz) comenzará a organizar y recolectar la información que se necesite para poder crear la integración.

También participaron de la grooming [Arturo](https://ar.linkedin.com/in/arturoiglesias/es) y [Damián](https://ar.linkedin.com/in/damianculotta).

Para enterarse más o participar de estos proyectos basta con participar de las charlas que se den en el canal #github en [Slack](https://join.slack.com/t/mugar/shared_invite/enQtNjUwNzExMzgyMjQ1LWM2Zjk3NThiYWVlYjMzNDcwOWRhZDliMmIxNGY5MDBkMDU1ZWJkNjEyM2U1NTU3NTE1ZDdlNTZmOWJlNGFhYzg) o participar de las grooming sessions (que por ahora son 1 vez al mes).










* Vamos a preparar el locale para poder exponer la traducción en un CSV único (para evitar problema con traducciones diferentes para una misma clave en Crowdin).
* Hay que definir cada módulo que será incluído y crear los issues a su debido momento.
* Tenemos que buscar un formato más prolijo para el Roadmap y ajustar el cronograma.
* Vamos a continuar trabajando con el módulo [CustomerIdentificationDocument](https://github.com/holamugar/module-customer-identification-document). Por eso este lunes a las 17 hs. habrá una llamada vía Hangout para conversar sobre los issues creados y cómo definirlos.

Un cambio que se hizo fue con el calendario público. Se ha creado uno nuevo, con los mismos eventos. El viejo calendario fue eliminado y el link al nuevo fue reemplazado en la página Calendario. Además, si te conectás a nuestro Slack, vas a recibir las notificaciones en el canal #general.

Para participar de estas definiciones y proyectos sólo hay que sumarse al canal #github en [Slack](https://join.slack.com/t/mugar/shared_invite/enQtNjUwNzExMzgyMjQ1LWM2Zjk3NThiYWVlYjMzNDcwOWRhZDliMmIxNGY5MDBkMDU1ZWJkNjEyM2U1NTU3NTE1ZDdlNTZmOWJlNGFhYzg) o participar de las grooming sessions (que por ahora son 1 vez al mes).