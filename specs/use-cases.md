# Casos de uso

## UC-01: Liquidar siniestro

**Actor:** Liquidador (actor principal). Gerente de Siniestros (actor secundario, solo en el flujo alternativo 5a).

**Precondición:** El siniestro está En liquidación y tiene adjuntos el informe de pericia y las fotos (RF-02).

**Flujo principal:**
1. El Liquidador selecciona un siniestro En liquidación.
2. Se ejecuta UC-02 Consultar informe y fotos de pericia (include).
3. El Liquidador registra que el siniestro está cubierto.
4. El Liquidador registra el monto calculado.
5. El sistema verifica que el monto sea numérico y que no supere el importe de autorización.
6. El Liquidador confirma.
7. El sistema registra la cobertura y el monto, y deja el siniestro en Monto ofrecido.

**Flujo(s) alternativo(s):**
- 3a. El siniestro no está cubierto: el sistema registra que no está cubierto, deja el siniestro Rechazado y el caso de uso termina.
- 5a. El monto supera el importe de autorización: se ejecuta UC-03 Autorizar monto (extend); el sistema envía la solicitud al Gerente y deja el siniestro En autorización. Si el Gerente autoriza, el siniestro pasa a Monto ofrecido y el caso continúa en el paso 7.
- 5b. El monto no es numérico o está vacío: el sistema lo rechaza y vuelve al paso 4.
- 5c. El Gerente rechaza el monto: [NEEDS CLARIFICATION: el caso y el diagrama de estados no dicen qué ocurre (¿vuelve a En liquidación para recalcular?). Decide Diego Almirón.]
- 5d. El importe de autorización: [NEEDS CLARIFICATION: el caso dice «cierto importe» y no lo define. Decide Diego Almirón.]

**Postcondición:** El siniestro queda con su cobertura y su monto numérico registrados, en estado Monto ofrecido; o Rechazado si no está cubierto; o En autorización si el monto espera al Gerente.

**Relaciones con otros casos de uso:**

| Relación | Caso de uso relacionado | Tipo (include/extend) | Justificación |
|----------|--------------------------|------------------------|----------------|
| UC-01 → UC-02 | Consultar informe y fotos de pericia | include | Siempre se ejecuta: el liquidador determina la cobertura y calcula el monto con el informe (Caso 3.3). Sin informe no hay liquidación. |
| UC-03 → UC-01 | Autorizar monto | extend | Solo ocurre si el monto supera el importe (Caso 3.3; V2; V3). Un monto menor completa la liquidación sin esto. |

Recordar (ver skill/SKILL.md): include = siempre se ejecuta como parte
del flujo, sin excepción. extend = extiende opcionalmente bajo una
condición específica, el flujo base es completo sin ella. Toda relación
sin justificación no cuenta como completa.

## Fragmentos considerados para este caso de uso

| Fragmento | Qué aporta al caso de uso |
|-----------|------------------------------|
| Caso 3.3 | El orden de los pasos: informe, cobertura, monto, autorización si corresponde y oferta al asegurado. |
| V2, V3 | El extend de la autorización y la regla de RF-04. |
| Planilla, 1014 y 1007 | El paso 5 y el flujo 5b: hoy el monto puede ser texto o estar vacío. |
| Planilla, 1022 | El flujo 5a: un incendio total de $11.200.000 con «escalar al gerente??» y sin registro de la decisión. |
| Diagrama de estados (1.3) | Los estados y las transiciones: En liquidación, En autorización, Monto ofrecido, Rechazado. |

