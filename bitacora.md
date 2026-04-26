# Bitácora de Acciones - Proyecto Violencia Digital

## 2026-04-26

*   **Investigación Inicial:** 
    *   Exploración de la carpeta `context`. 
    *   Análisis del código en `Analisis_Data_Fase1_Fase2.ipynb` y lectura del `INFORME.md`. Se comprendió la metodología para evaluar el nivel de conocimiento y prevención sobre violencia digital, las fases del proyecto (Limpieza y Feature Engineering), y la transformación de datos cualitativos a numéricos usando `pandas`.
*   **Configuración del Entorno de Ejecución:**
    *   Inicialización del proyecto y creación del entorno virtual utilizando `uv` con Python 3.12 (`uv init --python 3.12`).
    *   Instalación de las dependencias requeridas (`pandas`, `openpyxl`, `numpy`) ejecutando el comando `uv add pandas openpyxl numpy`.
*   **Procesamiento de Dimensiones de Estudiantes:**
    *   Instalación de las librerías `matplotlib`, `seaborn` e `ipykernel` para la visualización de datos en el notebook.
    *   Creación del notebook `Analisis_Estudiantes.ipynb` en la nueva carpeta `notebooks/`.
    *   Se implementó la limpieza y normalización de dimensiones geográficas, demográficas y académicas (`Municipio`, `Grado`, `Entorno`, `Unidad Educativa`, `Idioma Materno`) y la creación de la columna `Dim_Rango_Edad` conservando la columna original de edad y sin modificar el género.
    *   Se añadieron visualizaciones intermedias (histogramas de los índices y gráficos de barras para las dimensiones) dentro del notebook.
    *   Configuración para exportar el DataFrame final resultante a la nueva carpeta `output/`.
    *   **Corrección de Bug (Dim_Rango_Edad):** Se ajustó la función de categorización de edad usando expresiones regulares (`re.findall`) debido a que las respuestas originales contenían texto como "11años" o "13 o 14 años", lo que causaba un error en la conversión a número entero y clasificaba casi todo como "No Reportado".

*   **Procesamiento de Dimensiones de Docentes:**
    *   Creación del notebook `Analisis_Docentes.ipynb` en la carpeta `notebooks/`.
    *   Implementación de algoritmos de procesamiento para evaluar el **Índice de Conocimiento** (Preguntas 1, 2, 3, 4, 5, 6, 8, 12, 13, 14, 15) y el **Índice de Capacidades de Respuesta** (Preguntas 16, 21, 22) de los educadores, aplicando mapeos categóricos y binarios según la naturaleza de cada pregunta.
    *   Limpieza y normalización de dimensiones clave: `Municipio`, `Unidad Educativa`, `Nivel`, `Experiencia`, `Materia`, `Género`, `Indígena`, `Idioma`.
    *   Configuración de exportación del DataFrame transformado a `output/df_docentes_final.xlsx`.
