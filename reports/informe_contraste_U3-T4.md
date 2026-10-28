# Informe de Contraste y Análisis Comparativo: Proyecto BI Asistido por AI (U3-T4)

**Asignatura:** Business Intelligence  
**Tarea:** U3-T4 Contraste proyecto BI asistido con IA  
**Estudiante:** Sabrina Adrian Zelaya  
**Fecha de Entrega:** 27 de Octubre de 2026  

---

## 1. ¿Qué observaciones y conclusiones puedes sacar al realizar este análisis y contraste?

Al contrastar la ejecución realizada en mi computadora contra la solución de referencia presentada en las capturas, se desprenden las siguientes observaciones clave:

1. **Persistencia formal del plan (`docs/action_plan.md` vs. Chat):**
   - *En la referencia:* El plan de acción completo se guardó como un archivo Markdown dedicado dentro de `docs/action_plan.md`. Esto permite que la respuesta conversacional sea limpia, ejecutiva y sintética (~15 líneas), enlazando directamente al artefacto.
   - *En mi resultado inicial:* El plan se volcó exhaustivamente en el cuerpo del chat y en un informe general, lo que sobrecargó la conversación.

2. **Certificación Criptográfica de Inmutabilidad (Hashes SHA-256):**
   - *En la referencia:* El agente certifica explícitamente: *"Los cinco archivos crudos conservan sus hashes SHA-256 originales"*. Es un estándar riguroso de auditoría que demuestra que `data/raw/` no sufrió modificaciones.
   - *En mi resultado:* Se respetó la inmutabilidad a nivel de diseño en `AGENTS.md`, pero no se reportó el checksum SHA-256 en el mensaje de cierre.

3. **Coincidencia Exacta en el Diagnóstico Numérico y Anomalías:**
   - Ambos sistemas detectaron de manera idéntica el volumen del dataset: **650 perfiles, 8.133 relaciones, 5.200 publicaciones y 35.810 interacciones**, con 0 campos vacíos y 0 referencias huérfanas.
   - Ambos identificaron las anomalías de los datos sintéticos: **1.098 publicaciones** previas al registro del autor, **7.359 interacciones** previas al registro del usuario actor, seguimientos con fechas inconsistentes y la ausencia de una fecha de corte común.

4. **Higiene de Repositorio y Versionado en Git (`README.md`):**
   - *En la referencia:* Cada carpeta (`dashboards/`, `reports/`, `skills/`, `src/`, `data/outputs/`, `data/processed/`) cuenta con su propio `README.md`. En Git esto evita que los directorios vacíos desaparezcan y le da contexto inmediato a cualquier colaborador.
   - *En mi resultado:* Se crearon carpetas vacías o se implementaron directamente subdirectorios de skills, omitiendo los `README.md` base.

5. **Claridad del Punto de Decisión:**
   - La referencia cierra con 4 preguntas operativas directas (cuentas objetivo, tratamiento de anomalías temporales, reglas para nuevos lotes y arquitectura local), permitiendo al evaluador aprobar el inicio de la Fase 2 en 30 segundos.

**Conclusiones:** Ambos enfoques comprendieron cabalmente el problema de negocio y el patrón de Karpathy (`llm-wiki.md`), pero la referencia evidencia un estándar superior de ingeniería de software al separar el plan en disco, documentar carpetas con `README.md` y certificar la integridad con SHA-256.

---

## 2. ¿Qué puedes sugerir para obtener un resultado más similar al presentado acá?

Para alinear el resultado al estándar de la referencia, se sugieren las siguientes pautas:

1. **Instruir la creación de un archivo de plan dedicado:** Indicar expresamente en el prompt: *"Crea el plan de acción detallado en `docs/action_plan.md` y entrega en el chat únicamente un resumen ejecutivo de máximo 15 líneas con enlaces a los archivos creados y los puntos de decisión"*.
2. **Estandarizar la inicialización de carpetas con `README.md`:** Añadir como instrucción: *"Toda subcarpeta generada (`dashboards/`, `reports/`, `skills/`, `src/`, `data/processed/`, `data/outputs/`) debe incluir un `README.md` explicativo antes de alojar código o datos"*.
3. **Solicitar verificación explícita de inmutabilidad mediante SHA-256:** Pedir al agente que calcule y reporte los hashes criptográficos de los archivos en `data/raw/` al finalizar el diagnóstico para certificar la inmutabilidad.
4. **Disciplina estricta de alcance (evitar sobre-entregas tempranas):** No adelantarse a crear subcarpetas complejas (`wiki/concepts/` o subskills individuales) antes de que el usuario apruebe formalmente el Punto de Decisión. Mantener la estructura limpia con `wiki/index.md`, `wiki/log.md`, `wiki/objectives.md` y `skills/README.md`.
5. **Auditoría temporal cruzada completa:** Instruir al modelo a cruzar fecha de registro con fecha de publicación, fecha de interacción y fecha de seguimiento.

---

## 3. ¿Cuál crees que es el mejor resultado entre los dos y por qué?

**Veredicto:** El resultado de la **Referencia** es el mejor para la fase de Diagnóstico y Arquitectura.

### Justificación:
1. **Persistencia y Arquitectura Formal:** Guardar el plan en `docs/action_plan.md` es la práctica correcta en ingeniería; un plan en el chat se desvanece al reiniciar la sesión, mientras que en `docs/` queda registrado en el historial de versiones del proyecto.
2. **Economía Cognitiva:** La respuesta ejecutiva de 15 líneas en la referencia respeta el tiempo del tomador de decisiones, presentando los hallazgos críticos y los 4 acuerdos pendientes sin fatiga visual.
3. **Integridad Criptográfica:** El uso de hashes SHA-256 aporta certeza técnica absoluta sobre la no alteración de los datos crudos.
4. **Higiene de Repositorio:** El uso de `README.md` en cada módulo asegura que el proyecto sea portable, limpio y listo para versionarse en Git sin directorios huérfanos.

*Nota de Mérito de la Computadora Local:* Aunque la referencia es mejor en estructura y sobriedad, la ejecución local aportó mayor detalle matemático en las fórmulas de scoring ponderado y el análisis de reciprocidad diádica del grafo (2.6%). La combinación ideal es aplicar la profundidad analítica local bajo el orden y la síntesis de la referencia.
