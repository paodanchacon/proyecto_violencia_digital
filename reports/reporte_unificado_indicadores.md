# Reporte Unificado de Indicadores: Análisis de Violencia Digital e Interseccionalidad

**Proyecto:** Análisis de Violencia Digital (Estudiantes, Docentes y Padres)  
**Fecha:** 29 de abril de 2026  
**Documentación:** Consolidado de Notebooks 04, 05 y Resultados Power BI  

---

## 1. Introducción
Este reporte unifica los hallazgos obtenidos tras el procesamiento avanzado de datos (Python) y la visualización estratégica (Power BI). Se analizan las dimensiones de género, zona geográfica e interculturalidad para identificar vulnerabilidades específicas en el entorno digital de las unidades educativas intervenidas.

## 2. Metodología de Procesamiento (Estructura Técnica)

El trabajo se centró en la limpieza y normalización de variables complejas mediante los notebooks **04** y **05**:

*   **Notebook 04 (Preparación de Indicadores):** 
    *   Transformación de respuestas cualitativas (ej. "Sí, una o dos veces") en indicadores binarios numéricos (`ind_victimizacion_digital`).
    *   Homologación de la **Frecuencia de Uso** en 4 categorías estándar (< 1h, 1-3h, 3-6h, > 6h).
    *   Limpieza de la variable **Género** para asegurar comparabilidad.

*   **Notebook 05 (Relación Interculturalidad):**
    *   Procesamiento del indicador: **% de participantes que se autoidentifican con una nación o pueblo indígena originario**.
    *   Consolidación de una tabla unificada con los tres estamentos de la comunidad educativa (**Padres, Estudiantes y Docentes**).
    *   Georreferenciación de datos mediante el mapeo de municipios (La Paz, El Alto, Palca, Villa Montes, Santa Cruz) con coordenadas geográficas para análisis espacial.

---

## 3. Resultados y Hallazgos Principales (Dashboard Power BI)

A continuación se detallan los indicadores clave visualizados en el reporte unificado:

### I. Victimización y Brecha de Género
*   **Tasa Global de Victimización:** **19.52%** de los estudiantes reportan haber recibido comentarios sexualizados o burlas.
*   **Brecha de Género:** Las estudiantes mujeres presentan una tasa de victimización significativamente superior a los varones.
*   **Factor de Riesgo:** Existe una correlación directa entre el tiempo de conexión y la victimización, siendo los usuarios de **más de 6 horas** los más vulnerables.

### II. Presión por Envío de Contenido Íntimo (CSEA)
*   **Prevalencia:** **12.79%** de los encuestados sintieron presión para enviar fotos personales o íntimas.
*   **Foco Territorial:** El municipio de **Palca** destaca como la zona con mayor incidencia reportada en este indicador.
*   **Interseccionalidad:** Se observa una mayor vulnerabilidad en mujeres de zonas rurales/periurbanas.

### III. Brecha de Autonomía y Permisos
*   **Igualdad de Permisos:** Aunque el **75.4%** percibe igualdad, persiste un **24.6%** de brecha.
*   **Desigualdad Geográfica:** Las zonas **rurales** muestran una brecha de permisos más acentuada en comparación con las urbanas.
*   **Género:** Los varones reportan percibir mayores libertades o menores controles parentales en comparación con las mujeres.

### IV. Conocimiento de Riesgos (Grooming, Sextorsión, Deepfakes)
*   **Nivel de Alfabetización:** El conocimiento sobre *Ciberacoso* es alto, pero existe una brecha crítica en el término *Deepfake*, especialmente en zonas rurales.
*   **Incidencia por Zona:** Las zonas periurbanas y urbanas reportan mayor conocimiento técnico, pero también mayor exposición a estos riesgos.

### V. Acceso a la Justicia y Denuncia
*   **Desconocimiento Crítico:** El **37.22%** de los estudiantes **NO SABE** a dónde acudir para denunciar un caso de violencia digital.
*   **Disparidad Municipal:** 
    *   **Villa Montes** presenta el mayor nivel de conocimiento sobre mecanismos de denuncia.
    *   **Palca** muestra el nivel más bajo de información, señalando una necesidad urgente de campañas institucionales en esta zona.

---

## 4. Conclusiones Estratégicas
1.  **Vulnerabilidad Geográfica:** Palca y las zonas rurales requieren intervención prioritaria en prevención de CSEA y alfabetización sobre rutas de denuncia.
2.  **Riesgo por Exposición:** Las campañas de prevención deben enfocarse en la gestión del tiempo y herramientas de privacidad para usuarios intensivos (>6 horas).
3.  **Barreras Culturales:** La autoidentificación cultural influye en la percepción de seguridad y conocimiento de derechos; el 37% de ignorancia sobre rutas de denuncia es una barrera sistémica para el acceso a la justicia.

---
*Reporte generado automáticamente - Consolidación de Análisis de Datos e Insights de Visualización.*
