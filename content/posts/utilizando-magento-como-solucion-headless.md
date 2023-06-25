---
title: "Utilizando Magento como solución headless"
date: 2023-06-26
categorias: ["Plataformas"]
autores: ["Nicolás de Mayo"]
tags: ["headless","magento"]
description: "Experiencias utilizando Magento (Adobe Commerce) en un modelo headless desacoplando el frotend del backend. Ventajas y desventajas."
image: images/posts/2023/06/2023-06-26-01.jpg
---

En la actualidad no sólo han crecido los negocios de comercio electrónico como tal, sino que todo el ecosistema relacionado al desarrollo de ecommerce ha visto una franca expansión. Dia a dia aparecen nuevos jugadores, desde plataformas de ecommerce, herramientas de marketing, proveedores logísticos, OMS, WMS, ERP; todo el ecosistema aceleró su proceso de desarrollo. Es por eso que muchas de las preguntas que nos hacen hoy en dia, es "con cuál me caso" para que me ofrezca soluciones a las necesidades de mi negocio y me permita crecer a lo largo del tiempo.

¿Cuál es el stack tecnológico ideal para mi ecommerce? Lamentablemente no tengo esa respuesta (que hermosa frase), pero después de haber trabajado con tantas soluciones y distintos stacks, hoy me gustaría comentarles mi experiencia trabajando con Magento de manera Headless.

&nbsp;

## Primero, ¿a qué nos referimos con stack tecnológico? (si sos dev podés avanzar a la siguiente sección)

En el competitivo mundo del comercio electrónico, contar con un stack tecnológico sólido es fundamental para impulsar el crecimiento y el éxito de las unidades de negocio. El stack tecnológico se refiere a la combinación de tecnologías, frameworks y herramientas utilizadas en el desarrollo y funcionamiento de un ecommerce. Desempeña un papel clave en la capacidad de **adaptación, escalabilidad y eficiencia** de una tienda en línea. La elección de un buen stack te permitira:

**1. Adaptación ágil a las demandas del mercado**

El mercado del ecommerce es dinámico y está en constante evolución. Los comportamientos y preferencias de los usuarios cambian rápidamente y es crucial que un ecommerce se adapte en el menor tiempo posible. Un stack tecnológico bien diseñado y flexible te permite implementar rápidamente nuevas características, integrar herramientas de marketing y mejorar la experiencia del usuario.

**2. Escalabilidad para un crecimiento sostenible**

El crecimiento exitoso de un ecommerce implica aumentar el tráfico, el volumen de ventas y la base de clientes. Para lograrlo, es esencial contar con un stack tecnológico que pueda escalar de manera eficiente. Esto implica tener una infraestructura robusta y una arquitectura flexible que puedan soportar un aumento significativo en el tráfico sin sacrificar el rendimiento y la velocidad de carga.

**3. Eficiencia operativa y reducción de costos**

Un stack tecnológico optimizado no sólo mejora la experiencia del usuario y facilita la gestión de la tienda, sino que también puede conducir a una mayor eficiencia operativa y ahorro de costos (a quien no le gusta ahorrar costos). Al utilizar herramientas y plataformas integradas, automatizar procesos y optimizar la gestión de inventario, pedidos y pagos, podés reducir los tiempos de trabajo manual, minimizar errores y agilizar las operaciones diarias. Esto no solo mejora la productividad interna, sino que también reduce los costos operativos y permite invertir esos recursos en otras áreas clave del negocio.

**4. Experiencia del usuario**

La experiencia del usuario es un factor determinante en el éxito de cualquier ecommerce. Un stack tecnológico adecuado te brinda las herramientas necesarias para ofrecer una experiencia de usuario de alta calidad. Esto implica contar con un frontend atractivo y fácil de usar, una navegación intuitiva, tiempos de carga rápidos, opciones de pago seguras y una experiencia de compra fluida en todos los dispositivos.

&nbsp;

## Utilizando Magento (Adobe Commerce) como headless commerce.

Antes que nada, para quienes no hayan oído de este concepto, cuando hablamos de headless, nos referimos a una arquitectura de software en la que se separa la capa de **frontend**, de la capa de datos, lógica de negocios y administración del sitio (**backend**). En el contexto de una plataforma de comercio electrónico, esto significa que la interfaz de usuario (UI) y la experiencia de usuario (UX) se separan de la lógica de la plataforma.

La **comunicación entre el front y el back** estará a cargo de la **API de Magento,** y siendo más específicos, la **API GraphQL**. El lenguaje de consulta GraphQL se presenta como una alternativa mas flexible y eficiente a las API REST tradicionales, al permitir a los clientes solicitar y recibir solo los datos que necesitan en una sola llamada de API. En resumen, GraphQL pide solo lo que necesita, volviendo más eficaz las peticiones y respuestas (entre otras ventajas).

Si bien en la última versión de Magento (2.4.6 cuando se escribió este artículo), la API GraphQL ha crecido considerablemente, tanto en cantidad de queries como también tiempos de respuesta, pueden existir algunas queries faltantes (no olvidemos que tiene un número considerable de funcionalidades, aunque terminemos utilizando solo algunas). De todas maneras, todas las necesarias para la creación de un frontend y flujo de compras regular están cubiertas y son más que suficientes.

