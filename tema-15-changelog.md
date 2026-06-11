# Tema 15 — Changelog

> **Título oficial**: Sistemas de gestión de bases de datos relacionales, orientados a objetos y NoSQL: características y componentes. Administración de bases de datos.

---

## v1.0 — 2026-06-11 — Primera versión

**Estado**: pendiente de validación por María y Ana, y de revisión técnica del IAM (Jesús Cuadrado).

**Motivo**: desarrollo del Tema 15, tercer tema generado desde cero en la serie (tras T13 y T14), replicando la estructura y el formato de los Temas 1 y 11 ya validados.

### Alcance de la v1.0

| Entregable | Cantidad |
|---|---|
| Contenido teórico | ~3.600 palabras · 5 secciones (concepto/SGBD, transacciones y concurrencia, ANSI/SPARC, tipologías, administración) |
| Diagramas SVG inline | 12 (accesibles con `role`/`aria-label`) |
| Banco de preguntas tipo test | 60 preguntas A/B/C con explicación y referencia |
| Casos prácticos | 3 (Padrón/integridad, tributos/administración, datos abiertos/analítica) · 10 puntos cada uno |
| Fuentes Tier 1 | 21 referencias canónicas (Elmasri, Silberschatz-DB, Date, Codd, ISO 9075, CAP-Brewer, Kimball, Oracle/PostgreSQL, RGPD/ENS…) |

### Decisiones de generación

1. **Sin material de cliente**: solo el esqueleto `Test_Prompting/temas junio/15.md`. Desarrollado desde fuentes canónicas de bases de datos, todas referenciadas.
2. **Contexto Ayuntamiento de Madrid** en los casos prácticos (Padrón, tributos, datos abiertos, analítica demográfica).
3. **Frontera con T16, T17 y T19** cuidada: aquí SGBD y administración; el modelo conceptual entidad-relación va al T16, el diseño/normalización al T17 y el lenguaje SQL al T19.
4. **Referencias cruzadas validadas contra BOAM 10.032**: T13 (estructuras/ficheros/índices), T16 (modelo conceptual), T17 (diseño BBDD), T19 (SQL), T20 (POO), T26 (almacenamiento), T31 (cloud), T32 (seguridad). Todas comprobadas.

### Nota de longitud

El contenido quedó en ~3.600 palabras, por debajo de T13/T14. Cubre el temario oficial completo de forma densa; pendiente de expandir puntualmente las secciones que María/Ana o el IAM consideren cortas en la revisión.

### Pendientes para QA / próxima iteración

- **Rebalanceo del test** a ~20/20/20.
- **Verificación ortográfica** con corrector es_ES (cuidado con falsos positivos por términos técnicos en inglés y nombres de producto).

### Origen

Generado el 2026-06-11 en el flujo de trabajo de eTrivium, replicando el patrón de los Temas 1 (v2.1), 11 (v3.2), 13 (v1.0) y 14 (v1.0).
