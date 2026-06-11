# Tema 15 — Contenido Teórico

> **Título oficial**: Sistemas de gestión de bases de datos relacionales, orientados a objetos y NoSQL: características y componentes. Administración de bases de datos.
>
> **Bloque**: Parte II — Técnico
> **Nivel**: C1 — Técnico Auxiliar TIC, Ayuntamiento de Madrid
> **Versión**: v1.0 — Pendiente validación
> **Fecha generación**: 2026-06-11
> **Fuentes**: Ver tema-15-fuentes.md · **Diagramas**: Ver tema-15-diagramas.md · **Cambios**: Ver tema-15-changelog.md
>
> *Extensión: ~3635 palabras · 12 diagramas SVG embebidos · 4 tipos de callout transversales*

---

## Convenciones del documento

Este tema incluye cuatro tipos de **cajas callout** para facilitar el estudio:

> **[DATO CLAVE EXAMEN]** Información de alta densidad memorística, con alta probabilidad de aparecer en el test oficial.

> **[EJERCICIO RESUELTO]** Problema + solución paso a paso (transacciones, concurrencia, SQL de administración).

> **[EJEMPLO AYTO MADRID]** Aplicación real de la teoría al entorno municipal (Padrón, tributos, expedientes, datos abiertos).

> **[REFERENCIA CRUZADA]** Enlace conceptual a otros temas del temario oficial.

Los términos técnicos se mantienen en su nomenclatura original (SGBD, ACID, NoSQL, sharding…). Las fuentes se referencian con etiquetas breves tipo `[ELMASRI, cap. 21]` — el registro completo está en `tema-15-fuentes.md`.

---

## 1. Concepto de base de datos y SGBD

### 1.1. De los ficheros a las bases de datos

Antes de las bases de datos, las aplicaciones almacenaban su información en **ficheros propios**, lo que provocaba graves problemas [ELMASRI, cap. 1]:
- **Redundancia e inconsistencia**: el mismo dato (p. ej. el domicilio de un ciudadano) se repetía en varios ficheros y podía quedar desactualizado en unos y no en otros.
- **Dificultad de acceso** y dependencia: cada consulta nueva exigía programar a medida; los programas dependían del formato físico de los ficheros.
- **Problemas de integridad, concurrencia y seguridad**: difícil garantizar reglas, accesos simultáneos y permisos.

La **base de datos** resuelve esto con una **colección estructurada, integrada y compartida** de datos, con redundancia controlada, y un software que la gobierna: el SGBD.

### 1.2. Base de datos y Sistema de Gestión de Bases de Datos

Una **base de datos (BD)** es un conjunto de datos **relacionados** entre sí, organizados y almacenados de forma persistente, que modela una parcela del mundo real y se comparte entre múltiples usuarios y aplicaciones. [DATE]

Un **Sistema de Gestión de Bases de Datos (SGBD / DBMS)** es el software que **crea, gestiona y controla** el acceso a la base de datos, actuando de intermediario entre los usuarios/aplicaciones y los datos físicos. Garantiza el acceso **concurrente, seguro, íntegro y eficiente**. [ELMASRI, cap. 1][SILBERSCHATZ-DB, cap. 1]

> **[DATO CLAVE EXAMEN]** La **base de datos** es el conjunto de datos; el **SGBD (DBMS)** es el *software* que la gestiona. No confundirlos: Oracle, PostgreSQL o MySQL son SGBD; el padrón almacenado es la base de datos.

### 1.3. Funciones del SGBD

Las funciones esenciales de un SGBD son [DATE][CONNOLLY-BEGG]:
- **Definición de datos**: describir la estructura (tablas, tipos, restricciones) mediante el **DDL**.
- **Manipulación de datos**: insertar, consultar, modificar y borrar mediante el **DML**.
- **Control**: garantizar **integridad** (reglas y restricciones), **seguridad** (permisos), **concurrencia** (accesos simultáneos) y **recuperación** ante fallos.
- **Diccionario de datos (catálogo)**: almacena los **metadatos** —la descripción de la propia estructura de la base de datos (qué tablas, columnas, tipos, restricciones, usuarios existen)—. Es la "base de datos sobre la base de datos".

