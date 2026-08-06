# Análisis de Atenciones de Urgencia 2025

<aside>

### Resumen Ejecutivo

Proyecto de análisis y visualización de datos aplicado al área de salud, desarrollado utilizando Python, Pandas y Plotly Express.

El objetivo fue explorar el comportamiento de las atenciones de urgencia registradas durante el año 2025 en Chile, identificando tendencias temporales, distribución territorial, causas de atención predominantes y diferencias según grupos etarios.

El proyecto incluyó procesos de limpieza de datos, transformación de variables, análisis exploratorio y desarrollo de visualizaciones interactivas orientadas a facilitar la interpretación de información sanitaria.

</aside>

<aside>

### Objetivos del Proyecto

- Analizar el comportamiento de las atenciones de urgencia a nivel regional.
- Identificar períodos de mayor demanda asistencial.
- Explorar las principales causas de atención registradas.
- Evaluar diferencias en atenciones según grupos etarios.
- Desarrollar visualizaciones interactivas para comunicar hallazgos de manera clara y efectiva.
</aside>

### Preguntas Orientativas.

1. ¿Qué regiones presentan mayor número de atenciones?
2. ¿Cuáles fueron los meses con mayor demanda de urgencias?
3. ¿Qué causas de atención son más frecuentes?
4. ¿Cómo varían las atenciones según grupo etario?

<aside>

### Base de dato utilizado:

- **Nombre Archivo:** Atenciones Urgencias 2025 .csv
- **Fuente :** Departamento de Estadísticas e Información de Salud (DEIS)
- **Descripción:** Dataset hospitalario estructurado correspondiente a atenciones de urgencias hospitalarias del año 2025, utilizado con fines de análisis y visualización en un contexto profesional.
</aside>

<aside>

### Herramientas Utilizadas

1. Python
2. Pandas
3. Plotly Express
4. Jupyter Notebook
5. Análisis Exploratorio de Datos (EDA)
6. Limpieza y transformación de datos
7. Visualización interactiva
</aside>

## Proceso de Trabajo

<aside>

#### 1. Preparación y limpieza de datos

Se realizó la importación y validación del dataset, corrigiendo problemas de codificación, normalización de nombres geográficos y estandarización de variables categóricas.

También se trabajó en:

- manejo de valores inconsistentes,
- conversión de fechas,
- agrupación de categorías,
- y optimización de variables para análisis visual.

Extracto de códigos utilizados: 

```python
## Limpieza y estandarización de datos.
df["NombreRegion"] = df["NombreRegion"].str.strip()

df["NombreRegion"] = df["NombreRegion"].replace({
    "Metropolitana de Santiago": "Metropolitana",
    "De TarapacÃ¡": "Tarapacá",
    "De Los RÃ\xados": "Los Ríos",
    "De La AraucanÃ\xada": "Araucanía"
})
```

</aside>

<aside>

### 2. Análisis Exploratorio

Se desarrolló un análisis inicial para comprender:

- estructura del dataset,
- tipos de variables,
- distribución de datos,
- registros faltantes,
- y comportamiento general de las atenciones.

Esto permitió definir las variables más relevantes para el desarrollo de visualizaciones y análisis posteriores.

Extracto de códigos utilizados: 

```python
 #Análisis agregado de urgencias
 urgencias_mes = df.groupby("Mes")["Total"] \
    .sum() \
    .reset_index()
 #Análisis regional
 region_total = df.groupby("NombreRegion")["Total"] \
    .sum() \
    .reset_index() \
    .sort_values(by="Total", ascending=False)
```

</aside>

<aside>

### 3. Desarrollo de Visualizaciones

Se construyeron distintos gráficos interactivos utilizando Plotly, incluyendo:

- gráficos para tendencias temporales,
- histogramas para distribución de atenciones,
- gráficos de barras comparativas,
- análisis por grupos etarios, etc.

Las visualizaciones fueron diseñadas con enfoque ejecutivo y orientadas a facilitar la lectura e interpretación de resultados.

Extracto de códigos utilizados: 
ectura e interpretación de resultados.

Extracto de códigos utilizados: 

```python
#Visualización de causas y grupos etarios
fig = px.histogram(
    edad_df,
    x="Grupo_Etario",
    y="Cantidad",
    color="GlosaCausa",
    barmode="group",
    title="Principales Causas de Atención según Grupo Etario")
fig.show()
#Visualizción interactiva de tendencia temporal
fig = px.line(
    urgencias_mes, ........
```

<aside>

## Principales Hallazgos

#### 1. Tendencia temporal de urgencias

Se identificaron variaciones mensuales relevantes en la demanda de atenciones de urgencia durante el año 2025, observándose períodos con mayor presión asistencial.

#### 2. Distribución regional

Las regiones con mayor concentración poblacional presentaron también los mayores volúmenes de atenciones registradas.

#### 3. Principales causas de atención

Las causas respiratorias y traumatológicas concentraron una proporción importante de las atenciones de urgencia analizadas.

#### 4. Diferencias por grupo etario

La mayor cantidad de atenciones se concentró en población entre 15 y 64 años, aunque ciertos patrones específicos variaron según causa de atención

<aside>

### Impacto y Aplicación

Este tipo de análisis permite:

- apoyar procesos de toma de decisiones en salud,
- identificar tendencias epidemiológicas,
- visualizar presión asistencial,
- y mejorar la comunicación de información clínica y operativa.

Además, demuestra el potencial de las herramientas de análisis de datos para transformar información sanitaria en conocimiento accionable.

</aside>

<aside>

### Competencias Aplicadas

- Análisis de datos en salud
- Limpieza y transformación de datos
- Visualización de datos
- Storytelling con datos
- Interpretación de información sanitaria
- Python aplicado a salud
- Desarrollo de dashboards y reportes visuales
</aside>

<aside>


### Tecnologías

| Tecnología | Uso |
| --- | --- |
| Python | Análisis y procesamiento de datos |
| Pandas | Limpieza y manipulación de datos |
| Plotly Express | Visualización interactiva |
| Jupyter Notebook | Desarrollo y documentación del análisis |
</aside>

### Conclusión

La visualización de datos constituye una herramienta clave para transformar información compleja en conocimiento comprensible y útil para la gestión sanitaria.

Este proyecto permitió integrar análisis exploratorio, limpieza de datos y visualización interactiva para comunicar patrones relevantes asociados a las atenciones de urgencia en Chile durante 2025.

La combinación de herramientas como Python, Pandas y Plotly Express facilita la generación de análisis dinámicos, escalables y orientados a la toma de decisiones basadas en datos.
