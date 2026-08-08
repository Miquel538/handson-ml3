**1.- Cual es la profundidad aproximada de un árbol de decisión entrenado ( sin restricciones ) con un conjunto de entrenamiento con un millón de instancias?**

El límite de profundidad sin restriccion alguna viene detereminado por el número de caracteristicas que tenga dicho conjunto 

**2.- Es l impureza de Gini de un nodo generalmente más baja o mas alta que la de su padre? ¿Es por lo general más baja/alta, o siempre mas baja/alta?**

En general, la idea de la evolución de la impureza es que a medida que vamos bajando niveles del árbol esta se valla reduciendo. Responde a la lógica de acercarse mas al nodo puro. Si nos fijamos por ejemplo en el nodo Raiz, este es el mas impuro de todos y a medida que vamos descendiendo se van obteniendo nodos mas puros.  La impureza debería de ser siempre mas baja a medida que vamos descendiendo por el árbol.


**3.- Si un árbol de decisión está sobreajustando el conjunto de entrenamiento, ¿ es buena idea reducir max_depth?**

Definitivamente, ajustar els hiperparámetro max_depth permite aplicar regularización a los árboles de decisión, de manera que si, aplicar esta medida puede ayudar a reducir el sobreajuste.


**4.- Si un árbol de decisión está sobreajustando el conjunto de entrenamiento, ¿ es buena idea escalar las características de entrada?**

Los árboles de decisión no requieren de escalado ni de centrado de características de manera que esto no va a ayudar a reducir el max_depth.


**5.- Si se tarda una hora en entrenar un árbol de decisión con un conjunto de entrenamiento que contiene un millón de instancias, ¿ cuánto tiempo, aproximadamente, tardaremos en entrenar otro arbol de decision con un conjunto der entrenamiento con diez millones de instancias? Pista: Considera la complejidad computacional del algoritmo CART.**

En este caso se tardaría como 10 veces mas en hacer el entrenamiento, digamos que 11 - 12 horas


**6.- Si se tarda una hora en entrenar un árbol de decisión en un conjunto de entrenamiento dado, ¿ cuánto se tardarà aproximadamente si duplicas el número de características?**
Aproximadamente unas 2 horas.