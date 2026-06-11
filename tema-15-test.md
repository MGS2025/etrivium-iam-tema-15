# Tema 15 — Test de Autoevaluación

> **Título**: Sistemas de gestión de bases de datos relacionales, orientados a objetos y NoSQL: características y componentes. Administración de bases de datos.
> **Formato**: 60 preguntas tipo test A/B/C (formato oficial oposición)
> **Nivel**: C1 — Técnico Auxiliar TIC, Ayuntamiento de Madrid
> **Versión**: v1.0 — Pendiente validación
> **Fecha**: 2026-06-11
> **Fuentes**: ver tema-15-fuentes.md

---

## Instrucciones

- Cada pregunta tiene **3 opciones** (A, B, C). Solo una es correcta.
- Penalización en examen real: respuesta incorrecta descuenta **1/3** del valor de una correcta.
- Tiempo orientativo: 1 minuto por pregunta.
- Distribución: Concepto/SGBD (P1-P10), Transacciones y concurrencia (P11-P22), ANSI/SPARC (P23-P26), Tipologías (P27-P42), Administración (P43-P60).

---

### Pregunta 1

**¿Cuál es la diferencia entre una base de datos y un SGBD?**

A) La base de datos es el conjunto de datos; el SGBD es el software que la gestiona
B) Son lo mismo
C) El SGBD es el conjunto de datos; la base de datos es el hardware

<details><summary>Respuesta</summary>

**Correcta: A) La base de datos es el conjunto de datos; el SGBD es el software que la gestiona** La **base de datos** es el conjunto de datos; el **SGBD** (Oracle, PostgreSQL…) es el software que la gestiona.

*Referencia: §1.2 [ELMASRI]*
</details>

---

### Pregunta 2

**El principal problema del almacenamiento en ficheros propios por aplicación es:**

A) La redundancia e inconsistencia de los datos
B) Que ocupan poco espacio
C) Que son demasiado rápidos

<details><summary>Respuesta</summary>

**Correcta: A) La redundancia e inconsistencia de los datos** Los ficheros aislados duplican datos (redundancia) que pueden quedar inconsistentes entre aplicaciones; la BD los integra.

*Referencia: §1.1*
</details>

---

### Pregunta 3

**El diccionario de datos (catálogo) de un SGBD contiene:**

A) Las copias de seguridad
B) Solo los datos de los usuarios
C) Los metadatos: la descripción de la estructura de la base de datos

<details><summary>Respuesta</summary>

**Correcta: C) Los metadatos: la descripción de la estructura de la base de datos** El **diccionario de datos** almacena los **metadatos** (tablas, columnas, tipos, restricciones, usuarios): la descripción de la propia BD.

*Referencia: §1.3*
</details>

---

### Pregunta 4

**La sentencia `CREATE TABLE` pertenece al sublenguaje:**

A) DML
B) DCL
C) DDL

<details><summary>Respuesta</summary>

**Correcta: C) DDL** `CREATE`, `ALTER` y `DROP` son **DDL** (definición). El DML manipula datos; el DCL controla el acceso.

*Referencia: §1.5 [ISO-9075]*
</details>

---

### Pregunta 5

**Las sentencias `SELECT`, `INSERT`, `UPDATE` y `DELETE` forman parte del:**

A) DDL
B) TCL
C) DML (lenguaje de manipulación de datos)

<details><summary>Respuesta</summary>

**Correcta: C) DML (lenguaje de manipulación de datos)** Son **DML** (manipulación de datos). El DDL define la estructura; el TCL gestiona transacciones.

*Referencia: §1.5*
</details>

---

### Pregunta 6

**Las sentencias `GRANT` y `REVOKE` pertenecen al:**

A) DCL (control de acceso)
B) DDL
C) DML

<details><summary>Respuesta</summary>

**Correcta: A) DCL (control de acceso)** `GRANT` y `REVOKE` son **DCL**: conceden y retiran privilegios a usuarios y roles.

*Referencia: §1.5, §5.1*
</details>

---

### Pregunta 7

**`COMMIT` y `ROLLBACK` pertenecen al:**

A) DDL
B) DCL
C) TCL (control de transacciones)

<details><summary>Respuesta</summary>

