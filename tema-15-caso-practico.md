# Tema 15 — Casos Prácticos

> **Título oficial**: Sistemas de gestión de bases de datos relacionales, orientados a objetos y NoSQL: características y componentes. Administración de bases de datos.
> **Nivel**: C1 — Técnico Auxiliar TIC, Ayuntamiento de Madrid
> **Versión**: v1.0 — Pendiente validación
> **Fecha**: 2026-06-11
> **Formato**: 3 casos prácticos contextualizados al Ayuntamiento de Madrid · cada caso vale 10 puntos
> **Fuentes**: ver tema-15-fuentes.md

---

## Caso 1 — Integridad y concurrencia en la base de datos del Padrón

### Enunciado

La base de datos del Padrón Municipal registra a los habitantes (tabla HABITANTE) y los distritos (tabla DISTRITO). Varios empleados realizan altas, bajas y cambios de domicilio **a la vez**. Se ha detectado que, en algún caso, un cambio quedó a medias y que dos empleados modificaron el mismo registro pisándose. Como técnico, debe garantizar la coherencia de los datos.

### Cuestiones

**Cuestión 1 — Integridad referencial (3 puntos).** Cada habitante tiene un campo `distrito_id`. ¿Qué mecanismo del modelo relacional impide que un habitante quede asignado a un distrito inexistente, y cómo se llaman las claves implicadas?

**Cuestión 2 — Transacciones (3 puntos).** Un cambio de domicilio implica actualizar varias tablas. Si el sistema cae a mitad, ¿qué propiedad garantiza que no quede "a medias" y mediante qué sentencias se confirma o se deshace?

**Cuestión 3 — Concurrencia (2 puntos).** Dos empleados modifican el mismo registro a la vez y uno sobrescribe al otro. ¿Cómo se llama esa anomalía y qué dos técnicas usa el SGBD para controlar la concurrencia?

**Cuestión 4 — Durabilidad (2 puntos).** Una vez confirmada un alta, ¿qué garantiza que no se pierda aunque el servidor se apague justo después, y gracias a qué elemento?

### Solución orientativa

- **C1**: la **integridad referencial**: `distrito_id` es una **clave ajena (foránea)** que debe corresponder a la **clave primaria** `id` de DISTRITO; el SGBD rechaza un habitante con un distrito inexistente. *(§4.3)*
- **C2**: la **atomicidad** ("todo o nada"): las actualizaciones se agrupan en una **transacción**; si algo falla, `ROLLBACK` deshace todo; si todo va bien, `COMMIT` confirma. *(§2.1)*
- **C3**: es una **actualización perdida (lost update)**; el SGBD la controla con **bloqueos** (2PL) o con **MVCC** (multiversión). *(§2.2)*
- **C4**: la **durabilidad**: tras el `COMMIT`, el cambio persiste pese a un corte, gracias al **log de transacciones** (write-ahead logging). *(§2.1, §2.4)*

### Criterios de evaluación

| Aspecto | Puntos |
|---|---|
| Identifica la integridad referencial y las claves primaria/ajena | 3 |
| Explica la atomicidad y el uso de COMMIT/ROLLBACK | 3 |
| Reconoce la actualización perdida y cita bloqueos/MVCC | 2 |
| Explica la durabilidad apoyada en el log | 2 |

---

## Caso 2 — Administración y rendimiento de la base de datos de tributos

### Enunciado

La base de datos de tributos (IBI, tasas) responde con lentitud al consultar un recibo por NIF, y se necesita reforzar la seguridad de acceso y la política de copias. Como administrador (DBA), debe diagnosticar y proponer medidas.

### Cuestiones

**Cuestión 1 — Rendimiento (3 puntos).** La consulta de un recibo por NIF tarda demasiado. ¿Qué herramienta usaría para ver cómo el SGBD resuelve la consulta y qué medida aplicaría si detecta un recorrido completo de la tabla?

**Cuestión 2 — Seguridad de acceso (3 puntos).** El personal de atención solo debe poder consultar (no modificar) los recibos. ¿Mediante qué sublenguaje y sentencias lo configuraría, y por qué conviene usar roles?

**Cuestión 3 — Copias de seguridad (2 puntos).** Defina una política de copias que permita restaurar la base de datos al instante exacto anterior a un borrado accidental. ¿Cómo se llama esa capacidad y qué necesita?

**Cuestión 4 — Protección de datos (2 puntos).** Los recibos contienen datos personales. ¿Qué normativa obliga a controlar el acceso, registrar los accesos y proteger la información?

### Solución orientativa

