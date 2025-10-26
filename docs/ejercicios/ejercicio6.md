# Ejercicio 6 - Skate a Propulsión

## Descripción

Mike es un ciudadano de Lineapolis, una ciudad en la que todas sus casas están una al lado de la otra horizontalmente (querían minimizar los semáforos al fundar la ciudad). Al ser una ciudad tan simple, todas las casas tienen el mismo tamaño y están numeradas iniciando en 1 e incrementando de a 1 cada casa a la derecha. Mike vive en la casa 1 y quiere visitar a su amigo que vive en la casa $F$. Pero su camino no será tan fácil, al ser una única calle es muy difícil repararla y se han formado $N$ pozos a lo largo del camino, haciendo que en esos tramos sea imposible usar su confiable skate. Ante el apuro de visitar a su amigo, Mike decidió agregarle propulsores al skate alterando cómo funciona completamente!

Estos propulsores cuentan con una Potencia $P$, inicialmente en 1 de potencia. Estos permiten moverse de la siguiente forma: si estás parado en la casa $X$, podés impulsarte hasta cualquier casa en el rango $[X, X + P]$. Pero iniciar el movimiento o terminarlo en un pozo es peligroso ya que Mike se puede caer, así que en ningún momento tomará esa decisión, ¡preferiría quedarse quieto!

Afortunadamente hay $M$ mejoras disponibles de vecinos para el propulsor, aumentando **permanentemente** la potencia en $P_i$ (es decir, la potencia es acumulativa: si P = 1 y se obtiene una mejora de 2, la nueva potencia será P = 3 y se mantendrá así para el resto del viaje). Un mismo vecino puede ofrecer múltiples mejoras. Pero Mike no quiere parecer aprovechado, así que quiere minimizar la cantidad de mejoras que pide para llegar. Como se encuentra muy apurado te pide a ti que calcules la mínima cantidad de mejoras que necesita pedir y que le permita llegar a la casa de su amigo. Si no es capaz de llegar hay que imprimir "Imposible".

## Entrada

La primera línea contiene 3 enteros, $N$, $M$ y $F$ ($0 \leq N \leq 10^5$, $0 \leq M \leq 10^5$, $3 \leq F \leq 10^9$) siendo $N$ la cantidad de pozos, $M$ la cantidad de mejoras disponibles y $F$ la casa donde vive su amigo.

Las siguientes $N$ líneas contienen 2 enteros $I_i$ y $D_i$ ($2 \leq I_i \leq D_i \leq F - 1$) que representan dónde arranca y dónde termina el pozo $i$ respectivamente. Los pozos están ordenados y siempre hay al menos una calle bien entre 2 pozos ($D_i + 2 \leq I_{i+1}$).

Las próximas $M$ líneas contienen 2 enteros $X_i$ y $P_i$ ($2 \leq X_i \leq F, 1 \leq P_i \leq 10^9 $) siendo $X_i$ la casa donde está disponible una mejora de potencia $P_i$. Las mejoras están ordenadas por posición ($X_i \leq X_{i+1}$). Un mismo vecino puede ofrecer múltiples mejoras (apareciendo en varias líneas). Nunca va a haber una mejora disponible si su calle tiene pozos.

$N$ $M$ $F$

$I_1$ $D_1$

... ...

$I_N$ $D_N$

$X_1$ $P_1$

... ...

$X_M$ $P_M$

## Salida

Debe imprimir una única línea conteniendo la mínima cantidad de mejoras que necesita pedir. En caso de no poder llegar a la casa de su amigo imprimir "Imposible".

## Restricciones

- $0 \leq N \leq 10^5$
- $0 \leq M \leq 10^5$
- $3 \leq F \leq 10^9$
- Los pozos están ordenados
- $2 \leq I_i \leq D_i \leq F - 1$
- Entre 2 pozos siempre hay al menos una calle que está bien
- Nunca va a haber una mejora disponible si su calle tiene pozos
- $2 \leq X_i \leq F - 1, 1 \leq P_i \leq 10^9 $
- Las mejoras están ordenadas por posición
- $X_i \leq X_{i+1}$
- Un mismo vecino puede ofrecer múltiples mejoras
- Resolver usando estrategia greedy

## Complejidad Esperada

- **Tiempo**: $O(N\log M)$ donde $N$ es la cantidad de pozos y $M$ la cantidad de mejoras disponibles
- **Espacio** $O(N + M)$

## Ejemplo

### Input

```
2 3 12
3 4
8 10
2 2
5 3
7 1
```

### Output

```
2
```

### Explicación

Podemos representar de la siguiente manera la entrada, tenemos las casas del lado de abajo y arriba la calle, siendo M donde está Mike, # donde hay pozo, - donde hay calle bien y un número si ese vecino tiene una mejora.

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

Luego salta el pozo [3, 4], cayendo en la casa 5

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

Salta el pozo [8, 10], cayendo en la casa 11
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
