---
title: "Backlog 2020.03"
date: 2020-03-08
categories: ["Backlog"]
tags: ["backlog","extensiones","magento"]
description: "En vista de las recomendaciones del Ministerio de Salud de la Nación hemos decidido suspender todas nuestras meetups presenciales hasta nuevo aviso."
image: images/posts/2020/03/2020-03-08-01.png
---

El viernes pasado, como cada primer viernes de mes, se llevo a cabo la grooming session en la que intentamos repasar qué hicimos, qué queremos hacer y qué podemos hacer mejor.

La reunión se dividió en dos temas:

* ¿Cómo lograr mejor tracción y participación?
* ¿Cómo avanzar con los módulos que siempre decimos que queremos desarrollar?

Con respecto a lo primero, se siguen pensando acciones o formas que ayuden a reducir cualquier fricción que pudiera presentarse para aquellos que aún no han participado, pero tienen ganas (y no se animaron todavía).

Sobre el mismo tema, tenemos luego dos posturas sobre las cuales estamos trabajando: por un lado, seguir buscando formas de comunicar qué queremos hacer y cómo pueden ayudar. Por ejemplo, se han creado issues en el repositorio del módulo [Mugar_CustomerIdentificationDocument](https://github.com/holamugar/module-customer-identification-document/issues) y se ha notificado públicamente de ello (no sólo porque los repositorios son públicos sino por las notificaciones en Slack).

Hemos visto que en esos issues, a pesar de estar marcados como una primera contribución posible, no ha habido movimiento alguno.

Esto ha llevado a pensar que en cuanto a las acciones posibles, si bien pueden haber mejoras a implementar, se ha hecho bastante para permitir participar a quien tenga deseo de hacerlo; y es por eso que una postura es no destinar más energía a buscar nuevas formas de lograr tracción, sino, simplemente hacer. Parte de la estrategia original fue que los miembros más activos se retiraran un poco para permitir a otros miembros desarrollar un issue o tomar la posta sobre algún módulo, etc, etc. Esto no ha dado grandes resultados.

Se discutió una segunda mirada sobre esto mismo, que plantea el conversar con todas las (o las gran mayoría que se pueda) agencias que trabajan con Magento (y quizás con Merchants que podamos contactar) para relevar qué módulos se usan más o necesitan o generan un trabajo extra para regionalizar Magento para nuestro país. De esta manera se desarrollaría siguiendo un hilo confirmado por las agencias en lugar de lo surgido principalmente aquí.

En esta postura hubo puntos de vista disímiles, aunque no se impedirá que se haga el experimento de recolectar la información y ver cómo se puede avanzar, no es una postura adoptada por el momento.

Con respecto a los módulos, se tomaron algunas decisiones de cara al meta paquete Mugar_ArgentinaSetup.

* Vamos a preparar el locale para poder exponer la traducción en un CSV único (para evitar problema con traducciones diferentes para una misma clave en Crowdin).
* Hay que definir cada módulo que será incluído y crear los issues a su debido momento.
* Tenemos que buscar un formato más prolijo para el Roadmap y ajustar el cronograma.
* Vamos a continuar trabajando con el módulo [CustomerIdentificationDocument](https://github.com/holamugar/module-customer-identification-document). Por eso este lunes a las 17 hs. habrá una llamada vía Hangout para conversar sobre los issues creados y cómo definirlos.

Un cambio que se hizo fue con el calendario público. Se ha creado uno nuevo, con los mismos eventos. El viejo calendario fue eliminado y el link al nuevo fue reemplazado en la página Calendario. Además, si te conectás a nuestro Slack, vas a recibir las notificaciones en el canal #general.

Para participar de estas definiciones y proyectos sólo hay que sumarse al canal #github en [Slack](https://join.slack.com/t/mugar/shared_invite/enQtNjUwNzExMzgyMjQ1LWM2Zjk3NThiYWVlYjMzNDcwOWRhZDliMmIxNGY5MDBkMDU1ZWJkNjEyM2U1NTU3NTE1ZDdlNTZmOWJlNGFhYzg) o participar de las grooming sessions (que por ahora son 1 vez al mes).