# Tema 15 — Catálogo de Diagramas

> **Título oficial**: Sistemas de gestión de bases de datos relacionales, orientados a objetos y NoSQL: características y componentes. Administración de bases de datos.
>
> **Versión**: v1.0
> **Fecha**: 2026-06-11
> **Autor**: ETRIVIUM
> **Formato**: SVG inline (zero-dependencias, escalable, imprimible, accesible con role/aria-label)
> **Paleta**: Ayuntamiento de Madrid #0055a0 (primario) + #d13c3c (alertas) + #2d8659 (ventajas) + #e89822 (callouts)

---

## Índice de diagramas

| ID | Título | Sección | Tipo | Formato |
|---|---|---|---|---|
| D1 | De los ficheros a la base de datos | §1.1 | Comparativa | 660×300 |
| D2 | Componentes de un SGBD | §1.4 | Bloques | 660×320 |
| D3 | Propiedades ACID | §2.1 | Conceptual | 660×300 |
| D4 | Arquitectura ANSI/SPARC (3 esquemas) | §3 | Capas | 660×320 |
| D5 | Niveles de aislamiento | §2.3 | Tabla | 660×300 |
| D6 | Modelo relacional: claves y join | §4.3 | Estructura | 680×320 |
| D7 | Tipologías de SGBD | §4 | Mapa | 680×320 |
| D8 | Tipos de bases de datos NoSQL | §4.5 | Comparativa | 680×340 |
| D9 | Teorema CAP | §4.5 | Triángulo | 620×340 |
| D10 | OLTP vs OLAP y data warehouse | §4.6 | Comparativa | 680×320 |
| D11 | Distribución: fragmentación, replicación, sharding | §5.3 | Conceptual | 680×320 |
| D12 | Copias de seguridad y PITR | §5.5 | Línea de tiempo | 680×300 |

---

## D1 · De los ficheros a la base de datos

**Sección**: §1.1 — De los ficheros a las bases de datos
**Propósito**: Contrastar la redundancia del enfoque de ficheros con la BD integrada.

```svg
<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 660 300" role="img" aria-label="Comparación entre ficheros aislados con datos redundantes y una base de datos integrada">
  <style>.t{font:700 13px system-ui,sans-serif;fill:#0055a0}.b{font:600 11px system-ui,sans-serif;fill:#fff}.l{font:11px system-ui,sans-serif;fill:#444}</style>
  <text x="160" y="34" text-anchor="middle" class="t">Ficheros aislados</text>
  <rect x="60" y="55" width="90" height="44" rx="4" fill="#d13c3c"/><text x="105" y="81" text-anchor="middle" class="b">App A + datos</text>
  <rect x="60" y="110" width="90" height="44" rx="4" fill="#d13c3c"/><text x="105" y="136" text-anchor="middle" class="b">App B + datos</text>
  <rect x="60" y="165" width="90" height="44" rx="4" fill="#d13c3c"/><text x="105" y="191" text-anchor="middle" class="b">App C + datos</text>
  <text x="60" y="235" class="l">Datos duplicados → redundancia e inconsistencia</text>
  <text x="500" y="34" text-anchor="middle" class="t">Base de datos</text>
  <rect x="430" y="55" width="60" height="30" rx="4" fill="#3378b9"/><text x="460" y="75" text-anchor="middle" class="b">App A</text>
  <rect x="430" y="95" width="60" height="30" rx="4" fill="#3378b9"/><text x="460" y="115" text-anchor="middle" class="b">App B</text>
  <rect x="430" y="135" width="60" height="30" rx="4" fill="#3378b9"/><text x="460" y="155" text-anchor="middle" class="b">App C</text>
  <rect x="520" y="80" width="90" height="60" rx="6" fill="#2d8659"/><text x="565" y="105" text-anchor="middle" class="b">SGBD</text><text x="565" y="125" text-anchor="middle" class="b">+ BD única</text>
  <line x1="490" y1="70" x2="518" y2="100" stroke="#888"/><line x1="490" y1="110" x2="518" y2="110" stroke="#888"/><line x1="490" y1="150" x2="518" y2="120" stroke="#888"/>
  <text x="430" y="235" class="l">Datos integrados, sin redundancia, compartidos</text>
  <text x="650" y="290" text-anchor="end" font="11px system-ui,sans-serif" fill="#666">[Fuente: ELMASRI, cap. 1]</text>
</svg>
```

