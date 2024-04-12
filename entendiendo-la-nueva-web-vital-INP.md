# Entendiendo la nueva web vital INP

Interaction to Next Paint (INP)
Es una métrica que evalúa la capacidad de respuesta de una web usando la Event Timing Api, que es una herramienta que proporciona datos de interacción del usuario.

El INP observa la latencia de todas las interacciones de click, tap y keyboard con una página a lo largo de su vida útil e informa la duración mas larga, sin tener en cuenta los valores atípicos.

El objetivo de INP es minimizar el tiempo que transcurre desde que un usuario inicia una interacción hasta que se renderiza el siguiente fotograma, para todas o la mayoría de las interacciones que inicia el usuario.



https://github.com/cbasdev/blog-post-md/assets/33915497/20fe5893-fc6b-4544-a421-85f04ba8c49c


Cómo se calcula el INP

El INP se calcula observando todas las interacciones que se realizan en una página y tomando la interacción con peor latencia.


> 🗒️ Una *interacción* es un grupo de controladores de eventos que se activan durante el mismo gesto lógico del usuario. Por ejemplo, las interacciones "presionar" en un dispositivo con pantalla táctil incluyen varios eventos, como `pointerup`, `pointerdown` y `click`. Una interacción se puede generar con JavaScript, CSS, controles integrados del navegador, como elementos de formulario, o una combinación de todos estos elementos.

</aside>

<img width="760" alt="image" src="https://github.com/cbasdev/blog-post-md/assets/33915497/4fed60f1-41b8-48d1-b18e-1eb9fbc2f8d6">


**¿Qué contiene una interacción?**

<img width="795" alt="image" src="https://github.com/cbasdev/blog-post-md/assets/33915497/d4eb1788-976b-4714-82c3-3f44cf5fca95">


**¿Cuál es la diferencia entre INP y First Input Delay (FID)?**

Si bien ambas son métricas de respuesta, FID solo midió el retraso de entrada de la *primera* interacción en una página. INP mejora el FID teniendo en cuenta *todas* las interacciones de la página, desde la demora de entrada hasta el tiempo que lleva ejecutar los controladores de eventos y, por último, hasta que el navegador pinta el siguiente fotograma. INP es un indicador más confiable de la capacidad de respuesta general, independientemente del momento en que se producen las interacciones de la página.
