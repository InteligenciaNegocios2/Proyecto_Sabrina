# Metodología de Ingesta Continua y Gestión de Nuevos Datos

Garantizar la vigencia temporal del sistema sin comprometer la reproducibilidad ni el histórico exige una arquitectura de ingesta idempotente y versionada.

---

## Estrategia de Manejo de Nuevos CSVs

1. **Recepción en Lotes Temporales:**
   - Nuevos archivos se depositan con sufijos de lote (ejemplo: `data/raw/batch_20261101/` o prefijos `interacciones_20261101.csv`).
   - Los archivos crudos preexistentes permanecen intactos (principio de inmutabilidad).

2. **Deduplicación e Idempotencia en Capa Procesada (`data/processed/`):**
   - Inserción tipo `UPSERT` o unión con clave natural (`interaccion_id`, `publicacion_id`, `seguidor_id + seguido_id`).
   - Si un evento ya existía, se preserva su primera ocurrencia o se actualiza únicamente si hay corrección de estado.

3. **Cálculo Delta vs Reprocesamiento Completo:**
   - Para grafos medianos (< 100,000 usuarios), el reprocesamiento determinista completo asegura convergencia exacta de métricas globales como PageRank.
   - Para métricas acumulativas de engagement, se aplican ventanas temporales rodantes (ej. últimos 30 días, último trimestre, histórico total).

4. **Versionado de Salidas (`data/outputs/`):**
   - Cada ejecución de ranking genera un archivo fechado (ej. `ranking_influenciadores_20261027.parquet` o `.csv`) y un puntero de enlace simbólico o vista consolidada `latest`.
   - La wiki registra en `wiki/log.md` el volumen de nuevos registros incorporados y variaciones en el top 10.
