# Matriz de trazabilidad

| ID | Problema | Impacto | Propuesta | Artefacto | Estado |
|---|---|---|---|---|---|
| R-01 | “Rápidamente” carece de métrica y contexto. | Aceptación subjetiva. | Adoptar RF-01 y aprobar `T_max` y condiciones de medición. | `docs/requisitos.md` (RF-01, SP-01); `docs/hallazgos.md` (H-09); `e117284:src/descuentos.js:1-6` | Reformulado; políticas y parámetros pendientes. |
| R-02 | Elegibilidad y beneficio especial indefinidos. | Aplicación inconsistente del beneficio. | Adoptar RF-02 y aprobar `C_importante`, `B_especial` y el dominio de `esVip`. | `docs/requisitos.md` (RF-02, SP-02, SP-03, SP-05); `docs/hallazgos.md` (H-02, H-06); `e117284:src/descuentos.js:1,3` | Reformulado; políticas y parámetros pendientes. |
| R-03 | Excepción promocional sin activación ni límite. | Descuento superior al precio sin criterio verificable. | Adoptar RF-03 y aprobar la política promocional y el dominio de entrada. | `docs/requisitos.md` (RF-03, SP-04, SP-05); `docs/hallazgos.md` (H-04, H-05, H-07); `e117284:src/descuentos.js:2,4-5` | Reformulado; políticas y parámetros pendientes. |
| R-04 | Faltan fórmula aprobada, dominio, precisión, salida y manejo de errores. | Ausencia de oráculo de aceptación. | Adoptar RF-04 y aprobar las políticas de cálculo y respuesta. | `docs/requisitos.md` (RF-04, SP-03 a SP-08); `docs/hallazgos.md` (H-04 a H-08); `e117284:src/descuentos.js:1-6` | Reformulado; políticas y parámetros pendientes. |
