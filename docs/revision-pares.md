# Acta de revisión estática

## Identificación

| Elemento | Registro |
|---|---|
| Autor y responsable | Marcelo Darwin Peña Ochoa |
| Tipo de revisión | Revisión personal con asistencia automatizada |
| Estado | **Revisión estática finalizada** |
| Revisión independiente | No realizada |

## Objetivo y alcance

Verificar los requisitos, la trazabilidad, la inspección de `src/descuentos.js`, las correcciones H-01 a H-03 y las evidencias ESLint. El alcance excluye pruebas funcionales y aprobación de políticas de negocio. La metodología se apoya en Fagan (1976), ISTQB (2024) y Pressman y Maxim (2020); véase `docs/referencias.md`.

## Resultados documentados

| Control | Resultado | Evidencia |
|---|---|---|
| Requisitos | 4 requisitos originales, 4 reformulados y 8 supuestos identificados. | `docs/requisitos.md` |
| Inspección | Checklist de 10 preguntas y matriz con las 6 columnas exigidas. | `docs/checklist.md`; `docs/matriz-trazabilidad.md` |
| Hallazgos | 9 hallazgos: H-01 a H-03 corregidos; H-04 a H-09 conservan su estado registrado. | `docs/hallazgos.md` |
| Análisis estático | 5 errores y 0 advertencias inicialmente; 0 errores y 0 advertencias al finalizar. | `evidencias/lint-inicial.txt`; `evidencias/lint-final.txt` |
| Integridad | Código, configuración, dependencias y evidencias sin cambios durante la consolidación documental. | Comparación con `f42a3c3` |
| Validación funcional | No realizada. | Alcance de la actividad |

## Correcciones realizadas

| Hallazgo | Corrección | Evidencia |
|---|---|---|
| H-01 | Sustitución de `var` por `let` y `const` según reasignación. | `src/descuentos.js:2,9`; regla `no-var` |
| H-02 | Sustitución de igualdad no estricta por `esVip === true`; impacto semántico documentado. | `src/descuentos.js:3`; regla `eqeqeq` |
| H-03 | Incorporación de bloques explícitos en ambas condiciones. | `src/descuentos.js:3-8`; regla `curly` |
| Documentación | Consolidación de requisitos, trazabilidad, roles, referencias y estado de la PR. | Documentos de `docs/` y `README.md` |

## Evidencias utilizadas

- `evidencias/lint-inicial.txt`
- `evidencias/lint-final.txt`
- `docs/requisitos.md`
- `docs/checklist.md`
- `docs/matriz-trazabilidad.md`
- `docs/hallazgos.md`

## Conclusión

**Revisión estática finalizada.** Los requisitos, la trazabilidad, los hallazgos, las correcciones y las evidencias son consistentes con el alcance de la actividad. H-04 a H-09 y SP-01 a SP-08 conservan su estado real en los documentos correspondientes. El resultado final de ESLint acredita conformidad con las reglas configuradas; no demuestra corrección funcional. No se realizó revisión independiente.
