# ÁRBOLES DE HUFFMAN
<img width="665" height="417" alt="image" src="https://github.com/user-attachments/assets/253038bb-7dbd-49e0-81be-4eae69c31838" />

## Concepto:
### Los árboles de Huffman son una estructura de datos de tipo árbol binario extendido que se utiliza como base para un algoritmo de codificación eficiente, cuya finalidad es lograr una compresión de datos con redundancia mínima. Este algoritmo fue propuesto por David Huffman en 1952, durante su tiempo en el MIT, y es especialmente útil en la representación de un conjunto de símbolos de tal manera que la longitud media del código asociado a cada símbolo sea lo más corta posible.

### En términos de su funcionamiento, el árbol de Huffman asigna a cada símbolo o letra un código binario de longitud variable, donde los símbolos más frecuentes en el texto a comprimir reciben códigos más cortos y los menos frecuentes, códigos más largos. La clave está en la construcción del árbol binario, donde se agrupan los símbolos de acuerdo con su probabilidad de aparición, buscando siempre la minimización de la longitud total del código, y por lo tanto, una mejor eficiencia en la representación del texto.

## ¿Qué tiene de especial?🥇😃
### Una de las principales diferencias de los arboles de Huffman con los árboles convencionales de búsqueda binaria es que el arbol de Huffman **no se utiliza para ordenar elementos** sino que se usa para mapear o direccionar la frecuencia de cada letra en un espacio de memoria mucho menor, a rutas binarias, comparado al caracter que tenia anteriormente .


## Componentes Lógicos y Físicos de los arboles de Huffman🌳✨
### Es de crucial importantancia conocer los componentes de estos árboles para entender como funciona dicha estructura, dentro de los componentes podemos destacar los siguientes:

### 1. Nodo Raiz: 
En el contexto de los árboles de Huffman el nodo raiz es el que representa la ***suma de todas las frecuencias del conjunto de datos***, también es el nodo superior.

### 2. Nodos Hoja: 
Son aquellos nodos que no tienen hijos, en árboles de Huffman, cada nodo hoja ***guarda un símbolo del alfabeto*** y su frecuencia (peso, es decir las veces que se repite este carácter).

### 3. Nodos internos: 
Un nodo interno es definido como la raíz de un subárbol

### 4. Peso o Frecuencia:
Es el valor asociado a cada símbolo que indica cuántas veces aparece en el texto.

## Algoritmo de Huffman paso a paso🐾🖱️
### Para este componente realizaremos 2 ejercicios para explicarlo mejor:
## 1. ARRIETA
Recordemos que en una cadena de caracteres, cada letra equivale a guardar en la memoria 1 byte, que son 8 bits, *"ARRIETA"* contiene 7 caracteres, por lo que en total ocuparía 56 bits de almacenamiento.

### Paso 1= Realizar una tabla de frecuencias
Para cada una de las letras, haremos la cuenta de cuantas veces se repite en la palabra:
|Letra|Peso|
|:---:|:--:|
|A|2|
|R|2|
|I|1|
|E|1|
|T|1|
### Paso 2= Armar el árbol binario
1. Empezamos siempre con los caracteres que aparecen menos:
   A=2, R=2, 🫴I=1, 🫴E=1, 🫴T=1
2. Formamos pares entre los menores, donde su padre o raíz es la suma de ambos pesos
    🫴I=1 y 🫴E=1
```
          --------
         |Raíz (2)|
          --------
           /     \
       -----     -----
      |I (1)|   |E (1)|
       -----     -----
  ```
3. Seguimos con los menores
   A=2, R=2, 🫴IE=2, 🫴T=1
   ```
              ---------
             |Padre (3)|
              ---------
                /     \
          ---------    -----
         |Padre (2)|  |T (1)|
          ---------    -----
           /     \
       -----     -----
      |I (1)|   |E (1)|
       -----     -----
   ```
4. Terminamos de formar pares con los mayores
 🫴A=2,  🫴R=2, IET=3