---

## D2 · Componentes de un SGBD

**Sección**: §1.4 — Componentes del SGBD
**Propósito**: Mostrar los módulos internos entre los usuarios y los datos.

```svg
<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 660 320" role="img" aria-label="Componentes internos de un SGBD">
  <style>.b{font:600 12px system-ui,sans-serif;fill:#fff}.l{font:11px system-ui,sans-serif;fill:#444}</style>
  <rect x="180" y="30" width="300" height="36" rx="4" fill="#6ea3d2"/><text x="330" y="53" text-anchor="middle" class="b">Usuarios / Aplicaciones (consultas SQL)</text>
  <rect x="180" y="84" width="300" height="36" rx="4" fill="#0055a0"/><text x="330" y="107" text-anchor="middle" class="b">Procesador de consultas (optimizador)</text>
  <rect x="100" y="138" width="220" height="36" rx="4" fill="#0055a0"/><text x="210" y="161" text-anchor="middle" class="b">Gestor de transacciones (ACID)</text>
  <rect x="340" y="138" width="220" height="36" rx="4" fill="#0055a0"/><text x="450" y="161" text-anchor="middle" class="b">Gestor del diccionario</text>
  <rect x="180" y="192" width="300" height="36" rx="4" fill="#003d73"/><text x="330" y="215" text-anchor="middle" class="b">Gestor de almacenamiento (índices, buffer)</text>
  <rect x="180" y="246" width="300" height="36" rx="4" fill="#2d3748"/><text x="330" y="269" text-anchor="middle" class="b">Datos + índices + log en disco</text>
  <text x="650" y="308" text-anchor="end" font="11px system-ui,sans-serif" fill="#666">[Fuente: SILBERSCHATZ-DB, cap. 1]</text>
</svg>
```

---

## D3 · Propiedades ACID

**Sección**: §2.1 — Transacción y propiedades ACID
**Propósito**: Recordar las cuatro propiedades de una transacción.

```svg
<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 660 300" role="img" aria-label="Las cuatro propiedades ACID de una transacción">
  <style>.b{font:700 18px system-ui,sans-serif;fill:#fff}.t{font:700 13px system-ui,sans-serif;fill:#0055a0}.l{font:12px system-ui,sans-serif;fill:#1a1a1a}</style>
  <rect x="40" y="60" width="140" height="160" rx="8" fill="#0055a0"/><text x="110" y="100" text-anchor="middle" class="b">A</text><text x="110" y="130" text-anchor="middle" class="l" fill="#fff">Atomicidad</text><text x="110" y="160" text-anchor="middle" class="l" fill="#cfe2f3">todo o nada</text>
  <rect x="195" y="60" width="140" height="160" rx="8" fill="#3378b9"/><text x="265" y="100" text-anchor="middle" class="b">C</text><text x="265" y="130" text-anchor="middle" class="l" fill="#fff">Consistencia</text><text x="265" y="160" text-anchor="middle" class="l" fill="#dbe7f3">estados válidos</text>
  <rect x="350" y="60" width="140" height="160" rx="8" fill="#0055a0"/><text x="420" y="100" text-anchor="middle" class="b">I</text><text x="420" y="130" text-anchor="middle" class="l" fill="#fff">Aislamiento</text><text x="420" y="160" text-anchor="middle" class="l" fill="#cfe2f3">como en serie</text>
  <rect x="505" y="60" width="140" height="160" rx="8" fill="#2d8659"/><text x="575" y="100" text-anchor="middle" class="b">D</text><text x="575" y="130" text-anchor="middle" class="l" fill="#fff">Durabilidad</text><text x="575" y="160" text-anchor="middle" class="l" fill="#d9efe2">persiste</text>
  <text x="40" y="40" class="t">Toda transacción cumple:</text>
  <text x="650" y="290" text-anchor="end" font="11px system-ui,sans-serif" fill="#666">[Fuente: ACID-HAERDER]</text>
</svg>
```

