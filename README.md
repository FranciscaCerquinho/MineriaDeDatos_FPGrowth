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


### Funciones

**getDatabaseArray(databaseName)**
Función que devuelve un array con la base de datos
   - databaseName (string) : nombre de archivo de base de datos

**getItemsSupport(data_base_array,nr_arrays)**
Función que devuelve un diccionario donde la clave es el item y el valor es su soporte
   - data_base_array(array) : base de datos array
   - nr_arrays (number) : cantidad de arrays de bases de datos que quiero usar

**deleteElemsWithoutSupportMin(itemsSupport,min_support)**
Función que elimina elementos del diccionario que no tienen el soporte mínimo deseado y devuelve un nuevo diccionario
   - itemsSupport (diccionario) : diccionario donde la clave es el item y el valor es su soporte
   - min_support (number) : soporte mínimo deseado

**deleteArrayElements(array,itemsSupport)**
Función que elimina elementos del array de itemsets que no aparecen en el diccionario itemsSupport
   - array (array) : base de datos array
   - itemsSupport (diccionario) : diccionario donde la clave es el item y el valor es su soporte

**sortArrayElement(array,itemsSupport)**
Función que ordena elementos del array en orden descendente, teniendo en cuenta el soporte
   - array (array) : base de datos array
   - itemsSupport (diccionario) : diccionario donde la clave es el item y el valor es su soporte

**orderItemSet(data_base_array,itemsSupport,nr_arrays)**
Función que elimina elementos que no tienen el soporte mínimo deseado y ordena el array de la base de datos
   - data_base_array(array) : base de datos array
   - itemsSupport (diccionario) : diccionario donde la clave es el item y el valor es su soporte
   - nr_arrays (number) : cantidad de arrays de bases de datos que quiero usar

**returnPattern_stringIndex(pattern_string, list_patterns)**
Función que devuelve el index donde un elemento está en un array
   - pattern_string (string) : elem
   - list_patterns (array) : array

**getConditionalPattern_array(new_data_base_array,itemsSupport)**
Función que devuelve un diccionario donde para cada elemento tiene un diccionario con los "Conditional Pattern Base"
   - new_data_base_array (array) : base de datos array
   - itemsSupport (diccionario) : diccionario donde la clave es el item y el valor es su soporte

**changeListOfOccurrences(a, b,listOfOccurrences)**
Función que cuenta las ocurrencias de cada elemento de un array en otro array y devuelve la lista actualizada
   - a (array)
   - b (array)
   - listOfOccurrences (array) 

**getCommonValues(firstElem,listOfOccurrences,arrayLength)**
Función que compara el primer elemento([A, B, C])  de un array de arrays:([[A,B,C],[A,C,B],[A,B,E]] )
Crea un array de igual tamaño con las ocurrencias [1,1,1], luego compara otras matrices con esta y agrega una a esta matriz si un elemento igual está en la misma posición que mi primer elemento. 
En otras palabras, para [A, C, B] fue [2,1,1] y para [A, B, E] fue [3,2,1]
   - firstElem (array)
   - listOfOccurrences (array) 
   - arrayLength (array) : tamaño del array de arrays

**commonsElemInArrayOfArrays(array)**
Función que devuelve los primeros elementos comunes en todos los arrays de un array de arrays
   - array (array of arrays [][])

**getCommonsItems(conditionalPattern_array)**
Función que busca los items comunes en itemset de conditional pattern base
   - conditionalPattern_array (diccionario) : diccionario donde para cada elemento tiene un diccionario con los "Conditional Pattern Base"

**getFrequentPattern(dict_itemsComunes)**
Función que busca los frequent pattern usando la columna Items y Conditional FP-Tree
   - dict_itemsComunes (diccionario) : items comunes en itemset de conditional pattern base

**getFrequentItems(dict_frequent_pattern,itemsSupport)**
Función que devuelve un diccionario con los conjuntos de elementos más frecuentes y su soporte
   - dict_frequent_pattern (diccionario) : diccionario donde para cada elemento tiene un diccionario con los frequent pattern
   - itemsSupport (diccionario) : diccionario donde la clave es el item y el valor es su soporte

**fit(databaseName,nr_arrays,min_support)**
Función que aplica el algoritmo a la base de datos
   - databaseName (array) : base de datos array
   - nr_arrays (number) : cantidad de arrays de bases de datos que quiero usar
   - min_support (number) : soporte mínimo deseado

**join(singular_itemsets, comb)**
Función que crea todas las combinaciones únicas y diferentes de un array de elementos
   - singular_itemsets (array)
   - comb (array)

