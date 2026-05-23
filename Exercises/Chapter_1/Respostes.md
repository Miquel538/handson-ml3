Como definirias el machine Learning?

La capacidad de un software de aprender a realizar una tarea a partir de una experiencia previa y sin intervención al codigo, con un rendimiento aceptable.


¿Puedes nombrar 4 tipo de aplicaciones en las que destaca?

    - Analizar imágenes de productos en una cadena  de producción para clasificarlas.
    - Detectar tumores en escaneres cerebrales.
    - Clasificar artículos de noticias de manera automática.
    - Marcar de manera automática cometarios ofensivos en foros de discusión.


¿Que es un conjunto de entrenamiento etiquetado?

Un conjunto de entrenamiento etiquetado es aquel conjunto donde por cada instancia de entrenamiento se conoce la solución, dicha solución es la etiqueta.


¿Cuales son las dos tareas supervisadas mas comunes?

las tareas mas típicas són : La clasificación y la regresión.


¿Puedes nombrar 4 tareas no supervisadas comunes?
    - agrupación
    - visualización, 
    - reducción de dimensionalidad
    - detección de anomalías


¿Qué tipo de algoritmo utilizarias para permitir a un robot caminar por varios terrenos desconocidos?

Usaría un algoritmo de aprendizaje por refuerzo.


¿Definirías el problema de detección de spam como un problema de aprendizaje supervisado o no supervisado?

El problema de detección de spam es un problema de aprendizaje supervisado ya que se trabaja principalmente con conjuntos de datos donde sabemos si se trata de spam o no cada elemento del conjunto para hacer la inferencia.


¿Que es un sistema de aprendizaje online?

Un sistema de aprendizaje online conssite en el entrenamiento de modelos a partir de un dataset previamente fragmentado. El entrenamiento se realiza con cada fragmento de forma gradual, permitiendo asi la evolución y la adaptación de dichos modelos a los datos nuevos. El factor mas importante es el tiempo de entrenamiento de cada lote.


¿Que es el aprendizaje out of core?

El aprendizaje out of core se produce cuando el dataset que se usa para el entrenamiento, no se encuentra de forma completa en la misma máquina donde se entrena. De manera que para realizar el entrenamiento, se accede previamente a una parte de los datos desde la máquina donde se entrena, se realiza el entrenamiento y después se pasa a otro fragmento de datos para seguir con el entrenamiento.


¿Que tipo de algoritmo depende de una medida de similitud para hacer predicciones?

El tipo de algoritmo que depende de una medida de similitud para hacer predicciones son los algoritmos cuyo entrenamiento se basa en instancias.


¿Cual es la diferencia entre un parametro de modelo y un hiperparametro de modelo?

El parametro de un modelo, son los parámetros que el usuario o desarrollador pueden modificar mientras que el hiperparámetro son los parametros de los modelos que son ajustados en la fase de entrenamiento ( al reves).


¿Qué buscan los algoritmos basados en modelos? ¿Cuál es la estrategia mas comun que usan para tener exito? ¿Cómo hacen predicciones?

A partir de un conjunto de datos, extraer un modelo que se ajuste a las tendencias de dichos datos. La estrategia mas comun consiste en seleccionar dichos modelos y entrenarlos para hacer inferencia. Una vez ajustados los hiperparámetros del modelo, se introducen los valores de las variables d'entrada y se procede a hacer el cálculo. El resultado de dicho cálculo sería la prediccioón hecha.


¿Puedes nombrar cuatro de los principales retos del machine learning?

    - Cantidad insuficinete de datos
    - Datos de entrenamiento no representativos
    - Datos de mala calidad
    - SObre ajustar los datos de entrenamiento


Si tu modelo tiene un gran rendimiento en los datos de entrenamiento, pero generaliza mal a instancias nuevas, ¿Qué esta pasando? ¿Puedes nombrar 3 soluciones possibles?

Se esta produciendo sobreajuste. Para solucionar el sobreajuste se puede:
    - 1 Simplificar el modelo eligiendo uno con menos parametros,
    - 2 Reunir mas datos de entrenamiento
    - 3 Reducir el ruido en los datos de entrenamiento.


¿Que es un conjunto de prueba y por qué te convendría usarlo? 

El conjunto de prueba es una parte del conjunto de datos completamente aislado que permite medir el rendimiento del modelo con instancias nuevas- De manera que permite conocer como rendiria el modelo delante de instancias nuevas.


¿Cual es el objetivo de un conjunto de validación?

El conjunto de validación permite medir el rendimiento de varios modelos en una prefase de seleccion. Parte desde el mismo conjunto de entrenamiento.

¿Qué es el conjunto de entrenamiento-desarrollo, cuándo es necesario y como se utiliza?
l conjunto de entrenamiento-desarrollo o train-dev set es una parte de los datos que se separa del conjunto de entrenamiento, pero que no se usa para entrenar el modelo.

Sirve para diagnosticar si el problema viene de:

El modelo no aprende bien los datos de entrenamiento, es decir, hay alto sesgo.
El modelo aprende bien el entrenamiento, pero no generaliza a datos similares, es decir, hay alta varianza.
Hay una diferencia entre los datos de entrenamiento y los datos reales de desarrollo/prueba, es decir, hay data mismatch.

Se usa sobre todo cuando el conjunto de entrenamiento viene de una distribución distinta a la del conjunto de desarrollo o prueba.

¿Que puede salir mal si ajustamos hiperparámetros utilizando el conjunto de prueba?
Si usamos el conjunto de prueba para ajustar hiperparámetros, el problema es que el conjunto de prueba deja de ser una evaluación neutral.
Pero si probamos muchos modelos o configuraciones mirando el resultado en test, empezamos a adaptar nuestras decisiones a ese conjunto. Aunque no entrenemos directamente con esos datos, estamos usando su información para elegir el modelo.
Eso provoca sobreajuste al conjunto de prueba.