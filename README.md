# Detección temprana de degradación en rodamientos usando señales de vibración

## Contexto

Este proyecto analiza señales de vibración del dataset NASA IMS Bearings para identificar cambios progresivos antes de una falla en rodamientos.

El foco está en transformar señales crudas en indicadores simples e interpretables que permitan observar cambios asociados a degradación.

## Objetivo

Transformar señales crudas de vibración en indicadores interpretables que permitan observar degradación progresiva y apoyar decisiones de mantenimiento predictivo.

## Dataset

Se utiliza el dataset NASA IMS Bearings, correspondiente a ensayos run-to-failure en rodamientos instrumentados con sensores de vibración.

Fuente del dataset:

https://data.nasa.gov/dataset/ims-bearings

Los datos originales no se incluyen en este repositorio por tamaño. Deben descargarse desde la fuente original y ubicarse manualmente en la carpeta:

```text
data/raw/
```

Para este análisis se trabajó con el experimento:

```text
1st_test
```

y con el canal 5, asociado al Bearing 3.

## Estructura del proyecto

```text
IMS_Bearing_Project/
│
├── data/
│   ├── raw/
│   └── processed/
│
├── notebooks/
│   └── 01_ims_bearing_analysis.ipynb
│
├── outputs/
│   ├── figures
│   └── tables/
│
└── README.md
```

## Metodología

El análisis sigue una línea simple:

1. Carga de señales crudas de vibración.
2. Selección de un experimento y un canal de análisis.
3. Comparación de señales al inicio, mitad y final del experimento.
4. Extracción de indicadores estadísticos por archivo.
5. Análisis temporal de indicadores.
6. Análisis simple en frecuencia mediante FFT.
7. Cálculo de energía por bandas de frecuencia.
8. Modelo exploratorio para separar etapa normal y degradada.
9. Interpretación operacional orientada a mantenimiento predictivo.

## Indicadores utilizados

Los principales indicadores calculados fueron:

- RMS
- Desviación estándar
- Máximo absoluto
- Kurtosis
- Energía por bandas de frecuencia

Estos indicadores permiten resumir señales de alta frecuencia en variables más simples y comparables en el tiempo.

## Resultado esperado

El objetivo es identificar patrones de cambio antes de la falla y conectar estos indicadores con decisiones de mantenimiento predictivo.

El valor principal del análisis está en observar señales tempranas de degradación, no solo en detectar una falla cuando ya ocurrió.

## Limitaciones

Este proyecto es exploratorio. La etiqueta normal/degradado utilizada en el modelo fue definida a partir del tiempo y no desde una condición operacional medida directamente.

Además, el análisis se acotó a un experimento y a un canal asociado al Bearing 3. Para una aplicación industrial sería necesario incorporar más sensores, más experimentos y variables operacionales como carga, velocidad, historial de mantenimiento y condiciones de operación.

## Tecnologías utilizadas

- Python
- pandas
- numpy
- matplotlib
- scipy
- scikit-learn
- JupyterLab

## Nota operacional

Este enfoque es transferible a equipos rotatorios presentes en minería, como motores, bombas, ventiladores, correas transportadoras, chancadores y molinos.

La clave no es partir con modelos complejos, sino construir una primera capa de indicadores interpretables que ayuden a priorizar inspecciones, ajustar monitoreo y apoyar decisiones de confiabilidad.