> **[DATO CLAVE EXAMEN]** El **diccionario de datos** (o catálogo del sistema) contiene los **metadatos**: la descripción de la estructura de la BD. El SGBD lo consulta para resolver cada operación.

### 1.4. Componentes del SGBD

Internamente, un SGBD se organiza en módulos [SILBERSCHATZ-DB, cap. 1]:
- **Procesador de consultas**: interpreta y **optimiza** las sentencias (genera un *plan de ejecución* eficiente) y las ejecuta.
- **Gestor de transacciones**: garantiza las propiedades **ACID** y el control de concurrencia.
- **Gestor de almacenamiento (motor)**: gestiona los datos en disco, los **índices**, el buffer en memoria y el acceso físico.
- **Gestor del diccionario**: administra los metadatos.

> **[REFERENCIA CRUZADA]** El gestor de almacenamiento se apoya en las **estructuras de datos y la organización de ficheros** (índices B+árbol, organización directa/hash) que se desarrollan en el Tema 13.

### 1.5. Lenguajes de bases de datos

El estándar **SQL** integra varios sublenguajes [ISO-9075]:
- **DDL (Data Definition Language)**: define la estructura — `CREATE`, `ALTER`, `DROP`.
- **DML (Data Manipulation Language)**: manipula los datos — `SELECT`, `INSERT`, `UPDATE`, `DELETE`.
- **DCL (Data Control Language)**: controla el acceso — `GRANT`, `REVOKE`.
- **TCL (Transaction Control Language)**: gestiona las transacciones — `COMMIT`, `ROLLBACK`, `SAVEPOINT`.

> **[DATO CLAVE EXAMEN]** **DDL** define (CREATE/ALTER/DROP), **DML** manipula (SELECT/INSERT/UPDATE/DELETE), **DCL** controla el acceso (GRANT/REVOKE), **TCL** gestiona transacciones (COMMIT/ROLLBACK). Saber a qué grupo pertenece cada sentencia es de alto rendimiento en el test.

> **[REFERENCIA CRUZADA]** El lenguaje SQL en profundidad (estándar ANSI, procedimientos almacenados, disparadores) se desarrolla en el Tema 19.

### 1.6. Roles de usuario

- **Administrador de la base de datos (DBA)**: define la estructura física, gestiona usuarios y permisos, copias de seguridad, rendimiento y disponibilidad.
- **Diseñador**: modela los datos (conceptual, lógico, físico).
- **Programador de aplicaciones**: desarrolla los programas que acceden a la BD.
- **Usuario final**: consulta y actualiza datos a través de las aplicaciones.

---

## 2. Características: transaccionalidad y concurrencia

### 2.1. Transacción y propiedades ACID

Una **transacción** es una **unidad lógica de trabajo** formada por una o varias operaciones que deben ejecutarse como un **todo indivisible**: o se completan todas, o no se aplica ninguna. El ejemplo canónico es una transferencia bancaria (restar de una cuenta y sumar en otra). [SILBERSCHATZ-DB, cap. 17]

Toda transacción debe cumplir las propiedades **ACID** [ACID-HAERDER]:
- **Atomicidad (Atomicity)**: "todo o nada". Si falla cualquier paso, se deshacen (rollback) todos.
- **Consistencia (Consistency)**: la transacción lleva la BD de un estado válido a otro válido, respetando todas las reglas de integridad.
- **Aislamiento (Isolation)**: el resultado de transacciones concurrentes es como si se hubieran ejecutado en serie; una no ve los estados intermedios de otra.
- **Durabilidad (Durability)**: una vez confirmada (commit), el cambio persiste aunque falle el sistema (gracias al log).

> **[DATO CLAVE EXAMEN]** **ACID**: **A**tomicidad (todo o nada), **C**onsistencia (estados válidos), a**I**slamiento (como si fueran en serie), **D**urabilidad (persiste tras el commit). `COMMIT` confirma; `ROLLBACK` deshace.

