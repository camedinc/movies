# **Movies: Sistema de Recomendación de Películas**

Este proyecto implementa un **sistema de recomendación de películas** basado en **filtrado colaborativo** utilizando el dataset **MovieLens**. Se incluye un pipeline completo que abarca desde la carga y limpieza de datos hasta la implementación de un modelo basado en **SVD (Singular Value Decomposition)**, para generar recomendaciones personalizadas.

---

## **Índice**

1. [Descripción General](#1-descripción-general)  
2. [Estructura del Proyecto](#2-estructura-del-proyecto)  
3. [Requisitos del Sistema](#3-requisitos-del-sistema)  
4. [Pipeline del Proyecto](#4-pipeline-del-proyecto)  
5. [Instrucciones de Uso](#5-instrucciones-de-uso)  
6. [Ejemplo de Resultados](#6-ejemplo-de-resultados)  
7. [Referencias y Créditos](#7-referencias-y-créditos)  

---

## **1. Descripción General**

Los sistemas de recomendación son herramientas esenciales para personalizar la experiencia del usuario en plataformas digitales. Este proyecto aplica técnicas de **filtrado colaborativo** para analizar patrones de preferencia de los usuarios y recomendar películas basándose en sus valoraciones previas.

### **Objetivos principales**
- Implementar un modelo de recomendación eficiente.  
- Evaluar el modelo con métricas estándar, como RMSE.  
- Generar recomendaciones personalizadas para cualquier usuario del dataset.  

---

## **2. Estructura del Proyecto**

El proyecto está organizado de manera modular para garantizar claridad y escalabilidad:

```
Movies/
│
├── data/
│   ├── movies.csv          # Información de las películas (ID, título, géneros).
│   ├── ratings.csv         # Valoraciones de los usuarios (usuario, película, rating).
│   └── README.md           # Descripción del dataset (opcional).
│
├── src/
│   ├── data_loader.py      # Clase para cargar datos.
│   ├── data_cleaner.py     # Clase para limpiar y procesar datos.
│   ├── visualizer.py       # Herramientas para visualización (histogramas, etc.).
│   ├── recommender.py      # Implementación del modelo de recomendación.
│   ├── evaluation.py       # Evaluación del modelo (RMSE, métricas adicionales).
│   └── utils.py            # Funciones auxiliares (configuración, helpers).
│
├── notebooks/
│   └── main.ipynb          # Notebook principal con el pipeline integrado.
│
├── results/
│   ├── visualizations/     # Gráficos generados (opcional).
│   └── predictions.csv     # Resultados de las predicciones (opcional).
│
├── requirements.txt        # Dependencias del proyecto.
└── README.md               # Documentación principal.
```

---

## **3. Requisitos del Sistema**

### **Software necesario**
- **Python:** Versión 3.8 o superior.  
- **Dependencias:** Se detallan en el archivo `requirements.txt`. Instálalas ejecutando:

```bash
pip install -r requirements.txt
```

### **Librerías principales**
- `pandas`: Manipulación de datos.  
- `matplotlib`: Visualización de datos.  
- `surprise`: Modelos de recomendación basados en SVD.  
- `scipy`: Estadísticas avanzadas.

### **Dataset**
Descarga el dataset [MovieLens](https://grouplens.org/datasets/movielens/) y colócalo en la carpeta `data/`.

---

## **4. Pipeline del Proyecto**

Este es el flujo de trabajo que sigue el proyecto:

1. **Carga de datos:**  
   Se cargan los archivos `movies.csv` y `ratings.csv` mediante la clase `DataLoader`.

2. **Limpieza y preprocesamiento:**  
   - Eliminación de duplicados y valores nulos.  
   - Unión de las tablas `movies` y `ratings`.  

3. **Análisis exploratorio:**  
   Se generan visualizaciones como histogramas para analizar la distribución de los ratings y la frecuencia de las películas más valoradas.  

4. **Entrenamiento del modelo:**  
   - Implementación de **SVD** utilizando la librería `surprise`.  
   - División de datos en entrenamiento y validación.  
   - Evaluación del modelo con métricas como RMSE.  

5. **Generación de recomendaciones:**  
   - Obtención de predicciones para usuarios específicos.  
   - Creación de rankings personalizados de películas.  

---

## **5. Instrucciones de Uso**

1. **Configura el entorno:**  
   Asegúrate de que las dependencias están instaladas y los datos están en la carpeta `data/`.

2. **Ejecuta el notebook principal:**  
   Abre y ejecuta el archivo `main.ipynb` para ejecutar el pipeline completo.

3. **Obtén recomendaciones personalizadas:**  
   Utiliza la función `recomendar_peliculas(usuario_id, n)` en el notebook para generar las `n` mejores recomendaciones para cualquier usuario.

4. **Explora los resultados:**  
   Visualiza las métricas de evaluación y las recomendaciones generadas en la carpeta `results/`.

---

## **6. Ejemplo de Resultados**

### **Métricas de evaluación**
- RMSE del modelo entrenado: **0.87**.  
  Esto indica una precisión aceptable para las predicciones de ratings.

### **Recomendaciones generadas**
Para el usuario **3070**, las recomendaciones generadas son:

| **Película**              | **Género**         | **Rating Estimado** |
|---------------------------|--------------------|---------------------|
| The Shawshank Redemption  | Drama             | 4.9                 |
| The Godfather             | Crime, Drama      | 4.8                 |
| Pulp Fiction              | Crime, Thriller   | 4.7                 |

### **Visualizaciones**
Se generan gráficos como el siguiente histograma de la distribución de ratings:  
![Histograma](results/visualizations/rating_distribution.png)

---

## **7. Referencias y Créditos**

- **Dataset:**  
  Proporcionado por [GroupLens Research](https://grouplens.org/datasets/movielens/).

- **Librerías:**  
  - `pandas` para análisis de datos.  
  - `surprise` para el modelo basado en SVD.  
  - `matplotlib` para visualización.

- **Inspiración:**  
  Este proyecto está inspirado en los sistemas de recomendación utilizados por plataformas como Netflix y Amazon.
