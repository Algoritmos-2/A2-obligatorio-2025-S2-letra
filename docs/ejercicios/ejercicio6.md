# Ejercicio 6 - Skate a Propulsión

## Descripción

Mike es un ciudadano de Lineapolis, una ciudad en la que todas sus casas estan una al lado de la otra horizontalmente(Querian minimizar los semaforos al fundar la ciudad). Al ser una ciudad tan simple todas las casas tienen el mismo tamaño y estan numeradas iniciando en 1 e incrementando de a 1 cada casa a la derecha. Mike vive en la casa 1 y quiere visitar a su amigo que vive en la casa $F$. Pero su camino no sera tan facil, al ser una unica calle es muy dificil repararla y se han formando $N$ posos a lo largo del camino, haciendo que en esos tramos sea imposible usar su confiable skate. Ante el apuro de visitar a su amigo, Mike decidio agregarle propulsores al skate alterando como funciona completamente!

Estos propulsores cuentan con una Potencia $P$, inicialmente en 1 de potencia. Estos permiten moverse de la siguiente forma, Si estas parado en la casa $X$, podes impulsarte hasta cualquier casa en el rango $[X, X + P]$. Pero iniciar el movimiento o terminarlo en un poso es peligroso ya que Mike se puede caer asi que en ningun momento tomara esa desicion, preferiria quedarse quieto!

Afortunadamente hay $M$ vecinos que cuentan con mejoras para el propulsor, aumentando la potencia en $P_i$. Pero Mike no quiere parecer aprovechado asi que quiere minimizar la cantidad de veces que pide ayuda a sus vecinos para llegar. Como se encuentra muy apurado te pide a ti que calcules la minima cantidad de vecinos a los que pedirle ayuda y que le permita llegar a la casa de su amigo. Si no es capaz de llegar hay que imprimir "Imposible".

## Entrada

La primera linea contiene 3 enteros, $N$, $M$ y $F$ ($0 \leq N \leq 10^5$, $0 \leq M \leq 10^5$, $3 \leq F \leq 10^9$) siendo $N$ la cantidad de posos, $M$ los vecinos dispuestos a ayudar y $F$ la casa donde vive su amigo.

Las siguientes $N$ lineas contienen 2 enteros $I_i$ y $D_i$ ($2 \leq I_i \leq D_i \leq F - 1$) que representan la donde arranca y donde termina el poso i respectivamente. Los posos estan ordenados y siempre hay al menos una calle bien entre 2 posos ($D_i + 2 \leq I_{i+1}$).

Las proximas $M$ lineas contienen 2 enteros $X_i$ y $P_i$ ($2 \leq X_i \leq F, 1 \leq P_i \leq 10^9 $) siendo $X_i$ la casa de un vecino con una mejora de potencia $P_i$. Las potencias estan ordenadas ($X_i + 1 \leq X_{i+1}$) y nunca va a haber un vecino disponible si su calle tiene posos.

$N$ $M$ $F$

$I_1$ $D_1$

... ...

$I_N$ $D_N$

$X_1$ $P_1$

... ...

$X_M$ $P_M$


## Salida
Debe imprimir una unica linea conteniendo la minima candidad de vecinos a los que pedirle ayuda. En caso de no poder llegar a la casa de su amigo imprimir "Imposible".

## Restricciones
 - $0 \leq N \leq 10^5$
 - $0 \leq M \leq 10^5$
 - $3 \leq F \leq 10^9$
 - Los Posos estan ordenados
 - $2 \leq I_i \leq D_i \leq F - 1$
 - Entre 2 posos siempre hay al menos una calle que esta bien
 - Nunca va a haber un vecino disponible si su calle tiene posos
 - $2 \leq X_i \leq F - 1, 1 \leq P_i \leq 10^9 $
 - Los vecinos estan ordenados por posicion
 - $X_i + 1 \leq X_{i+1}$
## Complejidad Esperada
 
 - **Tiempo**: $O(N\log M)$ donde $N$ son la cantidad de posos y $M$ la cantidad de vecinos dispuestos a ayudar
 - **Espacio** $O(N + M)$

## Ejemplo

### Input
```
2 3 12
3 4
8 11
2 2
5 3
7 1
```
### Output
```
2
```

### Explicación
Podemos representar de la siguiente manera la entrada, tenemos las casas del lado de abajo y arriba la calle, siendo M donde esta Mike, # donde hay poso, - donde hay calle bien y un numero si ese vecino tiene una mejora.

Inicialmente su skate tiene un poder P = 1.
```
  M   2   #   #   3   -   1   #   #   #    -    -  
| 1 | 2 | 3 | 4 | 5 | 6 | 7 | 8 | 9 | 10 | 11 | 12 |
```
Una posible secuencia seria moverse a la casa 2 y pedirle ayuda.
P = 3
```
  -   M   #   #   3   -   1   #   #   #    -    -  
| 1 | 2 | 3 | 4 | 5 | 6 | 7 | 8 | 9 | 10 | 11 | 12 |
```
Luego salta el poso [2, 3], cayendo en la casa 5

P = 3
```
  -   -   #   #  M|3  -   1   #   #   #    -    -  
| 1 | 2 | 3 | 4 | 5 | 6 | 7 | 8 | 9 | 10 | 11 | 12 |
```
Decide no pedirle ayuda a la casa 5 y se mueve a la 7, esta vez pidiendole ayuda
P = 4
```
  -   -   #   #   3   -   M   #   #   #    -    -  
| 1 | 2 | 3 | 4 | 5 | 6 | 7 | 8 | 9 | 10 | 11 | 12 |
```
Salta el poso [8, 10], cayendo en la casa 11
P = 4
```
  -   -   #   #   3   -   -   #   #   #    M    -  
| 1 | 2 | 3 | 4 | 5 | 6 | 7 | 8 | 9 | 10 | 11 | 12 |
```
Finalmente va desde la casa 11 a la 12, donde vive su amigo
P = 4
```
  -   -   #   #   3   -   -   #   #   #    -    M  
| 1 | 2 | 3 | 4 | 5 | 6 | 7 | 8 | 9 | 10 | 11 | 12 |
```