> **[EJERCICIO RESUELTO]** Una transferencia de 100 € de la cuenta A a la B son dos operaciones: `UPDATE A SET saldo=saldo-100` y `UPDATE B SET saldo=saldo+100`. Si tras la primera el sistema cae, la **atomicidad** garantiza el `ROLLBACK` automático al reiniciar: no puede quedar dinero "desaparecido". Solo cuando ambas tienen éxito se hace `COMMIT`.

### 2.2. Concurrencia: problemas y control

Cuando varias transacciones se ejecutan **a la vez** sobre los mismos datos pueden producirse anomalías si no se controlan [ELMASRI, cap. 21]:
- **Lectura sucia (dirty read)**: una transacción lee datos que otra ha modificado pero aún no ha confirmado (y que luego podría deshacer).
- **Lectura no repetible (non-repeatable read)**: una transacción lee el mismo dato dos veces y obtiene valores distintos porque otra lo modificó en medio.
- **Lectura fantasma (phantom read)**: una consulta repetida devuelve filas nuevas que otra transacción insertó.
- **Actualización perdida (lost update)**: dos transacciones actualizan el mismo dato y una sobrescribe a la otra.

Mecanismos de **control de concurrencia**:
- **Bloqueos (locking)**: una transacción bloquea los datos que usa (compartido para lectura, exclusivo para escritura); el protocolo **2PL (bloqueo en dos fases)** garantiza la seriabilidad. Riesgo: **interbloqueo** entre transacciones.
- **MVCC (control de concurrencia multiversión)**: el SGBD mantiene **varias versiones** de cada dato, de modo que los lectores no bloquean a los escritores ni viceversa (lo usan PostgreSQL y Oracle). [POSTGRES-DOC]

> **[DATO CLAVE EXAMEN]** Anomalías de concurrencia: **lectura sucia** (lee no confirmado), **no repetible** (mismo dato cambia entre lecturas), **fantasma** (aparecen filas nuevas). Control con **bloqueos (2PL)** o **MVCC** (multiversión, lectores no bloquean a escritores).

### 2.3. Niveles de aislamiento

El estándar SQL define cuatro **niveles de aislamiento**, que equilibran consistencia y rendimiento [ISO-9075]:

| Nivel | Lectura sucia | No repetible | Fantasma |
|---|---|---|---|
| **Read Uncommitted** | Posible | Posible | Posible |
| **Read Committed** | Evitada | Posible | Posible |
| **Repeatable Read** | Evitada | Evitada | Posible |
| **Serializable** | Evitada | Evitada | Evitada |

Cuanto mayor el aislamiento, más consistencia pero menos concurrencia (rendimiento). El nivel por defecto suele ser **Read Committed** (Oracle, PostgreSQL).

### 2.4. Recuperación ante fallos

El SGBD garantiza la **durabilidad** y la **atomicidad** ante caídas mediante un **registro de transacciones (log)**: antes de aplicar cambios, anota en el log lo que va a hacer (técnica **WAL, Write-Ahead Logging**). Tras un fallo, usa el log para **rehacer (redo)** las transacciones confirmadas y **deshacer (undo)** las no confirmadas. Los **checkpoints** (puntos de control) acotan cuánto log hay que recorrer. [SILBERSCHATZ-DB, cap. 19]

> **[REFERENCIA CRUZADA]** El registro por diario (journaling) y los mecanismos de tolerancia a fallos del almacenamiento (RAID) que sustentan esta durabilidad se tratan en el Tema 13.

---

## 3. Modelo ANSI/SPARC (arquitectura de tres esquemas)

Para lograr la **independencia de datos**, la arquitectura **ANSI/SPARC** (1975) define **tres niveles de abstracción** [ANSI-SPARC][DATE]:
- **Nivel interno (físico)**: cómo se almacenan realmente los datos (ficheros, índices, organización física). Es el "cómo".
- **Nivel conceptual (lógico)**: la estructura global de toda la base de datos (entidades, relaciones, restricciones), independiente del almacenamiento. Es el "qué".
- **Nivel externo (vistas)**: las distintas **vistas** parciales que cada grupo de usuarios ve de la base de datos, adaptadas a sus necesidades y permisos.

