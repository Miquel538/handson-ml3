**1.- ¿Cuál es la profundidad aproximada de un árbol de decisión entrenado sin restricciones con un conjunto de entrenamiento de un millón de instancias?**

Suponiendo que el árbol está aproximadamente equilibrado, su profundidad será cercana a:

```text
log₂(1 000 000) ≈ 20
```

Por tanto, tendrá una profundidad aproximada de **20 niveles**. Este cálculo se debe a que, en un árbol binario equilibrado, cada división reduce aproximadamente a la mitad el número de instancias que llegan a cada nodo.

La profundidad no está limitada por el número de características, ya que una misma característica puede utilizarse varias veces en el árbol, aplicando diferentes umbrales. Si el árbol estuviera muy desequilibrado, podría alcanzar una profundidad considerablemente mayor.

---

**2.- ¿Es la impureza de Gini de un nodo generalmente más baja o más alta que la de su padre? ¿Es siempre más baja o más alta?**

La impureza de Gini de un nodo hijo es generalmente más baja que la de su padre, pero no tiene por qué serlo siempre.

El algoritmo CART busca divisiones que reduzcan la impureza conjunta de los nodos hijos, ponderándola según el número de instancias que recibe cada uno:

```text
G(hijos) = [m(izq) / m] · G(izq) + [m(der) / m] · G(der)
```

Por tanto, uno de los hijos puede tener una impureza superior a la del padre, siempre que el resultado ponderado de ambos hijos sea inferior. Entre las divisiones candidatas, CART escoge la que produzca la mayor reducción de esta impureza ponderada.

En consecuencia, al descender por el árbol la impureza tiende a disminuir de manera global, pero no se garantiza que cada nodo hijo sea individualmente más puro que su padre.

---

**3.- Si un árbol de decisión está sobreajustando el conjunto de entrenamiento, ¿es buena idea reducir `max_depth`?**

Sí. Reducir el hiperparámetro `max_depth` limita el número de niveles que puede desarrollar el árbol y, por tanto, reduce su complejidad.

Un árbol demasiado profundo puede crear reglas muy específicas para clasificar correctamente casi todas las instancias de entrenamiento, incluyendo el ruido y las particularidades de ese conjunto. Esto produce sobreajuste y puede empeorar su rendimiento con datos nuevos.

Al reducir `max_depth`, se obliga al árbol a aprender patrones más generales. No obstante, si se reduce demasiado, el árbol podría volverse excesivamente simple y sufrir subajuste.

También se puede regularizar un árbol mediante otros hiperparámetros, como `min_samples_split`, `min_samples_leaf` o `max_leaf_nodes`.

---

**4.- Si un árbol de decisión está sobreajustando el conjunto de entrenamiento, ¿es buena idea escalar las características de entrada?**

No. Escalar las características no suele ayudar a reducir el sobreajuste de un árbol de decisión.

Los árboles toman sus decisiones comparando el valor de una característica con un determinado umbral. Por ejemplo:

```text
edad ≤ 30
```

Si se escala la característica, los valores y el umbral cambiarán, pero la separación de las instancias seguirá siendo esencialmente la misma. Los árboles dependen principalmente del orden de los valores, no de su escala.

Por tanto, a diferencia de algoritmos como k-NN, las máquinas de vectores de soporte o algunos modelos entrenados mediante descenso de gradiente, los árboles de decisión no suelen necesitar que las características estén normalizadas o estandarizadas.

Para combatir el sobreajuste resulta más útil limitar la complejidad del árbol mediante sus hiperparámetros de regularización.

---

**5.- Si se tarda una hora en entrenar un árbol de decisión con un conjunto de entrenamiento que contiene un millón de instancias, ¿cuánto tiempo se tardará aproximadamente en entrenar otro árbol con diez millones de instancias?**

La complejidad computacional aproximada del algoritmo CART durante el entrenamiento es:

```text
O(n · m · log₂(m))
```

donde:

- `n` es el número de características.
- `m` es el número de instancias.

Al pasar de un millón a diez millones de instancias, el número de instancias se multiplica por 10. Sin embargo, el tiempo no se multiplica solamente por 10, porque también aumenta el término logarítmico.

La relación entre ambos tiempos es aproximadamente:

```text
10 · log₂(10 000 000) / log₂(1 000 000)
```

Como:

```text
log₂(1 000 000) ≈ 19,93
log₂(10 000 000) ≈ 23,25
```

obtenemos:

```text
10 · 23,25 / 19,93 ≈ 11,67
```

Por tanto, si el primer entrenamiento tarda una hora, el segundo tardará aproximadamente **11,7 horas**, es decir, alrededor de **11 horas y 40 minutos**.

Esta es una estimación teórica. El tiempo real también dependerá del equipo, la memoria disponible, las características de los datos y la implementación utilizada.

---

**6.- Si se tarda una hora en entrenar un árbol de decisión con un conjunto de entrenamiento dado, ¿cuánto se tardará aproximadamente si se duplica el número de características?**

Según la complejidad aproximada de CART:

```text
O(n · m · log₂(m))
```

el tiempo de entrenamiento crece de manera aproximadamente lineal con el número de características `n`.

Si se duplica el número de características y se mantienen constantes el número de instancias y el resto de las condiciones, el coste computacional también se duplicará aproximadamente.

Por tanto, si el entrenamiento original tarda una hora, al duplicar el número de características tardará alrededor de **dos horas**.

De nuevo, se trata de una aproximación teórica. El tiempo real puede variar según la información contenida en las nuevas características y los detalles de la implementación.