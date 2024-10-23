En este repositorio comparto el codigo de la red neuronal informada por la física (PINN) que implemente en Python para la solución del problema de referencia clasico "Lid-Driven Cavity 2D". 

El archivo "lid-driven-cavity-2d-pinn-code.ipynb" es un notebook con el codigo de la red neuronal. Este codigo esta ajustado para que al ejecutarse se entrene de forma automatica el modelo [2, 130, 30] con función de activación "swish". Si se desea cambiar la configuración del modelo (número de capas o cantidad de neuronas por capa), basta con dirigirse a la ultima celda de ese mismo notebook y asignar a la variable "MODELO" una lista con la configuración de capas y neuronas que se desee. Por ejemplo: 

MODELO = [2, 30, 30, 45, 3]  (NOTA: La lista siempre debe iniciar en 2 y terminar en 3)

Mientras que para imponer la función de activación "mish", se debe escribir "mish", en lugar de "swish" en la ultima celda del notebook "lid-driven-cavity-2d-pinn-code.ipynb".


La carpeta "Training Dataset", contiene los archivos descargables de los arreglos numpy de los puntos del dominio del problema que se usaron para entrenar la PINN del trabajo: "Redes Neuronales Informadas por la Física para la Resolución de EDPs No Lineales: Un Caso de Estudio con el Problema Bidimensional Lid-Driven Cavity" (por si alguien desea utilizar los mismos datos obtenidos que fueron usados en este trabajo)

xy_train.npy: Son las coordenadas (x,y) de los puntos en el interior del dominio.
xy_up.npy: Son las coordenadas (x,y) de los puntos en la frontera superior del dominio
xy_down.npy: Son las coordenadas (x,y) de los puntos en la frontera inferior del dominio
xy_left.npy: Son las coordenadas (x,y) de los puntos en la frontera izquierda del dominio
xy_right.npy: Son las coordenadas (x,y) de los puntos en la frontera derecha del dominio

Una vez descargados los archivos, pueden cargarse y asignarse a alguna variable, por ejemplo:

  import numpy as np
  xy_interiores = np.load("xy_train.npy")

Se determinó que el modelo con el mejor desempeño de todas las cofiguraciones que se consideraron, fue el [2, 130, 130, 30, 80, 80, 3] con activación "mish". Si se desea usar este modelo ya optimizado sin tener que entrenar la red neuronal, se puede descargar el archivo "2 130 130 30 80 80 3_mish_better_model.weights.h5", el cual se puede usar para cargar en el modelo [2, 130, 130, 30, 80, 80, 3] con activación "mish", los parámetros ya optimizados.
