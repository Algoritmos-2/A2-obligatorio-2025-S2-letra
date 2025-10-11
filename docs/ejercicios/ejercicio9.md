# Ejercicio 9 - A último momento

## Descripción

El obligatorio de Estructuras de datos y algoritmos 3 es muy similar al de su materia antecesora, con la pequeña diferencia de que no todos los ejercicios tienen el mismo puntaje.

Un día antes de la entrega, el profesor le recuerda que la entrega de todos los archivos no debe superar los S MB (megabytes) ni las L líneas de código entre todos ellos.

Como usted olvidó este detalle y no tiene tiempo a refactorizar su código para que cumpla con las restricciones, decide elegir aquellos ejercicios/archivos que le garanticen un mejor puntaje.

De cada ejercicio/archivo, usted sabe su tamaño, cantidad de líneas de código y el puntaje.

## Entrada

```txt
N
S
L
t1 l1 p1
t2 l2 p2
...
tN lN pN
```

- `N`: Es la cantidad de archivos.
- `S`: es el tamaño máximo que se puede subir para la entrega.
- `L`: es la cantidad máxima de lineas que puede tener la entrega.
- `t l p`: es `t` tamaño del archivo, `l` cantidad de lineas del archivo, y `p` puntos que vale ese ejercicio.

## Salida

```txt
P
```

La cantidad de puntos que obtendra por la entrega.

## Restricciones

$O(N*S*L)$ temporal y espacial

Debe realizarce con la técnica de **tabulación**

## Ejemplo

### Input

```txt
10
50
1000
16 665 1
6 501 8
25 904 7
18 591 5
7 683 6
22 88 1
24 497 9
22 565 7
31 414 9
49 389 2
```

### Output

```txt
17

```
