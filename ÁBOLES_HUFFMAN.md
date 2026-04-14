# ÁRBOLES DE HUFFMAN
<img width="665" height="417" alt="image" src="https://github.com/user-attachments/assets/253038bb-7dbd-49e0-81be-4eae69c31838" />

## Concepto:
### Los árboles de Huffman son una estructura de datos de tipo árbol binario extendido que se utiliza como base para un algoritmo de codificación eficiente, cuya finalidad es lograr una compresión de datos con redundancia mínima. Este algoritmo fue propuesto por David Huffman en 1952, durante su tiempo en el MIT, y es especialmente útil en la representación de un conjunto de símbolos de tal manera que la longitud media del código asociado a cada símbolo sea lo más corta posible.

### En términos de su funcionamiento, el árbol de Huffman asigna a cada símbolo o letra un código binario de longitud variable, donde los símbolos más frecuentes en el texto a comprimir reciben códigos más cortos y los menos frecuentes, códigos más largos. La clave está en la construcción del árbol binario, donde se agrupan los símbolos de acuerdo con su probabilidad de aparición, buscando siempre la minimización de la longitud total del código, y por lo tanto, una mejor eficiencia en la representación del texto.

## ¿Qué tiene de especial?🥇😃
### Una de las principales diferencias de los arboles de Huffman con los árboles convencionales de búsqueda binaria es que el arbol de Huffman **no se utiliza para ordenar elementos** sino que se usa para mapear o direccionar la frecuencia de cada letra en un espacio de memoria mucho menor, a rutas binarias, comparado al caracter que tenia anteriormente .


## Componentes Lógicos y Físicos de los arboles de Huffman🌳✨
## Es de crucial importantancia conocer los componentes de estos árboles para entender como funciona dicha estructura, dentro de los componentes podemos destacar los siguientes:

## 1. Nodo Raiz: 
En el contexto de los árboles de Huffman el nodo raiz es el que representa la ***suma de todas las frecuencias del conjunto de datos***, también es el nodo superior.

## 2. Nodos Hoja: 
Son aquellos nodos que no tienen hijos, en árboles de Huffman, cada nodo hoja ***guarda un símbolo del alfabeto*** y su frecuencia (peso, es decir las veces que se repite este carácter).

## 3. Nodos internos: 
Un nodo interno es definido como la raíz de un subárbol

## 4. Peso o Frecuencia:
Es el valor asociado a cada símbolo que indica cuántas veces aparece en el texto.

## Algoritmo de Huffman paso a paso🐾🖱️
### Para este componente realizaremos 2 ejercicios para explicarlo mejor:
#### ELIAS
