# Reporte de Preparación: Indicadores de Interculturalidad

Este reporte detalla el proceso de consolidación de los indicadores de interculturalidad para el proyecto de violencia digital, integrando datos de estudiantes, docentes y padres/cuidadores.

## 1. Objetivo
Unificar la variable de **Autoidentificación Cultural** en una única estructura de datos para permitir el análisis comparativo e interseccional en Power BI, facilitando la creación de mapas de calor geográficos exactos.

## 2. Fuentes de Datos
- **Docentes:** `raw_data/BBDD_Docentes_dash.xlsx` (Columna D5)
- **Padres/Cuidadores:** `raw_data/BBDD_Padres_dash.xlsx` (Columna P7)
- **Estudiantes:** `output/df_estudiantes_indicadores_COMPLETO.xlsx` (Columna Autoidentificación cultural)

## 3. Metodología de Procesamiento
Se implementó un pipeline en Python (`notebooks/05_Relacion_Interculturalidad.ipynb`) que realizó las siguientes tareas:

1.  **Homologación de Respuestas:** Estandarización de "Sí", "No" y "No responde".
2.  **Consolidación Long-Format:** Unión de las tres fuentes con la columna identificadora `Grupo`.
3.  **Georreferenciación Dual:**
    *   `Ubicacion_Mapa`: Columna descriptiva ("Municipio, Bolivia") para evitar ambigüedades.
    *   `Latitud` / `Longitud`: Coordenadas decimales precisas para los 5 municipios del estudio.
4.  **Indicador Numérico (Power BI Optimization):** Se creó la columna `Autoidentificacion_Numeric` (1 para Sí, 0 para No).

## 4. Resultados del Procesamiento (Counts)

| Grupo | Autoidentificación (Sí) | Autoidentificación (No) |
| :--- | :---: | :---: |
| **Docentes** | 84 | 103 |
| **Estudiantes** | 118 | 325 |
| **Padres** | 121 | 209 |

## 5. Recomendaciones para el Dashboard
- **Mapas Precisos:** Usar los campos `Latitud` y `Longitud` en el visual de Mapa para una ubicación satelital exacta.
- **Gráfico de Comparación:** Usar el promedio de `Autoidentificacion_Numeric` por `Grupo`.
- **Análisis por Nación:** Utilizar el TreeMap para visualizar la diversidad de naciones y pueblos indígenas originarios campesinos identificados.

---
**Archivo de salida:** `output/df_consolidado_interculturalidad.xlsx`
**Fecha de generación:** 2026-04-28 (Actualizado con coordenadas)
