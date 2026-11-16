# Auditoría estática de un módulo JavaScript de descuentos

Actividad académica de la Unidad 1 de Verificación y Validación de Software. El alcance comprende revisión de requisitos, inspección manual, análisis con ESLint y corrección controlada de defectos técnicos. No comprende pruebas funcionales ni aprobación de reglas de negocio.

## Tecnologías

- Node.js `v24.19.0`
- npm `11.17.0`
- ESLint `v10.15.0`
- Git

## Estructura

```text
src/descuentos.js                    Módulo auditado
docs/requisitos.md                   Requisitos reformulados y políticas pendientes
docs/checklist.md                    Checklist de inspección de requisitos
docs/matriz-trazabilidad.md          Relación entre requisitos, código y estado
docs/analisis-estatico-inicial.md    Configuración y diagnósticos iniciales
docs/hallazgos.md                    Registro de defectos, riesgos y decisiones pendientes
docs/revision-pares.md               Acta de revisión estática personal
docs/preparacion-pull-request.md     Estado y propuesta breve de la pull request
docs/referencias.md                  Fuentes académicas y normativas utilizadas
evidencias/lint-inicial.txt          Salida original de ESLint
evidencias/lint-final.txt            Salida posterior a las correcciones
eslint.config.js                     Reglas de análisis estático
package.json                         Dependencias y script lint
package-lock.json                    Bloqueo reproducible de dependencias
```

## Reproducibilidad

Instalar exactamente las dependencias registradas:

```bash
npm ci
```

Ejecutar únicamente el análisis estático:

```bash
npm run lint
```

## Evidencias

| Análisis | Errores | Advertencias | Código de salida | Evidencia |
|---|---:|---:|---:|---|
| Inicial | 5 | 0 | 1 | `evidencias/lint-inicial.txt` |
| Final | 0 | 0 | 0 | `evidencias/lint-final.txt` |

La ausencia de diagnósticos finales acredita conformidad con las reglas ESLint configuradas, no corrección funcional.

## Requisitos y hallazgos pendientes

Los hallazgos H-04 a H-09 y los supuestos SP-01 a SP-08 requieren aprobación antes de introducir cambios adicionales. SP-05 define el contrato de entrada pendiente y SP-06 comprende la fórmula y el mecanismo de salida.

## Historial y revisión técnica

Consultar el historial completo:

```bash
git log --all --oneline --graph
```

La [pull request #1](https://github.com/MarceloDarwin/ProyectoUnidadUno/pull/1) compara `feature/fase-c-inspeccion` con `master`; permanece abierta y sin fusionar. La revisión estática personal está finalizada y documentada en `docs/revision-pares.md`. No se realizó revisión independiente ni validación funcional.
