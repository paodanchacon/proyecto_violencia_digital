# Reporte de Preparación de Indicadores (Estudiantes)
**Proyecto:** Análisis de Violencia Digital
**Archivo de Origen:** `notebooks/04_Preparacion_Indicadores.ipynb`
**Fecha:** 27 de abril de 2026

---

## 1. Introducción
El presente reporte detalla el procesamiento de datos realizado sobre la encuesta de Estudiantes para el proyecto de Violencia Digital. El objetivo fue transformar las respuestas cualitativas en indicadores cuantitativos y categorías homologadas, permitiendo un análisis interseccional profundo (Género, Interculturalidad y Zona de Residencia) optimizado para su visualización en Power BI.

## 2. Procesos de Limpieza y Transformación
Se realizaron las siguientes tareas de ingeniería de datos:
*   **Homologación de Género (`genero_clean`)**: Unificación de categorías para comparativas estadísticas consistentes.
*   **Estandarización de Frecuencia de Uso (`frecuencia_uso_clean`)**: Clasificación en rangos de tiempo (Menos de 1h, 1-3h, 3-6h, más de 6h).
*   **Limpieza Geográfica (`zona_vivienda`)**: Clasificación de la zona de residencia en categorías Urbano/Rural/Periurbano.
*   **Conversión Numérica**: Transformación de escalas de respuesta (e.g., "Sí/No", niveles de conocimiento) a valores numéricos y escalas 0-100.

## 3. Indicadores Estratégicos Desarrollados
Se crearon 5 indicadores clave para medir la seguridad y violencia digital:

| Indicador | Descripción | Fuente |
|-----------|-------------|--------|
| **Victimización Digital** | % de estudiantes que reportan comentarios sexualizados o burlas. | Q21 |
| **Presión Contenido Íntimo** | Experiencia de presión para envío de material sensible. | Q20 |
| **Brecha de Permisos** | Diferencias de género en las reglas impuestas en el hogar. | Q43 |
| **Comprensión Técnica** | Nivel de conocimiento sobre riesgos (Grooming, Sextorsión, etc.). | Q22-Q27 |
| **Acceso a la Justicia** | Conocimiento de canales formales de denuncia. | Q49 |

## 4. Insights y Hallazgos Principales
*   **Desbalance Conocimiento vs. Acción**: Los estudiantes identifican los riesgos técnicos con relativa facilidad, pero muestran un desconocimiento crítico sobre los canales de denuncia.
*   **Impacto de la Conexión Intensiva**: Existe una correlación positiva entre el tiempo de conexión (>6 horas) y la frecuencia de incidentes de violencia digital.
*   **Ciberseguridad y Género**: El análisis de la brecha de permisos revela disparidades en el control parental que podrían condicionar la autonomía y resiliencia digital de las estudiantes.
*   **Vulnerabilidad ante IA**: El concepto de *Deepfake* es el menos comprendido entre los riesgos técnicos, representando un área de oportunidad para la prevención.

## 5. Entregables para Power BI
Se han generado dos archivos en la carpeta `/output`:
1.  `df_estudiantes_indicadores_COMPLETO.xlsx`: Base de datos total con indicadores.
2.  `df_estudiantes_indicadores_FILTRADO.xlsx`: Tabla optimizada con columnas demográficas y de resultados clave para el dashboard.

---
*Reporte generado automáticamente por Antigravity AI.*