La gran ventaja es la **independencia de datos**:
- **Independencia física**: se puede cambiar el almacenamiento (añadir un índice, mover ficheros) sin afectar al nivel conceptual ni a las aplicaciones.
- **Independencia lógica**: se puede cambiar el esquema conceptual (añadir una tabla o columna) sin afectar a las vistas externas existentes.

> **[DATO CLAVE EXAMEN]** **ANSI/SPARC** = 3 esquemas: **interno** (físico, cómo se almacena), **conceptual** (lógico global, qué datos), **externo** (vistas por usuario). Permite la **independencia de datos**: física (cambiar almacenamiento sin tocar la lógica) y lógica (cambiar la lógica sin tocar las vistas).

> **[EJEMPLO AYTO MADRID]** En la base de datos del Padrón, el nivel **conceptual** define las entidades (habitante, vía, distrito); el nivel **externo** ofrece a la oficina de estadística una vista agregada por distrito y al personal de atención una vista del habitante individual; el nivel **interno** decide los índices y el almacenamiento físico. Añadir un índice por código postal (nivel interno) no obliga a cambiar ninguna aplicación: eso es la independencia física.

---

## 4. Tipologías de SGBD

### 4.1. SGBD jerárquicos

Los datos se organizan en una **estructura de árbol** (relaciones padre-hijo 1:N). Históricos (IBM IMS). Rápidos para consultas que siguen la jerarquía, pero rígidos: una relación N:M es difícil de modelar y la navegación es por punteros. [ELMASRI, cap. 2]

### 4.2. SGBD en red (CODASYL)

Generalizan el modelo jerárquico permitiendo que un hijo tenga **varios padres** (grafo). Más flexibles, pero la programación sigue siendo **navegacional** (el programador recorre punteros), compleja de mantener.

### 4.3. SGBD relacionales

Propuestos por **E. F. Codd (1970)**, son el modelo **dominante**. Los datos se organizan en **tablas (relaciones)** formadas por **filas (tuplas)** y **columnas (atributos)**. Conceptos clave [CODD-1970][DATE]:
- **Clave primaria**: atributo(s) que identifican unívocamente cada fila.
- **Clave ajena (foránea)**: atributo que referencia la clave primaria de otra tabla, estableciendo la **integridad referencial**.
- **Álgebra relacional**: operaciones formales (selección, proyección, unión, **join**) que fundamentan las consultas.
- **SQL** es el lenguaje estándar para definirlas y consultarlas.

Ofrecen integridad, independencia de datos y un lenguaje declarativo potente. Ejemplos: **Oracle, PostgreSQL, MySQL, SQL Server, Db2**.

**Reglas de integridad** del modelo relacional [DATE]:
- **Integridad de entidad**: la clave primaria no puede ser nula ni repetirse.
- **Integridad referencial**: toda clave ajena debe corresponder a una clave primaria existente en la tabla referenciada (o ser nula). Impide "referencias huérfanas" (p. ej. un recibo asociado a un contribuyente que no existe).
- **Restricciones de dominio**: cada atributo solo admite valores de su tipo y de las reglas definidas (`CHECK`, `NOT NULL`, `UNIQUE`).

**Operaciones del álgebra relacional** (fundamento formal de las consultas): **selección** (σ, filtra filas por una condición), **proyección** (π, elige columnas), **unión/intersección/diferencia** (entre tablas compatibles), **producto cartesiano** y, sobre todo, la **reunión (join)**, que combina filas de dos tablas según una condición (la más usada es el *inner join* por igualdad de claves; existen *left/right/full outer join* para conservar filas sin pareja).

> **[DATO CLAVE EXAMEN]** El **modelo relacional** (Codd, 1970) organiza los datos en **tablas** con **clave primaria** (identifica, no nula ni repetida → integridad de entidad) y **clave ajena** (referencia a otra tabla → integridad referencial). El **join** combina tablas por sus claves. Es el modelo dominante y la base de **SQL**.

