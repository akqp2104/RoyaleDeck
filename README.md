# RoyaleDeck

Preparación de mazos compatibles para las guerras de clanes de Clash Royale.

En este juego, cada mazo reúne ocho cartas diferentes. Para una preparación de guerra se pueden utilizar cuatro mazos, pero una carta no puede repetirse entre ellos. El [contexto del juego](docs/contexto.md) explica las cartas, las partidas y esta restricción.

## Descripción del problema

Juego a Clash Royale y tanto mis amigos como yo hemos tenido dificultades al preparar los mazos para las guerras de clanes. Tenemos combinaciones que conocemos o que hemos visto utilizar a otros jugadores, pero varias de ellas necesitan las mismas cartas y no podemos utilizarlas juntas.

La dificultad aparece al elegir esos mazos por separado. Dos combinaciones que nos interesan pueden compartir una carta y obligarnos a descartar una de ellas. La alternativa que encontramos puede entrar en conflicto con un tercer mazo. Por ejemplo, dos mazos que contienen el hechizo Bola de Fuego no pueden formar parte del mismo conjunto de guerra, aunque sus otras siete cartas sean diferentes.

Acabamos revisando combinaciones y cambiando elecciones anteriores para intentar completar los cuatro mazos. Resolver un conflicto entre dos no basta: una pareja compatible puede impedir completar el conjunto con las demás alternativas que nos interesan. Sustituir cartas sueltas tampoco nos resulta equivalente, porque altera las combinaciones que queríamos utilizar.

Lo que necesitamos es poder preparar los cuatro mazos sin cartas repetidas entre ellos, aprovechando combinaciones que estemos dispuestos a jugar. No nos sirve reunir cuatro mazos cualesquiera si no conocemos su funcionamiento o no tenemos las cartas necesarias. Si queremos mantener uno concreto, esa preferencia también condiciona las alternativas restantes.

Cuando nuestras opciones no permiten completar los cuatro, necesitamos entender qué elecciones entran en conflicto y cuántos mazos podemos reunir sin reconsiderarlas. La dificultad que se aborda es decidir qué combinaciones pueden convivir en una misma preparación de guerra. La valoración de su eficacia en combate y de los niveles de las cartas queda fuera de este problema.


## Estado del proyecto

Se está preparando el objetivo 1: perfiles, recorridos de uso, historias de usuario y planificación incremental. Todavía no hay implementación del producto.

El [PR del objetivo 0](https://github.com/akqp2104/RoyaleDeck/pull/1) sigue pendiente de aprobación. Esta rama parte de su última revisión y permite avanzar en la planificación sin fusionar ese PR ni dar por superado su prerrequisito.

La disponibilidad de un catálogo relevante para los jugadores y la incorporación de los archivos están pendientes en [#6](https://github.com/akqp2104/RoyaleDeck/issues/6).

## Planificación

- [Perfiles y recorridos de uso](docs/usuarios.md).
- [Historias de usuario, prioridades y conceptos](docs/planificacion.md).
- [Hitos, entregables y criterios de viabilidad](docs/hitos.md).
- [Comprobación y condiciones para entregar el objetivo 1](docs/objetivo-1.md).
- [Historias de usuario en GitHub](https://github.com/akqp2104/RoyaleDeck/issues?q=is%3Aissue%20label%3Auser-stories).

## Datos y documentación

- [Fuentes de datos y limitaciones](docs/datos.md).
- [Contexto de uso y despliegue en la nube](docs/usuarios.md#contexto-de-acceso).
- [Ficha del cliente](docs/ficha-cliente.md).
- [Configuración del repositorio](config/configuracion.md).
