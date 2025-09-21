# Ejercicio 8 - [nombre del ejercicio]

## Descripción
Se te entregan varias baldosas de distintos colores, donde cada color es representado por un número positivo.
El juego consiste en ir sacando baldosas hasta que no quede ninguna.
En cada ronda puedes eliminar una subsecuencia continua de baldosas que:
- empiece y termine con el mismo color,
- tenga largo k >= 1

Dentro de la subsecuencia pueden haber baldosas de otros colores que son distintos a los extremos. A estas baldosas distintas se le llaman impurezas.
 
Al remover una subsecuencia de baldosas de largo k obtenemos un puntaje igual a: 
puntaje = (k*k) - (número de impurezas)
 
Se debe retornar la cantidad máxima de puntos que se pueden obtener eliminando todas las baldosas.

## Entrada
- La primera línea contiene un entero N, que representa la cantidad total de baldosas.
- La siguiente línea contiene N enteros representando los colores.

## Salida
Un único entero representando la cantidad máxima de puntos que se pueden obtener.

## Restricciones
- $1 \leq N \leq 10^3$

## Ejemplo

### Input
```
5
1 3 1 3 1
```

### Output
```
23
```