**Correcta: C) TCL (control de transacciones)** `COMMIT` (confirma) y `ROLLBACK` (deshace) son **TCL**, el control de transacciones.

*Referencia: §1.5, §2.1*
</details>

---

### Pregunta 8

**El componente del SGBD que genera el plan de ejecución eficiente de una consulta es:**

A) El gestor de almacenamiento
B) El procesador de consultas (optimizador)
C) El diccionario de datos

<details><summary>Respuesta</summary>

**Correcta: B) El procesador de consultas (optimizador)** El **procesador de consultas** interpreta y **optimiza** las sentencias generando un plan de ejecución eficiente.

*Referencia: §1.4*
</details>

---

### Pregunta 9

**El rol responsable de la estructura física, los permisos, las copias y el rendimiento de la BD es:**

A) El usuario final
B) El administrador de la base de datos (DBA)
C) El programador de aplicaciones

<details><summary>Respuesta</summary>

**Correcta: B) El administrador de la base de datos (DBA)** El **DBA** administra la estructura física, los usuarios, las copias de seguridad, la disponibilidad y el rendimiento.

*Referencia: §1.6*
</details>

---

### Pregunta 10

**Una función de control esencial del SGBD es:**

A) Garantizar integridad, seguridad, concurrencia y recuperación
B) Compilar el sistema operativo
C) Fabricar el hardware de almacenamiento

<details><summary>Respuesta</summary>

**Correcta: A) Garantizar integridad, seguridad, concurrencia y recuperación** El SGBD controla **integridad, seguridad, concurrencia y recuperación** ante fallos.

*Referencia: §1.3*
</details>

---

### Pregunta 11

**Una transacción se define como:**

A) Una copia de seguridad
B) Un índice de la base de datos
C) Una unidad lógica de trabajo indivisible (todo o nada)

<details><summary>Respuesta</summary>

**Correcta: C) Una unidad lógica de trabajo indivisible (todo o nada)** La **transacción** es una unidad lógica de trabajo que se ejecuta como un todo indivisible: o todo, o nada.

*Referencia: §2.1 [SILBERSCHATZ-DB]*
</details>

---

### Pregunta 12

**¿Qué significa la "A" de ACID?**

A) Acceso
B) Análisis
C) Atomicidad (todo o nada)

<details><summary>Respuesta</summary>

**Correcta: C) Atomicidad (todo o nada)** **A** = **Atomicidad**: si falla cualquier paso, se deshacen todos (rollback). ACID = Atomicidad, Consistencia, Aislamiento, Durabilidad.

*Referencia: §2.1 [ACID-HAERDER]*
</details>

---

### Pregunta 13

**La propiedad ACID que garantiza que un cambio confirmado persiste aunque caiga el sistema es:**

A) Atomicidad
B) Aislamiento
C) Durabilidad

<details><summary>Respuesta</summary>

**Correcta: C) Durabilidad** La **durabilidad** garantiza que, tras el `COMMIT`, el cambio persiste pese a fallos, gracias al log de transacciones.

*Referencia: §2.1*
</details>

---

### Pregunta 14

**La propiedad ACID que evita que una transacción vea los estados intermedios de otra concurrente es:**

A) Consistencia
B) Aislamiento
C) Durabilidad

<details><summary>Respuesta</summary>

**Correcta: B) Aislamiento** El **aislamiento** hace que el resultado de transacciones concurrentes sea como si se ejecutaran en serie.

*Referencia: §2.1*
</details>

---

### Pregunta 15

**Leer datos que otra transacción ha modificado pero aún no ha confirmado es una anomalía llamada:**

A) Lectura no repetible
B) Lectura sucia (dirty read)
C) Actualización perdida

<details><summary>Respuesta</summary>

**Correcta: B) Lectura sucia (dirty read)** La **lectura sucia** lee datos no confirmados que podrían deshacerse después.

*Referencia: §2.2*
</details>

---

### Pregunta 16

**El control de concurrencia en el que el SGBD mantiene varias versiones de cada dato, de modo que los lectores no bloquean a los escritores, es:**

A) Bloqueo en dos fases (2PL)
B) MVCC (control multiversión)
C) WAL

<details><summary>Respuesta</summary>

