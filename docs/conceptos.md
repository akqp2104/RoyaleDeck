# Conceptos del proyecto

## Clash Royale

Videojuego de estrategia en tiempo real en el que dos jugadores usan cartas para defender sus torres y atacar las del rival. Las partidas no se desarrollan por turnos.

## Carta

Cada carta representa un recurso que se puede utilizar durante una partida. Hay cartas de tropas, que aparecen y se desplazan por el campo; edificios, que se colocan en una posición; y hechizos, que producen un efecto sobre una zona o unos objetivos.

En los datos del proyecto, cada carta se identifica mediante un número (`id`). Ese identificador permite reconocer la misma carta aunque aparezca en distintos mazos o en posiciones diferentes.

## Mazo

Combinación de ocho cartas diferentes que un jugador utiliza en un combate. Usar una carta durante la partida no la elimina de su colección.

## Colección

Conjunto de cartas que ha conseguido un jugador. No debe confundirse con el catálogo del proyecto: los datos incluidos contienen cartas y mazos registrados en partidas, pero no indican qué cartas tiene cada jugador.

## Guerra de clanes

Competición en la que los miembros de un clan participan en combates para contribuir al resultado del grupo. Para prepararse, un jugador debe reunir cuatro mazos de ocho cartas cada uno. Una misma carta no puede aparecer en más de uno de esos cuatro mazos, por lo que se necesitan 32 cartas distintas.

## Compatibilidad entre mazos

En este proyecto, dos o más mazos son compatibles si no comparten ninguna carta. Esta definición solo se refiere a la regla de no repetir cartas en una guerra. No significa que los mazos tengan buena sinergia ni que sean eficaces contra un rival.

## Carta compartida o conflicto

Una carta compartida aparece en más de uno de los mazos que se quieren usar juntos. Por ejemplo, si dos mazos contienen Bola de Fuego, no pueden incluirse ambos en la misma selección de guerra.

## Combinación candidata

Composición de ocho cartas que el jugador está dispuesto a considerar para uno de sus combates. Que aparezca en los datos históricos no significa que el jugador la tenga en su colección o quiera utilizarla.

## Datos históricos

Los archivos del proyecto contienen composiciones observadas en partidas registradas el 31 de diciembre de 2020. Sirven para comprobar qué cartas forman cada mazo y cuáles se repiten entre combinaciones. Por su antigüedad, no demuestran que esos mazos sean recomendaciones actuales ni que permitan ganar.

## Nivel de una carta

Valor que refleja cuánto se ha mejorado una carta y que influye en sus características durante el combate. A efectos de la regla de guerra, dos cartas con el mismo identificador cuentan como la misma carta, aunque tengan niveles distintos.