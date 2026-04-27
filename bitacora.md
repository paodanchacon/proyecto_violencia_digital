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

*   **Procesamiento de Dimensiones de Padres/Cuidadores:**
    *   Creación del notebook `Analisis_Padres.ipynb` en la carpeta `notebooks/`.
    *   Implementación de algoritmos para evaluar el **Índice de Conocimiento sobre Seguridad Digital** (Preguntas 2, 3, 4, 5, 6) y el **Índice de Acompañamiento Familiar** (Preguntas 16, 18, 19, 20), mapeando frecuencias de acciones preventivas en el hogar y percepciones de riesgo.
    *   Limpieza y normalización de dimensiones sociodemográficas: `Municipio`, `Unidad Educativa`, `Nivel del Hijo`, `Relación` (con el estudiante), `Edad`, `Género`, `Indígena`, `Idioma`, `Instrucción`, `Zona` y `Número de Hijos`.
    *   Inclusión de visualizaciones intermedias, destacando el cruce entre la relación de cuidado y el género, así como la distribución por grado de instrucción y zona de residencia.
    *   Configuración de exportación a la capa de oro en `output/df_padres_final.xlsx`.

*   **Planificación del Dashboard:**
    *   Creación del documento `PLAN_POWERBI.md` detallando la estrategia en Power BI: Modelado de datos (uso directo de la Capa de Oro), arquitectura de navegación web, UI/UX, y definición de visualizaciones cruzando métricas de conocimiento/prevención con las dimensiones demográficas rescatadas para las tres poblaciones.

*   **Normalización de Índices (0 a 100):**
    *   Se actualizó el código en Python para los tres notebooks (`Analisis_Estudiantes.ipynb`, `Analisis_Docentes.ipynb`, `Analisis_Padres.ipynb`).
    *   Se añadieron las columnas normalizadas de Conocimiento y Prevención/Capacidades dividiendo sobre el máximo valor teórico y multiplicando por 100.
    *   Se volvieron a ejecutar los notebooks exportando los archivos finales a Excel con estas nuevas métricas, asegurando que el dashboard las lea uniformemente de 0 a 100.
