# Matriz de trazabilidad

| ID | Problema | Impacto | Propuesta | Artefacto | Estado |
|---|---|---|---|---|---|
| R-01 | Rendimiento expresado como “rápidamente”, sin métrica ni contexto. | Aceptación subjetiva. | Adoptar RF-01 y aprobar `T_max` y condiciones de medición. | `docs/requisitos.md` (RF-01, SP-01); `src/descuentos.js:1-6` | Reformulado; parámetros pendientes. |
| R-02 | Elegibilidad y beneficio especial indefinidos. | Aplicación inconsistente del descuento. | Adoptar RF-02 y aprobar `C_importante` y `B_especial`. | `docs/requisitos.md` (RF-02, SP-02, SP-03); `src/descuentos.js:1,3` | Reformulado; parámetros pendientes. |
| R-03 | Excepción promocional sin activación ni límite. | Descuento superior al precio sin criterio verificable. | Adoptar RF-03 y aprobar `P_promoción` y `L_promoción`. | `docs/requisitos.md` (RF-03, SP-04); `src/descuentos.js:2,4-5` | Reformulado; parámetros pendientes. |
| R-04 | Corrección sin fórmula completa, dominio, precisión ni manejo de errores. | Ausencia de oráculo de aceptación. | Adoptar RF-04 y aprobar las políticas de cálculo y respuesta. | `docs/requisitos.md` (RF-04, SP-05 a SP-08); `src/descuentos.js:1-6` | Reformulado; parámetros pendientes. |
