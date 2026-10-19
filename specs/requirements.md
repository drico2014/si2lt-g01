# Requerimientos

Completar a partir de los fragmentos de relevamiento del caso. Seguir
la convención de `skill/SKILL.md` (atómico, verificable, sin tecnología
mezclada).

## Requerimientos funcionales

| ID | Issue | Requerimiento | Nivel / Tipo | Fragmento(s) de origen | Verif. |
|-------|-------|---------------|--------------|------------------------|--------|

| RF-01 | G01-1 | El sistema debe registrar para cada siniestro un único estado elegido de una lista cerrada, sin admitir texto libre ni valor vacío. | Sistema / F | Caso 3.3; V1; planilla, columna ESTADO | Un estado fuera de la lista o vacío no se puede guardar. |
| RF-02 | G01-2 | El sistema debe permitir adjuntar al siniestro las fotos y el informe de pericia, con la fecha de carga y el perito que los envió. | Usuario / F | Caso 3.3; planilla, 1004 | Un siniestro con pericia muestra fotos e informe con fecha y perito. |
| RF-03 | G01-3 | El sistema debe registrar el monto calculado de cada siniestro como un valor numérico. | Usuario / F | Caso 3.3; planilla, columna MONTO ESTIM. | Un monto con texto o vacío no se puede guardar. |
| RF-04 | G01-4 | Un siniestro cuyo monto calculado supere el importe de autorización no debe poder pasar a Monto ofrecido sin la autorización registrada del Gerente de Siniestros. [NEEDS CLARIFICATION: el caso dice «si supera cierto importe» y no lo define. Decide Diego Almirón.] | Negocio / F | Caso 3.3; V2; V3; planilla, 1022 | Pend. |
| RF-05 | G01-5 | El sistema debe mostrar al Gerente de Siniestros el monto total comprometido en siniestros abiertos, calculado al momento de la consulta. [NEEDS CLARIFICATION: el caso no define qué estados cuentan como «abierto» ni qué monto se suma. Decide Diego Almirón.] | Usuario / F | V3; E1-6 | Pend. |


## Fragmentos que NO son requerimientos funcionales

Para cada fragmento del relevamiento que no calificó como RF, clasificar
según las categorías de `skill/SKILL.md` (objetivo/meta de negocio,
restricción técnica, RNF, dato de contexto) y justificar en una línea
por qué no es un RF.

| Fragmento | Texto | Categoría | Justificación |
|-----------|-------|-----------|---------------|
| V1 | «no sabés en qué estado está nada» | Dato de contexto | Origina RF-01. |
| V1 | «A veces pisamos filas… se perdió una denuncia entera» | Dato de contexto | Describe el problema de la planilla compartida; origina RF-01. |
| V2 | «Los siniestros importantes los tenemos que escalar al gerente. Eso sí está claro.» | Dato de contexto | Confirma la regla de RF-04, pero no define el importe. |
| V3 | «en cualquier momento» / «ya está desactualizado» | RNF | Pide actualización inmediata, pero no tiene métrica; la parte funcional es RF-05. |
| Caso 3.3 | La planilla está en una carpeta de red y la abren los cuatro liquidadores | Dato de contexto | Describe la situación actual, no pide nada al sistema nuevo. |
| Caso 3.3 | Las fotos van por WhatsApp al celular personal del liquidador | Dato de contexto | Origina RF-02. |
| Caso 3.3 | El asegurado acepta o rechaza el monto y se paga por transferencia | RF candidato | Es funcional, pero queda fuera de los cinco de esta entrega; ver E2-4 y E2-5. |
| Caso 3.3 | El asegurado llama al 0800 para saber el estado | RF candidato | Es funcional, pero depende de decidir si el asegurado entra en este frente; ver E2-5. |

## Conflictos u observaciones detectadas

Si al procesar los fragmentos aparece un conflicto de valores (ver
"Detección de conflictos" en la skill), documentarlo acá aunque no
afecte directamente un RF puntual.

-
