**1.- Si has entrenado cinco modelos diferentes en el mismo conjunto de entrenameniento exacto y todo consiguen una precisión del 95%, hay alguna posibilidad de que puedas combinar estos modelos para obtener mejores resultados? Si la respuesta es si,Cómo? Si la respuesta es no, por qué?**

Si se pueden combinar dichos modelos para obtener un resultado mejor, para ello se puede implementar un ensamble. La idea principal radica en que consiguiendo los resultados de la inferencia de cada modelo por la instancia que se quiere predecir, se puede usar distintas estrategias para elegir el valor resultante global de la inferencia. De normal dichos resultados globales, es decir, del ensamble, suelen ser mejores que los resultados individuales de cada modelo.


**2.-Cuál es la diferencia entre clasificadores hard voting y soft voting?**

Los clasificadores hard voting, dan como respuesta a la inferencia de cada modelos individual el valor de la clase a la qual pertenecen las instancias, mientras que los soft voting el resultado de los clasificadores es la probabilidad de pertenecenencia a cada clase.


**3.-Es possibler acleerar el entrenamiento de un ensamble con bagging distribuyéndolo a traves de múltiples servidores? Qué hay de los ensambles con pasting, los ensambles con boosting, los random forestso los ensambles con stacking?**


**4.- ¿Cuál es el beneficio de la evaluación out-of-bag?**


**5.- ¿Qué hace que los ensambles extra-trees sean más aleatorios que los random forests corrientes? ¿Cómo puede ayudar esta aleatoriedad extra? ¿Són los clasificadores extra-trees más lentos o más rapidosque los random forests corrientes?**


**6.- Si tu ensamble AdaBoost subajusta los datos de entrenamiento, ¿qué hiperparámetros deberías ajustar y como?**


**7.- Si tu ensamble gradient boosting sobreajusta el conjunto de entrenamiento, ¿Deberías aumentar o reducir la tasa de aprendizaje?**
