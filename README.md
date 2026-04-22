# Anomalía de Bouguer completa – Procesamiento y evaluación

Este repositorio contiene los scripts desarrollados en Python como parte del flujo metodológico utilizado para el procesamiento y análisis de Bouguer completa en Costa Rica.

## Descripción general

El código implementa las etapas de preprocesamiento, cálculo gravimétrico y evaluación cuantitativa del desempeño de métodos de interpolación, en concordancia con la metodología del estudio.

## Flujo de trabajo

El proceso completo se estructura en las siguientes etapas:

1. **Georreferenciación de datos**
   - Transformación de coordenadas de estaciones gravimétricas de WGS84 a CR-SIRGAS.

2. **Cálculo de anomalía de Bouguer completa**
   - Aplicación de correcciones gravimétricas:
     - Gravedad normal
     - Corrección de aire libre
     - Corrección atmosférica
     - Corrección de curvatura (Bullard B)
     - Modelado del efecto topográfico (g_topo)
   - Obtención de la anomalía de Bouguer completa (BC).

3. **Interpolación espacial (externa)**
   - Generación de superficies continuas de BC mediante:
     - Kriging
     - Spline
   - Esta etapa se realiza en software externo (por ejemplo, ArcGIS Pro).

4. **Restauración y evaluación**
   - Muestreo de los ráster interpolados en las estaciones.
   - Restauración del campo gravitacional:
     - disturbance_restored
     - g_obs_restored
   - Comparación con valores observados originales.
   - Cálculo de métricas estadísticas:
     - Bias
     - MAE
     - RMSE

## Objetivo

Evaluar cuantitativamente el desempeño de los métodos de interpolación Kriging y Spline en la estimación del campo gravimétrico, a partir de la comparación entre valores observados y valores restaurados.

## 📂 Estructura del repositorio

- `Bouguer.Via.HARMONICA.py` → cálculo de anomalía de Bouguer completa  
- `Script.Estaciones.WGS84.a.SIRGAS.py` → transformación de coordenadas  
- `Script.DTM.WGS84.a.SIRGAS.py` → reproyección del modelo digital de terreno  
- `Restauracion + Metricas.py` → evaluación cuantitativa (restore + métricas)

## Notas

- La interpolación espacial no se realiza en Python dentro de este repositorio.
- Los ráster de entrada (Kriging y Spline) deben ser generados previamente.
- El análisis se basa en la comparación directa entre valores observados y valores derivados del proceso de interpolación y restauración.
