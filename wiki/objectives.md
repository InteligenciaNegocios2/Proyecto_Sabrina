# Objetivos y Preguntas de Negocio del Proyecto BI

Este documento establece el marco estratégico, las preguntas clave de negocio, los criterios analíticos de éxito y las hipótesis de trabajo para el proyecto de Business Intelligence asistido por IA sobre redes sociales.

---

## 1. Preguntas Estratégicas del Proyecto

### Pregunta 1: ¿Qué cuentas tienen mayor probabilidad de poseer alto potencial de influencia?
* **Propósito de Negocio:** Identificar qué usuarios dentro de la red tienen la capacidad demostrable de amplificar mensajes, movilizar audiencias y generar resonancia cuantitativa y cualitativa.
* **Componentes del Concepto de Influencia:**
  1. *Centralidad de Red (Estructural):* Grado de entrada o popularidad directa (`in-degree`), autoridad calculada en el grafo (PageRank o HITS Authority), y ratio de atracción de seguidores respecto a cuentas seguidas.
  2. *Capacidad de Tracción (Engagement Generado):* Volumen total y promedio de interacciones recibidas en sus publicaciones (`Me_gusta`, `Comentario`, `Compartido`, `Guardado`), ponderadas por esfuerzo cognitivo del seguidor.
  3. *Calidad y Eficiencia de Contenido:* Relación entre impresiones obtenidas, calidad técnica/temática declarada del contenido (`calidad_contenido`) y tasa de conversión de impresiones a interacción (Engagement Rate sobre Impresiones).
  4. *Potencial Predictivo / Bayesiano:* Probabilidad condicionada de pertenecer a la clase de alta influencia dados sus atributos de perfil (verificación, nicho temático, país, frecuencia de publicación).

### Pregunta 2: ¿Qué perfiles son seguidores de alto valor por actividad y reciprocidad?
* **Propósito de Negocio:** Segmentar a la audiencia de la red para reconocer a aquellos usuarios que no son simples espectadores pasivos, sino activos generadores de valor relacional (evangelizadores de marca o nodos fidelizados).
* **Componentes del Valor del Seguidor:**
  1. *Actividad Transaccional:* Frecuencia, constancia y volumen de interacciones emitidas (`out-degree` de engagement).
  2. *Profundidad del Engagement:* Ponderación de acciones de alto compromiso (ej. un comentario o compartido tiene un peso analítico superior a un like pasivo).
  3. *Reciprocidad de Red:* Existencia de lazos bidireccionales en el grafo (el seguidor sigue a una cuenta que a su vez lo sigue) e interacciones cruzadas en publicaciones recíprocas.
  4. *Fidelidad y Relevancia:* Dispersión de sus interacciones (¿apoya con lealtad a un nicho/creador específico o interactúa erráticamente?).

### Pregunta 3: ¿Cómo se gestionan y actualizan los resultados a medida que llegan nuevos datos?
* **Propósito de Negocio:** Garantizar que el sistema de BI no sea una foto estática y desechable, sino un sistema dinámico capaz de incorporar datos incrementales (nuevos CSVs de relaciones, posts o interacciones) manteniendo el linaje, la comparabilidad histórica y la consistencia de la wiki.
* **Requisitos Clave:**
  1. Preservación estricta del histórico crudo (inmutabilidad).
  2. Mecanismo de ingesta idempotente (evitar duplicación de eventos de seguimiento o interacciones).
  3. Versionado de datasets analíticos y métricas consolidadas (`data/processed/` y `data/outputs/`).
  4. Actualización automatizada de la Wiki mediante el patrón *Ingest-Lint*.

---

## 2. Supuestos, Limitaciones e Información Faltante

1. **Datos Sintéticos:** Las variables de calidad y coordenadas geográficas provienen de un proceso estocástico simulado. Existen pequeñas inconsistencias temporales (posts previos a la fecha de registro), las cuales no invalidan el modelo de red pero deben tratarse con cautela si se realizan análisis de cohortes temporales estrictas.
2. **Ausencia de Texto Real de Comentarios:** El dataset clasifica interacciones como `Comentario`, pero no incluye el texto libre del comentario ni análisis de sentimiento. La profundidad se medirá mediante pesos de esfuerzo transaccional.
3. **Ausencia de Costos o Monetización:** No se disponen de variables de ingresos o conversiones comerciales directas; el "valor" se modela estrictamente desde la perspectiva de capital relacional y engagement.
