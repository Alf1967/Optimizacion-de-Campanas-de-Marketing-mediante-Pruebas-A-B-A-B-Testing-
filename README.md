# Optimización de Campañas de Marketing mediante Pruebas A/B (A/B Testing)

Este proyecto implementa un pipeline de datos robusto bajo el enfoque ETL (Extract, Transform, Load) utilizando Python para evaluar la significancia estadística de una nueva campaña de anuncios interactivos digitales frente a un grupo de control tradicional.

## 🎯 Enfoque del Negocio & Objetivos
Una plataforma de e-commerce masivo busca optimizar su Tasa de Conversión (Conversion Rate - CR). El objetivo estratégico es validar si los nuevos anuncios interactivos (`ad`) generan significativamente más ventas que los anuncios de servicio público base (`psa`), asegurando que la inversión en la nueva campaña esté respaldada por certezas matemáticas y no por fluctuaciones aleatorias del mercado.

## 🏗️ Arquitectura de la Solución (ETL Pipeline)
El código fue desarrollado en scripts puros de Python (`.py`) siguiendo buenas prácticas de ingeniería de software distribuidas en tres etapas esenciales:
*   **Extract:** Extracción automatizada del dataset crudo (`marketing_AB.csv`).
*   **Transform:** Limpieza de registros redundantes, manejo estricto de valores nulos con `dropna()` en variables clave y remoción de IDs de usuarios duplicados para evitar sesgos de tráfico.
*   **Load:** Carga de los datos curados en un repositorio local (`marketing_AB_clean.csv`) y exportación automática de reportes ejecutivos en texto plano.

---

## 📈 Línea Base del Experimento (Métricas Iniciales)

A partir de una muestra masiva de **588,101 usuarios únicos**, el proceso ETL consolidó las siguientes métricas de rendimiento del negocio:

| Grupo de Prueba | Total Usuarios (n) | Conversiones (x) | Tasa de Conversión (CR) |
| :--- | :--- | :--- | :--- |
| **ad** (Tratamiento) | 564,577 | 14,423 | **2.5547%** |
| **psa** (Control) | 23,524 | 420 | **1.7854%** |

---

## 🧪 Análisis Estadístico & Validación (Día 2)

Para validar la superioridad de la campaña se aplicó un **Z-Test de dos proporciones independientes** con un nivel de significancia $\alpha = 0.05$.

### Resultados del Modelo Estadístico:
*   **Z-Statistic (Valor Z):** 7.3701
*   **P-Value:** 8.5264e-14
*   **Confianza del Experimento:** 95%

### Rangos de Conversión Estimados (Intervalos de Confianza al 95%):
*   **Grupo Ad (Tratamiento):** [2.5135% a 2.5958%]
*   **Grupo Psa (Control):** [1.6162% a 1.9546%]
*   **🥇 Incremento Real Neto (Lift):** **[0.5951% a 0.9434%]**

### Conclusión Estratégica:
El P-Valor obtenido ($8.52 \times 10^{-14}$) es críticamente inferior al umbral de riesgo $\alpha$ ($0.05$). **Rechazamos contundentemente la Hipótesis Nula ($H_0$)**. La diferencia observada a favor del grupo `ad` está a más de 7 desviaciones estándar del promedio, demostrando con una certeza estadística absoluta que el nuevo formato publicitario interactivo es altamente efectivo.

Con un 95% de confianza, la implementación global de esta nueva campaña garantizará un **incremento neto de conversión de entre el 0.59% y el 0.94%**. A gran escala, esto representa un aumento masivo en el volumen de transacciones y un retorno de inversión publicitaria garantizado.

---

## 📊 Visualización e Insights en Tableau
El dataset transformado por la tubería ETL fue conectado directamente a **Tableau** para la creación de un Dashboard Ejecutivo Interactivo. 

### Componentes Clave del Cuadro de Mando:
1.  **Bloques de KPIs Operativos:** Visualización en tiempo real del volumen total de tráfico evaluado y volumen neto de éxitos.
2.  **Análisis de Tasa de Conversión con Línea de Referencia:** Gráfico de barras horizontales que contrasta visualmente el rendimiento del grupo de tratamiento, marcando de forma explícita el umbral base del grupo de control (1.79%) como meta mínima superada.
3.  **Monitoreo del Balance del Experimento:** Gráfico de distribución de tráfico segmentado por el día de mayor impacto publicitario (`most ads day`), validando que la asignación de usuarios por los algoritmos de marketing se ejecutó de forma balanceada y homogénea a lo largo de toda la semana.

---

## 🛠️ Tecnologías Utilizadas
*   **Python 3** (Pandas, NumPy)
*   **Statsmodels** (Proportions Z-Test, Confidence Intervals)
*   **Tableau Desktop / Public** (Business Intelligence & Data Visualization)

## 📊 Dashboard en Tableau
Puedes interactuar con el Dashboard ejecutivo final directamente en mi perfil de Tableau Public a través del siguiente enlace:

https://public.tableau.com/views/ResumenejecutivoABTesting/Dashboard_Impacto_Marketing?:language=en-US&:sid=&:redirect=auth&:display_count=n&:origin=viz_share_link
