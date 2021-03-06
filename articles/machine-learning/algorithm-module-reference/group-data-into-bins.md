---
title: Agrupación de datos en intervalos
titleSuffix: Azure Machine Learning
description: Obtenga información sobre cómo usar el módulo agrupar datos en ubicaciones para agrupar números o cambiar la distribución de datos continuos.
services: machine-learning
ms.service: machine-learning
ms.subservice: core
ms.topic: reference
author: likebupt
ms.author: keli19
ms.date: 05/19/2020
ms.openlocfilehash: b33aa3d2ab22fc986100d6141dd03d5547ef1862
ms.sourcegitcommit: 1f25aa993c38b37472cf8a0359bc6f0bf97b6784
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/26/2020
ms.locfileid: "83853737"
---
# <a name="group-data-into-bins"></a>Agrupación de datos en intervalos

En este artículo se describe cómo usar el módulo [agrupar datos en ubicaciones](group-data-into-bins.md) en Azure Machine Learning Designer (versión preliminar) para agrupar números o cambiar la distribución de datos continuos.

El módulo [agrupar datos en ubicaciones](group-data-into-bins.md) admite varias opciones para la cuantificación de datos. Puede personalizar el establecimiento de los extremo del intervalo y cómo se reparten los valores en ellos. Por ejemplo, puede:  

+ Escriba manualmente una serie de valores que sirvan como límites de la ubicación.  
+ Asigne valores a los depósitos mediante *cuantiles* o las clasificaciones de percentiles.  
+ Forzar una distribución uniforme de valores en las ubicaciones.  

### <a name="more-about-binning-and-grouping"></a>Más información sobre cuantificación y agrupación

La *Cuantificación* o agrupación de datos (a veces denominado *cuantificación*) es una herramienta importante para la preparación de datos numéricos para el aprendizaje automático y es útil en escenarios como estos:

+ Una columna de números continuos tiene demasiados valores únicos para modelar de forma eficaz, de modo que los valores se asignan de forma automática o manual a los grupos, con el fin de crear un conjunto más pequeño de rangos discretos.

+ Reemplace una columna de números por valores de categorías que representen rangos específicos.

    Por ejemplo, puede que desee agrupar los valores de una columna de edad especificando rangos personalizados, como 1-15, 16-22, 23-30, etc., para los datos demográficos de los usuarios.

+ Un conjunto de datos tiene algunos valores extremos, todos ellos fuera del rango esperado, y estos valores tienen una influencia insuficiente en el modelo entrenado. Para mitigar el sesgo en el modelo, puede transformar los datos en una distribución uniforme mediante el método cuantiles.

    Con este método, el módulo de [agrupaciones de datos en contenedores](group-data-into-bins.md) determina las ubicaciones de contenedor y los anchos de contenedor ideales para asegurarse de que aproximadamente el mismo número de muestras se encuentran en cada contenedor. A continuación, según el método de normalización que elija, los valores de los contenedores se transforman en percentiles o se asignan a un número de contenedor.

### <a name="examples-of-binning"></a>Ejemplos de cuantificación

En el diagrama siguiente se muestra la distribución de los valores numéricos anteriores y posteriores a discretización con el método de **cuantiles**. Observe que, en comparación con los datos sin procesar de la izquierda, los datos se han cuantificado y transformado en una escala de unidad normal.  

Se puede encontrar un ejemplo del resultado de la ejecución de esta canalización: https://ml.azure.com/visualinterface/authoring/Normal/87270db9-4651-448e-bd28-8ef7428084dc?wsid=%2Fsubscriptions%2Fe9b2ec51-5c94-4fa8-809a-dc1e695e4896%2Fresourcegroups%2Fmodule-ws-rg%2Fworkspaces%2Fmodule-prerelease-119&flight=cm&tid=72f988bf-86f1-41af-91ab-2d7cd011db47&smtendpoint=https%3A%2F%2Fsmt-test1.azureml-test.net

Dado que hay muchas maneras de agrupar los datos, todos los que se pueden personalizar, se recomienda experimentar con distintos métodos y valores. 

## <a name="how-to-configure-group-data-into-bins"></a>Configuración de datos de grupo en contenedores

1. Agregue el módulo de **Agrupación de datos en contenedores** a su canalización en el diseñador (versión preliminar). Puede encontrar este módulo en la categoría **Transformación de datos**.

2. Conecte el conjunto de datos que contiene datos numéricos a contenedor.  La cuantificación solo se puede aplicar a las columnas que contienen datos numéricos. 

    Si el conjunto de datos contiene columnas no numéricas, use el módulo [Seleccionar columnas del conjunto de datos](select-columns-in-dataset.md) para proyectar un subconjunto de columnas con el que trabajar.