- **C1**: el **plan de ejecución** (`EXPLAIN`) muestra cómo se resuelve la consulta; si hace un **recorrido completo de tabla** (full table scan), se **crea un índice** sobre el NIF, que reduce la búsqueda a O(log n). *(§5.7, §5.2)*
- **C2**: con **DCL**: `GRANT SELECT ON recibos TO rol_atencion;` (solo lectura) y nunca `GRANT UPDATE`; conviene usar **roles** porque asignar privilegios a un rol y el rol a los empleados simplifica la gestión de miles de usuarios y aplica el mínimo privilegio. *(§5.1)*
- **C3**: la **recuperación a un punto en el tiempo (PITR)**: combina una **copia de seguridad** con el **log de transacciones** para restaurar al instante justo anterior al borrado. *(§5.5)*
- **C4**: el **RGPD** y la **LOPDGDD** (y el **ENS**) obligan a controlar y registrar los accesos, minimizar y proteger los datos personales. *(§5.1, §5.6 [RGPD][LOPDGDD])*

### Criterios de evaluación

| Aspecto | Puntos |
|---|---|
| Usa el plan de ejecución y propone crear un índice | 3 |
| Configura DCL (GRANT SELECT) y justifica los roles | 3 |
| Propone PITR (copia + log) | 2 |
| Cita RGPD/LOPDGDD/ENS para los datos personales | 2 |

---

## Caso 3 — Elección de tecnología para los datos abiertos y la analítica

### Enunciado

El Ayuntamiento quiere: (a) mantener su gestión transaccional (Padrón, tributos) con garantías de integridad; (b) construir un sistema de **análisis** de la evolución demográfica y la recaudación por distrito y año; y (c) valorar publicar parte de los datos en una base de datos en la **nube**. Debe asesorar sobre la tecnología.

### Cuestiones

**Cuestión 1 — Gestión transaccional (2 puntos).** Para la gestión diaria con máxima integridad, ¿qué tipo de SGBD y qué tipo de procesamiento son los adecuados?

**Cuestión 2 — Analítica (3 puntos).** Para analizar la evolución por distrito y año cruzando varias fuentes, ¿qué infraestructura y qué tipo de procesamiento usaría, y cómo se llama el modelo de diseño típico?

**Cuestión 3 — NoSQL y CAP (3 puntos).** Si se optara por una base de datos distribuida NoSQL para un servicio web masivo, explique el compromiso que impone el **teorema CAP** y qué modelo (frente a ACID) suelen seguir estos sistemas.

**Cuestión 4 — Nube (2 puntos).** Antes de contratar una base de datos en la nube (DBaaS) con datos de ciudadanos, ¿qué dos cautelas debe valorar la Administración?

### Solución orientativa

- **C1**: un **SGBD relacional** (Oracle, PostgreSQL…) con procesamiento **OLTP**, que garantiza integridad y **ACID** para las operaciones transaccionales del día a día. *(§4.3, §4.6)*
- **C2**: un **data warehouse** alimentado desde las fuentes operacionales, explotado con procesamiento **OLAP** (cubos); el diseño típico es el **modelo en estrella** (tabla de hechos rodeada de dimensiones: tiempo, distrito, concepto). *(§4.6)*
- **C3**: el **teorema CAP** establece que, ante una **partición** de red (inevitable en un sistema distribuido), hay que elegir entre **consistencia** y **disponibilidad**; estos sistemas suelen seguir el modelo **BASE** (consistencia eventual) en lugar de ACID. *(§4.5)*
- **C4**: la **ubicación de los datos** y el cumplimiento del **RGPD** (datos en la UE, soberanía del dato) y del **ENS**, y el riesgo de **dependencia del proveedor (vendor lock-in)**. *(§5.8)*

### Criterios de evaluación

| Aspecto | Puntos |
|---|---|
| Propone SGBD relacional + OLTP con ACID para la gestión | 2 |
| Propone data warehouse + OLAP + modelo en estrella | 3 |
| Explica el compromiso CAP y el modelo BASE | 3 |
| Cita ubicación de datos/RGPD-ENS y vendor lock-in | 2 |

---

## Nota pedagógica

Los tres casos integran las tres partes del tema sobre supuestos reales del Ayuntamiento: el **Caso 1**, las **características** (integridad, transacciones ACID, concurrencia) sobre el Padrón; el **Caso 2**, la **administración** (rendimiento e índices, seguridad DCL, copias/PITR, RGPD) sobre los tributos; y el **Caso 3**, las **tipologías** (relacional/OLTP, OLAP/data warehouse, NoSQL/CAP) y la **nube** para datos abiertos y analítica. Todos enlazan con el cumplimiento del **RGPD/LOPDGDD** y del **ENS**.
