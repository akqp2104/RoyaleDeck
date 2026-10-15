# Hitos del producto

Los hitos se numeran desde cero y describen entregables acumulativos. Son distintos de los objetivos docentes: este objetivo 1 los planifica; no implementa todavía sus productos.

**Estado:** descripciones preparadas. Pendiente crear los milestones nativos de GitHub y efectuar las asignaciones indicadas.

## M0 — Base del dominio de mazos de guerra

**Destinatario:** quien continúe el desarrollo del motor.

**Producto entregable:** primera versión del código del dominio en el repositorio, con las declaraciones y restricciones necesarias para representar cartas reconocibles y combinaciones completas sin duplicaciones por orden. Se entregará en una revisión identificada, con instrucciones para comprobar su corrección sintáctica en el lenguaje elegido. No incluye selección de cuatro mazos, interfaz ni despliegue.

**Historia asignada:** [HU001 — #2](https://github.com/akqp2104/RoyaleDeck/issues/2).

**Viabilidad:** el código debe compilar o superar la comprobación sintáctica equivalente; los conceptos y restricciones deben corresponder a HU001, y el siguiente desarrollador debe poder apoyarse en ellos sin redefinir qué hace iguales dos mazos. La revisión debe comprobar que ocho cartas distintas describen un mazo y que reordenarlas no cambia su identidad. No se exige implementar en este hito el motor ni adelantar la batería de pruebas del objetivo 4.

**Por qué es mínimo:** entrega el vocabulario en código que necesita el cálculo posterior, sin incorporar lógica de selección antes de modelizarlo. Corresponde al trabajo que se iniciará en el objetivo 2.

## M1 — Motor ejecutable de preparación de guerra

**Destinatario:** equipo de desarrollo del servicio y participantes en la validación del resultado.

**Producto entregable:** versión ejecutable del cálculo apoyada en M0, distribuida en el repositorio con un punto de entrada documentado, los datos necesarios y pruebas automatizadas. Recibirá referencias de candidatos y una preferencia opcional; producirá una preparación completa o una selección máxima con sus conflictos. No necesita todavía un servicio público ni una interfaz gráfica.

**Historias asignadas:** [HU002 — #3](https://github.com/akqp2104/RoyaleDeck/issues/3), [HU003 — #4](https://github.com/akqp2104/RoyaleDeck/issues/4) y [HU004 — #5](https://github.com/akqp2104/RoyaleDeck/issues/5). Incorporará los criterios de HU001 como base.

**Viabilidad:** las pruebas deben cubrir una solución de cuatro, una primera elección que bloquea pero otra que permite completar, una preferencia imprescindible, un caso imposible con máximo conocido, alternativas repetidas y una entrada vacía. Cada resultado conserva mazos completos, usa solo candidatos admitidos y no repite cartas. En casos pequeños se contrastará la maximalidad con todas las selecciones posibles, sin limitarse a comparar el resultado con la propia implementación.

Los datos y su procedencia deben estar en el repositorio y el cálculo debe ejecutarse sin acceso a servicios externos. La relevancia para usuarios exige resolver [#6](https://github.com/akqp2104/RoyaleDeck/issues/6); superar pruebas con datos artificiales no basta para declararla.

**Incremento respecto a M0:** convierte la representación del dominio en un cálculo comprobable de principio a fin. Las HU se desarrollan en el orden indicado, sin esperar a completar toda la interfaz.

## M2 — Consulta remota de preparaciones

**Destinatario:** cliente que utilizará el servicio desde los dispositivos de los jugadores.

**Producto entregable:** versión desplegable del motor M1 con acceso de red, contrato de consulta documentado y configuración reproducible de despliegue. Es una previsión que se concretará al terminar M1, sin elegir ahora proveedor, framework o protocolo.

**Historias de referencia:** HU002–HU004. Los issues específicos de acceso remoto se derivarán de ellas cuando se concrete el hito; no se duplican las HU como deseos artificiales de infraestructura.

**Viabilidad:** una misma petición válida debe satisfacer las mismas reglas en ejecución local y remota. Las solicitudes de jugadores distintos deben mantener separadas sus preferencias, los errores de entrada deben distinguirse de la imposibilidad de completar cuatro y el servicio no debe necesitar acceder a APIs del juego. Se verificará mediante pruebas de integración y una comprobación desde un cliente externo.

**Incremento respecto a M1:** hace accesible el cálculo existente desde otros dispositivos. No añade nuevas promesas competitivas ni modifica las reglas de selección.

## Asignaciones que deben quedar en GitHub

| Milestone | Issues |
| --- | --- |
| M0 — Base del dominio de mazos de guerra | #2 |
| M1 — Motor ejecutable de preparación de guerra | #3, #4, #5 y el bloqueo de datos #6 |
| M2 — Consulta remota de preparaciones | Issues derivados pendientes de concretar tras M1 |

No se fijan fechas arbitrarias ni se cierran hitos por completar documentación. Las entregas y revisiones reales determinarán su avance.
