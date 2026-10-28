# AGENTS.md — Protocolo Operativo y Gobernanza del Proyecto BI Asistido por AI

Este documento rige la conducta, operaciones, flujo de trabajo y salvaguardas que todo agente inteligente (y colaborador humano) debe acatar en este repositorio. Está fundamentado en el patrón de **LLM Wiki** (Karpathy, 2026) y en las mejores prácticas de ingeniería de datos y Business Intelligence.

---

## 1. Principio Fundamental: Las 3 Capas de la Arquitectura

Siguiendo la arquitectura de conocimiento persistente:

1. **Capa Cruda (`data/raw/`):** La Fuente Única de Verdad (Single Source of Truth).
2. **Capa Wiki (`wiki/`):** La memoria persistente, incremental y transversal mantenida por el agente.
3. **Capa de Esquema y Gobernanza (`AGENTS.md` y `docs/`):** Las reglas operativas y contratos de datos.

---

## 2. Reglas Estrictas de Operación de Datos

### Regla 1: Inmutabilidad Absoluta de `data/raw/`
* **PROHIBICIÓN TOTAL:** Ningún agente ni proceso automatizado podrá modificar, renombrar, sobreescribir, transformar in-situ o eliminar ningún archivo ubicado dentro de `data/raw/`.
* Todo archivo en `data/raw/` se considera de solo lectura (`READONLY`).
* Si se reciben nuevos lotes de datos, estos se incorporan como nuevos archivos con estampado temporal o sufijos versionados dentro de `data/raw/incoming/` o con prefijos de lote, preservando siempre el histórico íntegro.

### Regla 2: Reproducibilidad Determinista
* Toda transformación de datos, cálculo de scores y generación de datasets analíticos debe residir en scripts versionados y reproducibles dentro de `src/` o empaquetados en `skills/`.
* No se permiten transformaciones manuales no registradas.
* Cualquier ejecución de pipeline debe poder repetirse desde cero a partir de `data/raw/` produciendo exactamente el mismo resultado en `data/processed/`.

### Regla 3: Versionado y Linaje de Resultados
* Los datasets intermedios y finales deben residir en `data/processed/` y `data/outputs/`.
* Las salidas analíticas y rankings deben incorporar metadatos de linaje: fecha de cálculo (`calculated_at`), versión del pipeline (`pipeline_version`) y hash o lista de fuentes procesadas (`source_batch`).
* Queda vetada la sobreescritura destructiva de rankings históricos sin versionado previo.

---

## 3. Protocolo de Mantenimiento de la Wiki (Patrón Karpathy)

La wiki no es un volcado pasivo de texto; es un artefacto estructurado, interconectado y acumulativo.

### Operación 1: Ingest (Ingesta de nuevas fuentes)
Al incorporar nuevos datos o requerimientos:
1. El agente inspecciona los datos crudos y reporta anomalías.
2. Genera o actualiza las páginas de entidad relevantes (`wiki/entities/`) y conceptos (`wiki/concepts/`).
3. Actualiza `wiki/index.md` con el enlace y resumen de cada página tocada.
4. Registra la acción en `wiki/log.md` con el formato estándar: `## [YYYY-MM-DD] ingest | <descripción>`.

### Operación 2: Query (Consultas y Respuestas Compuestas)
* Las respuestas analíticas complejas o comparaciones que resuelvan dudas de negocio no mueren en la conversación efímera: se redactan y archivan como páginas wiki (`wiki/analyses/` o `wiki/reports/`).
* Toda afirmación debe referenciar las fuentes y las métricas calculadas.

### Operación 3: Lint (Mantenimiento de Calidad de la Wiki)
Periódicamente el agente ejecutará una revisión de salud de la wiki:
* Verificar enlaces rotos u huérfanos.
* Detectar conceptos mencionados sin página de destino.
* Contrastar afirmaciones obsoletas contra nuevos datos.
* Validar que `wiki/index.md` y `wiki/log.md` se encuentren 100% sincronizados.

---

## 4. Uso y Estándar de `skills/`

Las herramientas reutilizables del agente deben modularizarse dentro de la carpeta `skills/`:
* Cada skill posee su propio `SKILL.md` con instrucciones claras de uso, dependencias, entradas esperadas y salidas.
* **Skills requeridas para este proyecto:**
  1. `skills/data-validator/`: Diagnóstico automático de calidad, encoding, nulos e integridad referencial.
  2. `skills/network-metrics/`: Cálculo modular de métricas de grafo (in-degree, out-degree, PageRank, reciprocidad diádica).
  3. `skills/engagement-scorer/`: Cálculo ponderado de interacciones y valor de seguidores.
  4. `skills/wiki-maintainer/`: Auditoría, linting e indexación automática de la wiki.

---

## 5. Separación de Fases y Puntos de Aprobación Humana

* **Fase 1: Diagnóstico y Diseño Conceptual (Fase Actual).**
  - Solo lectura de `data/raw/`.
  - Elaboración de diccionarios, inventarios, wiki base y planes de acción.
  - Prohibido codificar pipelines finales o rankings definitivos sin autorización.
* **Fase 2: Implementación de Pipelines de Datos.**
  - Requiere aprobación expresa del usuario del Plan de Acción y de los Puntos de Decisión.
* **Fase 3: Modelado de Redes e Inferencia.**
* **Fase 4: Dashboards y Reportes de BI.**
