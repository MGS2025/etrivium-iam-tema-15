# Tema 15 — Registro de Fuentes

> **Tema**: 15 — Sistemas de gestión de bases de datos relacionales, orientados a objetos y NoSQL: características y componentes. Administración de bases de datos.
>
> **Bloque**: Parte II — Técnico
> **Estado**: v1.0 — Pendiente validación
> **Fecha**: 2026-06-11
> **Criterio**: todo contenido teórico, diagrama y pregunta de test debe ser trazable a una fuente Tier 1. Las fuentes se citan inline con su ID (p. ej. `[ELMASRI, cap. 21]`).

---

## Fuentes Tier 1 (primarias)

### Teoría general de bases de datos

| ID | Título | Autor / Origen | Edición / Año | Secciones usadas | Referencia |
|---|---|---|---|---|---|
| ELMASRI | Fundamentals of Database Systems | Elmasri, Navathe | 7.ª ed., Pearson, 2016 | Concepto de SGBD, modelo relacional, transacciones, concurrencia, recuperación, BD distribuidas, NoSQL, almacenamiento (cap. 1-25) | ISBN 978-0133970777 |
| SILBERSCHATZ-DB | Database System Concepts | Silberschatz, Korth, Sudarshan | 7.ª ed., McGraw-Hill, 2019 | Arquitectura, transacciones ACID, control de concurrencia, recuperación, BD distribuidas, big data (cap. 1-23) | ISBN 978-0078022159 |
| DATE | An Introduction to Database Systems | C. J. Date | 8.ª ed., Addison-Wesley, 2003 | Modelo relacional, integridad, álgebra relacional, independencia de datos | ISBN 978-0321197849 |
| CONNOLLY-BEGG | Database Systems: A Practical Approach | Connolly, Begg | 6.ª ed., Pearson, 2014 | Ciclo de vida, administración, distribución, data warehouse | ISBN 978-0132943260 |
| CODD-1970 | A Relational Model of Data for Large Shared Data Banks | Edgar F. Codd | Communications of the ACM, 1970 | Fundamento del modelo relacional | doi.org/10.1145/362384.362685 |

### Estándares y arquitectura

| ID | Título | Origen | Año | Secciones usadas | Referencia |
|---|---|---|---|---|---|
| ANSI-SPARC | ANSI/X3/SPARC Three-Schema Architecture | ANSI/SPARC Study Group | 1975 | Arquitectura de tres esquemas: interno, conceptual, externo | ANSI/X3/SPARC DBMS Framework |
| ISO-9075 | ISO/IEC 9075 — SQL:2016 (Database language SQL) | ISO/IEC | 2016, rev. 2023 | DDL, DML, DCL, TCL; tipos; niveles de aislamiento | iso.org/standard/63555.html |
| ISO-9075-OR | ISO/IEC 9075-2 — SQL objeto-relacional | ISO/IEC | 2016 | Tipos estructurados y características objeto-relacionales (SQL:1999+) | iso.org/standard/63556.html |
| ACID-HAERDER | Principles of Transaction-Oriented Database Recovery (definición ACID) | Härder, Reuter | ACM Computing Surveys, 1983 | Origen formal de las propiedades ACID | doi.org/10.1145/289.291 |

### NoSQL, distribución y analítica

| ID | Título | Autor / Origen | Año | Secciones usadas | Referencia |
|---|---|---|---|---|---|
| CAP-BREWER | CAP Theorem (Towards Robust Distributed Systems) | Eric Brewer | 2000 (conjetura); Gilbert-Lynch demostración 2002 | Teorema CAP (consistencia, disponibilidad, particiones) | doi.org/10.1145/564585.564601 |
| SADALAGE-FOWLER | NoSQL Distilled | Sadalage, Fowler | Addison-Wesley, 2012 | Tipos de NoSQL (clave-valor, documental, columnar, grafos), BASE, agregados | ISBN 978-0321826626 |
| MONGODB-DOC | MongoDB Manual | MongoDB Inc. | 2024 | Modelo documental, sharding, réplica set | mongodb.com/docs |
| KIMBALL-DW | The Data Warehouse Toolkit | Ralph Kimball, Margy Ross | 3.ª ed., Wiley, 2013 | Data warehouse, modelo dimensional, OLAP, estrella/copo de nieve | ISBN 978-1118530801 |
| INMON-DW | Building the Data Warehouse | Bill Inmon | 4.ª ed., Wiley, 2005 | Definición de data warehouse corporativo (OLTP vs OLAP) | ISBN 978-0764599446 |

### Productos de referencia (documentación oficial)

| ID | Título | Origen | Uso |
|---|---|---|---|
| ORACLE-DBA | Oracle Database Administrator's Guide | Oracle | Administración: usuarios, tablespaces, RMAN, RAC, alta disponibilidad | docs.oracle.com |
| POSTGRES-DOC | PostgreSQL Documentation | PostgreSQL Global Dev. Group | MVCC, roles/privilegios, PITR, particionado, replicación | postgresql.org/docs |
| MYSQL-DOC | MySQL Reference Manual | Oracle | InnoDB, replicación, backup | dev.mysql.com/doc |

### Normativa aplicable (sector público)

| ID | Título | Origen | Año | Uso |
|---|---|---|---|---|
| RGPD | Reglamento (UE) 2016/679 — Protección de Datos | DOUE | 2016 (aplicación 2018) | Tratamiento de datos personales en BD: minimización, seguridad, derechos | eur-lex.europa.eu/eli/reg/2016/679 |
| LOPDGDD | Ley Orgánica 3/2018 de Protección de Datos y garantía de derechos digitales | BOE | 2018 | Desarrollo nacional del RGPD | boe.es/eli/es/lo/2018/12/05/3 |
| ENS-RD311 | Esquema Nacional de Seguridad (Real Decreto 311/2022) | BOE | 2022 | Seguridad, control de acceso, copias de seguridad de los sistemas de información | boe.es/buscar/doc.php?id=BOE-A-2022-7191 |

---

## Fuentes Tier 2 (secundarias — contraste y referencia rápida)

| ID | Título | Origen | Uso |
|---|---|---|---|
| DB-ENGINES | DB-Engines Ranking | solid IT | Popularidad y clasificación de SGBD por tipo |
| MARTIN-DDIA | Designing Data-Intensive Applications | Martin Kleppmann (O'Reilly, 2017) | Replicación, particionado, consistencia (contraste) |
| DATOS-MADRID | Portal de datos abiertos del Ayuntamiento de Madrid | Ayto. Madrid | Contexto real (Padrón, censo, callejero, tributos) para los casos | datos.madrid.es |

---

## Fuentes Tier 3 — NO utilizadas como cita

- Wikipedia (orientación, NO citada).
- Blogs técnicos, Medium, Stack Overflow.
- Documentación comercial de fabricantes sin valor técnico verificable.

---

## Notas de validación

- [ ] María/Ana revisa correspondencia contenido ↔ fuentes Tier 1.
- [ ] Verificar que las propiedades ACID y los niveles de aislamiento coinciden con ISO 9075 y [ACID-HAERDER].
- [ ] Confirmar el enunciado del teorema CAP y su matización (PACELC) si se incluye.
- [ ] Frontera con el Tema 17 (Diseño de BD, normalización) y el Tema 19 (SQL) — aquí SGBD y administración, allí diseño y lenguaje.
- [ ] Vigencia normativa: RGPD, LOPDGDD y ENS (RD 311/2022).
- [ ] Revisar refs cruzadas a otros temas vs BOAM 10.032 (ver changelog).
