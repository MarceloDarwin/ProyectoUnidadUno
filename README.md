# Auditoría estática de un módulo JavaScript de descuentos

Proyecto académico de Verificación y Validación de Software para revisar requisitos, inspeccionar código, registrar hallazgos y aplicar correcciones técnicas controladas sin ejecutar pruebas funcionales.

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
docs/revision-pares.md               Seguimiento y revisión humana pendiente
docs/preparacion-pull-request.md     Propuesta local de revisión técnica
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

Las salidas completas están en `evidencias/lint-inicial.txt` y `evidencias/lint-final.txt`.

## Requisitos y hallazgos pendientes

Las políticas SP-01 a SP-08 están registradas en `docs/requisitos.md`. Los hallazgos H-04 a H-09 y el impacto de la igualdad estricta sobre entradas no booleanas requieren aprobación humana antes de introducir cambios adicionales.

## Historial y revisión técnica

Consultar el historial completo:

```bash
git log --all --oneline --graph
```

La revisión técnica y sus limitaciones están documentadas en `docs/revision-pares.md`. La propuesta local de pull request está en `docs/preparacion-pull-request.md`; no constituye una revisión humana aprobada.
