# Plan de Acción: Proyecto BI Asistido por AI — Influenciadores y Seguidores

**Fase:** Diagnóstico y Diseño Conceptual (Pre-implementación)  
**Fecha:** 27 de octubre de 2026  
**Estado:** Pendiente de Aprobación

---

## 1. Resumen y Modelo Conceptual de los Datos
- **Perfiles (`usuarios.csv`):** 650 cuentas, distribuidas en 5 países y 6 nichos temáticos.
- **Red Social (`relaciones.csv`):** 8.133 aristas dirigidas. Grafo fuertemente asimétrico con solo 212 enlaces recíprocos (106 pares de follow mutuo, 2.6% de reciprocidad de red).
- **Publicaciones (`publicaciones.csv`):** 5.200 publicaciones de 646 autores distintos.
- **Interacciones (`interacciones.csv`):** 35.810 eventos de engagement (64.6% Likes, 16.8% Comentarios, 10.4% Compartidos, 8.3% Guardados).
- **Integridad y Calidad:** 100% integridad referencial (cero huérfanos). Se detectaron 1.098 posts y 7.359 interacciones con fechas anteriores al registro del usuario, evidenciando el carácter sintético de los datos.

---

## 2. Métricas Candidatas
1. **Potencial de Influencia:**
   - *Estructural:* In-Degree (número de seguidores directos) y PageRank (autoridad del grafo).
   - *Tracción:* Engagement ponderado total recibido (Pesos: Like=1, Comentario=2, Compartido=3, Guardado=3).
   - *Eficiencia:* Tasa de engagement por impresión generada.
   - *Probabilidad Condicionada:* P(Alta Influencia | Verificado, Nicho, Actividad).
2. **Seguidores de Alto Valor:**
   - *Volumen de Actividad:* Total de interacciones emitidas por seguidor.
   - *Ratio de Calidad/Esfuerzo:* Proporción de interacciones de alto compromiso (Comentarios + Compartidos + Guardados) sobre el total.
   - *Reciprocidad Directa:* Indicador de seguimiento mutuo e interacciones cruzadas con los perfiles seguidos.

---

## 3. Arquitectura Propuesta de Datos y Resultados
- **Capa Cruda (`data/raw/`):** Inmutable, verificada con hashes SHA-256.
- **Capa Procesada (`data/processed/`):** Tablas limpias en formato Parquet o base SQLite/DuckDB local con normalización de caracteres (Latin1 a UTF-8).
- **Capa de Salidas (`data/outputs/`):** Datasets analíticos versionados (`ranking_influenciadores_v1.csv` y `ranking_seguidores_v1.csv`).
- **Capa de Conocimiento (`wiki/`):** Catálogo persistente (`index.md`), bitácora (`log.md`), objetivos y fichas analíticas de entidades.

---

## 4. Skills Reutilizables Necesarias
- `data-validator`: Validación automatizada de calidad, codificación, esquemas e integridad referencial.
- `network-metrics`: Computación de métricas de análisis de redes sociales (SNA) y centralidades.
- `engagement-scorer`: Algoritmo de ponderación y normalización de scores.
- `wiki-maintainer`: Auditoría y linting de la base de conocimiento Markdown.

---

## 5. Estrategia para Nuevos CSVs sin Pérdida de Histórico
- **Almacenamiento por Lotes:** Nuevos archivos se incorporan en carpetas versionadas (`data/raw/batch_YYYYMMDD/`).
- **Ingesta Idempotente:** Unión deduplicada mediante claves compuestas (`interaccion_id`, `(seguidor_id, seguido_id)`).
- **Versionado de Salidas:** Rankings etiquetados cronológicamente sin sobreescritura destructiva.

---

## 6. Fases de Implementación, Validaciones y Entregables
1. **Fase 1 (Diagnóstico):** Inventario, diccionarios, verificación SHA-256, AGENTS.md y plan de acción. *(Completada)*.
2. **Fase 2 (ETL y Limpieza):** Scripts deterministas en `src/` para normalización y ensamblaje de tablas analíticas en `data/processed/`.
3. **Fase 3 (Modelado de Red y Scoring):** Algoritmos de grafos, cálculo de métricas y exportación a `data/outputs/`.
4. **Fase 4 (Entrega y Visualización):** Dashboards interactivos locales en `dashboards/` y reportes en `reports/`.

---

## 7. Riesgos y Preguntas Pendientes
- **Tratamiento de Anomalías Temporales:** Definir si los eventos previos a la fecha de registro se excluyen o si se consideran válidos bajo el supuesto de simulación sintética.
- **Ventana de Corte:** Determinar si el análisis considerará todo el histórico o ventanas rodantes (ej. últimos 6 meses).

---

## 8. Punto de Decisión
Antes de comenzar la Fase 2, se requiere aprobar formalmente:
1. Las cuentas objetivo y la ponderación específica de "seguidor de alto valor".
2. El corte, ventana y tratamiento de las 1.098 publicaciones y 7.359 interacciones anómalas.
3. Las reglas de ingesta incremental para nuevos lotes y control de duplicados.
4. Las métricas base y la arquitectura local propuesta.
