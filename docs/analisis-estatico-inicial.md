# Análisis estático inicial

## Configuración

| Regla | Nivel ESLint | Justificación técnica |
|---|---|---|
| `no-var` | Error | Identifica declaraciones con alcance de función y promueve declaraciones con alcance de bloque. |
| `eqeqeq` | Error | Evita conversiones implícitas mediante comparaciones de igualdad estricta. |
| `no-unused-vars` | Error | Detecta declaraciones sin uso que pueden indicar código innecesario u omisiones. |
| `curly` | Error | Exige bloques explícitos para reducir ambigüedad en el flujo de control y errores de mantenimiento. |

La configuración plana limita el análisis a `src/**/*.js`, usa ECMAScript vigente y declara `sourceType: "commonjs"`. No se habilitaron reglas adicionales.

## Ejecución

| Elemento | Resultado |
|---|---|
| Comando | `npm run lint` |
| ESLint | `v10.15.0` |
| Código de salida | `1` |
| Errores | 5 |
| Advertencias | 0 |
| Evidencia | `evidencias/lint-inicial.txt` |

## Diagnósticos

| Ubicación | Regla | Nivel ESLint | Hallazgo |
|---|---|---|---|
| `src/descuentos.js:2:3` | `no-var` | Error | Declaración mediante `var`. |
| `src/descuentos.js:3:13` | `eqeqeq` | Error | Comparación mediante igualdad no estricta. |
| `src/descuentos.js:3:22` | `curly` | Error | Estructura `if` sin bloque explícito. |
| `src/descuentos.js:4:25` | `curly` | Error | Estructura `if` sin bloque explícito. |
| `src/descuentos.js:5:3` | `no-var` | Error | Declaración mediante `var`. |

`no-unused-vars` no produjo diagnósticos. Esta ausencia solo indica que la regla no detectó declaraciones sin uso en el archivo analizado.

## Limitaciones

El análisis evalúa únicamente los patrones cubiertos por las reglas configuradas. No demuestra corrección funcional ni valida reglas de negocio, dominios de entrada, límites promocionales, precisión, rendimiento o resultados de ejecución. Esta delimitación es coherente con el alcance del análisis estático descrito por Ayewah et al. (2008) e ISTQB (2024); véase `docs/referencias.md`.
