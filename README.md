# More Cambio — Tasas

Libro de compra y venta de divisas para cambistas en Cuba, con aplicación de
escritorio (macOS) y móvil. Este repositorio describe cómo la aplicación
consume la **Tasa Representativa del Mercado Informal (TRMI)** de elTOQUE.

## Qué hace la aplicación

More Cambio es un libro de operaciones: se anota cada compra y cada venta de
divisas, y la aplicación calcula el inventario, el costo de lo comprado y la
ganancia. Funciona sin conexión, que es lo normal aquí; los datos viven en el
aparato y se sincronizan cuando hay internet.

La TRMI se usa como **referencia** junto al precio propio del usuario: la
aplicación enseña las dos a la vez, porque el precio al que uno opera y el que
marca el mercado no son lo mismo.

## Cómo se consume la API

- **Un solo servidor.** Las aplicaciones no llaman nunca a la API de elTOQUE.
  Un proceso programado en el servidor consulta el endpoint `/v1/trmi` y guarda
  el resultado; las aplicaciones leen de ahí.
- **Una consulta por hora**, como mucho. Con un único origen, el número de
  peticiones no crece con el número de usuarios: son las mismas para uno que
  para diez mil.
- **Divisas:** USD, EUR, MLC y USDT.
- **Atribución.** Toda pantalla que enseña un valor derivado de la TRMI cita a
  elTOQUE como fuente, tal como piden sus condiciones de uso.
- **No se redistribuyen los datos** ni se publica una tasa alternativa.

## Estado

En desarrollo, de uso propio y de un grupo pequeño de cambistas.

## Fuente

Tasas de referencia del mercado informal por [elTOQUE](https://eltoque.com).
Los valores son referenciales.