```
          --------
         |Raíz (4)|
          --------
           /     \
       -----     -----
      |A (2)|   |R (2)|
       -----     -----
```
5. Unimos ambos árboles
```
                       --------
                      |Raíz (7)|
                       --------
                        /     \
              ---------         ---------
             |Padre (3)|       |Padre (4)|
              ---------         ---------
                /     \           /     \
          ---------    -----    -----     -----
         |Padre (2)|  |T (1)|  |A (2)|   |R (2)|
          ---------    -----    -----     -----
           /     \
       -----     -----
      |I (1)|   |E (1)|
       -----     -----
```
### Paso 3: Agregamos los valores binarios
Todos los nodos que estén a la izquierda serán equivalentes a **0**, los de la derecha a **1**.
```
        
                       --------
                      |Raíz (7)|
                       --------
                        /     \
                  CERO          UNO
              ---------         ---------
             |Padre (3)|       |Padre (4)|
              ---------         ---------
                /     \           /     \
             CERO     UNO      CERO      UNO
          ---------    -----    -----     -----
         |Padre (2)|  |T (1)|  |A (2)|   |R (2)|
          ---------    -----    -----     -----
           /     \
       CERO      UNO
       -----     -----
      |I (1)|   |E (1)|
       -----     -----
```
### Paso 4: Tomar la dirección desde el primer nodo hasta el que queremos (desde que hay valores de cero o uno):
|Letra|Camino|
|:---:|:--:|
|A|10|
|R|11|
|I|000|
|E|001|
|T|01|

### Ese camino binario para cada caracter, son los bits de el espacio que tomará en el almacenamiento:
|Letra|Frecuencia|Código|Bits usados|
|:---:|:---:|:----:|:----:|
|A|2|10|2×2 = 4|
|R|2|11|2×2 = 4|
|T|1|01|1×2 = 2|
|I|1|000|1×3 = 3|
|E|1|001|1×3 = 3|

### Entonces el espacio en memoria solo sería de 16 bits (2 bytes)

### COMPARACIÓN:
#### ARRIETA = 56 bits (7 bytes)
#### HUFFMAN = 16 bits (8 bytes)
Cabe mencionar que no solo se redujo el tamaño para guardarlo en la memoria, si no que también **no se perdió ni un solo dato**.

## 2. SHILOH
En cada letra equivale a guardar en la memoria 1 byte, que son 8 bits, "SHILOH" contiene 6 caracteres, por lo que en total ocuparía 48 bits de almacenamiento.

### Paso 1= Realizar una tabla de frecuencias
Para cada una de las letras, haremos la cuenta de cuántas veces se repite en la palabra:
|Letra|Peso|
|:---:|:--:|
|S|1|
|H|2|
|I|1|
|L|1|
|O|1|
### Paso 2= Armar el árbol binario
1. Empezamos siempre con los caracteres que aparecen menos:
   🫴S=1, 🫴I=1, 🫴L=1, 🫴O=1, H=2
2. Formamos pares entre los menores, donde su padre o raíz es la suma de ambos pesos:
   🫴S=1 y 🫴I=1
```
          --------
         |Raíz (2)|
          --------
           /     \
       -----     -----
      |S (1)|   |I (1)|
       -----     -----
  ```
3. Seguimos con los menores
   🫴L=1, 🫴O=1, SI=2, H=2
```
          --------
         |Raíz (2)|
          --------
           /     \
       -----     -----
      |L (1)|   |O (1)|
       -----     -----
```
4. Seguimos formando pares
   🫴(SI)=2 y 🫴(LO)=2
   
```
                       --------
                      |Padre (4)|
                       --------
                        /     \
              ---------         ---------
             |Padre (2)|       |Padre (2)|
              ---------         ---------
                /     \           /     \
          -----    -----    -----     -----
         |S (1)|  |I (1)|  |L (O)|   |O (1)|
          -----    -----    -----     -----
```
5. Terminamos de formar el árbol con el último carácter
   🫴H=2 y 🫴(SILO)=4
```
                               --------
                              |Raiz (6)|
                               --------
                                /     \
                       --------        -----
                      |Padre (4)|     |H (2)|
                       --------        -----
                        /     \
              ---------         ---------
             |Padre (2)|       |Padre (2)|
              ---------         ---------
                /     \           /     \
          -----    -----    -----     -----
         |S (1)|  |I (1)|  |L (O)|   |O (1)|
          -----    -----    -----     -----
```
### Paso 3: Agregamos los valores binarios
Todos los nodos que estén a la izquierda serán equivalentes a **0**, los de la derecha a **1**.
```
                                 
                               --------
                              |Raiz (6)|
                               --------
                                /     \
                          CERO          UNO
                       --------        -----
                      |Padre (4)|     |H (2)|
                       --------        -----
                        /     \
                  CERO          UNO
              ---------         ---------
             |Padre (2)|       |Padre (2)|
              ---------         ---------
                /    \           /     \
           CERO      UNO      CERO     UNO
          -----    -----    -----     -----
         |S (1)|  |I (1)|  |L (O)|   |O (1)|
          -----    -----    -----     -----
```
### Paso 4: Tomar la dirección desde el primer nodo hasta el que queremos (desde que hay valores de cero o uno):
|Letra|Camino|
|:---:|:--:|
|S|000|
|H|1|
|I|001|
|L|010|
|O|011|

