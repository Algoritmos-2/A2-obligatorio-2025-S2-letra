# Ejercicio 10 - Búsqueda de producto en Amazon

## Descripción
Jeff Bezos quiere saber cuál de todos sus Fullfilment Centers (FC) es el más rápido en buscar un producto genérico aleatorio. Se sabe que este producto se encuentra en todos los FCs a evaluar por lo que no se debe consultar si se encuentra disponible. La consigna consta en encontrar el producto en la menor cantidad de pasos desde la entrada del FC (posición 0,0).

## Entrada
La primera línea contiene un caracter que significa el producto a buscar en los FC.

La segunda línea contiene un natural $P$, con ($1 \leq P \leq 1000$), este denota la cantidad de FCs en donde se va a buscar el producto.

La línea siguiente contiene dos naturales $M$ $N$, con ($1 \leq M \leq 100$) ($1 \leq N \leq 100$), que significan las dimensiones del siguiente FC, siendo $M$ las filas y $N$ las columnas del mismo. Por lo que las siguientes $M$ lineas del archivo de entrada contienen $N$ caracteres cada una.

Los productos en el FC están representados con caracteres, el único caracter que no significa un producto es el 'C' que significa un corredor, lugar por donde se puede mover.

## Salida
La salida contendrá el FC que pudo encontrar el producto en menor cantidad de pasos y , separado, la cantidad de pasos desde la entrada de dicho FC hasta el producto.

## Restricciones
- ($1 \leq P \leq 1000$)
- ($1 \leq M \leq 100$)
- ($1 \leq N \leq 100$)
- Entrar al FC cuenta como un paso.
- Para considerarse encontrado el producto se debe pararse sobre su celda.

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
1 12
```

### Explicación
El producto a buscar es 'S'.

Hay 3 FCs en donde buscar, con diferentes dimensiones cada uno.

El FC en encontrar el producto más rápidamente fue el 1 y lo hizo en 12 pasos.