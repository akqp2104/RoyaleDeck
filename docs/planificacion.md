# Historias de usuario y orden de trabajo

## Historias canónicas

Las historias y sus criterios de aceptación se mantienen en issues de GitHub con la etiqueta `user-stories`. Los enlaces siguientes son la referencia para el desarrollo; esta tabla no sustituye sus descripciones.

| Historia | Necesidad | Prioridad | Hito previsto |
| --- | --- | --- | --- |
| [HU001 — #2](https://github.com/akqp2104/RoyaleDeck/issues/2) | Reconocer una combinación sin duplicarla por su orden o nivel. | Primera: fundamenta las demás. | M0 |
| [HU002 — #3](https://github.com/akqp2104/RoyaleDeck/issues/3) | Reunir cuatro mazos entre alternativas aceptadas. | Primera lógica de selección. | M1 |
| [HU003 — #4](https://github.com/akqp2104/RoyaleDeck/issues/4) | Completar la preparación manteniendo un mazo concreto. | Después del caso sin preferencia. | M1 |
| [HU004 — #5](https://github.com/akqp2104/RoyaleDeck/issues/5) | Entender el máximo alcanzable y las incompatibilidades. | Después del caso de preparación completa. | M1 |

Las asignaciones anteriores son las previstas; su creación como milestones nativos está pendiente. Las HU no están implementadas ni deben cerrarse por haber redactado esta documentación.

## Vocabulario del dominio

- **Carta:** recurso del juego identificado por un identificador estable del catálogo. Nombre y nivel no sustituyen esa identidad.
- **Mazo completo:** ocho cartas distintas y reconocibles. Su orden no cambia la combinación.
- **Catálogo:** composiciones disponibles en los archivos del proyecto. No implica recomendación competitiva.
- **Candidato:** mazo completo del catálogo que el jugador admite como alternativa para una consulta.
- **Mazo imprescindible:** un único candidato opcional que tiene que pertenecer al conjunto obtenido.
- **Compatibilidad:** ausencia de cartas compartidas entre dos mazos.
- **Preparación completa:** cuatro candidatos distintos compatibles entre sí.
- **Selección máxima:** selección admisible de mayor tamaño, con un límite de cuatro, respetando el mazo imprescindible si lo hay. No basta con que no pueda añadirse otro mazo a una selección particular.
- **Imposibilidad:** no existe una preparación completa dentro de los candidatos y condiciones considerados; no significa que no exista en todo el juego.

## Qué se aborda primero

Se comienza por M0 y HU001. Quien desarrolle el objetivo 2 debe poder distinguir identidad de carta, igualdad de mazos y composición válida a partir de esa historia, plantear issues de dominio relacionados y elegir con la propietaria el lenguaje de trabajo. No se prescribe ahora una jerarquía de clases ni un algoritmo.

Después, M1 incorpora el cálculo conjunto. Los criterios de HU002–HU004 obligan a contemplar selecciones alternativas: que una primera elección quede bloqueada no demuestra que el problema no tenga solución.

La evidencia pendiente de [#6](https://github.com/akqp2104/RoyaleDeck/issues/6) debe avanzar antes de considerar útil para jugadores el producto M1. Se pueden estudiar las reglas con ejemplos de prueba claramente artificiales; eso no valida la relevancia del catálogo.

## Límites y decisiones pendientes

No se optimizan victorias, niveles, coste de mejora ni fuerza competitiva. La posesión y adecuación de las cartas se mantienen como juicio del jugador al admitir sus alternativas.

No se exige enumerar todos los conjuntos válidos: basta uno que cumpla las condiciones; si no alcanza cuatro, debe acreditarse que no existe otro mayor bajo las mismas condiciones.

No se decide todavía cómo localizar candidatos en una interfaz. Debe ser cómodo y no exigir transcribir cartas ni examinar todo el catálogo. Su validación forma parte de #6.

## Trazabilidad

Los futuros issues técnicos describirán problemas derivados de una HU y enlazarán su número. Los commits explicarán por qué se cambia algo y referenciarán el issue correspondiente. Un issue se cerrará mediante un commit cuando su necesidad quede satisfecha, no por anticipar la implementación.
