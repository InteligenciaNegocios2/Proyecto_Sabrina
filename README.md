# Proyecto BI Asistido por AI — Influenciadores y Seguidores

**Organización:** InteligenciaNegocios2  
**Repositorio:** Proyecto_Sabrina  
**Asignatura:** Business Intelligence  
**Estudiante:** Sabrina Adrian Zelaya  
**Fecha:** 27 de Octubre de 2026  

---

## 📌 Descripción del Proyecto

Este repositorio implementa la fase de **diagnóstico, diseño arquitectónico y gobernanza** para un sistema local de Business Intelligence asistido por IA, enfocado en el análisis de redes sociales (influenciadores y seguidores).

La solución adopta el paradigma de **LLM-Wiki** propuesto por Andrej Karpathy (`docs/llm-wiki.md`), estructurando una base de conocimiento persistente, modular y gobernable por agentes inteligentes.

---

## 📂 Estructura del Repositorio

```text
Proyecto_Sabrina/
│
├── AGENTS.md                                   # Reglas de inmutabilidad, reproducibilidad y gobernanza
├── informe_contraste_U3-T4.md                  # Informe de análisis y contraste (U3-T4)
│
├── docs/                                       # Documentación técnica
│   ├── action_plan.md                          # Plan de acción detallado para aprobación
│   ├── data_dictionary.md                      # Diccionario técnico de datos y modelo E-R
│   └── llm-wiki.md                             # Guía metodológica de Andrej Karpathy
│
├── data/                                       # Capas de datos
│   ├── raw/                                    # Fuente de verdad inmutable (CSVs originales)
│   │   ├── diccionario_datos.csv
│   │   ├── interacciones.csv
│   │   ├── publicaciones.csv
│   │   ├── relaciones.csv
│   │   └── usuarios.csv
│   ├── processed/                              # Datasets limpios y transformados (README.md)
│   └── outputs/                                # Rankings finales y métricas consolidadas (README.md)
│
├── wiki/                                       # Base de conocimiento persistente
│   ├── index.md                                # Catálogo general y mapa de navegación
│   ├── log.md                                  # Bitácora cronológica append-only
│   ├── objectives.md                           # Objetivos y preguntas de negocio
│   └── concepts/                               # Páginas conceptuales
│       ├── influencia.md
│       ├── seguidores.md
│       ├── reciprocidad.md
│       └── ingesta_continua.md
│
├── skills/                                     # Capacidades analíticas modulares
│   ├── README.md
│   ├── data-validator/SKILL.md                 # Validación de calidad y codificación
│   ├── network-metrics/SKILL.md                # Métricas de redes y grafos (SNA)
│   └── wiki-maintainer/SKILL.md                # Linting y mantenimiento de la wiki
│
├── src/                                        # Código fuente de pipelines ETL (README.md)
├── reports/                                    # Informes de entrega y contrastes
│   ├── README.md
│   ├── informe_entrega.md                      # Informe de entrega general
│   └── informe_contraste_U3-T4.md              # Informe de evaluación comparativa
│
└── dashboards/                                 # Visualizaciones y paneles interactivos (README.md)
```

---

## 🎯 Preguntas Clave de Negocio
1. **¿Qué cuentas tienen mayor potencial de influencia?**  
   Evaluado mediante autoridad en el grafo (PageRank, in-degree), tracción de engagement ponderado y tasa de conversión sobre impresiones.
2. **¿Qué perfiles son seguidores de alto valor por actividad y reciprocidad?**  
   Identificación de usuarios comprometidos mediante volumen de interacciones, ratio de esfuerzo (comentarios/guardados/compartidos) y reciprocidad diádica.
3. **¿Cómo se gestionan los resultados al recibir nuevos datos?**  
   Estrategia de ingesta idempotente por lotes sin sobreescritura destructiva, preservando siempre el histórico crudo.

---

## 📄 Entregables Clave en este Repositorio
* **Informe de Contraste:** [`informe_contraste_U3-T4.md`](informe_contraste_U3-T4.md)
* **Plan de Acción:** [`docs/action_plan.md`](docs/action_plan.md)
* **Diccionario de Datos:** [`docs/data_dictionary.md`](docs/data_dictionary.md)
* **Protocolo de Gobernanza:** [`AGENTS.md`](AGENTS.md)
* **Catálogo de la Wiki:** [`wiki/index.md`](wiki/index.md)
