FARC-HD for Python
FARC-HD (Fuzzy Association Rule-based Classification Model for High-Dimensional problems) es un potente algoritmo de aprendizaje automático diseñado para obtener una alta precisión y una gran interpretabilidad en problemas de clasificación con muchas variables.

Este proyecto es una reinterpretación moderna y optimizada del algoritmo original desarrollado por el grupo de investigación KEEL (Universidad de Granada).

✨ Características Principales
Interpretabilidad: Genera una base de reglas difusas (IF-THEN) fáciles de entender para humanos.

Alto Rendimiento: Implementación optimizada con Numba (Just-In-Time compilation) para una ejecución ultra rápida.

Ecosistema Scikit-Learn: Totalmente compatible con la API de sklearn (fit, predict, score).

Eficiencia en Alta Dimensión: Diseñado específicamente para manejar datasets con un gran número de características sin perder precisión.

🚀 Instalación
Puedes instalarlo directamente desde PyPI:

Bash
pip install farc-hd
💻 Ejemplo de Uso Rápido
Python
from farc_hd.FarcHDClassifier import FarcHDClassifier
from sklearn.datasets import load_iris
from sklearn.model_selection import train_test_split

# Cargar datos
data = load_iris()
X_train, X_test, y_train, y_test = train_test_split(data.data, data.target, test_size=0.3)

# Inicializar y entrenar el modelo
model = FarcHDClassifier(max_trials=1000, population_size=20)
model.fit(X_train, y_train)

# Predecir e imprimir reglas
y_pred = model.predict(X_test)
model.print_rules(variables=data.feature_names, classes=data.target_names)
📚 Créditos y Atribución
Este software es un port a Python del algoritmo FARC-HD original de KEEL.

Algoritmo Original: Jesús Alcalá-Fdez et al. (University of Granada).

Traducción y Optimización: Iñaki Mellado Ilundain.
JOse Antonio Sanz Delgado

Licencia: Inspirado en la filosofía de código abierto de KEEL.