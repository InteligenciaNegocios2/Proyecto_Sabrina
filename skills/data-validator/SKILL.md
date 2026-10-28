---
name: data-validator
description: Skill de validación de calidad, esquemas, codificación e integridad referencial para datasets crudos y procesados del proyecto BI.
---

# Data Validator Skill

## Propósito
Verificar automáticamente que cualquier conjunto de datos CSV en `data/raw/` o dataset procesado en `data/processed/` cumpla con los estándares de calidad definidos antes de ser utilizado por modelos o pipelines.

## Comprobaciones que Realiza
1. **Esquema y Nulos:** Comprobación de tipos aparentes y conteo de valores nulos o vacíos.
2. **Unicidad de Claves:** Validación de que claves primarias no contengan duplicados (`usuario_id`, `publicacion_id`, `interaccion_id`, `(seguidor_id, seguido_id)`).
3. **Integridad Referencial:** Detección de aristas o interacciones huérfanas sin usuario o post de origen.
4. **Codificación:** Alerta si el archivo contiene caracteres corruptos por diferencias entre UTF-8 y Latin-1.
5. **Consistencia Lógica:** Fechas de interacciones vs fechas de publicación y registro.