---

## D4 · Arquitectura ANSI/SPARC

**Sección**: §3 — Modelo ANSI/SPARC
**Propósito**: Los tres niveles de abstracción y la independencia de datos.

```svg
<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 660 320" role="img" aria-label="Arquitectura ANSI SPARC de tres esquemas: externo, conceptual e interno">
  <style>.b{font:600 12px system-ui,sans-serif;fill:#fff}.l{font:11px system-ui,sans-serif;fill:#444}</style>
  <rect x="60" y="40" width="160" height="40" rx="4" fill="#6ea3d2"/><text x="140" y="65" text-anchor="middle" class="b">Vista 1</text>
  <rect x="250" y="40" width="160" height="40" rx="4" fill="#6ea3d2"/><text x="330" y="65" text-anchor="middle" class="b">Vista 2</text>
  <rect x="440" y="40" width="160" height="40" rx="4" fill="#6ea3d2"/><text x="520" y="65" text-anchor="middle" class="b">Vista 3</text>
  <text x="610" y="35" text-anchor="end" class="l" fill="#0055a0">Nivel externo (vistas)</text>
  <rect x="120" y="130" width="420" height="44" rx="4" fill="#0055a0"/><text x="330" y="157" text-anchor="middle" class="b">Esquema conceptual (estructura lógica global)</text>
  <text x="610" y="125" text-anchor="end" class="l" fill="#0055a0">Nivel conceptual</text>
  <rect x="120" y="220" width="420" height="44" rx="4" fill="#003d73"/><text x="330" y="247" text-anchor="middle" class="b">Esquema interno (almacenamiento físico)</text>
  <text x="610" y="215" text-anchor="end" class="l" fill="#0055a0">Nivel interno</text>
  <line x1="330" y1="80" x2="330" y2="130" stroke="#2d8659" stroke-width="2"/><text x="340" y="110" class="l" fill="#2d8659">indep. lógica</text>
  <line x1="330" y1="174" x2="330" y2="220" stroke="#2d8659" stroke-width="2"/><text x="340" y="200" class="l" fill="#2d8659">indep. física</text>
  <text x="650" y="308" text-anchor="end" font="11px system-ui,sans-serif" fill="#666">[Fuente: ANSI-SPARC · DATE]</text>
</svg>
```

---

## D5 · Niveles de aislamiento

**Sección**: §2.3 — Niveles de aislamiento
**Propósito**: Qué anomalía evita cada nivel del estándar SQL.

```svg
<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 660 300" role="img" aria-label="Tabla de niveles de aislamiento SQL y las anomalías que evitan">
  <style>.h{font:700 11px system-ui,sans-serif;fill:#fff}.c{font:11px system-ui,sans-serif;fill:#1a1a1a}.ok{fill:#2d8659;font-weight:700}.no{fill:#d13c3c;font-weight:700}</style>
  <rect x="30" y="40" width="180" height="34" fill="#0055a0"/><rect x="210" y="40" width="140" height="34" fill="#0055a0"/><rect x="350" y="40" width="150" height="34" fill="#0055a0"/><rect x="500" y="40" width="130" height="34" fill="#0055a0"/>
  <text x="40" y="62" class="h">Nivel</text><text x="220" y="62" class="h">Lectura sucia</text><text x="360" y="62" class="h">No repetible</text><text x="510" y="62" class="h">Fantasma</text>
  <g class="c" font-size="11">
    <text x="40" y="96">Read Uncommitted</text><text x="270" y="96" class="no" text-anchor="middle">Sí</text><text x="415" y="96" class="no" text-anchor="middle">Sí</text><text x="555" y="96" class="no" text-anchor="middle">Sí</text>
    <text x="40" y="128">Read Committed</text><text x="270" y="128" class="ok" text-anchor="middle">No</text><text x="415" y="128" class="no" text-anchor="middle">Sí</text><text x="555" y="128" class="no" text-anchor="middle">Sí</text>
    <text x="40" y="160">Repeatable Read</text><text x="270" y="160" class="ok" text-anchor="middle">No</text><text x="415" y="160" class="ok" text-anchor="middle">No</text><text x="555" y="160" class="no" text-anchor="middle">Sí</text>
    <text x="40" y="192">Serializable</text><text x="270" y="192" class="ok" text-anchor="middle">No</text><text x="415" y="192" class="ok" text-anchor="middle">No</text><text x="555" y="192" class="ok" text-anchor="middle">No</text>
  </g>
  <line x1="30" y1="104" x2="630" y2="104" stroke="#e8ecf0"/><line x1="30" y1="136" x2="630" y2="136" stroke="#e8ecf0"/><line x1="30" y1="168" x2="630" y2="168" stroke="#e8ecf0"/>
  <text x="30" y="225" font="11px system-ui,sans-serif" fill="#444">A más aislamiento, más consistencia pero menos concurrencia. Por defecto: Read Committed.</text>
  <text x="650" y="288" text-anchor="end" font="11px system-ui,sans-serif" fill="#666">[Fuente: ISO-9075]</text>
</svg>
```

