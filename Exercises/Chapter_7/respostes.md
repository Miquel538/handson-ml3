# Respuestas a los ejercicios del capítulo 7

**1. Si has entrenado cinco modelos diferentes con el mismo conjunto de entrenamiento y todos consiguen una exactitud del 95 %, ¿puedes combinarlos para obtener mejores resultados? ¿Cómo?**

Sí, es posible crear un ensamble mediante votación mayoritaria (hard voting) o promediando las probabilidades predichas (soft voting). La mejora depende de que los modelos cometan errores suficientemente diferentes: los aciertos de unos pueden compensar los errores de otros. Tener la misma exactitud no significa equivocarse en las mismas instancias.

La diversidad de algoritmos puede ayudar incluso si todos se entrenan con los mismos datos. Sin embargo, la mejora no está garantizada: si sus predicciones y errores coinciden, combinarlos no aporta una ventaja. Hay que comprobar el rendimiento del ensamble con datos no utilizados para entrenar.

**2. ¿Cuál es la diferencia entre hard voting y soft voting?**

En hard voting, cada clasificador predice una clase y el ensamble elige la que recibe más votos. En soft voting, cada clasificador estima la probabilidad de cada clase; el ensamble promedia esas probabilidades y elige la clase con el promedio más alto. Ambos métodos admiten pesos para dar más importancia a determinados modelos.

La diferencia está en cómo se combinan las predicciones, no en que solo uno devuelva una clase final. Soft voting aprovecha la confianza de los modelos y puede funcionar mejor cuando sus probabilidades están bien calibradas.

**3. ¿Es posible acelerar el entrenamiento de bagging distribuyéndolo entre múltiples servidores? ¿Y el de pasting, boosting, Random Forest y stacking?**

Sí, en bagging los estimadores se entrenan de forma independiente sobre muestras obtenidas con reemplazo, por lo que pueden distribuirse entre servidores. Lo mismo ocurre con pasting, que utiliza muestras sin reemplazo, y con Random Forest, cuyos árboles pueden entrenarse en paralelo. La aceleración real depende también del coste de transferir datos y coordinar los procesos.

En boosting, los estimadores sucesivos dependen de los resultados de los anteriores, por lo que no pueden entrenarse todos simultáneamente como en bagging. Esto no impide paralelizar ciertas operaciones internas del entrenamiento de cada estimador.

En stacking, los modelos de un mismo nivel pueden entrenarse en paralelo, pero el siguiente nivel debe esperar a disponer de las predicciones que necesita como entradas. El blender podría usar un algoritmo cuyo propio entrenamiento sea paralelizable; la restricción es la dependencia entre niveles. Para evitar fuga de información, sus datos de entrenamiento deben proceder de predicciones sobre instancias no utilizadas para entrenar los modelos que las generan, mediante una partición reservada o predicciones out-of-fold.

**4. ¿Cuál es el beneficio de la evaluación out-of-bag?**

En bagging con muestreo con reemplazo, cada estimador deja fuera algunas instancias del conjunto original. Si se extraen tantas muestras como instancias originales hay, aproximadamente el 36,8 % queda fuera del entrenamiento de cada estimador. Estas son sus instancias out-of-bag (OOB).

Para evaluar el ensamble, cada instancia recibe una predicción combinando únicamente los estimadores que no entrenaron con ella. Después se comparan esas predicciones con los valores reales.

El beneficio principal es estimar la capacidad de generalización sin reservar un conjunto de validación separado, aprovechando los datos para entrenar. No garantiza obtener el mismo resultado que en un conjunto de prueba independiente, que sigue siendo útil para la evaluación final, especialmente si se ha usado OOB para seleccionar hiperparámetros.

**5. ¿Qué hace que Extra Trees sea más aleatorio que un Random Forest corriente? ¿Cómo ayuda esa aleatoriedad? ¿Es más lento o más rápido?**

Ambos introducen aleatoriedad al considerar subconjuntos de características para dividir los nodos. Extra Trees añade aleatoriedad en los umbrales: genera umbrales aleatorios para las características consideradas y selecciona la mejor división entre esos candidatos. Un Random Forest corriente busca el mejor umbral para las características consideradas.

Esta aleatoriedad adicional suele reducir la correlación entre los árboles y la varianza del ensamble, a costa de un posible aumento del sesgo. Puede mejorar la generalización, aunque no está garantizado.

Extra Trees suele entrenarse más rápido porque evita buscar exhaustivamente los mejores umbrales. Esto no implica necesariamente predicciones más rápidas: su coste también depende del número y la profundidad de los árboles.

**6. Si AdaBoost subajusta los datos de entrenamiento, ¿qué hiperparámetros deberías ajustar y cómo?**

Se puede aumentar el número de estimadores (`n_estimators`) para permitir más etapas de corrección, aumentar la tasa de aprendizaje (`learning_rate`) para dar más peso a cada corrección o aumentar la complejidad del estimador base, por ejemplo, incrementando la profundidad máxima de los árboles. También se pueden relajar otras restricciones del estimador base que estén causando el subajuste.

Reducir únicamente la tasa de aprendizaje, manteniendo el número de estimadores, normalmente no es la solución al subajuste: reduce el efecto de cada etapa. Una tasa menor puede funcionar si se compensa con más estimadores, pero hay que ajustar ambos parámetros conjuntamente y comprobar el resultado mediante validación. Ninguna de estas modificaciones garantiza una mejora por sí sola.

**7. Si gradient boosting sobreajusta, ¿deberías aumentar o reducir la tasa de aprendizaje?**

La respuesta habitual es reducir la tasa de aprendizaje. Manteniendo fijo el número de árboles, cada árbol aporta una corrección menor y el ensamble avanza más lentamente, lo que puede reducir el sobreajuste. También puede ayudar reducir el número o la complejidad de los árboles, o utilizar parada temprana basada en validación.

La tasa de aprendizaje debe considerarse junto con el número de estimadores. Si se reduce la tasa pero se añaden suficientes árboles, el modelo puede seguir ajustando los datos, reducir su sesgo y acabar sobreajustando. Por tanto, una tasa pequeña no garantiza una varianza baja ni evita por sí sola el sobreajuste.

En boosting hablamos de etapas o estimadores, más que de épocas: normalmente cada etapa añade un nuevo árbol. La estrategia práctica es elegir la tasa y el número de árboles mediante validación, deteniendo el entrenamiento cuando el rendimiento de validación deje de mejorar. Un menor error de entrenamiento, por sí solo, no demuestra un menor sesgo: también puede reflejar ajuste al ruido.
