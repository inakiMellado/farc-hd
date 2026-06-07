# FARC-HD for Python 🚀

[![PyPI version](https://img.shields.io/pypi/v/farc-hd.svg)](https://pypi.org/project/farc-hd/)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![Python Versions](https://img.shields.io/pypi/pyversions/farc-hd.svg)](https://pypi.org/project/farc-hd/)

**FARC-HD (Fuzzy Association Rule-based Classifier for High-Dimensional Problems)** es una implementación moderna y optimizada en Python de uno de los algoritmos de clasificación difusa más reconocidos en la literatura científica.

Diseñado para problemas de clasificación complejos y de alta dimensionalidad, FARC-HD combina minería de reglas de asociación, lógica difusa y optimización evolutiva para generar modelos altamente interpretables sin sacrificar rendimiento.

La librería está totalmente integrada con el ecosistema de **scikit-learn**, permitiendo utilizarla en flujos de trabajo estándar de Machine Learning.

---

## ✨ Características

### 🔗 Compatible con Scikit-Learn

Implementa la API estándar de scikit-learn:

* `fit()`
* `predict()`
* `predict_proba()`
* `score()`

Compatible con:

* `Pipeline`
* `GridSearchCV`
* `cross_val_score`
* `train_test_split`

---

### ⚡ Alto rendimiento

La implementación ha sido optimizada mediante:

* **Numba (JIT Compilation)**
* **NumPy vectorizado**
* Gestión eficiente de memoria
* Optimizaciones específicas para grandes conjuntos de datos

Esto permite reducir significativamente los tiempos de ejecución respecto a implementaciones tradicionales en Python.

---

### 🔍 Modelos interpretables

A diferencia de muchos algoritmos modernos de tipo *black box*, FARC-HD genera una base explícita de reglas difusas:

```text
IF PetalLength IS High AND PetalWidth IS Medium
THEN Class = Virginica
```

Las reglas pueden inspeccionarse fácilmente para comprender el comportamiento del modelo.

---

### 🧠 Detección automática de variables

El clasificador puede identificar automáticamente:

* Variables continuas
* Variables enteras
* Variables categóricas

También es posible especificar manualmente las variables categóricas.

---

### 🛡️ Robustez para producción

Incluye mecanismos de protección frente a:

* Divisiones por cero
* Variables con varianza nula
* Consumo excesivo de memoria
* Profundidades de búsqueda no controladas

---

## 📦 Instalación

Instala la librería directamente desde PyPI:

```bash
pip install farc-hd
```

### Requisitos

* Python ≥ 3.8
* NumPy
* Numba
* Scikit-Learn

---

## 🚀 Ejemplo rápido

```python
from sklearn.datasets import load_iris
from sklearn.model_selection import train_test_split
from farc_hd import FarcHDClassifier

# Dataset Iris
X, y = load_iris(return_X_y=True)

X_train, X_test, y_train, y_test = train_test_split(
    X,
    y,
    test_size=0.2,
    random_state=42
)

# Crear clasificador
clf = FarcHDClassifier(
    n_labels=5,
    minsup=0.05,
    minconf=0.8,
    depth=3
)

# Compilación JIT opcional
clf.warm_up()

# Entrenamiento
clf.fit(X_train, y_train)

# Predicciones
y_pred = clf.predict(X_test)

# Evaluación
print(
    f"Accuracy: {clf.score(X_test, y_test):.4f}"
)

# Inspección del modelo
clf.print_predictions(y_pred, y_test)
clf.print_rules()
```

---

## ⚙️ Parámetros principales

| Parámetro               | Tipo        | Valor por defecto | Descripción                                 |
| ----------------------- | ----------- | ----------------- | ------------------------------------------- |
| `n_labels`              | int         | 5                 | Número de etiquetas difusas por variable    |
| `minsup`                | float       | 0.05              | Soporte mínimo para Apriori                 |
| `minconf`               | float       | 0.8               | Confianza mínima de las reglas              |
| `depth`                 | int         | 3                 | Máximo número de antecedentes por regla     |
| `k_parameter`           | int         | 2                 | Parámetro del razonamiento difuso           |
| `max_trials`            | int         | 20000             | Evaluaciones máximas del algoritmo genético |
| `population_size`       | int         | 50                | Tamaño de la población                      |
| `alpha`                 | float       | 0.05              | Peso de la función fitness                  |
| `type_inference`        | int         | 1                 | 0 = Winner Rule, 1 = Additive Combination   |
| `seed`                  | int         | 53743421          | Semilla aleatoria                           |
| `categorical_variables` | list | None | None              | Variables categóricas definidas manualmente |

---

## 📈 Casos de uso

FARC-HD resulta especialmente útil cuando se necesita:

* Interpretabilidad del modelo
* Explicaciones basadas en reglas
* Clasificación en datasets de alta dimensionalidad
* Sistemas expertos
* Aplicaciones médicas o financieras donde la transparencia es importante
* Investigación en lógica difusa y Soft Computing

---

## 📚 Referencia académica

Este proyecto surge del Trabajo Fin de Grado:

> **"Adaptación del algoritmo FARC-HD a Python: optimización y análisis de rendimiento"**
>
> Universidad Pública de Navarra (UPNA), 2026.

El objetivo fue trasladar la implementación clásica desarrollada en Java a un entorno Python moderno, manteniendo la precisión original e incorporando optimizaciones avanzadas de rendimiento.

---

## 🤝 Contribuciones

Las contribuciones son bienvenidas.

Si encuentras un error o tienes una propuesta de mejora:

1. Abre un *Issue*
2. Crea una rama
3. Envía un *Pull Request*

---

## 📄 Licencia

Este proyecto se distribuye bajo la licencia MIT.

Consulta el archivo `LICENSE` para más información.
