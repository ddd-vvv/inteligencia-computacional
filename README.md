# Inteligencia Computacional (EL4106)

Tareas y proyecto final del curso **EL4106 – Inteligencia Computacional**, Departamento de Ingeniería Eléctrica, Universidad de Chile (semestre Otoño 2024).

- **Profesor del curso:** Javier Ruiz del Solar
- **Auxiliar:** Patricio Loncomilla Z.

El curso cubre clasificación de patrones, deep learning y clustering aplicados a problemas de ingeniería eléctrica. Este repositorio reúne mis soluciones: cinco tareas computacionales y un proyecto final. Cada una incluye el enunciado, los datos, el notebook y el informe en PDF.

## Contenido

| Carpeta | Tema | Técnicas | Dataset |
|---|---|---|---|
| [`Tarea_1`](Tarea_1) | Clasificadores bayesianos | Naive Bayes, Gaussiana multivariada, curvas ROC y Precision-Recall | MAGIC Gamma Telescope (UCI) |
| [`Tarea_2`](Tarea_2) | Support Vector Machines | Kernels lineal, polinomial y gaussiano, búsqueda de hiperparámetros | Wine Quality (UCI) |
| [`Tarea_3`](Tarea_3) | Selección de características | Métodos wrapper y de filtro, SVM lineal, Random Forest | Heart Disease, Cleveland (UCI) |
| [`Tarea_4`](Tarea_4) | Redes neuronales | MLP en PyTorch, ReLU vs Tanh, 10 vs 40 neuronas, 1 vs 2 capas | Dígitos escritos a mano (imágenes 8x8, 64 características) |
| [`Tarea_5`](Tarea_5) | Clustering | K-Means, DBSCAN, clustering jerárquico aglomerativo, PCA | Mice Protein Expression, Data Cortex Nuclear (UCI) |
| [`Proyecto`](Proyecto) | Clasificador de actividades físicas | Filtrado de señales, extracción y selección de características, Random Forest, SVM, KNN, Naive Bayes | UCF-iPhone (IMU de smartphone, modificado) |

## Proyecto final

Clasificación de 8 actividades físicas (subir/bajar escaleras, correr, caminar, saltar la cuerda, entre otras) a partir de 9 señales de una IMU de iPhone: acelerómetro, giroscopio y magnetómetro, de 3 ejes cada uno. Las señales se muestrean a 60 Hz y se entregan en ventanas de 125 muestras.

Flujo de trabajo:

1. Lectura de datos y split train/validación por **personas distintas**, para evitar fuga de información.
2. Visualización y análisis de las señales, y decisión sobre qué señales conservar.
3. Filtrado pasabajos para reducir el ruido.
4. Extracción y selección de características por canal.
5. Comparación de Random Forest, SVM (lineal, polinomial, gaussiano y sigmoide), KNN y Naive Bayes.
6. Evaluación final sobre un conjunto de prueba sin etiquetas, enviada a Kaggle: **score 0.76250**.

### Aprendizajes

Primero probé modelos secuenciales (LSTM), pensando que eran los adecuados para series de tiempo, pero no funcionaron bien con estos datos. El problema se resolvía mejor con una buena extracción de características sobre señales filtradas y clasificadores clásicos. La lección principal: **probar primero modelos simples**, y complejizar solo si hace falta.

Ver [`Proyecto/solution`](Proyecto/solution) para el notebook y el informe.

## Estructura

```
Tarea_N/
├── material/   # enunciado y datos entregados por el curso
└── solution/   # notebook, informe en PDF y README con instrucciones
Proyecto/
├── material/   # enunciado y dataset (.zip)
└── solution/   # notebook e informe
2022_2_EL4106.pdf   # programa del curso
```

## Cómo ejecutar

Los notebooks se desarrollaron en **Google Colab**. Cada `Tarea_N/solution/README.md` explica cómo ejecutarla (subir el dataset de `material/` y correr las celdas en orden).

Para ejecutarlos localmente:

```bash
python -m venv .venv && source .venv/bin/activate
pip install numpy pandas matplotlib seaborn scikit-learn torch jupyter xlrd
jupyter notebook
```

`xlrd` solo se necesita en la Tarea 5: `pandas` lo usa para leer archivos Excel antiguos (`.xls`) y no viene incluido con `pip install pandas`. En Colab ya está instalado. En el Proyecto hay que descomprimir primero `dataset_2024_full_alumnos_v01.zip`.

## Stack

Python · NumPy · pandas · scikit-learn · PyTorch · Matplotlib · Seaborn · Jupyter / Colab

## Autor

**Diego Vega**

## Licencia

MIT, ver [`LICENSE`](LICENSE). Aplica solo a mis soluciones (notebooks, scripts e informes en `solution/`). No aplica a las carpetas `material/` ni al programa del curso, que pertenecen a sus autores.

## Nota

Los enunciados y el programa del curso fueron elaborados por el equipo docente (profesor Javier Ruiz del Solar, auxiliar Patricio Loncomilla Z.). Los datasets pertenecen a sus fuentes originales (UCI Machine Learning Repository, UCF-iPhone). Se incluyen solo con fines educativos y de portafolio; las soluciones y los informes son de mi autoría.
