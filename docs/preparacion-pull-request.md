# Propuesta local de pull request

Estado: borrador no publicado. Preparado mediante asistencia automatizada de Codex; la revisión y aprobación humanas permanecen pendientes.

## Identificación

| Elemento | Valor |
|---|---|
| Rama base | `master` |
| Rama origen | `feature/fase-c-inspeccion` |
| Título | Corregir hallazgos de análisis estático y documentar inspección |

## Descripción propuesta

### Alcance

- Corrige H-01 a H-03: declaraciones `var`, igualdad no estricta y estructuras condicionales sin bloques.
- Registra nueve hallazgos diferenciados y conserva H-04 a H-09 como pendientes.
- Incorpora el resultado final de ESLint y el seguimiento para revisión por pares.

### Verificación

- Análisis inicial: `evidencias/lint-inicial.txt`.
- Análisis final: `evidencias/lint-final.txt`, código de salida 0, sin diagnósticos.
- Trazabilidad: `docs/hallazgos.md` y `docs/revision-pares.md`.

### Riesgos y requisitos pendientes

- El cambio a `esVip === true` deja de aceptar valores no booleanos que antes podían cumplir la comparación por coerción. El contrato de entrada SP-05 requiere confirmación.
- H-04 a H-09 dependen de SP-01 a SP-08; no se implementaron políticas de validación, promociones, límites, precisión o rendimiento.
- `evidencias/lint-inicial.txt` contiene una ruta absoluta del entorno local y el historial registra un correo de autor distinto de GitHub `noreply`. El propietario autorizó conservar ambos datos sin anonimización ni reescritura del historial.
- No se ejecutaron pruebas funcionales.

## Comentarios técnicos propuestos

### C-01 — `src/descuentos.js:3`

La igualdad estricta elimina la coerción presente en `esVip == true`. Debe confirmarse que el contrato admite exclusivamente booleanos; de lo contrario, valores no booleanos pueden cambiar de comportamiento. Referencias: H-02 y SP-05.

### C-02 — `src/descuentos.js:6-10`

Cuando `porcentaje > 100`, el flujo registra un mensaje y continúa hasta devolver el total. Antes de modificarlo deben aprobarse la identificación de promociones y la respuesta `E_inválida`. Referencias: H-04, H-07, SP-04 y SP-08.

## Limitaciones del acta asistida

La revisión automatizada comprueba reglas configuradas, consistencia documental y trazabilidad local. No valida intención de negocio, corrección funcional ni equivalencia para entradas no booleanas. Ningún comentario se ha publicado y no existe aprobación humana registrada.
