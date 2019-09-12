## Tarea 1: Minería de Datos IIC2433

#### Francisca Leão Cerquinho Ribeiro da Fonseca - 19410263
#### 17 Septiembre 2019

## Definiciones
 **Itemset:** Colección de uno o más ítems
 
 **Soporte:** Frecuencia relativa que un itemset aparece en la base de datos. 
 Esto se calcula como el número itemset que aparece en la base de datos de compras dividido por el número total de compras (transacciones).

 **Itemset frecuente:** Un itemset que aparece en una frecuencia mayor a un umbral. El umbral está determinado por uno o bien viene dado.

 **Regla de asociación:** Es una expresión de la forma X -> Y Donde X e Y son itemsets
 
 **Confianza:** 

    confianza(X -> Y) = soporte(X,Y) / soporte(X)

 **Lift:** Permite medir el incremento del lado derecho de la regla (consecuente) dada la compra del lado izquierdo (antecedente)
 Confianza de la regla dividido por el soporte del consecuente.

    Lift = confianza(X -> Y) / soporte(Y)

**- Lift > 1:** La probabilidad del consecuente de la regla aumentó dado que el consumidor compró los ítems del antecedente
**- Lift = 1:** La probabilidad no se vio afectada, es decir, el consecuente no se ve influenciado por el antecedente
**- Lift < 1:** El antecedente tuvo un efecto negativo en la ocurrencia del consecuente, lo que baja su probabilidad

## Instruccíones adicionales


Para seleccionar la cantidad de arrays de bases de datos que queremos usar, cambie la variable **'nr_arrays'** definida en el primer bloque de código. El soporte mínimo deseado para cada elemento también se define, la variable se llama **'min_support'**.

Durante la implementación del algoritmo FP-Growth, traté de comentar sobre el código y dibujé tablas ilustrativas en todo el código, para que sea más fácil de entender.

En la parte final, para filtrar las 10 mejores reglas de membresía, el soporte, confianza y lift mínimos deseados se definen en las variables:
- desiredSupport
- desiredConfidence
- desiredLift