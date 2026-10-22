# RoyaleDeck

Preparación de mazos compatibles para las guerras de clanes de Clash Royale.

## Contexto del juego

Clash Royale es un videojuego de estrategia en tiempo real: los dos jugadores actúan simultáneamente, sin esperar turnos. Cada uno defiende sus torres e intenta destruir las del contrario utilizando cartas digitales.

Una **carta** representa un recurso que se puede utilizar durante la partida:

- **Tropas:** unidades que aparecen en el campo de batalla y se desplazan para atacar, como un caballero o un grupo de arqueras.
- **Edificios:** estructuras que se colocan en una posición, por ejemplo un cañón defensivo.
- **Hechizos:** efectos que se aplican sobre una zona o unos objetivos, como una bola de fuego que causa daño.

Antes del combate, cada jugador prepara un **mazo de ocho cartas diferentes**. Durante la partida utiliza las cartas que tiene disponibles en la mano; al jugar una, entra otra del mazo. Las cartas vuelven a estar disponibles a lo largo del combate: utilizarlas no las elimina de la colección. Jugar una carta consume **elixir**, un recurso que se recupera con el tiempo. Por eso importa tanto qué cartas se eligen como cuándo y dónde se utilizan. Supercell explica este recurso en su [documentación sobre el elixir](https://support.supercell.com/clash-royale/es/articles/elixir.html).

La **colección** es el conjunto de cartas que un jugador ha conseguido. Cada carta tiene un **nivel de mejora**, que influye en sus características durante el combate. El nivel no cambia su identidad: dos cartas de Caballero con niveles distintos siguen siendo la misma carta a efectos de las restricciones de los mazos.

Un **clan** es un grupo de jugadores. En las **guerras de clanes**, sus miembros participan en combates para contribuir al resultado del grupo. Cada jugador puede preparar cuatro mazos, pero **ninguna carta puede repetirse entre ellos**: completarlos requiere 32 cartas distintas. Son cuatro combinaciones para distintos combates, no un único mazo de 32 cartas. Esta condición se recoge en las [reglas oficiales de los mazos de guerra](https://support.supercell.com/clash-royale/es/articles/war-decks-1.html).

## Descripción del problema

Juego a Clash Royale y tanto mis amigos como yo hemos tenido dificultades al preparar los mazos para las guerras de clanes. Tenemos combinaciones que conocemos o que hemos visto utilizar a otros jugadores, pero varias de ellas necesitan las mismas cartas y no podemos utilizarlas juntas.

La dificultad aparece al elegir esos mazos por separado. Dos combinaciones que nos interesan pueden compartir una carta y obligarnos a descartar una de ellas. La alternativa que encontramos puede entrar en conflicto con un tercer mazo. Por ejemplo, dos mazos que contienen el hechizo Bola de Fuego no pueden formar parte del mismo conjunto de guerra, aunque sus otras siete cartas sean diferentes.

Acabamos revisando combinaciones y cambiando elecciones anteriores para intentar completar los cuatro mazos. Resolver un conflicto entre dos no basta: una pareja compatible puede impedir completar el conjunto con las demás alternativas que nos interesan. Sustituir cartas sueltas tampoco nos resulta equivalente, porque altera las combinaciones que queríamos utilizar.

Lo que necesitamos es poder preparar los cuatro mazos sin cartas repetidas entre ellos, aprovechando combinaciones que estemos dispuestos a jugar. No nos sirve reunir cuatro mazos cualesquiera si no conocemos su funcionamiento o no tenemos las cartas necesarias. Si queremos mantener uno concreto, esa preferencia también condiciona las alternativas restantes.

Cuando nuestras opciones no permiten completar los cuatro, necesitamos entender qué elecciones entran en conflicto y cuántos mazos podemos reunir sin reconsiderarlas. La dificultad que se aborda es decidir qué combinaciones pueden convivir en una misma preparación de guerra. La valoración de su eficacia en combate y de los niveles de las cartas queda fuera de este problema.

## Datos y procedencia

La fuente disponible de composiciones de mazos es el archivo [BattlesStaging_01012021_WL_tagged.csv](https://huggingface.co/datasets/Grandediw/clash-royale-battle/blob/main/BattlesStaging_01012021_WL_tagged.csv), publicado por Grandediw en el conjunto [Clash Royale Battle](https://huggingface.co/datasets/Grandediw/clash-royale-battle).

La muestra preparada en [data/partidas.csv](data/partidas.csv) contiene 16.126 partidas del 31 de diciembre de 2020. En ella aparecen 15.941 combinaciones distintas de ocho cartas. Se ha comprobado que contiene conjuntos de cuatro mazos sin cartas compartidas. Esto acredita que hay ejemplos de compatibilidad en los datos, pero no que esos conjuntos coincidan con las preferencias de un jugador concreto.

Los archivos contienen la información necesaria para reconocer las cartas de cada mazo:

| Archivo y campos | Información disponible y relación con el problema |
| --- | --- |
| CSV: `winner.card1.id` a `winner.card8.id` | Las ocho cartas del mazo de uno de los participantes. |
| CSV: `loser.card1.id` a `loser.card8.id` | Las ocho cartas del mazo del otro participante. |
| JSON: `id` y `name` | Correspondencia entre cada identificador y el nombre de la carta, para interpretar qué cartas comparten dos mazos. |

La igualdad de identificadores permite reconocer una misma carta aunque aparezca en posiciones diferentes. El orden de las ocho cartas no convierte una combinación en un mazo distinto. Los resultados de las partidas, las copas y los niveles registrados no acreditan que un mazo sea adecuado para una persona concreta.

Por ejemplo, en la muestra aparece la combinación Knight, Princess, Ice Spirit, Goblin Gang, Inferno Tower, Rocket, Goblin Barrel y The Log. Cualquier otro mazo que contenga Knight será incompatible con ella dentro del mismo conjunto de guerra, con independencia del resultado de las partidas en las que se hayan utilizado.

Los nombres proceden del archivo [clash_royale_cards_1.json](https://huggingface.co/datasets/Nitesh-04/Clash-Royale-Cards-Data/blob/main/clash_royale_cards_1.json), publicado por Nitesh Kakkar. La correspondencia necesaria está preparada en [data/cartas.json](data/cartas.json). La procedencia de las extracciones y las licencias declaradas se detallan en [data/FUENTES.md](data/FUENTES.md).

La muestra es histórica: acredita que esas combinaciones se utilizaron en las partidas registradas, pero no que sean recomendaciones competitivas actuales. Las cartas que componen cada mazo permiten comprobar si dos combinaciones tienen cartas en común. Los archivos no contienen nuestras preferencias ni nuestra colección personal.

Las composiciones y los nombres están disponibles en archivos CSV y JSON descargables. El estudio de las coincidencias entre sus cartas no requiere información en tiempo real del juego ni consultas a cuentas personales.

## Contexto de uso y despliegue en la nube

La preparación de los mazos está vinculada a un juego móvil y la dificultad afecta a distintos jugadores, cada uno con sus preferencias. Consultar las mismas referencias desde sus dispositivos, sin tener que descargar y preparar los archivos de datos, hace razonable un despliegue en la nube. Las decisiones sobre la tecnología y el funcionamiento concreto corresponden a objetivos posteriores.

## Documentación

- [Perfil del jugador y recorrido de uso](docs/user-journey.md).
- [Conceptos del juego y del problema](docs/conceptos.md).
- [Configuración del repositorio](config/configuracion.md).

![Fotografía de la ficha del cliente](media/cliente.jpg)