**Correcta: B) MVCC (control multiversión)** El **MVCC** mantiene varias versiones; los lectores no bloquean a los escritores (lo usan PostgreSQL y Oracle).

*Referencia: §2.2 [POSTGRES-DOC]*
</details>

---

### Pregunta 17

**El nivel de aislamiento SQL que evita todas las anomalías (sucia, no repetible y fantasma) es:**

A) Serializable
B) Read Committed
C) Repeatable Read

<details><summary>Respuesta</summary>

**Correcta: A) Serializable** **Serializable** es el nivel más alto: evita lectura sucia, no repetible y fantasma, a costa de menos concurrencia.

*Referencia: §2.3 [ISO-9075]*
</details>

---

### Pregunta 18

**La técnica por la que el SGBD anota en un log lo que va a hacer antes de aplicarlo se denomina:**

A) Sharding
B) Write-Ahead Logging (WAL)
C) Normalización

<details><summary>Respuesta</summary>

**Correcta: B) Write-Ahead Logging (WAL)** El **WAL** (registro anticipado) anota los cambios en el log antes de aplicarlos, permitiendo redo/undo tras un fallo.

*Referencia: §2.4 [SILBERSCHATZ-DB]*
</details>

---

### Pregunta 19

**Tras un fallo, el SGBD usa el log para:**

A) Borrar la base de datos
B) Crear nuevos usuarios
C) Rehacer (redo) las transacciones confirmadas y deshacer (undo) las no confirmadas

<details><summary>Respuesta</summary>

**Correcta: C) Rehacer (redo) las transacciones confirmadas y deshacer (undo) las no confirmadas** La recuperación **rehace** las confirmadas y **deshace** las no confirmadas, garantizando atomicidad y durabilidad.

*Referencia: §2.4*
</details>

---

### Pregunta 20

**El protocolo de bloqueo que garantiza la seriabilidad de las transacciones es:**

A) El sharding
B) El bloqueo en dos fases (2PL)
C) El modelo en estrella

<details><summary>Respuesta</summary>

**Correcta: B) El bloqueo en dos fases (2PL)** El **2PL (bloqueo en dos fases)** garantiza la seriabilidad; su riesgo es el interbloqueo entre transacciones.

*Referencia: §2.2*
</details>

---

### Pregunta 21

**La propiedad ACID de consistencia significa que:**

A) Los datos se replican en varios nodos
B) Las consultas son rápidas
C) La transacción lleva la BD de un estado válido a otro válido, respetando la integridad

<details><summary>Respuesta</summary>

**Correcta: C) La transacción lleva la BD de un estado válido a otro válido, respetando la integridad** La **consistencia** garantiza que la transacción respeta todas las reglas de integridad, pasando de un estado válido a otro.

*Referencia: §2.1*
</details>

---

### Pregunta 22

**Una lectura fantasma (phantom read) se produce cuando:**

A) Una consulta repetida devuelve filas nuevas insertadas por otra transacción
B) Se borra la base de datos
C) Se pierde la conexión

<details><summary>Respuesta</summary>

**Correcta: A) Una consulta repetida devuelve filas nuevas insertadas por otra transacción** La **lectura fantasma** aparece cuando una consulta repetida ve filas nuevas insertadas por otra transacción. La evita el nivel Serializable.

*Referencia: §2.2, §2.3*
</details>

---

### Pregunta 23

**La arquitectura ANSI/SPARC define tres esquemas:**

A) Primario, secundario y terciario
B) DDL, DML y DCL
C) Interno, conceptual y externo

<details><summary>Respuesta</summary>

**Correcta: C) Interno, conceptual y externo** **ANSI/SPARC**: nivel **interno** (físico), **conceptual** (lógico global) y **externo** (vistas).

*Referencia: §3 [ANSI-SPARC]*
</details>

---

### Pregunta 24

**Poder añadir un índice (cambio de almacenamiento) sin afectar a las aplicaciones es un ejemplo de:**

A) Independencia lógica de datos
B) Independencia física de datos
C) Replicación

<details><summary>Respuesta</summary>

**Correcta: B) Independencia física de datos** La **independencia física** permite cambiar el nivel interno (índices, ficheros) sin afectar al conceptual ni a las aplicaciones.

