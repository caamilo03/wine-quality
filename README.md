# Análisis exploratorio y caracterización de variables fisicoquímicas asociadas a la calidad del vino

Proyecto de aula — **Fundamentos de Ciencia de Datos**  
Universidad de Antioquia · Ingeniería de Sistemas · Semestre 2026-1

**Autores:**  
- Jose Camilo Loaiza Hoyos — `camilo.loaiza1@udea.edu.co`  
- Sarai Restrepo Rodríguez — `sarai.restrepo@udea.edu.co`  

**Docente:** María Bernarda Salazar Sánchez, Ph.D.

---

## Descripción del proyecto

Este proyecto aplica un ciclo completo de ciencia de datos sobre el conjunto *Wine Quality* del UCI Machine Learning Repository (Cortez et al., 2009), que reúne mediciones fisicoquímicas de 6 497 muestras de vinos *Vinho Verde* portugueses (tintos y blancos) junto con evaluaciones sensoriales de calidad.

El análisis cubre cuatro unidades del curso:

1. **Comprensión y contextualización:** definición del problema, descripción del dataset, inspección inicial.
2. **Análisis exploratorio de datos (EDA):** análisis univariado, bivariado (correlaciones Pearson/Spearman, chi²) y multivariado (PCA).
3. **Detección de datos atípicos:** métodos IQR, Z-score, Isolation Forest y LOF.
4. **Preprocesamiento:** eliminación de duplicados, imputación KNN (demostración MCAR), transformación Yeo–Johnson y escalamiento StandardScaler.

---

## Estructura del repositorio

```
wine-quality/
├── datos/
│   ├── winequality-red.csv          # Dataset original — vino tinto (1 599 muestras)
│   ├── winequality-white.csv        # Dataset original — vino blanco (4 898 muestras)
│   └── procesados/
│       └── winequality_procesado.csv  # Dataset limpio, transformado y escalado
├── proyecto_aula/
│   └── proyecto_wine_quality.ipynb  # Notebook principal del proyecto
├── sesiones_practicas/
│   ├── sp_1_Camilo_Loaiza_Sarai_Restrepo.ipynb
│   ├── sp_2_Camilo_Loaiza_Sarai_Restrepo.ipynb
│   ├── sp_3_Camilo_Loaiza_Sarai_Restrepo.ipynb
│   ├── sp_4_Camilo_Loaiza_Sara_Restrepo.ipynb
│   └── sp_5_Camilo_Loaiza_Sarai_Restrepo.ipynb
├── articulo/
│   └── figuras/                     # Figuras exportadas para el artículo académico
└── README.md
```

---

## Cómo ejecutar el notebook

1. Clonar el repositorio:
   ```bash
   git clone https://github.com/caamilo03/wine-quality.git
   cd wine-quality
   ```

2. Instalar las dependencias:
   ```bash
   pip install -r requirements.txt
   ```

   Si prefieres instalar manualmente, usa:
   ```bash
   pip install numpy pandas matplotlib seaborn scipy scikit-learn joblib
   ```

   > Importante: instala los paquetes en el mismo intérprete o kernel que ejecuta el notebook. En VS Code, selecciona el kernel correcto antes de correr las celdas de importación.

3. Abrir el notebook principal:
   ```bash
   jupyter notebook proyecto_aula/proyecto_wine_quality.ipynb
   ```

   > El notebook también puede ejecutarse directamente en [Google Colab](https://colab.research.google.com/github/caamilo03/wine-quality/blob/main/proyecto_aula/proyecto_wine_quality.ipynb).

4. Ejecutar todas las celdas en orden. Las figuras se exportan automáticamente a `articulo/figuras/` y el dataset procesado a `datos/procesados/`.

---

## Dataset

- **Fuente:** UCI Machine Learning Repository — [Wine Quality](https://archive.ics.uci.edu/dataset/186/wine+quality)
- **Referencia:** Cortez, P., Cerdeira, A., Almeida, F., Matos, T., & Reis, J. (2009). Modeling wine preferences by data mining from physicochemical properties. *Decision Support Systems*, *47*(4), 547–553.
- **Licencia:** Uso libre para fines académicos y de investigación.

---

## Principales hallazgos

- `alcohol` es la variable con mayor correlación monótona con la calidad (ρ Spearman ≈ 0,45).
- PC1 del PCA separa nítidamente vinos tintos de blancos (27,5 % de la varianza explicada).
- El gradiente de calidad en el espacio PCA es difuso, lo que anticipa la necesidad de modelos no lineales.
- Se eliminaron 1 177 filas duplicadas exactas (18,1 % del conjunto crudo).
- La transformación Yeo–Johnson redujo drásticamente la asimetría de `residual sugar`, `chlorides` y `sulphates`.