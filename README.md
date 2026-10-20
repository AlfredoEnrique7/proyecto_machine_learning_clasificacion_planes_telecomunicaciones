# Proyecto modelo de Machine Learning: Clasificación de planes de telecomunicaciones

## Descripción 
En el competitivo sector de las telecomunicaciones, la retención de clientes y la optimización de los ingresos a través de estrategias de *upselling* (ofrecer planes de mayor valor) son pilares fundamentales para el crecimiento de cualquier compañía. 

El objetivo principal de este proyecto es construir un **Modelo de Machine Learning (ML) de Clasificación Binaria** capaz de analizar el comportamiento de consumo mensual de los usuarios (minutos, llamadas, mensajes y datos móviles utilizados) para predecir con alta precisión qué clientes pertenecen o son candidatos óptimos para el plan de tarifas **Ultimate** frente al plan de tarifas **Regular**.

## Conclusiones
Tras completar el flujo integral de Ciencia de Datos incorporando las recomendaciones avanzadas de la revisión técnica para mitigar las limitaciones lineales, se consolidan las siguientes conclusiones definitivas del pipeline predictivo:

| Eje de Evaluación | Componente Diagnosticado | Hallazgo Numérico Clave | Impacto Metodológico y de Negocio Megaline |
| :--- | :--- | :---: | :--- |
| **1. Robustez del Pipeline** | Curación y Calidad Estructurada del Dataset. | **82.43% Exactitud** | La deduplicación en dos fases eliminó la colisión por redondeo. La consistencia entre validación (80.56%) y prueba (82.43%) confirma un pipeline robusto, completamente libre de sobreajuste (*overfitting*). |
| **2. Frontera No Lineal** | Comportamiento ante la Complejidad de Consumo. | **52.00% Sensibilidad** | El ensamble Random Forest resolvió el cuello de botella de la Regresión Logística. Elevó el *Recall* del plan Ultimate al 52.00% (rescatando a 102 usuarios premium) manteniendo una **alta Precisión del 85.00%**. |
| **3. Validación Final** | Éxito en la Prueba de Cordura (*Sanity Check*). | **+13.07% de Ganancia** | El modelo de ensamble destruyó el sesgo de la inercia estadística, superando con holgura al modelo ingenuo de línea base (82.43% vs. 69.36%), ratificando la captura de patrones legítimos de consumo. |

### Recomendaciones para Futuras Iteraciones (Trabajo Futuro)

Para continuar optimizando el rendimiento predictivo y reducir el margen remante de Falsos Negativos en la plataforma, se sugieren los siguientes procedimientos secuenciales:

1. **Balanceo de Pesos Nativo:** Configurar el hiperparámetro de inicialización del clasificador de bosque aleatorio activando la propiedad adaptativa `class_weight='balanced'` o `class_weight='balanced_subsample'`.
2. **Ajuste de Umbral de Decisión (*Threshold Tuning*):** Desplazar el umbral probabilístico de clasificación por defecto (0.5) hacia valores más bajos mediante la función `.predict_proba()`, priorizando la captura de usuarios premium.
3. **Modelos de Impulso Gradual:** Evaluar el comportamiento de algoritmos basados en *Gradient Boosting* (como `XGBoost` o `LightGBM`), los cuales suelen optimizar la tasa de aciertos sobre la clase minoritaria de forma iterativa y secuencial.

## Tecnologías utilizadas
**1. Manipulación y análisis de datos (`pandas`, `numpy`):** Estructuras vectorizadas indispensables para la carga de datos estructurados (DataFrames), operaciones algebraicas de alta velocidad y la fase de curación y limpieza de registros.

**2. Visualización estadística (`seaborn`, `matplotlib`):** Librerías gráficas para el desarrollo del Análisis Exploratorio de Datos (EDA), esenciales para plasmar de forma visual la distribución de las variables y auditar las matrices de error.

**3. Aprendizaje automático y modelado estructural (`scikit-learn`):** Ecosistema modular central empleado para la automatización de la partición de datos, estandarización de magnitudes numéricas y el entrenamiento de las arquitecturas lineales y basadas en árboles.

* **Arquitectura de componentes de Scikit-Learn (`sklearn`)**

  | Módulo de Scikit-Learn | Componente Específico | Rol y Función Técnica en el Proyecto |
| :--- | :--- | :--- |
| **`sklearn.model_selection`** | `train_test_split` | Responsable de ejecutar la **división tripartita y estratificada (60/20/20)** del dataset para aislar correctamente los conjuntos de entrenamiento, validación y prueba final. |
| **`sklearn.preprocessing`** | `StandardScaler` | Encargado de la **estandarización de las características continuas**, escalando las magnitudes numéricas para que compartan una media igual a 0 y una desviación estándar de 1, evitando sesgos por escala. |
| **`sklearn.linear_model`** | `LogisticRegression` | Algoritmo lineal utilizado para instanciar el primer **modelo de línea base** desbalanceado y evaluar el comportamiento de los coeficientes. |
| **`sklearn.tree`** | `DecisionTreeClassifier` | Algoritmo no lineal basado en estructuras de árboles, seleccionado como la arquitectura del **modelo campeón** tras restringir su crecimiento. |
| **`sklearn.utils`** | `resample` | Herramienta de remuestreo estadístico implementada en el **Enfoque 2 (Upsampling)** para realizar el sobremuestreo con reemplazo de la clase minoritaria en el set de entrenamiento. |

## Ver el análisis completo
👉 [Haz clic aquí para ver el código y los gráficos interactivos](proyecto_machine_learning_clasificacion_planes_telecomunicaciones.ipynb)