---

## D6 · Modelo relacional: claves y join

**Sección**: §4.3 — SGBD relacionales
**Propósito**: Mostrar clave primaria, clave ajena e integridad referencial.

```svg
<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 680 320" role="img" aria-label="Dos tablas relacionadas por clave primaria y clave ajena">
  <style>.t{font:700 12px system-ui,sans-serif;fill:#0055a0}.h{font:700 11px monospace;fill:#fff}.c{font:11px monospace;fill:#1a1a1a}.l{font:11px system-ui,sans-serif;fill:#444}</style>
  <text x="120" y="34" class="t">HABITANTE</text>
  <rect x="40" y="44" width="220" height="26" fill="#0055a0"/><text x="50" y="62" class="h">DNI (PK) | nombre | distrito_id</text>
  <rect x="40" y="70" width="220" height="24" fill="#e8f0f8"/><text x="50" y="87" class="c">0001A | Ana | 7</text>
  <rect x="40" y="94" width="220" height="24" fill="#fff"/><text x="50" y="111" class="c">0002B | Luis | 7</text>
  <text x="480" y="34" class="t">DISTRITO</text>
  <rect x="420" y="44" width="200" height="26" fill="#2d8659"/><text x="430" y="62" class="h">id (PK) | nombre</text>
  <rect x="420" y="70" width="200" height="24" fill="#e8f5ee"/><text x="430" y="87" class="c">7 | Chamberí</text>
  <path d="M 260 100 C 340 100 340 82 418 82" stroke="#d13c3c" stroke-width="2" fill="none" marker-end="url(#a6)"/>
  <text x="300" y="135" class="l" fill="#d13c3c">distrito_id (clave ajena) → id (clave primaria)</text>
  <text x="40" y="200" class="l">Integridad referencial: distrito_id debe existir en DISTRITO (no hay distritos "huérfanos").</text>
  <text x="40" y="230" class="l">El JOIN combina ambas tablas por esa relación de claves.</text>
  <defs><marker id="a6" markerWidth="10" markerHeight="10" refX="8" refY="5" orient="auto"><polygon points="0,0 10,5 0,10" fill="#d13c3c"/></marker></defs>
  <text x="670" y="308" text-anchor="end" font="11px system-ui,sans-serif" fill="#666">[Fuente: CODD-1970 · DATE]</text>
</svg>
```

---

## D7 · Tipologías de SGBD

**Sección**: §4 — Tipologías de SGBD
**Propósito**: Mapa de los modelos de SGBD.