*Referencia: §3*
</details>

---

### Pregunta 25

**El nivel externo de ANSI/SPARC corresponde a:**

A) El almacenamiento físico
B) El log de transacciones
C) Las vistas parciales adaptadas a cada grupo de usuarios

<details><summary>Respuesta</summary>

**Correcta: C) Las vistas parciales adaptadas a cada grupo de usuarios** El **nivel externo** son las **vistas**: lo que cada grupo de usuarios ve de la BD, según sus necesidades y permisos.

*Referencia: §3*
</details>

---

### Pregunta 26

**El nivel conceptual de ANSI/SPARC describe:**

A) Cómo se almacenan físicamente los datos
B) Solo los índices
C) La estructura lógica global de toda la base de datos

<details><summary>Respuesta</summary>

**Correcta: C) La estructura lógica global de toda la base de datos** El **nivel conceptual** describe la estructura lógica global (entidades, relaciones, restricciones), independiente del almacenamiento.

*Referencia: §3*
</details>

---

### Pregunta 27

**El modelo de datos dominante, propuesto por Codd en 1970, es:**

A) El jerárquico
B) El relacional (tablas)
C) El de grafos

<details><summary>Respuesta</summary>

**Correcta: B) El relacional (tablas)** El **modelo relacional** (Codd, 1970) organiza los datos en tablas y es el dominante; es la base de SQL.

*Referencia: §4.3 [CODD-1970]*
</details>

---

### Pregunta 28

**En el modelo relacional, el atributo que referencia la clave primaria de otra tabla es:**

A) El índice
B) La clave ajena (foránea)
C) La vista

<details><summary>Respuesta</summary>

**Correcta: B) La clave ajena (foránea)** La **clave ajena (foránea)** referencia la clave primaria de otra tabla, estableciendo la integridad referencial.

*Referencia: §4.3*
</details>

---

### Pregunta 29

**La integridad de entidad exige que la clave primaria:**

A) Pueda ser nula
B) Cambie en cada consulta
C) No sea nula ni se repita

<details><summary>Respuesta</summary>

**Correcta: C) No sea nula ni se repita** La **integridad de entidad**: la clave primaria no puede ser nula ni repetirse (identifica unívocamente cada fila).

*Referencia: §4.3 [DATE]*
</details>

---

### Pregunta 30

**La operación del álgebra relacional que combina filas de dos tablas según una condición es:**

A) La reunión (join)
B) La proyección
C) La selección

<details><summary>Respuesta</summary>

**Correcta: A) La reunión (join)** El **join (reunión)** combina filas de dos tablas según una condición (normalmente la igualdad de claves).

*Referencia: §4.3*
</details>

---

### Pregunta 31

**Un SGBD que extiende el modelo relacional con tipos complejos, herencia y objetos, manteniendo SQL, es:**

A) Jerárquico
B) Clave-valor
C) Objeto-relacional

<details><summary>Respuesta</summary>

**Correcta: C) Objeto-relacional** El **objeto-relacional (ORDBMS)** extiende el relacional con objetos manteniendo SQL (Oracle, PostgreSQL, SQL:1999+).

*Referencia: §4.4 [ISO-9075-OR]*
</details>

---

### Pregunta 32

**Las bases de datos NoSQL se caracterizan por:**

A) Ser siempre relacionales
B) Renunciar al modelo relacional estricto para ganar escalabilidad horizontal y flexibilidad de esquema
C) No poder almacenar grandes volúmenes

<details><summary>Respuesta</summary>

**Correcta: B) Renunciar al modelo relacional estricto para ganar escalabilidad horizontal y flexibilidad de esquema** **NoSQL** ("Not only SQL") gana escalabilidad horizontal y esquema flexible, en respuesta al big data.

*Referencia: §4.5 [SADALAGE-FOWLER]*
</details>

---

### Pregunta 33

**MongoDB es un ejemplo de base de datos NoSQL de tipo:**

A) Documental
B) Clave-valor
C) Grafos

<details><summary>Respuesta</summary>

**Correcta: A) Documental** **MongoDB** es **documental** (documentos JSON/BSON). Redis es clave-valor; Neo4j, de grafos.

*Referencia: §4.5 [MONGODB-DOC]*
</details>

