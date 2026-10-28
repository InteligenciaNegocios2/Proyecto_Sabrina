---
name: wiki-maintainer
description: Skill para auditoría, linting, sincronización del índice y registro cronológico de la base de conocimiento wiki (patrón Karpathy).
---

# Wiki Maintainer Skill

## Propósito
Asegurar que la base de conocimiento persistente en `wiki/` se mantenga íntegra, libre de enlaces rotos, consistente con los últimos datasets ingresados y fiel a los estándares establecidos en `AGENTS.md`.

## Operaciones Principales
1. **Lint de Enlaces:** Escanea todos los archivos `.md` en busca de hipervínculos rotos o páginas huérfanas sin enlaces entrantes.
2. **Sync de `index.md`:** Verifica que toda nueva página creada en `wiki/` o `docs/` se encuentre debidamente catalogada con un enlace y un resumen descriptivo.
3. **Auditoría de `log.md`:** Verifica que los encabezados sigan el formato estándar `## [YYYY-MM-DD] <acción> | <resumen>`.
4. **Detección de Brechas de Información:** Alerta sobre conceptos técnicos o preguntas analíticas no cubiertas.
