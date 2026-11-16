# Registro y propuesta breve de pull request

Estado verificado: [PR #1](https://github.com/MarceloDarwin/ProyectoUnidadUno/pull/1) abierta, no borrador y sin fusionar. No registra revisores solicitados, comentarios ni aprobaciones en GitHub.

## Identificación

| Elemento | Valor |
|---|---|
| Rama base | `master` |
| Rama origen | `feature/fase-c-inspeccion` |
| Título | Corregir hallazgos de análisis estático y documentar inspección |

## Versión breve propuesta

### Alcance

- Corrige H-01 a H-03: declaraciones `var`, igualdad no estricta y estructuras condicionales sin bloques.
- Registra nueve hallazgos: tres corregidos y seis pendientes.
- Incorpora el análisis final y el acta de revisión asistida.

### Verificación

- Análisis inicial: 5 errores, 0 advertencias y código de salida 1; `evidencias/lint-inicial.txt`.
- Análisis final: 0 errores, 0 advertencias y código de salida 0; `evidencias/lint-final.txt`.
- Trazabilidad: `docs/hallazgos.md` y `docs/revision-pares.md`.
- Revisión estática personal finalizada por Marcelo Darwin Peña Ochoa.

### Riesgos y requisitos pendientes

- El cambio a `esVip === true` deja de activar el beneficio para determinados valores no booleanos. El contrato de entrada SP-05 requiere confirmación.
- H-04 a H-09 y SP-01 a SP-08 permanecen pendientes de aprobación; su relación individual consta en los documentos de requisitos y hallazgos.
- No se implementaron políticas de validación, promociones, límites, precisión o rendimiento.
- No se ejecutaron pruebas funcionales.

## Comentarios técnicos propuestos

### C-01 — `src/descuentos.js:3`

La igualdad estricta elimina la coerción de `esVip == true`. Debe confirmarse si el contrato admite exclusivamente booleanos; determinados valores no booleanos pueden dejar de activar el beneficio. Referencias: H-02 y SP-05.

### C-02 — `src/descuentos.js:6-10`

Cuando `porcentaje > 100`, el flujo registra un mensaje y continúa hasta devolver el total. Antes de modificarlo deben aprobarse la identificación de promociones y la respuesta `E_inválida`. Referencias: H-04, H-07, SP-04 y SP-08.

## Estado de revisión

Marcelo Darwin Peña Ochoa finalizó la revisión estática personal. Codex preparó C-01 y C-02 como asistencia automatizada. Los comentarios no se han publicado y no existe revisión independiente ni aprobación en GitHub.