---

### Pregunta 34

**Neo4j es una base de datos NoSQL de tipo:**

A) Columnar
B) De grafos
C) Documental

<details><summary>Respuesta</summary>

**Correcta: B) De grafos** **Neo4j** es de **grafos** (nodos y relaciones), ideal para redes y recomendaciones.

*Referencia: §4.5*
</details>

---

### Pregunta 35

**El teorema CAP afirma que un sistema distribuido solo puede garantizar a la vez:**

A) Las tres propiedades C, A y P
B) Dos de las tres: Consistencia, Disponibilidad y tolerancia a Particiones
C) Ninguna de ellas

<details><summary>Respuesta</summary>

**Correcta: B) Dos de las tres: Consistencia, Disponibilidad y tolerancia a Particiones** El **teorema CAP** (Brewer): solo **dos de tres** (Consistencia, Disponibilidad, Particiones). Ante una partición se elige entre C y A.

*Referencia: §4.5 [CAP-BREWER]*
</details>

---

### Pregunta 36

**El modelo BASE, alternativa a ACID en muchos NoSQL, prioriza:**

A) La consistencia inmediata por encima de todo
B) La disponibilidad y la consistencia eventual
C) El cifrado de los datos

<details><summary>Respuesta</summary>

**Correcta: B) La disponibilidad y la consistencia eventual** **BASE** (Basically Available, Soft state, Eventual consistency) prioriza disponibilidad y consistencia eventual frente a la consistencia inmediata de ACID.

*Referencia: §4.5*
</details>

---

### Pregunta 37

**Redis es un ejemplo de base de datos NoSQL de tipo:**

A) De grafos
B) Relacional
C) Clave-valor

<details><summary>Respuesta</summary>

**Correcta: C) Clave-valor** **Redis** es **clave-valor**, de acceso ultrarrápido (caché, sesiones).

*Referencia: §4.5*
</details>

---

### Pregunta 38

**El procesamiento OLTP se caracteriza por:**

A) Operaciones transaccionales cortas del día a día
B) Consultas analíticas masivas sobre datos históricos
C) No usar bases de datos

<details><summary>Respuesta</summary>

**Correcta: A) Operaciones transaccionales cortas del día a día** **OLTP** = transaccional, operaciones cortas del día a día (el Padrón en funcionamiento). OLAP es el analítico.

*Referencia: §4.6*
</details>

---

### Pregunta 39

**Un data warehouse (almacén de datos) sirve para:**

A) Sustituir al sistema operativo
B) Cifrar los discos
C) Consolidar datos históricos de varias fuentes para el análisis (OLAP)

<details><summary>Respuesta</summary>

**Correcta: C) Consolidar datos históricos de varias fuentes para el análisis (OLAP)** El **data warehouse** consolida datos históricos para el análisis (OLAP), separándolo de los sistemas operacionales (OLTP).

*Referencia: §4.6 [KIMBALL-DW]*
</details>

---

### Pregunta 40

**El modelo de diseño típico de un data warehouse, con una tabla de hechos rodeada de dimensiones, es:**

A) El modelo en estrella
B) El modelo jerárquico
C) El modelo en red

<details><summary>Respuesta</summary>

**Correcta: A) El modelo en estrella** El **modelo en estrella** (tabla de hechos + dimensiones) es el diseño típico de un data warehouse para OLAP.

*Referencia: §4.6*
</details>

---

### Pregunta 41

**Cassandra es un ejemplo de base de datos NoSQL de tipo:**

A) Documental
B) Columnar (familias de columnas)
C) Clave-valor

<details><summary>Respuesta</summary>

**Correcta: B) Columnar (familias de columnas)** **Cassandra** es **columnar** (familias de columnas), optimizada para grandes volúmenes y mucha escritura.

*Referencia: §4.5*
</details>

---

### Pregunta 42

**Los SGBD jerárquicos organizan los datos en:**

A) Una estructura de árbol (relaciones padre-hijo 1:N)
B) Tablas relacionadas por claves
C) Documentos JSON

<details><summary>Respuesta</summary>

**Correcta: A) Una estructura de árbol (relaciones padre-hijo 1:N)** Los **jerárquicos** usan una estructura de **árbol** (padre-hijo 1:N); son históricos (IBM IMS) y rígidos para N:M.

