# Requerimientos

Completar a partir de los fragmentos de relevamiento del caso. Seguir
la convención de `skill/SKILL.md` (atómico, verificable, sin tecnología
mezclada).

## Requerimientos funcionales

| ID | Issue | Requerimiento | Nivel / Tipo | Fragmento(s) de origen | Verif. |
|-------|-------|---------------|--------------|------------------------|--------|
| RF-01 | G01-1 | El sistema debe registrar para cada siniestro un único estado elegido de una lista cerrada, sin admitir texto libre ni valor vacío. Los estados son: Denunciado, En pericia, En liquidación, En autorización, Monto ofrecido, Pagado, Cerrado y Rechazado. | Sistema / F | Caso 3.3; V1; planilla, columna ESTADO; E1-2 y E1-3 | Un estado fuera de la lista o vacío no se puede guardar. |
| RF-02 | G01-2 | El sistema debe permitir adjuntar al siniestro las fotos y el informe de pericia, con el perito que los envió y la fecha de carga, que el sistema registra automáticamente al guardarlos. | Usuario / F | Caso 3.3; planilla, 1004 | Un siniestro con pericia muestra fotos e informe con fecha de carga automática y perito. |
| RF-03 | G01-3 | El sistema debe registrar el monto calculado de cada siniestro como un valor numérico entero, ingresado solo con dígitos, sin separador de miles ni decimales, y mostrar la suma de los montos guardados. | Usuario / F | Caso 3.3; planilla, columna MONTO ESTIM.; E1-2 | Un monto con texto o vacío no se puede guardar; uno numérico guardado se puede sumar sin conversión. |
| RF-04 | G01-4 | Un siniestro cuyo monto calculado supere $3.000.000, o que sea de robo total o incendio total (cualquiera sea el monto), no debe poder pasar a Monto ofrecido sin la autorización registrada del Gerente de Siniestros. | Negocio / F | Caso 3.3; V2; V3; planilla, 1022; Acta 3.ª §3.6 | Un siniestro de más de $3.000.000, o de robo o incendio total, no pasa a Monto ofrecido sin autorización registrada; uno por debajo y de otro tipo, sí. |
| RF-05 | G01-5 | El sistema debe mostrar al Gerente de Siniestros el monto total comprometido en siniestros abiertos, calculado al momento de la consulta. [NEEDS CLARIFICATION: el caso no define qué estados cuentan como «abierto» ni qué monto se suma. Decide Diego Almirón.] | Usuario / F | V3; E1-6 | Pend. |

## Historial de cambios

| Req. | Versión | Fecha | Qué cambió | Issue |
|------|---------|-------|------------|-------|
| RF-01 | v2 | 02/11 | Se agrega la lista de los ocho estados (defecto de especificación hallado en la E3). | G01-1 |
| RF-02 | v2 | 02/11 | Se aclara que la fecha de carga la registra el sistema (defecto hallado en la E3). | G01-2 |
| RF-03 | v2 | 02/11 | Se define el formato del monto: entero, solo dígitos; y la suma de montos (defecto hallado en la E3). | G01-3 |
| RF-04 | v1 | 19/10 | [NEEDS CLARIFICATION: importe de autorización a partir del cual autoriza el Gerente. Decide Diego Almirón.] | G01-4 |
| RF-04 | v2 | 02/11 | Decidido en Acta 3.ª §3.6: más de $3.000.000, o robo total / incendio total sin importar el monto. Reemplaza el criterio del acta anterior. Sale la etiqueta pendiente-decision. | G01-8 |
| RF-06 | v1 | 02/11 | Nuevo: si el siniestro es del Gerente, autoriza el Director. | G01-9 |

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
