---
title: "Buenas prácitas - Branching Model"
date: 2023-05-04
categorias: ["Plataformas"]
autores: ["Facundo Capua"]
tags: ["buenas practicas"]
description: "Una recopilación de buenas prácticas para el uso de ramas en un proyecto Magento."
image: images/posts/2023/05/2023-05-04-01.png
---

Hoy en día en todos los proyectos de desarrollo de software utilizamos [git](https://git-scm.com/) como herramienta principal para el control de versiones. Además de utilizar git, precisamos de una buena [estrategia para nuestras ramas (branches)](https://www.damianculotta.com.ar/control-de-versiones/trunk-based-development-y-otras-estrategias-de-branching/) de forma tal que podamos trabajar de forma ordenada y eficiente.

La idea de este post no es explicar como funciona git ni explicar branching strategies, sino más bien dar una serie de buenas prácticas para el uso de ramas en un proyecto Magento.

## Ramas principales y entornos

La idea es tener dos ramas principales, una para desarrollo y otra para producción. En el caso de Magento, la rama de desarrollo sería `develop` y la rama de producción sería `master`.

La rama `develop` es la rama donde se desarrolla el proyecto. En esta rama se van a ir agregando los features que se vayan desarrollando. La rama `master` es la rama que se va a utilizar para generar los releases. En esta rama se van a ir agregando los releases que se vayan generando.

El objetivo es que cada rama principal esté mapeada a un entorno. Asumiendo que contamos con 3 entornos (desarrollo, staging y producción), la rama `develop` estaría mapeada al entorno de desarrollo y la rama `master` estaría mapeada al entorno de staging.

## Ramas de features

El objetivo de las ramas de features es poder aislar el desarrollo de un feature en particular. Por ejemplo, si tenemos que desarrollar un feature que consiste en agregar un nuevo bloque en el home, lo ideal sería crear una rama de feature para ese desarrollo. De esta forma, el resto del equipo puede seguir trabajando en otros features sin tener que esperar a que se termine el desarrollo del feature en cuestión.

El objetivo es que estas ramas es que sean de corta duración y rápidamente mergear en la rama `develop`.

Si bien se puede dar el escenario de que se tengan que desarrollar varios features en paralelo, lo ideal es que cada desarrollador trabaje en un feature a la vez. De esta forma, se evitan conflictos y se puede mantener un orden en el desarrollo. Inclusive si un desarrollador tiene que trabajar en varios features en paralelo, puede pausar el desarrollo de un feature y continuar con otro.

## Tags para producción

Siempre que pasemos cambios a producción tenemos que crear un tag. El tag es una referencia a un commit en particular. En este caso, el commit al que se hace referencia es el commit que se encuentra en la rama `master`.

El uso de tags tiene ciertos beneficios:

- Nos permite identificar de forma rápida los releases que se fueron generando.
- Nos permite hacer un rollback a un release anterior en caso de ser necesario (no siempre es posible ni recomendable).
- Nos permite identificar de forma rápida los cambios que se fueron pasando a producción (para hacer troubleshooting, por ejemplo).

## Respetar el flujo de trabajo

Uno de los puntos más importantes es respetar el flujo de trabajo. Esto significa que una rama de feature pasa a la rama `develop`, una rama de `develop` pasa a la rama `master` y una rama de `master` pasa a producción.

Aunque parezca obvio, muchas veces se dan casos en los que se pasa una rama de feature directamente a producción o se pasa una rama de `develop` a producción. Esto genera un desorden en el flujo de trabajo y puede generar problemas en el entorno productivo.

## Conclusiones

En este post vimos una serie de buenas prácticas para el uso de ramas en un proyecto Magento. Estas buenas prácticas están basadas en mi experiencia personal y en la experiencia de otros desarrolladores con los que he trabajado.

Adicionalmente, tenemos que trabajar en equipo y estar coordinados más allá de la estrategia de branching que se utilice. No podemos esperar que una serie de prácticas nos cubran todos los escenarios posibles. Siempre van a existir casos particulares que van a requerir de una solución particular. Lo importante es tener una serie de prácticas que nos permitan trabajar de forma un poco más ordenada y eficiente.

Estas prácticas no son las únicas ni son las mejores, pero son las que mejor me han funcionado hasta el momento.
