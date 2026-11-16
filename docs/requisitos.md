# Revisión de requisitos

Línea base evaluada: requisitos R-01 a R-04 y código del commit `e117284`. Se aplican criterios de claridad, consistencia, completitud y verificabilidad compatibles con ISO/IEC/IEEE 29148.

## Diagnóstico

| ID | Defecto | Impacto | Acción propuesta |
|---|---|---|---|
| R-01 | “Rápidamente” no define tiempo máximo, carga, entorno ni método de medición. | El requisito de rendimiento no es verificable y admite decisiones de aceptación subjetivas. | Especificar umbral temporal y condiciones reproducibles de medición. |
| R-02 | “Clientes importantes” y “descuento especial” carecen de criterios de elegibilidad y regla de cálculo. | Distintas interpretaciones pueden asignar beneficios y resultados incompatibles. | Definir la política de elegibilidad y la regla completa del beneficio. |
| R-03 | La excepción “en promociones” no identifica promociones válidas, vigencia ni límite permitido. | No puede determinarse cuándo un descuento superior al precio es válido; existe riesgo de resultados negativos no controlados. | Definir activación, alcance y límites de cada excepción promocional. |
| R-04 | “Resultado correcto” es circular: no especifica fórmula, dominio de entrada, precisión ni tratamiento de datos inválidos. | No existe un oráculo objetivo para verificar el resultado. | Definir cálculo, entradas válidas, precisión y respuesta ante entradas inválidas. |

## Requisitos reformulados y criterios de aceptación

Los símbolos `T_max`, `C_importante`, `B_especial`, `P_promoción`, `L_promoción`, `R_precisión` y `E_inválida` representan políticas pendientes; no constituyen valores asumidos.

| ID | Requisito reformulado | Criterios de aceptación objetivos |
|---|---|---|
| RF-01 | Para solicitudes incluidas en el perfil de carga y el entorno de referencia aprobados, el módulo deberá completar el cálculo en un tiempo no mayor que `T_max`. | El procedimiento de medición aprobado registra un tiempo menor o igual que `T_max` para el perfil de carga definido. La aceptación queda bloqueada hasta aprobar esos parámetros. |
| RF-02 | El módulo deberá aplicar `B_especial` únicamente cuando el cliente cumpla `C_importante`; en caso contrario, no deberá aplicarlo. | Para entradas equivalentes, el caso elegible incorpora exactamente `B_especial` y el no elegible lo excluye, conforme a la política aprobada. |
| RF-03 | Sin una `P_promoción` activa, el descuento final no deberá superar el precio. Con una promoción activa, solo podrá excederlo dentro de `L_promoción`. | Caso no promocional: `descuentoFinal ≤ precio`. Caso promocional: la excepción está identificada, vigente y dentro de `L_promoción`. |
| RF-04 | Para cada entrada válida, el módulo deberá devolver `total = precio - descuentoFinal`, aplicando las reglas aprobadas y `R_precisión`; para una entrada inválida deberá aplicar `E_inválida`. | El valor devuelto coincide con el oráculo calculado a partir de las políticas aprobadas. Las entradas fuera del dominio producen exactamente `E_inválida`. |

## Supuestos pendientes de confirmación

No se adopta ninguna de las siguientes decisiones como regla vigente.

| ID | Política o dato pendiente | Requisitos afectados |
|---|---|---|
| SP-01 | Valor de `T_max`, perfil de carga, entorno y procedimiento de medición. | RF-01 |
| SP-02 | Equivalencia, si existe, entre “cliente importante” y `esVip`, y criterio de elegibilidad `C_importante`. | RF-02 |
| SP-03 | Naturaleza, magnitud, unidad y orden de aplicación de `B_especial`. | RF-02, RF-04 |
| SP-04 | Identificación, vigencia y límite `L_promoción` de las promociones que permiten exceder el precio. | RF-03, RF-04 |
| SP-05 | Dominio válido de `precio`, `porcentaje` y `esVip`, incluidas condiciones nulas, no numéricas, negativas y límites. | RF-03, RF-04 |
| SP-06 | Confirmación de la fórmula del descuento base y del significado de `porcentaje`. | RF-04 |
| SP-07 | Moneda, precisión y regla `R_precisión`. | RF-04 |
| SP-08 | Respuesta `E_inválida`: rechazo, mensaje, excepción o valor de retorno. | RF-04 |

## Verificación y validación aplicadas

La verificación estática determina si los requisitos y el código son claros, consistentes, completos, trazables y verificables, sin ejecutar el módulo. La validación deberá confirmar con las partes interesadas que las políticas pendientes representan la necesidad de negocio. Esta fase aporta verificación documental; no sustituye esa validación.
