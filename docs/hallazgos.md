# Hallazgos de inspección

## Roles

| Rol | Asignación | Responsabilidad |
|---|---|---|
| Autor y responsable de la revisión personal | Marcelo Darwin Peña Ochoa. La autoría del código base docente no se atribuye. | Consolidar los resultados y cerrar la revisión estática personal. |
| Revisor independiente | No participó. | No se atribuye aprobación independiente. |
| Asistencia y registro | Codex, asistencia automatizada. | Registrar evidencia y aplicar correcciones autorizadas; no emite aprobación independiente. |

## Criterio de severidad

- **Alta:** puede producir importes inválidos o incumplir una restricción funcional.
- **Media:** puede alterar el comportamiento por coerción, precisión o falta de criterios de aceptación.
- **Baja:** afecta mantenibilidad o claridad sin impacto funcional demostrado.

## Registro

| ID | Origen | Ubicación | Descripción | Severidad | Evidencia | Acción | Estado |
|---|---|---|---|---|---|---|---|
| H-01 | ESLint | `32eaeff:src/descuentos.js:2,5` | Uso de `var`, con alcance de función, en dos declaraciones. Defecto técnico confirmado. | Baja | `evidencias/lint-inicial.txt`; regla `no-var`. | Usar `let` para la variable reasignada y `const` para la asignación única. | Corregido; verificado por `lint-final.txt`. |
| H-02 | ESLint | `32eaeff:src/descuentos.js:3` | Igualdad no estricta sobre `esVip`; la coerción admite valores no booleanos. Defecto técnico confirmado. | Media | `evidencias/lint-inicial.txt`; regla `eqeqeq`. | Sustituir por `esVip === true` y registrar el cambio para entradas no booleanas. | Corregido; verificado por `lint-final.txt`. |
| H-03 | ESLint | `32eaeff:src/descuentos.js:3-4` | Dos estructuras `if` carecen de bloques explícitos. Defecto técnico confirmado. | Baja | `evidencias/lint-inicial.txt`; regla `curly`. | Incorporar llaves sin cambiar las sentencias controladas. | Corregido; verificado por `lint-final.txt`. |
| H-04 | Inspección manual | `32eaeff:src/descuentos.js:4-6` | Un porcentaje superior a 100 solo genera un mensaje; el cálculo y el retorno continúan. Riesgo potencial porque la respuesta para una entrada inválida no está aprobada. | Alta | `docs/requisitos.md` (RF-03, RF-04, SP-04, SP-08). | Definir la política promocional y `E_inválida` antes de modificar el flujo. | Pendiente de decisión de negocio. |
| H-05 | Inspección manual | `32eaeff:src/descuentos.js:1-5` | No se validan tipo, finitud, signo ni límites de las entradas; JavaScript puede aplicar coerción o propagar `NaN`. Riesgo potencial. | Alta | `docs/requisitos.md` (SP-05); ausencia de validaciones en el código. | Aprobar el dominio de entrada y después implementar su validación. | Pendiente de decisión de negocio. |
| H-06 | Trazabilidad de requisitos | `32eaeff:src/descuentos.js:3` | El incremento fijo de 10 no está respaldado por una política aprobada de elegibilidad, magnitud, unidad u orden de aplicación. | Alta | `docs/requisitos.md` (RF-02, SP-02, SP-03). | Validar `C_importante` y `B_especial` con las partes interesadas antes de cambiar el cálculo. | Regla de negocio pendiente. |
| H-07 | Trazabilidad de requisitos | `32eaeff:src/descuentos.js:2-5` | El código no limita el descuento al precio ni identifica una promoción activa; no puede asegurar RF-03. | Alta | `docs/requisitos.md` (RF-03, SP-04); `docs/matriz-trazabilidad.md` (R-03). | Aprobar la identificación y los límites promocionales antes de implementar el control. | Regla de negocio pendiente. |
| H-08 | Trazabilidad de requisitos | `32eaeff:src/descuentos.js:2-6` | No existe regla de moneda, precisión o redondeo para determinar el resultado aceptable. | Media | `docs/requisitos.md` (RF-04, SP-07). | Aprobar `R_precisión` antes de incorporar redondeo. | Regla de negocio pendiente. |
| H-09 | Trazabilidad de requisitos | `docs/requisitos.md` (RF-01, SP-01) | El rendimiento no puede verificarse mientras `T_max`, la carga, el entorno y el método de medición permanezcan sin aprobación. | Media | Criterio de aceptación de RF-01 bloqueado por SP-01. | Aprobar los parámetros y planificar una medición separada de esta inspección. | Criterio de aceptación pendiente. |

## Impacto semántico

Las comparaciones `esVip == true` y `esVip === true` evalúan igual cuando `esVip` es booleano. Determinados valores no booleanos dejan de activar el beneficio con igualdad estricta. SP-05 no define aún el dominio y no se ejecutaron pruebas funcionales; por tanto, no se afirma equivalencia funcional del módulo.
