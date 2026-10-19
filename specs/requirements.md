# Requerimientos

Completar a partir de los fragmentos de relevamiento del caso. Seguir
la convención de `skill/SKILL.md` (atómico, verificable, sin tecnología
mezclada).

## Requerimientos funcionales

| ID | Issue | Requerimiento | Nivel / Tipo | Fragmento(s) de origen | Verif. |
|-------|-------|---------------|--------------|------------------------|--------|

| RF-01 | G01-1 | El sistema debe registrar para cada siniestro un único estado elegido de una lista cerrada, sin admitir texto libre ni valor vacío. | Sistema / F | Caso 3.3; V1; planilla, columna ESTADO | Un estado fuera de la lista o vacío no se puede guardar. |
| RF-02 | | |
| RF-03 | | RF-03 | G01-3 | El sistema debe registrar el monto calculado de cada siniestro como un valor numérico. | Usuario / F | Caso 3.3; planilla, columna MONTO ESTIM. | Un monto con texto o vacío no se puede guardar. |
| RF-04 | G01-4 | Un siniestro cuyo monto calculado supere el importe de autorización no debe poder pasar a Monto ofrecido sin la autorización registrada del Gerente de Siniestros. [NEEDS CLARIFICATION: el caso dice «si supera cierto importe» y no lo define. Decide Diego Almirón.] | Negocio / F | Caso 3.3; V2; V3; planilla, 1022 | Pend. |
| RF-05 | | |

## Fragmentos que NO son requerimientos funcionales

Para cada fragmento del relevamiento que no calificó como RF, clasificar
según las categorías de `skill/SKILL.md` (objetivo/meta de negocio,
restricción técnica, RNF, dato de contexto) y justificar en una línea
por qué no es un RF.

| Fragmento | Texto | Categoría | Justificación |
|-----------|-------|-----------|----------------|
| | | | |
| | | | |

## Conflictos u observaciones detectadas

Si al procesar los fragmentos aparece un conflicto de valores (ver
"Detección de conflictos" en la skill), documentarlo acá aunque no
afecte directamente un RF puntual.

-
