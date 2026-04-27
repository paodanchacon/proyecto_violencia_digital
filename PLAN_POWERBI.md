# Plan de Trabajo: Dashboard de Violencia Digital en Power BI

Este documento detalla la estrategia paso a paso para construir un dashboard profesional en Power BI utilizando los datos de la "Capa de Oro" (`df_estudiantes_final.xlsx`, `df_docentes_final.xlsx`, `df_padres_final.xlsx`). El objetivo es maximizar la interpretabilidad de los índices de **Conocimiento** y **Prevención/Capacidades** en las tres poblaciones.

## Fase 1: Importación y Modelado de Datos (Data Modeling)

Dado que todo el pre-procesamiento complejo ya se realizó en Python, esta fase en Power BI será muy ágil.

1.  **Importación Directa:** Cargar los tres archivos `.xlsx` desde la carpeta `output/`.
2.  **Modelo de Datos:**
    *   Se mantendrán inicialmente como tres **Tablas de Hechos independientes** (Estudiantes, Docentes, Padres) debido a que cada población tiene métricas de evaluación distintas.
    *   **Dimensión Transversal (Opcional pero Recomendada):** Crear una tabla desconectada de dimensión compartida `Dim_Unidad_Educativa` (con un ID único) para poder filtrar las tres tablas de manera simultánea al hacer análisis comparativos por colegio.
3.  **Creación de Medidas DAX Principales:**
    *   *Promedios:* `Promedio Conocimiento Estudiantes = AVERAGE('df_estudiantes'[Indice_Conocimiento])`
    *   *Promedios:* `Promedio Prevención Estudiantes = AVERAGE('df_estudiantes'[Indice_Prevencion])`
    *   *Y las medidas análogas para Docentes (Conocimiento / Capacidad de Respuesta) y Padres (Conocimiento / Acompañamiento).*

## Fase 2: Arquitectura y Diseño de la Interfaz (UI/UX)

Para lograr un dashboard premium con apariencia de aplicación web:

1.  **Estructura de Páginas (Navegación Web-like):**
    *   **0. Portada (Home):** Contexto del proyecto y KPIs agregados (total encuestados).
    *   **1. Vista Estudiantes:** Foco en vulnerabilidades y capacidades de los jóvenes.
    *   **2. Vista Docentes:** Foco en la preparación del entorno escolar.
    *   **3. Vista Padres:** Foco en las barreras y reglas del hogar.
    *   **4. Visión 360º (Unidad Educativa):** Una vista que contraste a los 3 actores de un mismo colegio.
2.  **Diseño Visual:**
    *   **Fondo Estático:** Diseñar un fondo limpio (en PowerPoint o Figma) e importarlo como "Page Background" para optimizar el rendimiento.
    *   **Navegación:** Un menú lateral (Sidebar) con botones usando *Page Navigation*.
    *   **Paleta de Colores:** Usar colores semánticos (ej. verde/azul para altos índices de prevención, amarillo/rojo para alertas o desconocimiento).

## Fase 3: Construcción de Visualizaciones Clave

Para proyectar las variables, utilizaremos los siguientes gráficos cruzados con las dimensiones pertinentes:

### A. Vista Estudiantes
*   **Métricas principales:** Tarjetas (Cards) con el Promedio de Conocimiento y Promedio de Prevención.
*   **Relación Conocimiento vs Prevención:** *Scatter Plot* (Gráfico de dispersión) para ver si a mayor conocimiento hay mayor prevención.
*   **Dimensiones críticas:**
    *   *Gráfico de Barras:* Índice promedio por **Rango de Edad** (¿Son los más jóvenes los más vulnerables?).
    *   *Gráfico de Columnas Clúster:* Índices cruzados por **Género** y **Entorno** (Rural vs Urbano).

### B. Vista Docentes
*   **Métricas principales:** Tarjetas con el Índice de Conocimiento y Capacidades de Respuesta.
*   **Dimensiones críticas:**
    *   *Gráfico de Barras:* Capacidades de respuesta desglosadas por **Experiencia** (¿Los docentes más nuevos están mejor preparados digitalmente?).
    *   *Gráfico de Anillo/Dona:* Nivel de enseñanza (**Nivel**) vs Nivel de conocimiento.
    *   *Matriz (Tabla de Calor):* Índice de Conocimiento vs **Materia** impartida.

### C. Vista Padres / Cuidadores
*   **Métricas principales:** Tarjetas con el Índice de Conocimiento y Acompañamiento Familiar.
*   **Dimensiones críticas:**
    *   *Gráfico de Barras Horizontales:* Acompañamiento Familiar cruzado por **Grado de Instrucción** y **Zona**.
    *   *Gráfico de Barras Apiladas:* Índices según la **Relación** (Madres vs Padres vs Abuelos).
    *   *Gráfico de Cascada (Waterfall) o Líneas:* Evolución del acompañamiento según la **Edad** del cuidador o la cantidad de hijos.

### D. Mapas de Calor (Matrices con Formato Condicional)
Los mapas de calor son excepcionales para identificar visual y rápidamente "focos rojos" al cruzar dos variables demográficas. Se logran usando el visual de **Matriz (Matrix)** y aplicando "Formato Condicional" al fondo de los valores:
*   **Estudiantes:** Filas = `Dim_Grado`, Columnas = `Dim_Genero`, Valores = Promedio de **Índice de Prevención** (Rojo = bajo, Verde = alto).
*   **Docentes:** Filas = `Dim_Materia`, Columnas = `Dim_Nivel`, Valores = Promedio de **Capacidades de Respuesta**.
*   **Padres:** Filas = `Dim_Instruccion`, Columnas = `Dim_Zona`, Valores = Promedio de **Acompañamiento Familiar**.

### E. Mapas de Calor Geográficos (Filled Maps / Shape Maps)
Ideales para la **Visión 360º** o como filtros globales interactivos en el dashboard. Utilizan la dimensión espacial para colorear regiones según sus métricas de vulnerabilidad o conocimiento.
*   **Mapa de Municipios (Filled Map):** 
    *   **Ubicación:** `Dim_Municipio` (Clasificado en PBI como "Ciudad" o "Municipio").
    *   **Color de relleno:** Promedio del `Índice de Conocimiento Global` (promediando a los 3 actores).
    *   *Uso:* Permite ver qué municipio de Bolivia concentra la mayor o menor preparación digital.
*   **Análisis Intra-Urbano (Zona/Entorno):**
    *   Se puede usar un gráfico de dona sobre el mapa geográfico o usar la dimensión `Dim_Zona` (Urbana/Rural/Periurbana) de los padres cruzada con el municipio para visualizar brechas digitales entre zonas de la misma ciudad.

## Fase 4: Interactividad Avanzada y Pulido
1.  **Tooltips de Página:** Crear páginas de Tooltip ocultas para mostrar desglose demográfico cuando el usuario pase el mouse por encima de un colegio específico.
2.  **Filtros (Slicers):** Un panel de filtros desplegable (usando *Bookmarks*) para no saturar el espacio de la pantalla. Filtros recomendados: Municipio, Unidad Educativa.
3.  **Ajustes de Formato:** Asegurar que todos los valores decimales estén formateados correctamente y ocultar las tablas crudas de la vista del reporte.