> **[REFERENCIA CRUZADA]** El **diseño** de bases de datos relacionales (modelo lógico, **normalización**) se desarrolla en el Tema 17; el **modelo conceptual** entidad-relación, en el Tema 16.

### 4.4. SGBD orientados a objetos y objeto-relacionales

- **Orientados a objetos (OODBMS)**: almacenan **objetos** (con atributos y métodos), integrándose de forma natural con los lenguajes OO; útiles para datos complejos (CAD, multimedia), pero poco extendidos.
- **Objeto-relacionales (ORDBMS)**: extienden el modelo relacional con **tipos complejos**, herencia y objetos, manteniendo SQL. Es el enfoque adoptado por Oracle y PostgreSQL (SQL:1999+). [ISO-9075-OR]

> **[REFERENCIA CRUZADA]** Los conceptos de objeto, clase, herencia y método en que se apoyan estos SGBD se desarrollan en el Tema 20 (Programación orientada a objetos).

### 4.5. SGBD NoSQL

Los **NoSQL** ("Not only SQL") renuncian al modelo relacional estricto para ganar **escalabilidad horizontal** y flexibilidad de esquema, en respuesta al **big data** y las aplicaciones web masivas. Tipos principales [SADALAGE-FOWLER]:
- **Clave-valor**: pares clave→valor, acceso ultrarrápido (Redis, DynamoDB).
- **Documental**: documentos JSON/BSON flexibles (MongoDB).
- **Columnar (familias de columnas)**: optimizados para grandes volúmenes y escritura (Cassandra, HBase).
- **De grafos**: nodos y relaciones, ideales para redes y recomendaciones (Neo4j).

Muchos NoSQL siguen el modelo **BASE** (Basically Available, Soft state, Eventual consistency) en lugar de ACID, priorizando la **disponibilidad** y la **consistencia eventual** sobre la consistencia inmediata.

**Teorema CAP (Brewer)**: un sistema distribuido solo puede garantizar **dos** de estas tres propiedades a la vez: **Consistencia**, **Disponibilidad** (Availability) y **tolerancia a Particiones** (Partition tolerance). Como las particiones de red son inevitables en un sistema distribuido, en la práctica se elige entre **consistencia** y **disponibilidad** ante una partición. [CAP-BREWER]

**Resumen de los tipos NoSQL:**

| Tipo | Modelo de datos | Casos de uso típicos | Ejemplo |
|---|---|---|---|
| Clave-valor | Pares clave → valor | Caché, sesiones, acceso ultrarrápido | Redis, DynamoDB |
| Documental | Documentos JSON/BSON | Catálogos, perfiles, esquema flexible | MongoDB |
| Columnar | Familias de columnas | Big data, mucha escritura, series temporales | Cassandra, HBase |
| Grafos | Nodos y relaciones | Redes sociales, recomendaciones, rutas | Neo4j |

**Relacional vs NoSQL:** el relacional aporta esquema rígido, **ACID** e integridad fuerte (ideal para datos estructurados y transacciones, como tributos o nóminas); el NoSQL aporta **esquema flexible** y **escalado horizontal** (ideal para grandes volúmenes, datos semiestructurados y alta disponibilidad). No son excluyentes: muchas organizaciones combinan ambos (persistencia políglota).

> **[DATO CLAVE EXAMEN]** **NoSQL** = no relacional, escala horizontal: **clave-valor** (Redis), **documental** (MongoDB), **columnar** (Cassandra), **grafos** (Neo4j). Muchos siguen **BASE** (consistencia eventual) en vez de ACID. **Teorema CAP**: solo 2 de 3 — **C**onsistencia, **A**vailability (disponibilidad), **P**artición. Relacional = integridad fuerte (ACID); NoSQL = flexibilidad y escala.

### 4.6. SGBD multidimensionales y analítica de datos

