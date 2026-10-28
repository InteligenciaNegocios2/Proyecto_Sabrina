# Índice General de la Wiki del Proyecto BI

Bienvenido al catálogo central de conocimiento persistente del proyecto **BI Influenciadores y Seguidores Asistido por AI**.  
Este índice es mantenido de forma incremental por el agente y sirve como mapa de navegación de todos los conceptos, modelos, entidades y registros analíticos.

---

## 1. Gobernanza y Marco de Trabajo

* [Objetivos del Proyecto](objectives.md): Definición detallada de las tres preguntas de negocio, alcance y criterios de éxito.
* [Registro de Operaciones (Log)](log.md): Bitácora cronológica inmutable de ingestas, lintings y decisiones.
* [Diccionario de Datos](../docs/data_dictionary.md): Especificación técnica de fuentes crudas, esquemas y anomalías observadas.
* [Protocolo de Agentes](../AGENTS.md): Reglas de inmutabilidad, reproducibilidad y gobernanza.

---

## 2. Conceptos Centrales y Metodología

* [Concepto: Potencial de Influencia](concepts/influencia.md): Definición multidimensional (red, engagement recibido, calidad de contenido y alcance).
* [Concepto: Seguidores de Alto Valor](concepts/seguidores.md): Perfiles de valor superior por volumen de actividad, intensidad de engagement y reciprocidad con la comunidad.
* [Concepto: Reciprocidad de Red](concepts/reciprocidad.md): Aristas bidireccionales en el grafo, interacciones mutuas y fidelidad de audiencia.
* [Metodología de Ingesta Continua](concepts/ingesta_continua.md): Estrategia de procesamiento delta y acumulación histórica de nuevos CSVs.

---

## 3. Catálogo de Datos y Pipelines

* **Datos Crudos (`data/raw/`):**
  - `usuarios.csv`: 650 perfiles.
  - `relaciones.csv`: 8,133 aristas seguidor → seguido.
  - `publicaciones.csv`: 5,200 publicaciones.
  - `interacciones.csv`: 35,810 eventos de engagement.
* **Capas Analíticas Planificadas:**
  - `data/processed/`: Tablas limpias, tipadas y enriquecidas con métricas de red.
  - `data/outputs/`: Rankings históricos versionados y tablas listas para consumo BI.

---

## 4. Skills y Capacidades Modulares

* `skills/data-validator/`: Diagnóstico y validación de calidad de datos crudos.
* `skills/network-metrics/`: Computación de centralidades y reciprocidades de grafo.
* `skills/engagement-scorer/`: Algoritmo ponderado de interacciones y calidad.
* `skills/wiki-maintainer/`: Mantenimiento y verificación de enlaces y frescura en la wiki.
