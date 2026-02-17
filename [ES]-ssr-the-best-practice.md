# 99% de las apps deberían ser SSR (Update: La Era de las Islas)

Hola, quiero actualizar una de las reflexiones que más ha resonado en mi camino como desarrollador: por qué el renderizado en el servidor no es solo una opción, sino una necesidad para la web moderna.

Si en 2021 decíamos que el SSR era el futuro, hoy en 2024 el juego ha evolucionado. Ya no solo nos importa *dónde* se renderiza, sino **cuánto JavaScript (JS)** le obligamos a cargar al cliente.

---

## El Panorama Actual: SSR vs. CSR

Para refrescar, definamos las estrategias base:

### Server Side Rendering (SSR)
* **Ventajas:** El mejor *First Contentful Paint* (FCP), SEO impecable y el navegador del usuario descansa (menos consumo de RAM).
* **Evolución:** Gracias a los **React Server Components (RSC)**, ahora podemos decidir qué componentes se quedan 100% en el servidor sin enviar ni un solo byte de JS al navegador.

### Client Side Rendering (CSR)
* **Ventajas:** Menos carga inicial para el servidor y transiciones fluidas tras la carga inicial.
* **Desventajas:** El "bundle" de JS ha crecido tanto que los dispositivos móviles sufren para procesar sitios web pesados.

---

## La Nueva Frontera: Islands Architecture (Arquitectura de Islas) 🏝️

Aquí es donde mi perspectiva cambió. Si antes el SSR enviaba todo el HTML y luego "hidrataba" toda la página (activando el JS), las **Islas** proponen algo más inteligente.

Imagina un océano de **HTML estático** (rápido, ligero, sin JS) donde flotan pequeñas **islas de interactividad**.

* **¿Cómo funciona?** El 90% de tu página (textos, imágenes, pies de página) se sirve como HTML puro. Solo los componentes que realmente necesitan interacción (un carrito, un buscador dinámico) cargan su propio JavaScript de forma aislada.
* **Frameworks líderes:** Astro, Fresh y Qwik (con su concepto de *Resumibilidad*).

### ¿Por qué esto es mejor que el SSR tradicional?
1.  **Zero JS por defecto:** Si una página no tiene islas, el usuario descarga 0KB de JavaScript.
2.  **Carga bajo demanda:** Las islas pueden cargarse solo cuando entran en el *viewport* del usuario, ahorrando datos y batería.
3.  **Adiós al bloqueo del hilo principal:** Al no tener que "hidratar" toda la página de golpe, el sitio es interactivo instantáneamente.

---

## Comparativa de Rendimiento

| Estrategia | Interactividad | Carga de JS en Cliente | Ideal para... |
| :--- | :--- | :--- | :--- |
| **CSR** | Lenta al inicio | Muy Alta | Dashboards privados complejos. |
| **SSR (Tradicional)** | Media (Hidratación) | Alta | E-commerce y Blogs grandes. |
| **Islands / RSC** | **Instantánea** | **Mínima / Selectiva** | El 99% de la web pública. |

---

## Conclusión: El rendimiento es el mensaje

Sigo sosteniendo que el **99% de las apps deben ser SSR**, pero con el matiz moderno: **SSR con Arquitectura de Islas o Server Components**. 

Empresas como Instagram, TikTok y los e-commerce más grandes del mundo ya no envían aplicaciones gigantescas al cliente; envían HTML optimizado y solo el JS necesario para que la experiencia se sienta viva. Hablar de performance hoy no es solo hablar de servidores, es hablar de **enviar menos código**.