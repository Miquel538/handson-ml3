1.- ¿Que algoritmo de entrenamiento de regresion lineal puedes utilizar si tienes un conjunto de entrenamiento con millones de caracteristicas?

Para realizar un entrenemaiento de regression lineal con un conjunto de entrenamiento con tantas caracteristicas usaria modelos de descenso de gradiente estocastico o por minilotes

2.- Imagina que las características de tu conjunto de entrenamiento tienen escalas muy diferentes. ¿ Que algoritmo podría verse afectado por ello y como? ¿ Que puedes hacer al respecto?

Loas algoritmos que se pueden ver afectados por ello son los de descenso de gradiente. Al no escalar las características el algoritmo necesita mas iteraciones para llegar al minimo global y por tanto tarda mas tiempo. PAra evitar esto hay que escalar todas las caracteristicas ya sea aplicando un Standard Scaler.

3.- ¿ Puede el descenso de gradiente atascarse en un mínimo local cunado se entrena un modelo de regresión logística?

El descenso de gradiente no se puede atascar en un míniomo local debido a que los modelos de regresión logística son convexos de manera que solo tienen un único mínimo global

4.- ¿Todos los algoritmos de descenso de gradiente llevan al mismo modelo , simepre y cuando dejemos que se ejecuten el tiempo suficiente?

Si el problema es convexo, como regresión lineal o logística, todos los algoritmos de descenso de gradiente se acercarán al mínimo global si la tasa de aprendizaje es adecuada. Sin embargo, SGD y Mini-batch GD no convergerán exactamente si la tasa de aprendizaje no disminuye, sino que oscilarán alrededor del óptimo. 

5.- Imagina que utilizas el descenos de gradiente por lotes y trazas el error de validación en cada repetición. Si observas que el error de validacion sube de forma consistente, ¿ Que es probable que este ocurriendo? ¿ Cómo puedes arreglarlo?

Si el error de validación sube de forma consistente, puede que la tasa de aprendizaje sea demasiado alta y el algoritmo esté divergiendo. Si además sube el error de entrenamiento, habría que reducir la learning rate. Si el error de entrenamiento baja pero el de validación sube, entonces probablemente hay overfitting y conviene detener el entrenamiento o regularizar.

6.- Es aconsejable detener el descenso de gradiente por minilotes cuando de inmediato sube el error de validación?
No es aconsejable del todo, es mejor guardar los parametros del último modelo que ha reducido el error de validacion menor y dejar hacer unas pocas iteraciones mas, si los resultados no mejoran pues detener alli el entrenamiento.

7.- ¿ Que algoritmos de descenso de gradiente ( de entre los que hemos tratado ) llegarà mas ràpido a las proximidades de la solucion óptima?¿ Cuál convergerá de verdad ? ¿ Como puedes hacer que los otros también convergan ?
El mas rapido será el estocastico, el DG por lotes será el que convergerá de verdad. Para que el resto de algoritmos convergan se puede aplicar la estrategia del learning schedule de manera que se van reduciendo el tamaño de las iteraciones a medida que progresa el algoritmo.

8 .- Imagina que estas usando regresión polinomial. Trazas las curvas de aprendizaje y te das cuenta de que hay un espacio grande entre ele error de entrenamiento y el error de valdiación. ¿ Que està pasando ? ¿ Cuales son tres manera de solucionarlo ?

Si el error de entrenamiento es mucho menor que el de validación, el modelo está sobreajustando. Para solucionarlo se puede reducir el grado del polinomio, aplicar regularización como Ridge o Lasso, o aumentar el tamaño del conjunto de entrenamiento.

9 .- Imagina que estas usando regresión de arista y observas que el error de entrenamiento y el error de validacion son casi iguales y bastante altos. ¿ Dirías que el modelo sufre de sesgo alto o de varianza alta? ¿ Deberías incrementar el hiperparámetro de la regularización  alpha o reducirlo ?

El modelo sufre de sesgo alto, al ser el error de valdiacion y entrenamiento altos significa que ni por los datos de entrenamiento el modelo consigue generalizar de forma correcta. Por lo tanto hay que reducir alpha para disminuir el sesgo y permitir mas varianza al modelo.

10 .- ¿ por que te convendría usar :

- regresión de arista en vez de regresion lineal simple ( es decir, sin ninguna regularización )?
Conviene usar Ridge en vez de regresión lineal simple porque una pequeña regularización suele mejorar la generalización y reducir el riesgo de sobreajuste.
- regresion Lasso en vez de regressión de arista?
En caso de tener muchas caracteristicas en el dataset cuya importancia para hacer las predicciones sea baja, Lasso permite eliminar estas caracteristicas inservibles.
- red elástica en vez de regresión Lasso ?
En caso de tener mas caracteristicas que instancias de entrenamiento o cuando las caracteristicas estan correlacionadas fuertemente.

11 .- Imagina que quieres clasificar fotografías como exterior / interior y dia / noche. ¿ Deberías implementar dos clasificadores de regresión logísitca o un clasificador de regresión softmax ?
Hay que implementar dos classificadores de regresión logistica, softmax permite assignar probabilidades a varias labels y genera como salida solo la label cuya probabilidad sea mas alta, es decir una única salida, por lo tanto no nos sirve para este tipo de problema.

12 .- Implementa descenso de gradiente por lotes con detención temprana para una regresión softmax sin utilitzar SCikit - Learn, solo NumPy. Úsalo en una tarea de classificación como el conjunto de datos IRIS.



