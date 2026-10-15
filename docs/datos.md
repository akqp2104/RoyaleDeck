# Datos y procedencia

La fuente disponible de composiciones de mazos es el archivo [BattlesStaging_01012021_WL_tagged.csv](https://huggingface.co/datasets/Grandediw/clash-royale-battle/blob/main/BattlesStaging_01012021_WL_tagged.csv), publicado por Grandediw en el conjunto [Clash Royale Battle](https://huggingface.co/datasets/Grandediw/clash-royale-battle).

La muestra preparada fuera de esta rama, prevista para `data/partidas.csv`, contiene 16.126 partidas del 31 de diciembre de 2020. En ella aparecen 15.941 combinaciones distintas de ocho cartas. Se ha comprobado que contiene conjuntos de cuatro mazos sin cartas compartidas. Esto acredita que hay ejemplos de compatibilidad en los datos, pero no que esos conjuntos coincidan con las preferencias de un jugador concreto.

Los archivos contienen la información necesaria para reconocer las cartas de cada mazo:

| Archivo y campos | Información disponible y relación con el problema |
| --- | --- |
| CSV: `winner.card1.id` a `winner.card8.id` | Las ocho cartas del mazo de uno de los participantes. |
| CSV: `loser.card1.id` a `loser.card8.id` | Las ocho cartas del mazo del otro participante. |
| JSON: `id` y `name` | Correspondencia entre cada identificador y el nombre de la carta, para interpretar qué cartas comparten dos mazos. |

La igualdad de identificadores permite reconocer una misma carta aunque aparezca en posiciones diferentes. El orden de las ocho cartas no convierte una combinación en un mazo distinto. Los resultados de las partidas, las copas y los niveles registrados no acreditan que un mazo sea adecuado para una persona concreta.

Por ejemplo, en la muestra aparece la combinación Knight, Princess, Ice Spirit, Goblin Gang, Inferno Tower, Rocket, Goblin Barrel y The Log. Cualquier otro mazo que contenga Knight será incompatible con ella dentro del mismo conjunto de guerra, con independencia del resultado de las partidas en las que se hayan utilizado.

Los nombres proceden del archivo [clash_royale_cards_1.json](https://huggingface.co/datasets/Nitesh-04/Clash-Royale-Cards-Data/blob/main/clash_royale_cards_1.json), publicado por Nitesh Kakkar. La correspondencia necesaria está preparada en `data/cartas.json`. La procedencia de las extracciones y las licencias declaradas se detallan en `data/FUENTES.md`.

La muestra es histórica: acredita que esas combinaciones se utilizaron en las partidas registradas, pero no que sean recomendaciones competitivas actuales. Las cartas que componen cada mazo permiten comprobar si dos combinaciones tienen cartas en común. Los archivos no contienen nuestras preferencias ni nuestra colección personal.

Las composiciones y los nombres están disponibles en archivos CSV y JSON descargables. El estudio de las coincidencias entre sus cartas no requiere información en tiempo real del juego ni consultas a cuentas personales.


## Estado en el repositorio

Al iniciar Objetivo-1 estos tres archivos todavía no están incorporados. Los nombres anteriores indican su destino previsto; no son enlaces a archivos existentes. Los recuentos describen la muestra previamente preparada, no un inventario ya publicado en esta rama.

La validación con preferencias reales y la incorporación de datos con procedencia verificable se siguen en [el issue #6](https://github.com/akqp2104/RoyaleDeck/issues/6). No se considera resuelta por disponer de muchas combinaciones históricas. Las pruebas artificiales del futuro motor deberán distinguirse de esa validación.
