---
name: network-metrics
description: Skill para calcular métricas de análisis de redes sociales (SNA), centralidades, reciprocidad de enlaces y autoridad en el grafo de seguidores.
---

# Network Metrics Skill

## Propósito
Procesar la tabla de relaciones y transacciones para construir la representación del grafo dirigido y calcular las métricas cuantitativas que alimentan el ranking de influenciadores y de seguidores.

## Métricas Calculadas
1. **Grado de Entrada (`in_degree`):** Conteo de seguidores únicos recibidos por cada perfil.
2. **Grado de Salida (`out_degree`):** Conteo de cuentas que sigue cada perfil.
3. **Ratio Follower/Following:** Indicador estructural de asimetría relacional.
4. **PageRank / Eigenvector Centrality:** Medida de la calidad e importancia de quienes siguen a cada cuenta.
5. **Reciprocidad Diádica:** Identificación de pares $(u, v)$ donde ambos se siguen mutuamente.
6. **Densidad de Comunidad y Nicho:** Grado de conexión interna por nicho temático (`Gastronomía`, `Viajes`, etc.).