### Ese camino binario para cada caracter, son los bits de el espacio que tomará en el almacenamiento:
|Letra|Frecuencia|Código|Bits usados|
|:---:|:---:|:----:|:----:|
|S|2|000|1×3 = 3|
|H|2|1|2×1 = 2|
|I|1|001|1×3 = 3|
|L|1|010|1×3 = 3|
|O|1|011|1×3 = 3|
### Entonces el espacio en memoria solo sería de 14 bits 

### COMPARACIÓN:
#### SHILOH = 48 bits (6 bytes)
#### HUFFMAN = 14 bits (casi 1 byte)

## Código en Python🐍💻
### ARRIETA:
```python
class Nodo:
    def __init__(self, dato, peso):
        self.dato = dato
        self.peso = peso
        self.izq = None
        self.der = None


class ArbolHuffman:
    def __init__(self):
        self.raiz = None

    def construir_arbol(self):
        # Letras de ARRIETA
        A = Nodo("A", 2)
        R1 = Nodo("R1", 2)
        R2 = Nodo("R2", 2)
        I = Nodo("I", 1)
        E = Nodo("E", 1)
        T = Nodo("T", 1)

        # Uniones (listas enlazadas)
        IE = Nodo("IE", I.peso + E.peso)
        IE.izq = I
        IE.der = E

        IET = Nodo("IET", IE.peso + T.peso)
        IET.izq = IE
        IET.der = T

        RR = Nodo("RR", R1.peso + R2.peso)
        RR.izq = R1
        RR.der = R2

        RIET = Nodo("RIET", RR.peso + IET.peso)
        RIET.izq = RR
        RIET.der = IET

        self.raiz = Nodo("ARRIETA", A.peso + RIET.peso)
        self.raiz.izq = A
        self.raiz.der = RIET

    def mostrar(self, nodo, nivel=0):
        if nodo:
            print("  " * nivel + f"{nodo.dato} ({nodo.peso})")
            self.mostrar(nodo.izq, nivel + 1)
            self.mostrar(nodo.der, nivel + 1)


# -------------------------
# EJECUCIÓN
# -------------------------

arbol = ArbolHuffman()
arbol.construir_arbol()

print("Árbol de Huffman (ARRIETA):\n")
arbol.mostrar(arbol.raiz)

# Cálculo de bits
original = 7 * 8   # 56 bits
huffman = 16       # resultado del ejercicio

print("\n--- COMPRESIÓN ---")
print(f"Sin Huffman: {original} bits")
print(f"Con Huffman: {huffman} bits")
print(f"Reducción: {original - huffman} bits")

```
### SHILOH:
```python
class Nodo:
    def __init__(self, dato, peso):
        self.dato = dato
        self.peso = peso
        self.izq = None
        self.der = None


class ArbolHuffman:
    def __init__(self):
        self.raiz = None

    def construir_arbol(self):
        # Letras de SHILOH
        S = Nodo("S", 1)
        I = Nodo("I", 1)
        L = Nodo("L", 1)
        O = Nodo("O", 1)
        H = Nodo("H", 2)

        # Uniones (listas enlazadas)
        SI = Nodo("SI", S.peso + I.peso)
        SI.izq = S
        SI.der = I

        LO = Nodo("LO", L.peso + O.peso)
        LO.izq = L
        LO.der = O

        SILO = Nodo("SILO", SI.peso + LO.peso)
        SILO.izq = SI
        SILO.der = LO

        self.raiz = Nodo("SHILOH", H.peso + SILO.peso)
        self.raiz.izq = H
        self.raiz.der = SILO

    def mostrar(self, nodo, nivel=0):
        if nodo:
            print("  " * nivel + f"{nodo.dato} ({nodo.peso})")
            self.mostrar(nodo.izq, nivel + 1)
            self.mostrar(nodo.der, nivel + 1)


# -------------------------
# EJECUCIÓN
# -------------------------

arbol = ArbolHuffman()
arbol.construir_arbol()

print("Árbol de Huffman (SHILOH):\n")
arbol.mostrar(arbol.raiz)

# Cálculo de bits
original = 6 * 8   # 48 bits
huffman = 14       # resultado del ejercicio

print("\n--- COMPRESIÓN ---")
print(f"Sin Huffman: {original} bits")
print(f"Con Huffman: {huffman} bits")
print(f"Reducción: {original - huffman} bits")
```