```svg
<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 680 320" role="img" aria-label="Mapa de tipologías de SGBD">
  <style>.b{font:600 12px system-ui,sans-serif;fill:#fff}.l{font:10px system-ui,sans-serif;fill:#444}</style>
  <rect x="270" y="30" width="140" height="36" rx="6" fill="#0055a0"/><text x="340" y="53" text-anchor="middle" class="b">SGBD</text>
  <g>
    <rect x="20" y="110" width="120" height="50" rx="6" fill="#6ea3d2"/><text x="80" y="132" text-anchor="middle" class="b">Jerárquico</text><text x="80" y="150" text-anchor="middle" class="l" fill="#fff">árbol (IMS)</text>
    <rect x="150" y="110" width="120" height="50" rx="6" fill="#6ea3d2"/><text x="210" y="132" text-anchor="middle" class="b">En red</text><text x="210" y="150" text-anchor="middle" class="l" fill="#fff">CODASYL</text>
    <rect x="280" y="110" width="120" height="50" rx="6" fill="#2d8659"/><text x="340" y="132" text-anchor="middle" class="b">Relacional</text><text x="340" y="150" text-anchor="middle" class="l" fill="#fff">tablas/SQL ★</text>
    <rect x="410" y="110" width="120" height="50" rx="6" fill="#3378b9"/><text x="470" y="132" text-anchor="middle" class="b">Objeto / OR</text><text x="470" y="150" text-anchor="middle" class="l" fill="#fff">objetos</text>
    <rect x="540" y="110" width="120" height="50" rx="6" fill="#e89822"/><text x="600" y="132" text-anchor="middle" class="b">NoSQL</text><text x="600" y="150" text-anchor="middle" class="l" fill="#fff">escala horiz.</text>
    <rect x="280" y="190" width="120" height="50" rx="6" fill="#3378b9"/><text x="340" y="212" text-anchor="middle" class="b">Multidim.</text><text x="340" y="230" text-anchor="middle" class="l" fill="#fff">OLAP/cubos</text>
  </g>
  <line x1="340" y1="66" x2="80" y2="110" stroke="#bbb"/><line x1="340" y1="66" x2="210" y2="110" stroke="#bbb"/><line x1="340" y1="66" x2="340" y2="110" stroke="#bbb"/><line x1="340" y1="66" x2="470" y2="110" stroke="#bbb"/><line x1="340" y1="66" x2="600" y2="110" stroke="#bbb"/>
  <text x="40" y="280" class="l">★ Modelo dominante (Codd, 1970). Históricos: jerárquico y red. Modernos: NoSQL, multidimensional.</text>
  <text x="670" y="308" text-anchor="end" font="11px system-ui,sans-serif" fill="#666">[Fuente: ELMASRI, cap. 2]</text>
</svg>
```

---

## D8 · Tipos de bases de datos NoSQL

**Sección**: §4.5 — SGBD NoSQL
**Propósito**: Los cuatro tipos de NoSQL con su modelo y ejemplo.

```svg
<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 680 340" role="img" aria-label="Los cuatro tipos de bases de datos NoSQL">
  <style>.t{font:700 13px system-ui,sans-serif;fill:#fff}.l{font:11px system-ui,sans-serif;fill:#fff}.e{font:11px system-ui,sans-serif;fill:#cfe2f3}</style>
  <rect x="30" y="40" width="300" height="120" rx="8" fill="#0055a0"/>
  <text x="50" y="68" class="t">Clave-valor</text><text x="50" y="92" class="l">clave → valor · acceso ultrarrápido</text><text x="50" y="120" class="e">Redis, DynamoDB</text>
  <rect x="350" y="40" width="300" height="120" rx="8" fill="#3378b9"/>
  <text x="370" y="68" class="t">Documental</text><text x="370" y="92" class="l">documentos JSON · esquema flexible</text><text x="370" y="120" class="e">MongoDB</text>
  <rect x="30" y="180" width="300" height="120" rx="8" fill="#2d8659"/>
  <text x="50" y="208" class="t">Columnar</text><text x="50" y="232" class="l">familias de columnas · big data</text><text x="50" y="260" class="e">Cassandra, HBase</text>
  <rect x="350" y="180" width="300" height="120" rx="8" fill="#e89822"/>
  <text x="370" y="208" class="t">Grafos</text><text x="370" y="232" class="l">nodos + relaciones · redes/rutas</text><text x="370" y="260" class="e">Neo4j</text>
  <text x="670" y="328" text-anchor="end" font="11px system-ui,sans-serif" fill="#666">[Fuente: SADALAGE-FOWLER]</text>
</svg>
```

---

## D9 · Teorema CAP