*Referencia: §4.1*
</details>

---

### Pregunta 43

**Conceder solo lectura de una tabla a un rol se hace con:**

A) `DROP TABLE tabla;`
B) `GRANT SELECT ON tabla TO rol;`
C) `COMMIT;`

<details><summary>Respuesta</summary>

**Correcta: B) `GRANT SELECT ON tabla TO rol;`** `GRANT SELECT ON tabla TO rol;` concede el privilegio de **lectura**. Gestionar por roles simplifica la administración.

*Referencia: §5.1 [ISO-9075]*
</details>

---

### Pregunta 44

**Agrupar los privilegios en conjuntos que se asignan a los usuarios se hace mediante:**

A) Índices
B) Roles
C) Vistas materializadas

<details><summary>Respuesta</summary>

**Correcta: B) Roles** Los **roles** agrupan privilegios; asignar roles (no privilegios sueltos) simplifica la gestión de muchos usuarios.

*Referencia: §5.1*
</details>

---

### Pregunta 45

**Repartir (particionar) los datos entre varios nodos según una clave para escalar horizontalmente se denomina:**

A) Replicación
B) Sharding
C) Normalización

<details><summary>Respuesta</summary>

**Correcta: B) Sharding** El **sharding** reparte los datos entre nodos según una clave, para escalar horizontalmente (típico en NoSQL).

*Referencia: §5.3*
</details>

---

### Pregunta 46

**Mantener copias idénticas de los datos en varios nodos se denomina:**

A) Replicación
B) Fragmentación
C) Indexación

<details><summary>Respuesta</summary>

**Correcta: A) Replicación** La **replicación** mantiene copias en varios nodos: mejora la disponibilidad y la lectura, pero complica la consistencia.

*Referencia: §5.3*
</details>

---

### Pregunta 47

**La conmutación automática a un nodo de respaldo cuando falla el principal se llama:**

A) Commit
B) Sharding
C) Failover

<details><summary>Respuesta</summary>

**Correcta: C) Failover** El **failover** es la conmutación por error a un nodo de respaldo, base de la alta disponibilidad.

*Referencia: §5.4*
</details>

---

### Pregunta 48

**La recuperación a un punto en el tiempo (PITR) se consigue:**

A) Solo con una copia completa
B) Combinando una copia de seguridad con el log de transacciones
C) Borrando el log

<details><summary>Respuesta</summary>

**Correcta: B) Combinando una copia de seguridad con el log de transacciones** El **PITR** restaura una copia y aplica el **log** hasta el instante exacto anterior al incidente.

*Referencia: §5.5 [POSTGRES-DOC]*
</details>

---

### Pregunta 49

**Una copia de seguridad incremental:**

A) Copia toda la base de datos cada vez
B) No es posible
C) Copia solo lo que ha cambiado desde la última copia

<details><summary>Respuesta</summary>

**Correcta: C) Copia solo lo que ha cambiado desde la última copia** La copia **incremental** copia solo lo cambiado desde la última, ahorrando espacio y tiempo frente a la completa.

*Referencia: §5.5*
</details>

---

### Pregunta 50

**Analizar cómo el optimizador resuelve una consulta lenta se hace con:**

A) El plan de ejecución (EXPLAIN)
B) Un GRANT
C) Un ROLLBACK

<details><summary>Respuesta</summary>

**Correcta: A) El plan de ejecución (EXPLAIN)** El **plan de ejecución** (`EXPLAIN`) muestra cómo el optimizador resuelve la consulta, base del *tuning*.

*Referencia: §5.7*
</details>

---

### Pregunta 51

**La principal palanca para acelerar una consulta que hace un recorrido completo de una tabla grande es:**

A) Borrar la tabla
B) Desactivar la integridad referencial
C) Crear un índice adecuado

<details><summary>Respuesta</summary>

**Correcta: C) Crear un índice adecuado** Crear un **índice** adecuado convierte un recorrido completo (full table scan) en una búsqueda O(log n).

*Referencia: §5.7*
</details>

---

### Pregunta 52

**El espacio lógico sobre ficheros donde el DBA organiza el almacenamiento físico de la BD se denomina:**

