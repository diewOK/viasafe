# ViaSafe: Análisis y Predicción de Riesgo Vial

*Nota: Este proyecto fue desarrollado de forma estrictamente académica para el curso de Aprendizaje de Máquina. No representa un sistema comercial.*

## Descripción del Proyecto
ViaSafe es una iniciativa orientada a identificar y predecir los niveles de riesgo de accidentes de tránsito en base a datos históricos y características de su entorno. Mediante el uso de técnicas de Minería de Datos y Aprendizaje de Máquina (Machine Learning), el trabajo busca modelar patrones que ayuden a la prevención de accidentes y aporten a una mejor gestión en la seguridad vial.

## Contexto 
El análisis de riesgo vial permite comprender bajo qué condiciones ocurren incidentes de mayor severidad. La capacidad de anticipar la probabilidad de eventos peligrosos, basándose en variables horarias, climáticas y de complejidad de las rutas, proporciona información académica fundamental para el diseño de políticas públicas orientadas a disminuir los índices de siniestralidad.

## Dataset
Se ha construido y consolidado un conjunto de datos en formato tabular (`.csv`) a partir de información que caracteriza los incidentes de tránsito. El dataset contempla variables explicativas como:
- Horario de los siniestros.
- Condiciones climáticas.
- Nivel de complejidad de la vía.
- Gravedad del accidente (variable objetivo).

Para efectos iniciales, este repositorio utiliza un dataset simplificado en la carpeta `data/`.

## Metodología
El flujo de trabajo dentro del entorno de experimentación siguió las siguientes etapas:
1. **Análisis Exploratorio de Datos (EDA)**: Se analizó la distribución de las variables y sus correlaciones. Notamos el típico problema de un escenario vial: existe un fuerte desbalance de clases (muchos accidentes menores y muy pocos de alta gravedad).
2. **Aplicación de Técnicas de Balanceo**: Para tratar este desajuste y evitar el sesgo de la clase mayoritaria en los modelos, implementamos tres técnicas:
   - SMOTE (Synthetic Minority Over-sampling Technique)
   - ADASYN (Adaptive Synthetic Sampling Method)
   - Random Under-Sampling
3. **Entrenamiento de Modelos**: Se experimentó con un abanico de modelos para abordar el desafío de clasificación:
   - Regresión Logística (utilizado como línea base)
   - Random Forest
   - XGBoost
   - Red Neuronal Simple (Perceptrón Multicapa)

## Resultados Generales
Nuestra evaluación puso especial énfasis en la métrica **Recall (Sensibilidad)**. En el contexto de un accidente de tránsito grave, penalizamos fuertemente fallar en predecirlo (falsos negativos), por lo que tener un mayor nivel de alarma ante un riesgo real es deseable. 

- Tras someter los perfiles a técnicas de sobremuestreo sintético (como SMOTE), modelos como **Random Forest** y **XGBoost** lograron la mejor capacidad para detectar correctamente los escenarios de alta peligrosidad, incrementando sustancialmente la detección.
- Las técnicas de balanceo permitieron mitigar drásticamente el sesgo algorítmico, comprobándose diferencias notables versus el caso sin balancear.

## Estructura del Repositorio
```text
📦 ViaSafe-ML
 ┣ 📂 data
 ┃ ┗ 📜 viasafe_dataset.csv     # Dataset base en formato procesable
 ┣ 📂 docs
 ┃ ┗ 🖼️ mockup.png              # Prototipo visual general del flujo
 ┣ 📂 notebooks
 ┃ ┗ 📓 viasafe_analysis.ipynb  # Código completo: EDA, Balanceo y Modelamiento
 ┗ 📜 README.md                 # Documentación e instrucciones
```

## Instrucciones de Uso

Para ejecutar el experimento y revisar el código paso a paso:
1. Clonar o descargar este repositorio localmente, o subir los archivos a Google Drive.
2. Abrir **Google Colab** en su navegador web (https://colab.research.google.com/).
3. Ir a *Archivo > Subir notebook* y cargar el documento ubicado en `notebooks/viasafe_analysis.ipynb`.
4. (Opcional) Si quiere cargar los datos desde archivo, subir `data/viasafe_dataset.csv` a su entorno temporal del Colab virtual.
5. Ejecutar las celdas en orden secuencial para observar los resultados de entrenamiento.
