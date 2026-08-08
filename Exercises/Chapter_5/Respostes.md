**1.- ¿ Cuál es la idea fundamental tras las máquinas de vectores soporte ?**

La idea fundamental de las máquinas de vectores soporte es encontrar una frontera de decisión que separe las clases dejando el mayor margen posible entre dicha frontera y las instancias de entrenamiento más cercanas.

En una clasificación de margen suave, el SVM busca un equilibrio entre conseguir un margen amplio y permitir algunas violaciones del margen o errores de clasificación. Además, mediante el uso de kernels, los SVM pueden construir fronteras de decisión no lineales.

**2.- ¿ Qúe es un vector soporte ?**

Un vector soporte es una instancia de entrenamiento situada sobre los límites del margen o dentro de este. En una clasificación de margen suave también pueden ser vectores soporte las instancias que violan el margen o que están mal clasificadas.

Estas instancias son especialmente importantes porque determinan la posición y la orientación de la frontera de decisión. Las instancias que se encuentran fuera del margen no influyen directamente en dicha frontera.

**3.- ¿ Por que es importante escalar las entradas cuando se utilizan SVM ?**

Es importante escalar las características porque los SVM se basan en distancias y productos entre las características para construir la frontera de decisión.

Cuando las características tienen escalas muy diferentes, aquellas con valores más grandes pueden dominar el entrenamiento, mientras que las características con valores pequeños pueden quedar prácticamente ignoradas. Esto puede provocar que el margen y la frontera de decisión no sean adecuados.

Para evitarlo, se pueden escalar las características mediante herramientas como StandardScaler.

**4.- ¿ Puede un classificador SVM generar como salida un a puntuacion de confianza cuando clasifica una instacia ? ¿ Qué hay de una probabilidad ?**

LSí. Los clasificadores SVM disponen del método decision_function(), que devuelve una puntuación de decisión con signo.

El signo indica a qué lado de la frontera se encuentra la instancia y, en una clasificación binaria, qué clase predice el modelo. El valor absoluto de la puntuación indica lo alejada que está la instancia de la frontera: cuanto mayor sea, mayor será generalmente la confianza del modelo en la clasificación.

Los SVM no generan probabilidades directamente. Sin embargo, al crear un modelo SVC se puede utilizar probability=True. En ese caso, Scikit-Learn realiza una calibración adicional mediante validación cruzada y entrena un modelo de regresión logística que transforma las puntuaciones del SVM en probabilidades estimadas. Después estarán disponibles los métodos predict_proba() y predict_log_proba().

**5.- ¿ Cómo puedes elegir entre LinearSVC, SVC, y SGDClassifier ?**

LinearSVC es una buena opción cuando el problema es lineal y el conjunto de entrenamiento contiene muchas instancias o muchas características. Está especialmente optimizado para entrenar SVM lineales.

SVC puede utilizar tanto kernels lineales como kernels no lineales, como el kernel RBF o el polinomial. Es adecuado para problemas no lineales y para conjuntos de datos pequeños o medianos, pero no escala bien cuando el número de instancias es muy grande. En cambio, sí puede funcionar bien con conjuntos que tienen muchas características.

SGDClassifier puede entrenar un clasificador SVM lineal utilizando loss="hinge". Es especialmente útil para conjuntos de datos muy grandes, para aprendizaje incremental o cuando los datos no caben completamente en memoria, ya que puede entrenarse por lotes mediante partial_fit().

**6.- Supongamos que has entrenado un classificador SVM con un kernel de función de base radial, pero parece que subajusta el conjunto de entrenamiento. ¿ Deberías aumentar o reducir gamma ? ¿ Qué pasa con C ?**

Si un SVM con kernel RBF subajusta el conjunto de entrenamiento, se puede aumentar gamma, C o ambos.

Al aumentar gamma, cada instancia de entrenamiento tiene una zona de influencia más pequeña. Esto permite que la frontera de decisión sea más irregular y se adapte con mayor precisión al conjunto de entrenamiento.

Al aumentar C, se penalizan más las violaciones del margen. Por tanto, el modelo acepta un margen más estrecho con el objetivo de clasificar correctamente más instancias del conjunto de entrenamiento. En otras palabras, aumentar C reduce la regularización.

No obstante, aumentar demasiado gamma o C puede provocar sobreajuste.

**7.- ¿ Qué supone para un modelo ser insensible a Epsilon ?**

En un modelo de regresión SVM, ser insensible a ϵ significa que los errores cuya magnitud sea inferior a ϵ no se penalizan.

El modelo construye una especie de calle alrededor de sus predicciones cuya anchura viene determinada por ϵ. Las instancias que se encuentran dentro de esta calle no generan pérdida y, por tanto, añadirlas o moverlas sin sacarlas del margen no afecta al modelo.

**8.- ¿ Para que sirve el truco kernel ?**

El truco kernel permite entrenar un SVM no lineal como si las instancias hubieran sido transformadas a un espacio de características de mayor dimensión, pero sin calcular explícitamente dicha transformación.

En ese espacio de mayor dimensión, un SVM lineal puede encontrar una separación que corresponde a una frontera no lineal en el espacio original.

El kernel calcula directamente los productos entre las instancias transformadas, evitando el coste computacional de crear todas las nuevas características. Por ejemplo, un kernel polinomial puede representar combinaciones polinómicas de las características, mientras que el kernel RBF equivale a trabajar en un espacio de características de dimensión muy elevada.


