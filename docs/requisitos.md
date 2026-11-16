# Revisión de requisitos

Línea base evaluada: requisitos R-01 a R-04 y código del commit `e117284`. Se aplican criterios de claridad, consistencia, completitud y verificabilidad descritos en ISO/IEC/IEEE 29148:2018 y Wiegers y Beatty (2013); no se declara conformidad normativa. Véase `docs/referencias.md`.

## Diagnóstico

| ID | Requisito original | Defecto | Impacto | Acción propuesta |
|---|---|---|---|---|
| R-01 | «El descuento debe calcularse rápidamente». | “Rápidamente” no define tiempo máximo, carga, entorno ni método de medición. | La aceptación del rendimiento sería subjetiva. | Especificar umbral temporal y condiciones reproducibles de medición. |
| R-02 | «Los clientes importantes obtendrán un descuento especial». | “Clientes importantes” y “descuento especial” no definen elegibilidad ni cálculo. | Pueden aplicarse beneficios incompatibles. | Definir elegibilidad y regla completa del beneficio. |
| R-03 | «El descuento no puede superar el precio, excepto en promociones». | La excepción no identifica promociones válidas, vigencia ni límite. | No puede determinarse cuándo es admisible superar el precio. | Definir activación, alcance y límites promocionales. |
| R-04 | «Se debe mostrar el resultado correcto». | “Correcto” es circular; faltan fórmula, dominio, precisión, mecanismo de salida y tratamiento de datos inválidos. | No existe un oráculo ni una salida verificable. | Definir cálculo, dominio, precisión, salida y respuesta ante entradas inválidas. |

## Requisitos reformulados y criterios de aceptación

Los símbolos `T_max`, `C_importante`, `B_especial`, `P_promoción`, `L_promoción`, `M_salida`, `R_precisión` y `E_inválida` representan políticas pendientes; no constituyen valores asumidos. `descuentoFinal` designa el descuento total que resulte de las políticas aprobadas. Ningún criterio puede cerrarse hasta aprobar los SP asociados.

| ID | Requisito reformulado | Criterios de aceptación objetivos |
|---|---|---|
| RF-01 | Para solicitudes incluidas en el perfil de carga y el entorno de referencia aprobados, el módulo deberá completar el cálculo en un tiempo no mayor que `T_max`. | El procedimiento aprobado registra un tiempo menor o igual que `T_max` para el perfil de carga definido. |
| RF-02 | El módulo deberá aplicar `B_especial` únicamente cuando el cliente cumpla `C_importante`; en caso contrario, no deberá aplicarlo. | Dos casos idénticos salvo por el cumplimiento de `C_importante` incluyen, respectivamente, la aplicación y la exclusión del efecto aprobado para `B_especial`. |
| RF-03 | Sin una `P_promoción` activa, el descuento final no deberá superar el precio. Con una promoción activa, solo podrá excederlo dentro de `L_promoción`. | Caso no promocional: `descuentoFinal ≤ precio`. Caso promocional: la excepción está identificada, vigente y dentro de `L_promoción`. |
| RF-04 | Para cada entrada válida, el módulo deberá producir `total = precio - descuentoFinal` mediante `M_salida`, aplicando las reglas aprobadas y `R_precisión`; para una entrada inválida deberá aplicar `E_inválida`. | La salida coincide con el oráculo calculado a partir de las políticas aprobadas. Las entradas fuera del dominio producen exactamente `E_inválida`. |

## Supuestos pendientes de confirmación

No se adopta ninguna de las siguientes decisiones como regla vigente.

| ID | Política o dato pendiente | Requisitos afectados |
|---|---|---|
| SP-01 | Valor de `T_max`, perfil de carga, entorno y procedimiento de medición. | RF-01 |
| SP-02 | Equivalencia, si existe, entre “cliente importante” y `esVip`, y criterio de elegibilidad `C_importante`. | RF-02 |
| SP-03 | Naturaleza, magnitud, unidad y orden de aplicación de `B_especial`. | RF-02, RF-04 |
| SP-04 | Identificación, vigencia y límite `L_promoción` de las promociones que permiten exceder el precio. | RF-03, RF-04 |
| SP-05 | Dominio válido de `precio`, `porcentaje` y `esVip`, incluidas condiciones nulas, no numéricas, negativas y límites. | RF-02, RF-03, RF-04 |
| SP-06 | Confirmación de la fórmula del descuento base, del significado de `porcentaje`, de la relación `total = precio - descuentoFinal` y de `M_salida`. | RF-04 |
| SP-07 | Moneda, precisión y regla `R_precisión`. | RF-04 |
| SP-08 | Respuesta `E_inválida`: rechazo, mensaje, excepción o valor de retorno. | RF-04 |

## Verificación y validación aplicadas

La verificación estática determina si los requisitos y el código son claros, consistentes, completos, trazables y verificables, sin ejecutar el módulo. La validación deberá confirmar con las partes interesadas que las políticas pendientes representan la necesidad de negocio. Esta fase aporta verificación documental; no sustituye esa validación.
