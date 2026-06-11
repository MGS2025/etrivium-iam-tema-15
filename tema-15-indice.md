# Tema 15 — Índice

> **Título oficial**: Sistemas de gestión de bases de datos relacionales, orientados a objetos y NoSQL: características y componentes. Administración de bases de datos.
>
> **Bloque**: Parte II — Técnico (Temas 11-40)
> **Nivel**: C1 — Técnico Auxiliar TIC, Ayuntamiento de Madrid

---

## Estructura del tema

1. **Concepto de base de datos y SGBD**
   1.1. De los ficheros a las bases de datos (problemas del enfoque de ficheros)
   1.2. Base de datos y Sistema de Gestión de Bases de Datos (SGBD/DBMS)
   1.3. Funciones del SGBD (definición, manipulación, control, diccionario de datos)
   1.4. Componentes del SGBD (motor, procesador de consultas, gestor de transacciones, gestor de almacenamiento)
   1.5. Lenguajes: DDL, DML, DCL, TCL
   1.6. Roles: administrador (DBA), diseñador, programador, usuario final

2. **Características: transaccionalidad y concurrencia**
   2.1. Transacción y propiedades ACID (atomicidad, consistencia, aislamiento, durabilidad)
   2.2. Concurrencia: problemas (lectura sucia, no repetible, fantasma) y control (bloqueos, MVCC)
   2.3. Niveles de aislamiento (SQL estándar)
   2.4. Recuperación ante fallos (log de transacciones, checkpoints)

3. **Modelo ANSI/SPARC (arquitectura de tres esquemas)**
   3.1. Nivel interno (físico), conceptual y externo (vistas)
   3.2. Independencia de datos (física y lógica)

4. **Tipologías de SGBD**
   4.1. SGBD jerárquicos
   4.2. SGBD en red (CODASYL)
   4.3. SGBD relacionales (modelo de Codd; tablas, claves, álgebra relacional; SQL)
   4.4. SGBD orientados a objetos y objeto-relacionales
   4.5. SGBD NoSQL (clave-valor, documental, columnar, grafos; teorema CAP; BASE)
   4.6. SGBD multidimensionales y analítica de datos (OLAP, data warehouse, OLTP vs OLAP)

5. **Administración de bases de datos**
   5.1. Administración de usuarios y seguridad (privilegios, roles, GRANT/REVOKE)
   5.2. Administración del almacenamiento (tablespaces, índices, particionado)
   5.3. SGBD distribuidos (fragmentación, replicación, sharding)
   5.4. Disponibilidad y alta disponibilidad (clústeres, replicación, failover)
   5.5. Copias de seguridad y recuperación (backup completo/incremental, PITR)
   5.6. Gobernanza del dato (calidad, metadatos, ciclo de vida, protección de datos)
   5.7. Rendimiento: diagnóstico y resolución de incidencias (índices, plan de ejecución, tuning)
   5.8. SGBD en la nube (DBaaS): modelos, ventajas e inconvenientes

---

## Conceptos clave para memorizar

| Concepto | Dato clave |
|---|---|
| SGBD (DBMS) | Software que gestiona el acceso concurrente, seguro e íntegro a una base de datos |
| Diccionario de datos | Metadatos: descripción de la estructura de la BD (catálogo del sistema) |
| DDL / DML / DCL / TCL | Definición / Manipulación / Control de acceso / Control de transacciones |
| Transacción | Unidad lógica de trabajo, indivisible (todo o nada) |
| ACID | Atomicidad, Consistencia, Aislamiento, Durabilidad (ACID) |
| Concurrencia | Varios usuarios a la vez; se controla con bloqueos o MVCC |
| ANSI/SPARC | Arquitectura de 3 esquemas: interno, conceptual, externo (vistas) |
| Independencia de datos | Cambiar un nivel sin afectar a los superiores (física y lógica) |
| Modelo relacional | Codd (1970): datos en tablas (relaciones) con claves; base de SQL |
| Clave primaria / ajena | Identifica unívocamente / referencia a otra tabla (integridad referencial) |
| SQL | Lenguaje estándar (ISO 9075) de definición y consulta relacional |
| NoSQL | No relacional: clave-valor, documental, columnar, grafos; escala horizontal |
| Teorema CAP | Solo 2 de 3: Consistencia, Disponibilidad, tolerancia a Particiones |
| BASE | Alternativa a ACID en NoSQL: disponibilidad sobre consistencia inmediata |
| OLTP vs OLAP | Transaccional (operaciones diarias) vs analítico (consultas masivas, data warehouse) |
| Sharding / replicación | Repartir datos / copiarlos para escalar y dar disponibilidad |
| GRANT / REVOKE | Conceder / retirar privilegios a usuarios y roles |
| Backup + PITR | Copia de seguridad y recuperación a un punto en el tiempo (con el log) |
| DBaaS | Base de datos como servicio en la nube |

---

*Tiempo estimado de estudio: 9-11 horas*
*Extensión del contenido: ~9.000-11.000 palabras · 12 diagramas SVG embebidos*
