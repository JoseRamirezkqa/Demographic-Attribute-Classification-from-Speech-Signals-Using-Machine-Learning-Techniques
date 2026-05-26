# Clasificación de Atributos Demográficos a partir de Señales de Voz mediante Técnicas de Machine Learning

## Descripción del Proyecto

Este proyecto desarrolla un modelo de Inteligencia Artificial capaz de clasificar atributos demográficos a partir de señales de voz utilizando técnicas de **Machine Learning supervisado**. Específicamente, se aborda la clasificación de **edad** y **género** mediante el análisis de características acústicas extraídas de grabaciones de voz.

El trabajo incluye la construcción del conjunto de características, el entrenamiento de distintos modelos de clasificación, la evaluación de su desempeño y el análisis de técnicas no supervisadas y de reducción de dimensionalidad para explorar la estructura de los datos.

---

## Objetivo

Desarrollar un modelo de Inteligencia Artificial que clasifique edad y género a partir de señales de voz utilizando aprendizaje supervisado y métricas de evaluación de desempeño.

---

## Motivación

En los centros de atención telefónica (*Call Centers*), adaptar la interacción al perfil del cliente puede mejorar significativamente la experiencia de servicio. Sin embargo, obtener información demográfica de manera directa no siempre es posible o conveniente.

Este proyecto propone una solución basada en el análisis automático de la voz para inferir atributos demográficos y apoyar la recomendación de categorías de atención, considerando la variabilidad acústica presente en las señales de voz.

---

## Dataset

El proyecto utiliza datos provenientes del corpus **Mozilla Common Voice**, uno de los conjuntos de datos abiertos más grandes para investigación en procesamiento de voz.

### Dataset original

🔗 https://datacollective.mozillafoundation.org/datasets/cmj8u3p26007dnxxbwyo07lb8#user-content-fn-1

### Tamaño del dataset

El conjunto de datos original contiene aproximadamente:

| Conjunto | Cantidad |
|-----------|-----------:|
| Entrenamiento | 355.918 grabaciones |
| Prueba | 15.897 grabaciones |
| Validación | 15.897 grabaciones |

Además, el corpus textual asociado contiene:

| Tipo | Cantidad |
|--------|-----------:|
| Oraciones totales | 1.087.200 |
| Oraciones validadas | 1.082.136 |
| Oraciones invalidadas | 5.064 |
| Oraciones reportadas | 2.643 |

Para este proyecto se realizó un proceso de filtrado y selección de registros que permitieran trabajar específicamente con las variables demográficas de interés.

---

## Características Extraídas

A partir de cada señal de voz se extrajeron descriptores acústicos utilizados posteriormente en los modelos de aprendizaje automático:

- RMS (Root Mean Square Energy)
- Zero Crossing Rate (ZCR)
- Pitch (Frecuencia Fundamental)
- 13 coeficientes MFCC (Mel-Frequency Cepstral Coefficients)

Estas características conforman el conjunto de variables utilizado para el entrenamiento y evaluación de los modelos.

---

## Metodología

### 1. Extracción de Características

Las grabaciones de voz son procesadas utilizando herramientas de análisis de audio para obtener características acústicas representativas.

### 2. Clasificación Supervisada

Se evaluaron diferentes algoritmos de aprendizaje supervisado:

- Gaussian Naive Bayes (GNB)
- Random Forest (RF)
- Support Vector Machine (SVM)

Los modelos fueron entrenados para las tareas de:

- Clasificación de género
- Clasificación de edad
- Clasificación de Acento

### 3. Aprendizaje No Supervisado

Con el objetivo de analizar la estructura inherente de los datos se implementaron técnicas de agrupamiento:

- K-Means
- DBSCAN
- Clustering Jerárquico

### 4. Reducción de Dimensionalidad

Se estudió el impacto de reducir la dimensionalidad del conjunto de características mediante:

- PCA (Principal Component Analysis)
- t-SNE (t-Distributed Stochastic Neighbor Embedding)

Posteriormente se evaluó si estas representaciones mejoraban el desempeño de los modelos de clasificación.

---

## Flujo General del Proyecto

```text
Audios
   │
   ▼
Extracción de Características
(RMS, ZCR, Pitch, MFCC)
   │
   ▼
Dataset de Características
   │
   ├──────────────┐
   ▼              ▼
Clasificación   Agrupamiento
Supervisada     No Supervisado
   │              │
   ▼              ▼
GNB           K-Means
RF            DBSCAN
SVM           Jerárquico
   │
   ▼
PCA / t-SNE
   │
   ▼
Evaluación de Resultados
```

---

## Estructura del Repositorio

```text
.
├── ProyectoIA.ipynb
├── ProyectoIA2.ipynb
├── No_supervizado.ipynb
├── df_features.csv
├── datos_finales.csv
├── modelos_preprocesados/
├── seleccionados/
├── resultados_backup/
└── README.md
```

### Descripción de los notebooks

| Archivo | Descripción |
|----------|------------|
| `ProyectoIA.ipynb` | Extracción de características y clasificación supervisada |
| `ProyectoIA2.ipynb` | Experimentos complementarios y evaluación de modelos |
| `No_supervizado.ipynb` | Clustering y reducción de dimensionalidad |

---

## Recursos Adicionales en Google Drive

Para facilitar la ejecución de los notebooks en Google Colab, algunos archivos procesados se encuentran alojados en Google Drive.

### Carpeta compartida

📁 https://drive.google.com/drive/folders/1K35YSXnIpGltAWtTyYPYXI7LPSYY5IYt?usp=sharing

### ¿Por qué se utiliza Google Drive?

Algunos archivos generados durante el proyecto tienen un tamaño considerable o requieren un tiempo significativo de procesamiento. Por esta razón, se almacenan externamente para:

- Reducir el tamaño del repositorio.
- Evitar reprocesamientos innecesarios.
- Disminuir los tiempos de ejecución.
- Facilitar la reproducción de los experimentos.

### Contenido de la carpeta

La carpeta incluye recursos tales como:

- Datasets procesados.
- Archivos de características extraídas.
- Modelos preprocesados.
- Resultados intermedios.
- Archivos auxiliares utilizados por los notebooks.

### Uso en Google Colab

```python
from google.colab import drive
drive.mount('/content/drive')
```

Una vez montado Google Drive, los notebooks pueden acceder directamente a los archivos previamente procesados sin necesidad de regenerarlos.

---

## Librerías Utilizadas

Las principales librerías empleadas en el desarrollo del proyecto son:

```bash
numpy
pandas
matplotlib
seaborn
scikit-learn
librosa
scipy
plotly
```

Instalación:

```bash
pip install -r requirements.txt
```

---

## Resultados

Los experimentos permiten comparar el desempeño de diferentes algoritmos de Machine Learning para la clasificación de atributos demográficos a partir de señales de voz.

Asimismo, se analiza el efecto de las técnicas de agrupamiento y reducción de dimensionalidad sobre la representación y separabilidad de los datos.

---

## Autor

**Jose David Ramirez Cacua**  
Estudiante de Ingeniería de Sistemas  
Universidad Industrial de Santander (UIS)

---

## Licencia

Este repositorio tiene fines académicos y de investigación.