Frente al procesamiento **OLTP (transaccional)** —muchas operaciones cortas del día a día (altas, consultas puntuales)—, el procesamiento **OLAP (analítico)** está orientado a **consultas masivas** para el análisis y la toma de decisiones. [KIMBALL-DW][INMON-DW]
- Un **data warehouse (almacén de datos)** consolida datos históricos de varias fuentes para el análisis, separándolo de los sistemas operacionales.
- Los **SGBD multidimensionales / OLAP** organizan los datos en **cubos** con dimensiones (tiempo, territorio, concepto) que permiten agregaciones rápidas (*drill-down*, *roll-up*). El **modelo en estrella** (una tabla de hechos rodeada de dimensiones) es el diseño típico.

> **[DATO CLAVE EXAMEN]** **OLTP** = transaccional, operaciones cortas del día a día (el Padrón en funcionamiento). **OLAP** = analítico, consultas masivas sobre datos históricos (cuadros de mando). El **data warehouse** consolida datos para análisis; se modela en **cubos** y **estrella**.

> **[EJEMPLO AYTO MADRID]** La gestión diaria del Padrón y de los tributos es **OLTP**. Para analizar la evolución demográfica por distrito y año, o cruzar recaudación con población, se construye un **data warehouse** con datos consolidados y se explota con herramientas **OLAP** (cuadros de mando del Ayuntamiento).

---

## 5. Administración de bases de datos

La **administración** (a cargo del **DBA**) abarca todo el ciclo de vida operativo de la base de datos. [CONNOLLY-BEGG][ORACLE-DBA]

### 5.1. Administración de usuarios y seguridad

El SGBD controla **quién** puede hacer **qué** sobre cada objeto, mediante **privilegios** concedidos a usuarios y **roles** (agrupaciones de privilegios). Se gestionan con **DCL**: `GRANT` concede y `REVOKE` retira. Aplica el principio de **mínimo privilegio**. Además, los datos personales obligan a cumplir el **RGPD/LOPDGDD** (minimización, control de acceso, cifrado, registro de accesos). [ISO-9075][RGPD]

> **[EJERCICIO RESUELTO]** `GRANT SELECT ON padron TO rol_atencion;` concede solo **lectura** del padrón al rol de atención al ciudadano; `REVOKE UPDATE ON padron FROM rol_atencion;` garantiza que ese rol no pueda modificar. Conceder por **roles** (no usuario a usuario) simplifica la gestión de miles de empleados.

### 5.2. Administración del almacenamiento

El DBA organiza el almacenamiento físico: **tablespaces** (espacios lógicos sobre ficheros), **índices** (para acelerar las consultas, normalmente B+árbol), y el **particionado** de tablas grandes (por rango de fechas, por territorio) para mejorar el rendimiento y el mantenimiento.

> **[REFERENCIA CRUZADA]** Los índices (B+árbol), la organización de ficheros y los sistemas de almacenamiento subyacentes se tratan en el Tema 13; el almacenamiento y su virtualización, en el Tema 26.

### 5.3. SGBD distribuidos

Una base de datos **distribuida** reparte los datos entre varios nodos/servidores [ELMASRI, cap. 23]:
- **Fragmentación**: dividir una tabla horizontal (por filas) o verticalmente (por columnas).
- **Replicación**: mantener **copias** de los datos en varios nodos (mejora disponibilidad y lectura, complica la consistencia).
- **Sharding**: repartir (particionar) los datos entre nodos según una clave, para **escalar horizontalmente** (típico en NoSQL).

### 5.4. Disponibilidad y alta disponibilidad

La **alta disponibilidad (HA)** busca que el servicio siga operativo ante fallos: **clústeres** de servidores, **replicación** primario-secundario y **conmutación por error (failover)** automática a un nodo de respaldo. Se mide en porcentaje de disponibilidad (p. ej. el "99,99 %"). [ORACLE-DBA]

### 5.5. Copias de seguridad y recuperación

El DBA define la política de **backup**:
- **Completo (full)**: copia toda la base de datos.
- **Incremental / diferencial**: copia solo lo cambiado desde la última copia, ahorrando espacio y tiempo.
- **Recuperación a un punto en el tiempo (PITR, Point-In-Time Recovery)**: combinando una copia con el **log de transacciones** se restaura la BD al instante exacto anterior a un incidente. [POSTGRES-DOC]

