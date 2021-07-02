###################################################### README #############################################################
Este proyecto está basado en el trabajo del 2017 "Unpaired Image-to-Image Translationusing Cycle-Consistent Adversarial Networks", arXiv:1703.10593. Para la implementación utilicé, como base, la brindada por la página oficial de keras https://keras.io/examples/generative/cyclegan/.

Los datos son de la base de datos para cycle_gan de tensorflow https://www.tensorflow.org/datasets/catalog/cycle_gan 


Yo trabajé en colab. En caso de querer usar la notebook, el vínculo es público: https://colab.research.google.com/drive/1Yk2QiEtVHMlmVTKSjh_gYJG0mp56JPzq?usp=sharing y simplemente tenes que vincular el drive y descomentar la línea 11 de la celda 3 con el path que corresponda al punto zip del problema que quieras.

Para usar el .py, primero es necesario descargar la carpeta del problema que quieras (checkpoints_somethingA2somethingB) y pararse dentro de la misma para correr el codigo. De ahí todos los pasos siguientes pasos son necesarios:

------------------------------------------------------ PASO 1 -------------------------------------------------------------
Para correr el programa primero hay que elegir el problema (variable problem al inicio del programa):
"horse2zebra", "facades", "apple2orange","ukiyoe2photo","vangogh2photo","cezanne2photo"(default), "iphone2dslr_flower","summer2winter_yosemite" y "monet2photo".

ATENCIÓN: No incluyo las opciones maps y cityscapes debido a que no poseo modelos pre-entrenados con esas bases de datos.
Una corrida de 10 épocas puede llegar a tardar 100'~150', no los presento como opción. Yo no llegué a correrlos :(
La misma razón es justifica que las épocas en el diccionario de arriba sean tan distintas.

------------------------------------------------------ PASO 2 -------------------------------------------------------------
Es necesario indicarle a la variable rooth_path, un string que contenga el path en donde se encuentran los archivos que contienen los pesos a cargar. 
Para el caso del default es de la forma (recorda que yo trabaje en colab):
rooth_path='/content/cyclegan_checkpoints.063'

Si queres elegir otro modelo simplemente cambia "cezanne2photo" por el que desees y 63 por su analogo en:
best_model_epochs={"horse2zebra":90, "facades":67,  "apple2orange":38,
                   "ukiyoe2photo":77,"vangogh2photo":40,"cezanne2photo":63, 
                   "iphone2dslr_flower":35,"summer2winter_yosemite":28,
                   "monet2photo":33}

----------------------------------------------------- PASO 3 -------------------------------------------------------------
Debido a lo costoso que es este modelo, no sugiero correr más de una época para probar si el código funciona. Esto se puede setear seteando run=True. Si, a pesar de las advertencias te animas a correrlo con más épocas, podes elegir la cantidad de épocas mediante la variable epoch2train.

Valor por default run <-> False
Valor por default epochs2train <-> 1
----------------------------------------------------- PASO 4 -------------------------------------------------------------
Al igual que en el trabajo que motivó a este proyecto, se pueden ver las predicciones hechas por el modelo con los datos de train y con los de test. Esto se elige seteando la variable data2show a 'test' o 'train'. Con la variable n_examples se elige el número de ejemplos a mostrar (un ejemplo incluye dos transformaciones: A->B y B->A).

NOTA: Al igual que en el trabajo, lo más probable es que los resultados con train sean mejores que los que se obtienen con test. Los resultados completos de todas las aplicaciones tanto de entrenamiento como de datos de prueba, se pueden ver en la página web de los autores del paper https://junyanz.github.io/CycleGAN/

Valor por default data2show <-> 'test'
Valor por default n_examples <-> 3

############################################################################################################################