3. Especifique el modo cuantificación. El modo cuantificación determina otros parámetros, por lo que debe asegurarse de seleccionar primero la opción **Modo cuantificación**. Se admiten los siguientes tipos de cuantificación:

    **Cuantiles**: El método de cuantil asigna valores a cubos basándose en rangos de percentil. Cuantiles también se conoce como alto de cuantificación de igualdad.

    **Mismo ancho**: Con esta opción, debe especificar el número total de contenedores. Los valores de la columna se colocarán en contenedores de forma que cada contenedor tiene el mismo intervalo entre los valores de inicio y fin. Como resultado, algunos contenedores pueden tener más valores si los datos se agrupan en torno a un punto determinado.

    **Bordes personalizados**: Puede especificar los valores que comienzan cada cubo. El valor del borde siempre es el límite inferior del contenedor.  Por ejemplo, suponga que desea agrupar los valores en dos contenedores, uno con valores mayores que 0 y otro con valores menores o iguales que 0. En este caso, para los bordes del contenedor, escribiría 0 en **Lista separada por comas de los bordes del contenedor**. La salida del módulo sería 1 y 2, que indica el índice de la ubicación de cada valor de fila. Tenga en cuenta que la lista de valores separados por comas debe estar en orden ascendente, como 1, 3, 5, 7.

4. **Número de cubos**: Si usa los modos de cuantificación **cuantiles** y **mismo ancho**, use esta opción para especificar el número de ubicaciones, o de *cuantiles*, que desea crear.

5. Para **Columnas a bin**, use el selector de columnas para elegir las columnas que tienen los valores que desea discretizar. Las columnas deben tener un tipo de datos numéricos.

    La misma regla de cuantificación se aplica a todas las columnas que elija. Por tanto, si necesita cuantificar columnas con un método distinto, use una instancia independiente de [Agrupación de datos en contenedores](group-data-into-bins.md) para cada conjunto de columnas.

    > [!WARNING]
    > Si elige una columna que no es un tipo permitido, se genera un error en tiempo de ejecución. El módulo devuelve un error en cuanto encuentra cualquier columna de un tipo no permitido. Si comete un error, revise todas las columnas seleccionadas. El error no muestra todas las columnas no válidas.

6. En **Modo de salida**, indique cómo desea que se generen los valores cuantificados.

      + **Anexión**: Crea una nueva columna con los valores discretizados y se anexa a la tabla de entrada.

      + **Inplace**: Reemplaza los valores originales por los nuevos valores en el conjunto de datos.

      + **ResultOnly**: Devuelve solo las columnas de resultados.

7. Si selecciona el modo de cuantificación de **Cuantiles**, use la opción **Normalización de cuantiles** para determinar cómo se normalizan los valores antes de la ordenación en cuantiles. Tenga en cuenta que la normalización de los valores transforma los valores, pero no afecta al número final de contenedores.

    Se admiten los siguientes tipos de normalización:

    + **Percent**: Los valores se normalizan en el rango [0100]

    + **PQuantile**: Los valores se normalizan en el rango [0,1]

    + **QuantileIndex**:  Los valores se normalizan en el rango [1, número de ubicaciones]

8. Si elige la opción **Bordes personalizados**, escriba una lista separada por comas de números que se usará como *Bordes del contenedor* en el cuadro de texto de la **Lista + de bordes del contenedor**.  Los valores marcan el punto que divide los contenedores; por lo tanto, si escribe un valor de borde de contenedor, se generarán dos contenedores; Si escribe dos valores de borde de contenedor, se generarán tres contenedores, etc.

    Los valores se deben ordenar en función del orden de creación de los contenedores, de menor a mayor.

10. **Columnas de etiqueta como de categorías**: Seleccione esta opción para indicar que las columnas cuantificadas se deben controlar como variables de categorías.

11. Envíe la canalización.

### <a name="results"></a>Results

El módulo [Grupo de datos en bins](group-data-into-bins.md) devuelve un conjunto de datos donde cada elemento se cuantifica según el modo especificado. 

También devuelve una **Transformación de cuantificación**, que es una función que puede pasarse al módulo [Aplicar transformación](apply-transformation.md) para contener nuevos ejemplos de datos usando el mismo modo y los mismos parámetros de cuantificación.  

> [!TIP]
> Recuerde que si usa cuantificación en los datos de entrenamiento, debe usar el mismo método cuantificación en los datos que usa para las pruebas y la predicción. Esto incluye el método de cuantificación, las ubicaciones del contenedor y el ancho del contenedor. 
> 
> Para asegurarse de que los datos se transforman siempre mediante el mismo método de cuantificación, se recomienda guardar transformaciones de datos útiles y, a continuación, aplicarlos a otros conjuntos de datos mediante el módulo [Aplicar transformación](apply-transformation.md).

## <a name="next-steps"></a>Pasos siguientes

Consulte el [conjunto de módulos disponibles](module-reference.md) para Azure Machine Learning. 
