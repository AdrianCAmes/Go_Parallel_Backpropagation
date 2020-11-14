# Go Parallel Backpropagation
Este proyecto es una implementación del algoritmo de aprendizaje supervisado Backpropagation en el lenguaje Go, añadiendo características de paralelismo al código para mejorar su rendimiento.

## Acerca del algoritmo usado
Como ya se mencionó anteriormente, el algoritmo implementado en este trabajo es Backpropagation, el cual es un algoritmo de aprendizaje supervisado. Se dice que es un algoritmo supervisado ya que, al momento de entrenar la red, se le dará un valor esperado por cada patrón de entrenamiento, lo cual le servirá para diagnosticar qué tan alejada está la respuesta obtenida de la respuesta correcta. 
Para ejecutar este algoritmo es imperativo realizar dos etapas, las cuales son:

### Propagación hacia adelante: 
En esta etapa, la red neuronal recibe un set de datos y se encarga de predecir cuál será el valor de salida mediante la multiplicación escalar de los pesos y las entradas de las neuronas. Asimismo, vale indicar que al resultado de aquella multiplicación se le debe añadir el valor del bias respectivo a cada neurona y, finalmente, hacer que todo aquello pase a través de una función de activación (sigmoidal para este trabajo).

### Propagación hacia atrás: 
Esta es la etapa en la cual la red neuronal realiza el aprendizaje. Para ello, lo primero que se debe efectuar es el cálculo del error entre el valor esperado y el valor que la red predijo. Luego, se comienza a propagar dicho error desde la última capa hacia las capas anteriores, utilizándolo para actualizar los pesos y bias de la red.

## Acerca del dataset usado
El dataset que se tomó como referencia para el entrenamiento es el conocido dataset de Iris, el cual contiene información acerca de la clasificación de flores Iris dependiendo de ciertas características. Nótese que Iris es un tipo de flor y para el presente trabajo se están tomando en cuenta dos de sus clases: Iris Setosa e Iris Versicolour.
		
Cada patrón de este dataset contiene cinco atributos, los cuales serán explicados a continuación.
Los cuatro primeros valores de cada patrón de entraniemnto representan lo siguiente:
* Longitud del sépalo en cm.
* Ancho del sépalo en cm.
* Longitud del pétalo en cm.
* Ancho del pétalo en cm.

El último atributo representa a qué clase pertenece la flor Iris evaluada, asímismo, este campo es el que se tomará como el valor esperado al cual nuestra red neuronal debería apuntar. Tómese como referencia la siguiente clasificación:
* Clase:
  - 0 -> Iris Setosa
  - 1 -> Iris Versicolour

## ¿Cómo se paraleliza el algoritmo?
En este trabajo, se propone paralelizar el algoritmo dividiendo el set de datos inicial en cuatro partes. Luego de la división, se realizará paralelamente la propagación hacia adelante de cada una de las partes y, posteriormente, una vez que se han propagado todas, se avisa al hilo principal mediante el uso de canales y se prosigue con una sola etapa de propagación hacia atrás (aprendizaje). Una ejecución de lo mencionado anteriormente es considerado como una época, y el algoritmo realizará "n" cantidad de épocas para su aprendizaje. Luego, se plantea calcular el error de todo el modelo para estimar qué tan precisa es la predicción de resultados en la red neuronal. Esto se logará mediante el cálculo del error cuadrático medio de todas épocas. Finalmente, las métricas del modelo (error y tiempo de ejecución) serán impresas para su visualización.

## Topología de red neural
La topología de la red implementada en el trabajo es la de perceptrón multicapa. Esta consta de una capa de entrada, con cuatro neuronas; una capa intermedia, con dos neuronas; y una capa de salida, con una neurona.

## Enlaces consultados
[Build Your Own Neural Network in Go](https://towardsdatascience.com/neural-network-from-scratch-in-go-language-b98e2abcced3)