**Sección**: §4.5 — Teorema CAP
**Propósito**: Solo dos de las tres propiedades a la vez.

```svg
<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 620 340" role="img" aria-label="Triángulo del teorema CAP: consistencia, disponibilidad y tolerancia a particiones">
  <style>.v{font:700 14px system-ui,sans-serif;fill:#0055a0}.l{font:11px system-ui,sans-serif;fill:#444}</style>
  <polygon points="310,50 110,280 510,280" fill="#e8f0f8" stroke="#0055a0" stroke-width="2"/>
  <circle cx="310" cy="50" r="8" fill="#0055a0"/><text x="310" y="38" text-anchor="middle" class="v">C — Consistencia</text>
  <circle cx="110" cy="280" r="8" fill="#0055a0"/><text x="110" y="305" text-anchor="middle" class="v">A — Disponibilidad</text>
  <circle cx="510" cy="280" r="8" fill="#0055a0"/><text x="510" y="305" text-anchor="middle" class="v">P — Particiones</text>
  <text x="310" y="190" text-anchor="middle" font="700 13px system-ui,sans-serif" fill="#d13c3c">Solo 2 de 3</text>
  <text x="310" y="215" text-anchor="middle" class="l">Ante una partición de red (inevitable),</text>
  <text x="310" y="232" text-anchor="middle" class="l">se elige entre Consistencia y Disponibilidad</text>
  <text x="610" y="330" text-anchor="end" font="11px system-ui,sans-serif" fill="#666">[Fuente: CAP-BREWER]</text>
</svg>
```

---

## D10 · OLTP vs OLAP y data warehouse

**Sección**: §4.6 — SGBD multidimensionales
**Propósito**: Distinguir procesamiento transaccional del analítico.

```svg
<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 680 320" role="img" aria-label="Comparación OLTP y OLAP con el data warehouse en medio">
  <style>.t{font:700 13px system-ui,sans-serif;fill:#fff}.l{font:11px system-ui,sans-serif;fill:#444}.b{font:600 11px system-ui,sans-serif;fill:#fff}</style>
  <rect x="30" y="50" width="180" height="160" rx="8" fill="#0055a0"/>
  <text x="120" y="78" text-anchor="middle" class="t">OLTP</text>
  <text x="45" y="108" class="b">Transaccional</text><text x="45" y="130" class="b">Operaciones cortas</text><text x="45" y="152" class="b">del día a día</text><text x="45" y="186" class="b">Padrón, tributos…</text>
  <rect x="250" y="90" width="180" height="80" rx="8" fill="#e89822"/><text x="340" y="125" text-anchor="middle" class="t">Data Warehouse</text><text x="340" y="148" text-anchor="middle" class="b">consolida e historiza</text>
  <rect x="470" y="50" width="180" height="160" rx="8" fill="#2d8659"/>
  <text x="560" y="78" text-anchor="middle" class="t">OLAP</text>
  <text x="485" y="108" class="b">Analítico</text><text x="485" y="130" class="b">Consultas masivas</text><text x="485" y="152" class="b">Cubos, estrella</text><text x="485" y="186" class="b">Cuadros de mando</text>
  <path d="M 210 130 L 248 130" stroke="#444" stroke-width="2" marker-end="url(#a10)"/>
  <path d="M 430 130 L 468 130" stroke="#444" stroke-width="2" marker-end="url(#a10)"/>
  <defs><marker id="a10" markerWidth="10" markerHeight="10" refX="8" refY="5" orient="auto"><polygon points="0,0 10,5 0,10" fill="#444"/></marker></defs>
  <text x="670" y="308" text-anchor="end" font="11px system-ui,sans-serif" fill="#666">[Fuente: KIMBALL-DW · INMON-DW]</text>
</svg>
```

---

## D11 · Distribución: fragmentación, replicación, sharding

**Sección**: §5.3 — SGBD distribuidos
**Propósito**: Las tres técnicas de distribución de datos.