> **[DATO CLAVE EXAMEN]** Tipos de copia: **completa** (todo), **incremental/diferencial** (solo lo cambiado). El **PITR** (recuperación a un punto en el tiempo) usa la copia + el **log** para volver al instante previo a un error. El backup es exigencia del **ENS**.

### 5.6. Gobernanza del dato

La **gobernanza** establece las políticas y responsabilidades sobre el dato como activo corporativo: **calidad** (exactitud, completitud), **metadatos**, **ciclo de vida** (retención y borrado), **clasificación** y **protección de datos personales** (RGPD/LOPDGDD). Define roles como el *data steward* y garantiza el cumplimiento normativo. [RGPD][LOPDGDD]

### 5.7. Rendimiento: diagnóstico y resolución de incidencias

El **tuning** (ajuste de rendimiento) parte de analizar las consultas lentas con el **plan de ejecución** (`EXPLAIN`), que muestra cómo el optimizador resuelve la consulta. Las palancas habituales: **crear índices** adecuados, **reescribir consultas** ineficientes, **actualizar estadísticas** del optimizador, ajustar la **memoria/buffer** y revisar bloqueos e interbloqueos. [SILBERSCHATZ-DB]

> **[EJEMPLO AYTO MADRID]** Si la consulta de un ciudadano por DNI en el Padrón tarda demasiado, el DBA revisa el **plan de ejecución**: si detecta un *full table scan* (recorrido completo de millones de filas), crea un **índice** sobre el DNI, que reduce la búsqueda a O(log n). Es la aplicación directa de los índices del Tema 13 a la administración real.

### 5.8. SGBD en la nube (DBaaS)

La **base de datos como servicio (DBaaS)** ofrece SGBD gestionados en la nube (Amazon RDS/Aurora, Azure SQL, Google Cloud SQL):
- **Ventajas**: el proveedor gestiona la infraestructura, las copias, los parches y el escalado; pago por uso; alta disponibilidad y escalado elásticos.
- **Inconvenientes/gobierno**: dependencia del proveedor (*vendor lock-in*), **ubicación de los datos** y cumplimiento (RGPD: datos en la UE), seguridad compartida y costes variables. En el sector público, la decisión debe respetar el **ENS**, el RGPD y los requisitos de soberanía del dato.

> **[REFERENCIA CRUZADA]** Los modelos de servicio en la nube (IaaS/PaaS/SaaS) y sus implicaciones se desarrollan en el Tema 31; la seguridad de la información y el cifrado, en el Tema 32.

---

## Resumen final

Este tema describe los **sistemas de gestión de bases de datos** en tres grandes planos:

1. **Concepto y características** — el **SGBD** como software que gestiona el acceso concurrente, seguro e íntegro a la **base de datos**; sus funciones (DDL/DML/DCL/TCL), su **diccionario de datos** y sus componentes; las **transacciones ACID**, el control de **concurrencia** (bloqueos, MVCC, niveles de aislamiento) y la **recuperación** (log, WAL); y la arquitectura **ANSI/SPARC** de tres esquemas con su **independencia de datos**.
2. **Tipologías** — jerárquicos y en red (históricos), **relacionales** (Codd, dominantes, base de SQL), **objeto-relacionales**, **NoSQL** (clave-valor, documental, columnar, grafos; CAP, BASE) y **multidimensionales/OLAP** (data warehouse).
3. **Administración** — usuarios y seguridad (GRANT/REVOKE, RGPD), almacenamiento (tablespaces, índices, particionado), **distribución** (fragmentación, replicación, sharding), **alta disponibilidad**, **copias de seguridad** (full/incremental, PITR), **gobernanza**, **rendimiento** (índices, plan de ejecución) y **nube (DBaaS)**.

La idea transversal para el C1: el SGBD **protege la integridad y la coherencia de la información compartida** mediante transacciones y control de concurrencia; y su administración en la Administración pública debe garantizar **disponibilidad, copias de seguridad y cumplimiento** del **RGPD/LOPDGDD** y del **ENS**.