**generate(itemset_freq)**
Función que devuelve un diccionario las reglas de asociación donde la clave es la regla y el valor es su soporte, confianza e lift
   - itemset_freq (diccionario) : diccionario con frequent_pattern y su soporte

**top10ReglasSupConfLift(dict_itemsets_conf_sup,support, confidence, lift)**
Filtrar las mejores 10 reglas de acuerdo a dos criterios de calidad definidos (support, confidence, lift)
   - dict_itemsets_conf_sup (diccionario) : un diccionario las reglas de asociación donde la clave es la regla y el valor es su soporte, confianza e lift
   - support (number) : soporte deseado
   - confidence (number) : confidence deseado
   - lift (number)) : lift deseado

**top10Reglas(dict_itemsets_conf_sup,support, confidence)**
Filtrar las mejores 10 reglas de acuerdo a dos criterios de calidad definidos (support, confidence, lift)
   - dict_itemsets_conf_sup (diccionario) : un diccionario las reglas de asociación donde la clave es la regla y el valor es su soporte, confianza e lift
   - support (number) : soporte deseado
   - confidence (number) : confidence deseado
   - lift (number) : lift deseado

**convertRulesToTuples(associationRules)**
Función que pone las reglas en el formato deseado por la función de visualizacion previa
   - associationRules (diccionario) : reglas

**makeAdditionalInformation(associationRules,dict_itemsets_conf_sup,metric)**
   - associationRules (diccionario) : reglas
   - dict_itemsets_conf_sup (diccionario) :  un diccionario las reglas de asociación donde la clave es la regla y el valor es su soporte, confianza e lift
   - metric (number) : si es 0 tenemos el soporte, si es 1 tenemos la confianza

**visualize(rules,withAdditionalInformation)**
Función que devuelve un gráfico con las reglas de asociación
   - rules (diccionario)  
   - withAdditionalInformation (diccionario) 

#### Draw Tables
**drawItemsSupportTable(itemsSupport)**
Tabla con el total de support de cada item
   - itemsSupport (diccionario) : diccionario donde la clave es el item y el valor es su soporte

**drawElemsWithoutSupportMinTable(itemsSupport)**
Tabla con el total de support de cada item que tiene el soporte mínimo deseado
   - itemsSupport (diccionario) : diccionario donde la clave es el item y el valor es su soporte

**orderItemSetTable(new_data_base_array)**
Tabla con los itemsets ordenados que tienen el support mínimo deseado
   - new_data_base_array (array) : base de datos array

**conditionalPatternArrayTable(conditionalPattern_array)**
Tabla con los itemsets ordenados y su conditional pattern
   - conditionalPattern_array (diccionario) : diccionario donde la clave es el item y el valor es un diccionario con los "Conditional Pattern Base"

**getCommonsItemsTable(dict_itemsComunes,conditionalPattern_array)**
Tabla con los items comunes en itemset de conditional pattern base
   - dict_itemsComunes (diccionario) : dicionario donde la clave es el item y el valor es un diccionario con los items comunes en el conditional pattern base
   - conditionalPattern_array (diccionario) : diccionario donde la clave es el item y el valor es un diccionario con los "Conditional Pattern Base"

**frequentPatternTable(dict_frequent_pattern)**
Tabla con los itemset más frecuentes (dict_frequent_pattern) (itemsSupport + dict_itemsComunes)
   - dict_frequent_pattern (diccionario) : dicionario donde la clave es el item y el valor es un diccionario con los frequent pattern

**frequentItemsTable(itemset_freq)**
Tabla con los itemset más frecuentes (itemsSupport + dict_frequent_pattern)
   - itemset_freq (diccionario) : diccionario con frequent_pattern y su soporte

**drawAssociationRulesTable(dict_itemsets_conf_sup,associationRules,desiredSupport,desiredConfidence,desiredLift)**
Tabla con las reglas de asociación y su soporte, confianza y lift
   - dict_itemsets_conf_sup (diccionario) : 
   - desiredSupport (number) : soporte deseado 
   - desiredConfidence (number) : confidence deseado
   - desiredLift (number) : lift deseado


Para seleccionar la cantidad de arrays de bases de datos que queremos usar, cambie la variable **'nr_arrays'** definida en el primer bloque de código. El soporte mínimo deseado para cada elemento también se define, la variable se llama **'min_support'**.

Durante la implementación del algoritmo FP-Growth, traté de comentar sobre el código y dibujé tablas ilustrativas en todo el código, para que sea más fácil de entender.

En la parte final, para filtrar las 10 mejores reglas de membresía, el soporte, confianza y lift mínimos deseados se definen en las variables:
- desiredSupport
- desiredConfidence
- desiredLift