```svg
<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 680 320" role="img" aria-label="Fragmentación, replicación y sharding en bases de datos distribuidas">
  <style>.t{font:700 12px system-ui,sans-serif;fill:#0055a0}.b{font:600 11px system-ui,sans-serif;fill:#fff}.l{font:10px system-ui,sans-serif;fill:#444}</style>
  <text x="110" y="34" text-anchor="middle" class="t">Fragmentación</text>
  <rect x="50" y="50" width="60" height="30" fill="#6ea3d2"/><rect x="110" y="50" width="60" height="30" fill="#3378b9"/>
  <text x="80" y="70" text-anchor="middle" class="b">Frag 1</text><text x="140" y="70" text-anchor="middle" class="b">Frag 2</text>
  <text x="110" y="105" text-anchor="middle" class="l">divide la tabla en trozos</text>

  <text x="340" y="34" text-anchor="middle" class="t">Replicación</text>
  <rect x="290" y="50" width="60" height="30" fill="#2d8659"/><rect x="360" y="50" width="60" height="30" fill="#2d8659"/>
  <text x="320" y="70" text-anchor="middle" class="b">Copia</text><text x="390" y="70" text-anchor="middle" class="b">Copia</text>
  <text x="340" y="105" text-anchor="middle" class="l">copias idénticas (disponibilidad)</text>

  <text x="570" y="34" text-anchor="middle" class="t">Sharding</text>
  <rect x="510" y="50" width="40" height="30" fill="#e89822"/><rect x="555" y="50" width="40" height="30" fill="#e89822"/><rect x="600" y="50" width="40" height="30" fill="#e89822"/>
  <text x="530" y="70" text-anchor="middle" class="b">A-H</text><text x="575" y="70" text-anchor="middle" class="b">I-P</text><text x="620" y="70" text-anchor="middle" class="b">Q-Z</text>
  <text x="570" y="105" text-anchor="middle" class="l">reparto por clave (escala horizontal)</text>
  <text x="40" y="170" class="l">Una BD distribuida combina estas técnicas para escalar y dar disponibilidad en varios nodos.</text>
  <text x="670" y="308" text-anchor="end" font="11px system-ui,sans-serif" fill="#666">[Fuente: ELMASRI, cap. 23]</text>
</svg>
```

---

## D12 · Copias de seguridad y PITR

**Sección**: §5.5 — Copias de seguridad y recuperación
**Propósito**: Cómo la copia + el log permiten recuperar a un punto en el tiempo.

```svg
<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 680 300" role="img" aria-label="Recuperación a un punto en el tiempo combinando copia completa y log de transacciones">
  <style>.t{font:700 12px system-ui,sans-serif;fill:#0055a0}.l{font:11px system-ui,sans-serif;fill:#444}.b{font:600 11px system-ui,sans-serif;fill:#fff}</style>
  <line x1="40" y1="120" x2="640" y2="120" stroke="#888" stroke-width="2"/>
  <rect x="60" y="100" width="80" height="40" fill="#0055a0"/><text x="100" y="125" text-anchor="middle" class="b">Backup full</text>
  <rect x="380" y="105" width="14" height="30" fill="#2d8659"/><rect x="420" y="105" width="14" height="30" fill="#2d8659"/><rect x="460" y="105" width="14" height="30" fill="#2d8659"/><rect x="500" y="105" width="14" height="30" fill="#2d8659"/>
  <text x="300" y="95" class="l" fill="#2d8659">log de transacciones (cambios continuos)</text>
  <line x1="540" y1="70" x2="540" y2="160" stroke="#d13c3c" stroke-width="2" stroke-dasharray="4"/><text x="540" y="60" text-anchor="middle" class="l" fill="#d13c3c">fallo / error</text>
  <text x="540" y="185" text-anchor="middle" class="l" fill="#d13c3c">se recupera al instante justo anterior</text>
  <text x="40" y="230" class="l">PITR = restaurar la copia completa + aplicar el log hasta el momento elegido.</text>
  <text x="40" y="252" class="l">Tipos de copia: completa · incremental / diferencial (solo lo cambiado).</text>
  <text x="670" y="288" text-anchor="end" font="11px system-ui,sans-serif" fill="#666">[Fuente: POSTGRES-DOC · SILBERSCHATZ-DB]</text>
</svg>
```
