# Ejercicio 10 - Búsqueda de producto en Amazon

## Descripción

Jeff Bezos quiere saber cuál de todos sus Fulfillment Centers (FC) es el más rápido en buscar un producto genérico aleatorio. Se sabe que este producto se encuentra en todos los FCs a evaluar, por lo que no se debe consultar si está disponible.

El objetivo es encontrar el producto usando **backtracking** para explorar todos los posibles caminos desde la entrada del FC (posición 0,0) y determinar cuál FC puede encontrar el producto en la menor cantidad de pasos.

## Entrada

- La primera línea contiene un carácter que representa el producto a buscar en los FCs.
- La segunda línea contiene un natural $P$ ($1 \leq P \leq 1000$), que denota la cantidad de FCs en donde se va a buscar el producto.

Para cada FC (repetir $P$ veces):

- Una línea con dos naturales $M$ y $N$ ($1 \leq M \leq 100$, $1 \leq N \leq 100$), que representan las dimensiones del FC: $M$ filas y $N$ columnas.
- Las siguientes $M$ líneas contienen $N$ caracteres **separados por espacios**, representando el mapa del FC.

**Caracteres del mapa:**

- `'C'`: Corredor (celda por donde se puede mover)
- Cualquier otro carácter: Representa un producto (NO se puede atravesar, solo se puede llegar a él si es el producto buscado)

## Salida

Imprimir el **índice del FC** (comenzando en 1) que encontró el producto en menor cantidad de pasos, seguido de un espacio y la **cantidad de pasos** necesarios.

Si varios FCs encuentran el producto en la misma cantidad de pasos, devolver el de **menor índice**.

## Restricciones

- $1 \leq P \leq 1000$
- $1 \leq M \leq 100$
- $1 \leq N \leq 100$
- La posición inicial es siempre $(0, 0)$ (esquina superior izquierda del mapa)
- Se puede mover solo por celdas con `'C'` (corredores) o hacia el producto buscado
- Movimientos permitidos: **4 direcciones** (arriba, abajo, izquierda, derecha)
- **Cada movimiento de una celda a otra cuenta como un paso**
- **Estar en la posición inicial (0,0) NO cuenta como paso**. El primer paso se cuenta al moverse a otra celda
- Para considerarse encontrado, se debe llegar a la celda del producto
- Se debe utilizar **backtracking** para explorar todos los caminos posibles y encontrar el más corto
- Se garantiza que siempre existe un camino válido desde (0,0) hasta el producto en cada FC

## Ejemplo

### Input

```
S
3
7 6
C C C C C C
C A B D F C
C G H I J C
C C C C C C
C K L M N C
C O P Q S C
C C C C C C
13 12
C K L L D I C L J U P M
C C C C C C C C C C C C
X C C Q W P I J T D B Z
G T C C X Z X Z X Z X Z
C C C C C C C C C C C C
L V O H C C Q F K H T Y
G G G G G C C N V M S A
C C C C C C C C C C C C
G G G G G G G C C R M D
G G G G G G G G C C P S
C C C C C C C C C C C C
A S D F G H S A C Q W M
C C C C C C C C C C C C
7 7
C C C C C C O
G D B L C C P
T W A X C C R
C C C C C C L
C C C C C C A
H A S K C C S
J D A F C C H
```

### Output

```
1 11
```

### Explicación

El producto a buscar es 'S'.

Hay 3 FCs en donde buscar, con diferentes dimensiones cada uno.

El FC en encontrar el producto más rápidamente fue el 1 y lo hizo en 11 pasos.