A) Tablespace
B) Vista
C) Trigger

<details><summary>Respuesta</summary>

**Correcta: A) Tablespace** Los **tablespaces** son los espacios lógicos sobre ficheros donde se organiza el almacenamiento (tablas, índices).

*Referencia: §5.2*
</details>

---

### Pregunta 53

**La base de datos como servicio gestionada en la nube se denomina:**

A) DBaaS
B) DDL
C) OLAP

<details><summary>Respuesta</summary>

**Correcta: A) DBaaS** **DBaaS** (Database as a Service): SGBD gestionados en la nube (Amazon RDS, Azure SQL, Cloud SQL).

*Referencia: §5.8*
</details>

---

### Pregunta 54

**Un inconveniente típico del DBaaS para una Administración pública es:**

A) La ubicación de los datos y el cumplimiento del RGPD (soberanía del dato)
B) Que nunca tiene copias de seguridad
C) Que es siempre gratuito

<details><summary>Respuesta</summary>

**Correcta: A) La ubicación de los datos y el cumplimiento del RGPD (soberanía del dato)** El **DBaaS** plantea dudas de **ubicación de los datos** y cumplimiento del **RGPD/ENS** (soberanía), además del *vendor lock-in*.

*Referencia: §5.8*
</details>

---

### Pregunta 55

**La gobernanza del dato incluye:**

A) Calidad, metadatos, ciclo de vida y protección de datos personales
B) Solo el cifrado del disco
C) Únicamente la compra de hardware

<details><summary>Respuesta</summary>

**Correcta: A) Calidad, metadatos, ciclo de vida y protección de datos personales** La **gobernanza** abarca calidad, metadatos, ciclo de vida, clasificación y protección de datos (RGPD/LOPDGDD).

*Referencia: §5.6 [RGPD]*
</details>

---

### Pregunta 56

**El tratamiento de datos personales en una base de datos del Ayuntamiento debe cumplir:**

A) El RGPD y la LOPDGDD
B) Solo el manual del fabricante
C) Ninguna normativa

<details><summary>Respuesta</summary>

**Correcta: A) El RGPD y la LOPDGDD** Los datos personales obligan a cumplir el **RGPD** y la **LOPDGDD** (minimización, control de acceso, cifrado, registro de accesos).

*Referencia: §5.1, §5.6 [RGPD][LOPDGDD]*
</details>

---

### Pregunta 57

**La alta disponibilidad de una base de datos se logra principalmente con:**

A) Borrando índices
B) Reduciendo la seguridad
C) Clústeres, replicación y failover

<details><summary>Respuesta</summary>

**Correcta: C) Clústeres, replicación y failover** La **alta disponibilidad** se apoya en clústeres, replicación primario-secundario y conmutación por error (failover).

*Referencia: §5.4*
</details>

---

### Pregunta 58

**Dividir una tabla por filas entre varios nodos es una forma de:**

A) Normalización
B) Fragmentación horizontal
C) Indexación

<details><summary>Respuesta</summary>

**Correcta: B) Fragmentación horizontal** Dividir una tabla por **filas** es **fragmentación horizontal**; por columnas, vertical. Es base de la distribución.

*Referencia: §5.3*
</details>

---

### Pregunta 59

**Una ventaja del DBaaS es:**

A) Que el proveedor gestiona infraestructura, copias, parches y escalado
B) Que elimina la necesidad de seguridad
C) Que los datos nunca salen del equipo local

<details><summary>Respuesta</summary>

**Correcta: A) Que el proveedor gestiona infraestructura, copias, parches y escalado** El **DBaaS** descarga en el proveedor la infraestructura, las copias, los parches y el escalado, con pago por uso.

*Referencia: §5.8*
</details>

---

### Pregunta 60

**El particionado de una tabla muy grande por rango de fechas sirve para:**

A) Mejorar el rendimiento y el mantenimiento
B) Eliminar la clave primaria
C) Impedir las consultas

<details><summary>Respuesta</summary>

**Correcta: A) Mejorar el rendimiento y el mantenimiento** El **particionado** (por fecha, territorio…) mejora el rendimiento de las consultas y facilita el mantenimiento de tablas grandes.

*Referencia: §5.2*
</details>
