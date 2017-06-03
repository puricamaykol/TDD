Pruebas Unitarias
-----------------

Son un tipo de prueba automatizada en las que se testea la mínima unidad posible de código, siendo este un método o función. 

Características de las pruebas unitarias bien hechas:

 - Corren rápido.
 - Tienen poca configuración.
 - Corren de forma aislada: Una prueba no depende de las otras. Se debería poder cambiar el orden en que corren.
 - Son entendibles: Deben tener nombres/descripciones consistentes e
   informativas y usar data que las haga fácil de leer y entender.
 - Utilizan data real: Aunque la data en las pruebas unitarias se guarde en objetos ficticios, esta data debe tener los mismos formatos y tipos que la data que se usaría en producción.
 - Debe representar un pequeño avance para corroborar el funcionamiento de un sistema. Debería apuntar a un único asunto.

TDD
---

TDD (Test driven development o Desarrollo conducido por pruebas) es un enfoque para la realización de pruebas unitarias en el que de forma iterativa se escribe primero una prueba, la cual debe fallar (de lo contrario, no aporta ningún valor o está mal escrita), para posteriormente desarrollar el código que hace que esta prueba pase y finalmente refactorizar de ser necesario, repitiendo este ciclo hasta que se complete el requerimiento. 
En la imagen se aprecia el algoritmo TDD:

 1. Red: Se escribe una prueba que falla.
 2. Green: Se escribe el código que hace que la prueba pase.
 3. Refactor: Se aplican buenas prácticas, se elimina código repetido,
    etc.

![enter image description here](https://lh6.googleusercontent.com/fb7DDzFsPzOh3lU5qH0WCYdqxiO_RK1Ijt5mTShxgoDqQZ1QAVVAFTY6j0fiDGDTI8GmoI0eT8yuC_Y=w1280-h858)


ATDD
----

ATDD (Acceptance Test Driven Development o Desarrollo conducido por pruebas de aceptación) es un enfoque para realizar pruebas automatizadas de software en el que partiendo del requerimiento se definen una serie de ejemplos reales que ayudan a definir los criterios de aceptación que el sistema debe cumplir para que pueda ser considerado aceptable. Se tratan de pruebas de caja negra, en las que se validan las salidas deseadas para determinadas entradas.
![enter image description here](https://lh3.googleusercontent.com/0lipOCZPgFYliba3CR1SPIhTBv32IP_QVb3ml39uspULxbq4fKSnghwhjCnmZF380cm8LlZO=s0 "ciclo atdd tdd.jpg")
A grandes rasgos el proceso sería el siguiente:

 - Se parte de una historia de usuario.
 - Esa historia de usuario va a tener N pruebas de aceptación
   representadas como ejemplos puntuales.
 - Se automatiza la prueba de aceptación/ejemplo.
 - Ese ejemplo se comienza a implementar siguiendo un enfoque TDD, es decir, de forma cíclica hasta que se cumpla la funcionalidad  (que pasen todas las pruebas unitarias y la prueba de aceptación).
 - Se inicia de nuevo el ciclo.

> Las historias de usuario y los ejemplos deben ser puntuales y
> centrarse en el qué y no en el cómo. No deberían especificar nada
> relacionado a la interfaz gráfica de usuario, porque la interacción
> entre el usuario y la UI no le aporta valor al desarrollador al
> momento de entender el requerimiento.

¿Por qué aplicar TDD y ATDD?
----------------------------

Ambos atacan aspectos diferentes:

| ATDD | TDD |
| --- | --- |
| Tiene un enfoque macro, haciendo pruebas de caja negra, en las que se valida el comportamiento deseado por el cliente en función de entradas y salidas. Por ejemplo, si se ingresa un usuario con nombre, apellido y cédula, el criterio de aceptación podría ser que se retorne un mensaje que diga que se creó un usuario con tales atributos, y que en la BD efectivamente se haya registrado dicho usuario.| Se enfoca en lo micro, haciendo énfasis en cómo está arquitectado el software (sería poder ver dentro de la caja negra). Se valida que cada método de forma aislada haga lo que debe hacer. |
| Apunta a validar que el requerimiento del cliente se esté cumpliendo. | Apunta a mantener el código en el mínimo necesario (evitando la sobreingeniería), a diseñar la arquitectura del software de modo tal que este sea entendible, testeable y escalable, es decir, que esté preparado para los cambios. |
