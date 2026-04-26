# Informe Técnico: Procesamiento de Datos - Proyecto de Violencia Digital

## 1. Planteamiento del problema inicial
El proyecto surge a partir de la incorporación del analista de datos a una iniciativa orientada a evaluar y mitigar la "Violencia Digital". El requerimiento central consiste en estructurar un procedimiento profesional y metodológico para evaluar el conocimiento y las capacidades preventivas de tres poblaciones clave: Estudiantes (Jóvenes), Docentes (Educadores) y Padres de Familia (Cuidadores).

La entidad contratante definió 6 **variables de evaluación** específicas, vinculando cada variable a un conjunto de preguntas exactas dentro de las encuestas aplicadas. El reto principal radica en tomar bases de datos crudas exportadas de la plataforma de encuestas y transformarlas en métricas accionables. Para ello, se solicitó el diseño de un plan de acción apalancado en **Python** para la limpieza y manipulación de los datos, y **Power BI** para la visualización e inteligencia de negocios final.

## 2. Análisis de datos de entrada
Para la elaboración del pipeline de procesamiento, se analizaron tres fuentes principales de información:
1. **Matriz de Requerimientos (Imagen):** Documento rector que dictamina qué preguntas corresponden a qué métricas. Por ejemplo, dictaminó que el "Conocimiento sobre violencia digital en estudiantes" se evalúa con las preguntas 22 a 26, y sus "Capacidades de prevención" con las preguntas 14, 15, 19, 20 y 27 a 31.
2. **Cuestionarios Físicos (`.docx`):** El análisis del documento original de la encuesta permitió descubrir la naturaleza de las preguntas. Se identificaron preguntas de opción múltiple de respuesta única, respuestas de selección múltiple y matrices de escala Likert (1 a 4). 
3. **Bases de Datos Crudas (`.xlsx`):** Al inspeccionar el archivo `BBDD_Estudiantes_dash.xlsx`, se identificaron retos técnicos comunes en datos de encuestas:
   - Nombres de columnas con caracteres invisibles o saltos de línea (ej. `\n(Puede marcar más de una opción)`).
   - Preguntas tipo "Matriz" (Q19 y Q27) que se exportan separándose en múltiples columnas por cada sub-ítem evaluado.
   - Respuestas almacenadas como cadenas de texto complejas en lugar de valores numéricos estandarizados.

## 3. Diseño del procesamiento
Para evitar la ineficiencia de procesar campos de texto directamente en Power BI, se diseñó una etapa de **Feature Engineering** (Ingeniería de Características) en Python usando la librería `pandas`. El procesamiento sigue estas lógicas algorítmicas:

*   **Identificación por Substrings:** Dado que las respuestas en Excel pueden variar por faltas de ortografía o formatos (`"a) Es cuando un adulto..."` vs `"Es cuando..."`), se utilizó la función `.lower()` combinada con la búsqueda de palabras clave (ej. `'adulto contacta' in texto`) para asignar puntajes de **1 (correcto/seguro)** o **0 (incorrecto/riesgoso)**.
*   **Extracción con Expresiones Regulares (Regex):** Para columnas de matriz Likert que contenían números y texto (ej. `"3 Sé bastante"`), se implementó `str.extract(r'(\d+)')` para aislar y sumar dinámicamente el valor numérico.
*   **Mapeo Estructural (Diccionarios):** Para respuestas cualitativas sin número (ej. `"Sé poco"`, `"Lo conozco bien"`), se programó una función de asignación (`if 'poco' in t: return 2`) que normaliza el texto a una escala de 1 a 4.
*   **Construcción de Índices:** Agrupación y suma matemática (`sum(axis=1)`) de las columnas procesadas para generar **Variables Compuestas** (`Indice_Conocimiento`, `Indice_Prevencion_Total`), resumiendo el rendimiento general del individuo en un solo número.

## 4. Resultados obtenidos
*   **Plan de Acción Estructurado:** Se generó y entregó un plan metodológico de 5 fases, justificando el uso de Python como motor de transformación de datos y Power BI como capa de visualización final.
*   **Resolución de Errores Críticos:** Se superaron problemas de entornos virtuales (`ModuleNotFoundError` de Pandas/Openpyxl) y discrepancias de nombres de columnas (`KeyError`) mediante inspección directa del Excel.
*   **Pipelines de Estudiantes Completados:** Se formularon exitosamente dos grandes módulos de código que procesan el **100% de los requerimientos para los Estudiantes**:
    1.  Cálculo de `Indice_Conocimiento` (evaluado sobre 5 puntos).
    2.  Cálculo de `Indice_Prevencion_Total` (evaluado sobre 47 puntos, abarcando comportamientos aislados y las dos matrices cognitivas completas).

## 5. Descripción del Notebook generado
El entregable central hasta el momento es el archivo **`Analisis_Data_Fase1_Fase2.ipynb`**. Este cuaderno de Jupyter actúa como el entorno de ejecución automatizado y está segmentado en bloques lógicos:

*   **Celda de Configuración:** Instala dinámicamente las dependencias requeridas (`%pip install pandas openpyxl`) e importa las librerías necesarias.
*   **Carga y Exploración:** Conecta las rutas locales hacia los archivos `.xlsx` (`df_estudiantes`, `df_docentes`, `df_padres`) y permite la visualización cruda de los encabezados para detectar formatos irregulares.
*   **Módulo de Conocimiento:** Contiene la función `evaluar_conocimiento()`, la cual transforma las 5 preguntas conceptuales de los jóvenes en puntuaciones binarias y devuelve el índice finalizado.
*   **Módulo de Prevención:** Alberga la función maestra `calcular_indice_prevencion_final()`, destacable por su robustez al procesar simultáneamente preguntas de opción múltiple, matrices de números extraídos por Regex (Q19) y matrices de texto convertidas lógicamente (Q27).

El Notebook está estructurado no solo como un archivo de código, sino como un documento replicable que recibirá, en fases posteriores, el tratamiento equivalente para las bases de datos de Docentes y Padres de familia, sirviendo como la "capa de oro" previa a la ingesta en Power BI.
