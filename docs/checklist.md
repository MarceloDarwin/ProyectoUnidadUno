# Checklist de inspección de requisitos

Alcance: requisitos originales R-01 a R-04, reformulación y trazabilidad de la Fase A. Estados: **Conforme**, **Parcial** y **No conforme**.

| # | Pregunta técnica | Resultado | Observación | Evidencia |
|---:|---|---|---|---|
| 1 | ¿Cada requisito original tiene un identificador único y estable? | Conforme | Los cuatro enunciados están identificados sin duplicidad. | R-01, R-02, R-03 y R-04. |
| 2 | ¿Cada requisito expresa una obligación singular y delimitada? | No conforme | R-03 combina una restricción general con una excepción no definida. | Texto de R-03: “excepto en promociones”. |
| 3 | ¿Los términos cualitativos están definidos sin ambigüedad? | No conforme | “Rápidamente”, “importantes”, “especial” y “correcto” no tienen definición operativa. | Textos de R-01, R-02 y R-04. |
| 4 | ¿El requisito de rendimiento contiene métricas y condiciones reproducibles? | No conforme | Faltan umbral temporal, carga, entorno y método de medición. | R-01; pendiente SP-01. |
| 5 | ¿La regla de cálculo del descuento base está especificada? | No conforme | El código contiene una fórmula, pero los requisitos no la establecen ni la validan como política. | `src/descuentos.js:2`; pendiente SP-06. |
| 6 | ¿La elegibilidad y el beneficio del cliente importante están definidos? | No conforme | No se define quién califica ni cómo se calcula el beneficio. | R-02; pendientes SP-02 y SP-03. |
| 7 | ¿La excepción promocional es consistente y verificable? | No conforme | No se identifican activación, vigencia ni límite de la excepción. | R-03; pendiente SP-04. |
| 8 | ¿El dominio de entradas y sus condiciones límite están especificados? | No conforme | No hay reglas para valores nulos, no numéricos, negativos ni extremos. | R-01 a R-04; pendiente SP-05. |
| 9 | ¿Existe un oráculo que defina salida, precisión y tratamiento de errores? | No conforme | R-04 no determina precisión, redondeo ni respuesta ante entradas inválidas. | R-04; pendientes SP-07 y SP-08. |
| 10 | ¿Existe trazabilidad entre requisito original, reformulación y código? | Conforme | La matriz relaciona cada R-01 a R-04 con su RF correspondiente y con el código; esta relación no acredita conformidad de la implementación. | `docs/matriz-trazabilidad.md`; `src/descuentos.js:1-6`. |
