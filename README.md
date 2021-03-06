Pruebas Unitarias
-----------------

Son un tipo de prueba automatizada en las que se testea la mínima unidad posible de código, siendo esta un método o función. 

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

![ciclotdd](https://lh3.googleusercontent.com/LE4-IvwcIG3KqBN3PMTgAaxWsR8qBOLUJ3jPKWjlXzmE_2bKmYmsok3dw0qMIo7fSZDnD6zh=s0 "ciclo tdd.jpg")


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

----------




Estructura de las Historias de usuarios (HU) y los  Criterios de aceptación para ATDD/TDD
-----------------------------------------------------

Para llevar a cabo el proceso de ATDD es necesario disminuir al máximo las ambigüedades en las historias de usuario y en lo que estas implican, para esto se establecen ciertos estándares que facilitan su comprensión y la posterior automatización de criterios de aceptación:

  Creación de historias de usuarios: La historias de usuario (HU)
   representan las funcionalidades necesitadas por el cliente desde su
   punto de vista y en su lenguaje, es decir, un lenguaje no técnico, y
   expresan de forma concreta el qué y no el cómo.

 

> Todos hemos visto HU escritas de forma vaga o ambigua o inclusa con una redacción tan pobre que solo la persona que las escribió es capaz de entenderlas. Ciertamente qué tan bien estén escritas va a depender de quien se encargue de hacerlo. Usar una estructura convencional permite corregir eso.

De modo de establecer un estándar se ha extendido el uso de este formato:

 

    Título (Una línea describiendo la historia)
          Narrativa: 
          Como [un rol] 
          Yo quiero [característica] 
          De manera que [beneficio]


Creación de criterios de aceptación: Los criterios de aceptación ayudan a elaborar en detalle la HU (una HU tendrá N criterios de aceptación), estableciendo en conjunto con el cliente las cosas que se deben cumplir o que deben ocurrir para que el cliente considere la HU como completada. La intención de los criterios de aceptación es aumentar la comprensión del alcance de la HU. Deben ser ejemplos concretos y reales del comportamiento que debe presentar el sistema, esto facilitará traducir esos criterios en pruebas automatizadas. Al igual que las HU los criterios de aceptación deben poseer una estructura estándar, de modo que sean de fácil comprensión por todos los Stake Holders, así como para los desarrolladores y analistas. La herramienta Cucumber popularizó el uso del lenguaje Gherkin:

 

    Criterio de Aceptación: (presentados como Escenarios)
    	       Escenario 1: Título 
    		Dado [contexto/precondiciones]
    		Y [algo más de contexto]... 
    		Cuando [acción realizada por el usuario] 
    		Entonces [resultado] 
    		Y [otro resultado]...

> Nota: No está de más aclarar que se deben hacer los respectivos
> ajustes gramaticales dependiendo del caso.

Ejemplo:

Historia de usuario:
    
    Como dueño de una cuenta
    Yo quiero retirar efectivo de un cajero automático
    De manera que pueda tener dinero en efectivo.

Criterios de aceptación escritos como escenarios de ejemplo.

    Escenario 1: La cuenta tiene suficientes fondos
    Dado que el balance de la cuenta es $100
    Y la tarjeta es válida
    Y el cajero tiene suficiente dinero
    Cuando el dueño de la cuenta solicita $20
    Entonces el cajero debe dispensar $20
    Y el balance de la cuenta debe ser $80
    Y la tarjeta debe ser retornada

   

    Escenario 2: La cuenta no tiene suficientes fondos
    Dado que el balance de la cuenta es $10
    Y la tarjeta es válida
    Y el cajero tiene suficiente dinero
    Cuando el dueño de la cuenta solicita $20
    Entonces el cajero no debe dispensar dinero
    Y el cajero debe decir que no hay suficientes fondos
    Y el balance de la cuenta debe ser $10
    Y la tarjeta debe ser retornada


----------

Escribir código "testeable" y escalable: Los principios S.O.L.I.D.
------------------------------------------------------------------

Los principios SOLID son una serie de prácticas que buscan escribir código testeable, entendible, robusto y escalable. 
Como suele suceder con muchos términos en desarrollo de software se trata de un acrónimo.

 

 - Single responsibility 
 - Open/closed
 - Liskov substitution
 - Interface segregation
 - Dependency Inversion

**Single responsibility:** Una clase debería encargarse de una sola cosa. Si una clase se encarga de manejar el proceso de facturación, no debería conectarse a la BD para hacer consultas, esto lo debería hacer otra clase, por ejemplo un modelo. Tampoco debería formatear cadenas, debería existir una clase utilitaria o helper que se encargue de esto. Pensemos en el mantenimiento del código, una responsabilidad representa una posible razón para cambiar, tener más de una puede hacer que el código se vuelve difícil de mantener y entender.

**Open/Closed:** Abierta para la extensión y cerrada para la edición. Si el código está funcional y ya pasa todas las pruebas debería quedarse como está, por el contrario deberíamos ser capaces de extender ese código agregando nuevas funcionalidades sin modificar el código original.

**Liskov substitution:** Quizá sea el principio más difícil de entender, dado que quien lo escribió, Bárbara Liskov, usó terminología matemática para postularlo.

> Sea ϕ(x) una propiedad comprobable acerca de los objetos x de tipo T. Entonces ϕ(y) debe ser verdad para los objetos y del tipo S donde S, es un subtipo de T.

 Básicamente implica que si T y S son clases y S es una clase "hija" de T, S debería ser capaz de reemplazar a T, sin que el código falle. Esto describe la herencia de clases.
 
**Interface segregation:** El código debería estar comprendido por múltiples interfaces (no confundir con la UI), las cuales establecen la arquitectura del mismo, y dado que aplicamos el principio de responsabilidad única, una interfaz tampoco debería definir métodos que correspondan a múltiples responsabilidades.

**Dependency Inversion:** La inversión de dependencias, relacionada (y confundida) con la inversión de control y la inyección de dependencias, establece que se invierte la dependencia en el sentido de que nuestro código no depende de una clase concreta, sino que por el contrario depende de una interfaz o contrato (una abstracción).