La estrategia de desacoplar el frontend del backend nos ofrece ventajas y desafíos importantes a ser tenidos en cuenta para cualquier negocio.

### Ventajas:

1. **Flexibilidad en la experiencia de usuario**: Utilizar lenguajes modernos en el front (React, Vue.js o Angular etc), permite mejorar la UI de un ecommerce, sin los desafíos que nos solemos encontrar al optimizar un frontend de Magento (aunque seas un experto frontend en algún momento odiaste Knockout JS). También modificando el stack del front los cambios se vuelven más controlados.

2. **Mayor rendimiento**: Al separar el frontend y backend, se puede optimizar el rendimiento de ambas partes de la aplicación. Podes implementar estrategias de caché y optimización en el frontend pre renderizando recursos estáticos, lo que resulta en tiempos de carga más rápidos y una experiencia de usuario mejorada. Además, al eliminar la carga del frontend del servidor de Magento, se puede mejorar la capacidad de respuesta del backend y manejar mejor el tráfico y la escalabilidad.

3. **Facilidad de integración**: Con una arquitectura headless, es más fácil integrar Magento con otros sistemas y servicios. Para quienes busquen **experiencias omnicanal**, pueden desarrollar aplicaciones o POS físicos digitalizados (totems utilizados en locales físicos) conectados al mismo backend.

4. **Mayor escalabilidad**: Al separar el frontend y backend, posibilidad de escalar y gestionar cada parte por separado según las necesidades. Podes escalar el frontend independientemente del backend, lo que te brinda una mayor capacidad para manejar aumentos en el tráfico y el volúmen de usuarios sin afectar el rendimiento general de la aplicación. El equipo de administración de la tienda puede trabajar sin problemas desde el backend, sin importar la concurrencia en el front, manteniendo el stack operativo en todo momento.

5. **Universalización de tecnología:** Ya no es necesario lidiar con los desafíos del frontend de Magento o salir a buscar profesionales particularmente especializados en Magento (sabemos que muchas veces escasean), lo que universaliza las oportunidades de crecimiento del equipo en tecnologías frontend en auge.

6. **Módulos de terceros:** Algunos vendors ya están comenzando a lanzar sus extensiones con compatibilidad PWA, ya sea con los servicios necesarios del módulo en GraphQL o con los archivos necesarios para implementar la funcionalidad en el frontend de PWA Studio.

7. **Debugging:** La capa GraphQL devuelve siempre la informacion que se utiliza en el storefront de la tienda, por lo tanto se vuelve una ventaja técnica a la hora de debuggear. Existen en el mercado vastas interfaces GraphQL (entre ellas el mismisimo Postman) que permiten realizar las mismas queries que realiza el front PWA identificando posibles errores de informacion o respuestas no esperadas.

### Desventajas:

1. **Funcionalidades nativas**: Muchas funcionalidades nativas que naturalizamos en el frontend de Magento, deben ser desarrolladas adicionalmente en el nuevo frontend. Para dar un ejemplo, en este apartado se pueden considerar widgets y opciones de personalización de layout incluidos en Magento.

2. **Costos de infraestructura**: Si bien nos brinda mayor escalabilidad, los costos de infraestructura también aumentan dado que se incorporan nuevas instancias en el stack.

3. **Customizaciones frontend**: Todas aquellas customizaciones frontend o provenientes de alguna extensión, deben ser consideradas para homologar su desarrollo en el frontend. Esto se convierte en un esfuerzo indirecto a ser considerado.

4. **Mayor costo y time to market**: La implementación de una solución headless con Magento puede requerir más tiempo y recursos en comparación con un enfoque tradicional. El desarrollo y la integración de un frontend personalizado, así como el mantenimiento continuo de las partes frontend y backend, pueden generar costos adicionales.

&nbsp;

Considerando que los costos y el time to market en el desarrollo de un nuevo frontend afectan a este modelo, se vuelve necesario considerar alternativas existentes que brinden un punto de partida aceptable para evitar partir desde cero (no reinventar la rueda):

* PWA Studio: Esta es la solución PWA oficial de Magento, desarrollada por el equipo de Adobe. PWA Studio proporciona un conjunto de herramientas para crear web app progresivas, incluyendo un kit de desarrollo de software (SDK) y una biblioteca de componentes reutilizables. Venia es el Luma de PWA: https://venia.magento.com/

* Vue Storefront: Esta es una PWA de código abierto que se integra con Magento 2 y otras plataformas de comercio electrónico populares, como WooCommerce y Shopify. Vue Storefront utiliza Vue.js como su marco principal y proporciona una arquitectura modular y extensible.

* ScandiPWA: Esta es una solución PWA de código abierto desarrollada por Scandiweb, una agencia de desarrollo de comercio electrónico. ScandiPWA utiliza React.js y Redux como sus principales tecnologías de frontend y proporciona una arquitectura modular y extensible.

&nbsp;

En conclusión, adoptar una arquitectura headless con Magento tiene ventajas significativas en términos de flexibilidad, rendimiento, integración y escalabilidad. Sin embargo, también puede implicar una mayor complejidad de desarrollo, mayores costos y dependencia de habilidades técnicas especializadas. Es importante evaluar cuidadosamente tus necesidades comerciales y capacidades técnicas antes de tomar la decisión de utilizar Magento como solución headless.