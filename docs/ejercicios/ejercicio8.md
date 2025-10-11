# Ejercicio 8 - Crystal Cascade

## Descripción

Tienes una línea horizontal de fragmentos de cristal de diferentes colores. Cada color está representado por un número positivo.

Tu objetivo es eliminar todos los fragmentos para obtener el máximo puntaje posible.

**Reglas del juego:**

- En cada turno, puedes seleccionar un **grupo de fragmentos consecutivos del mismo color**
- Si eliminas un grupo de K fragmentos, estos resuenan y obtienes **K² puntos de energía** <- Sweet!
- Los fragmentos restantes se deslizan automáticamente para llenar el espacio vacío, formando una nueva línea continua

**Importante:** Solo puedes eliminar fragmentos que estén juntos y sean del mismo color. No puedes saltar fragmentos de otros colores.

Se debe retornar la cantidad máxima de puntos que se pueden obtener eliminando todos los fragmentos.

## Entrada

- La primera línea contiene un entero N, que representa la cantidad total de fragmentos.
- La siguiente línea contiene N enteros representando los colores de los fragmentos.

## Salida

Un único entero representando la cantidad máxima de puntos que se pueden obtener.

## Restricciones

- $1 \leq N \leq 100$

## Complejidad Esperada

- **Tiempo**: $O(N^4)$ donde $N$ es la cantidad de fragmentos
- **Espacio**: $O(N^3)$ para la tabla de memoización

## Ejemplos

### Ejemplo 1

#### Input

```
5
1 2 1 1 2
```

#### Output

```
11
```

#### Explicación

Estrategia óptima:

1. Eliminar `[2]` en posición 1: 1² = 1 punto → Queda `[1, 1, 1, 2]`
2. Eliminar `[1, 1, 1]`: 3² = 9 puntos → Queda `[2]`
3. Eliminar `[2]`: 1² = 1 punto

**Total: 1 + 9 + 1 = 11 puntos**

Si hubiéramos eliminado de otra forma:

- Eliminar primero `[1]`: 1 punto → Queda `[2, 1, 1, 2]`
- Eliminar `[1, 1]`: 4 puntos → Queda `[2]`
- Eliminar `[2, 2]`: 4 puntos
- Total: 1 + 4 + 4 = 9 puntos (subóptimo)

### Ejemplo 2

#### Input

```
3
3 3 3
```

#### Output

```
9
```

#### Explicación

La única estrategia es eliminar `[3, 3, 3]` completo: 3² = 9 puntos.

Si elimináramos de a uno obtendríamos: 1 + 1 + 1 = 3 puntos (mucho peor).

### Ejemplo 3

#### Input

```
9
1 3 2 2 2 3 4 3 1
```

#### Output

```
23
```

#### Explicación

Una estrategia óptima (hay varias):

1. Eliminar `[2, 2, 2]`: 3² = 9 puntos → Queda `[1, 3, 3, 4, 3, 1]`
2. Eliminar `[4]`: 1² = 1 punto → Queda `[1, 3, 3, 3, 1]`
3. Eliminar `[3, 3, 3]`: 3² = 9 puntos → Queda `[1, 1]`
4. Eliminar `[1, 1]`: 2² = 4 puntos

**Total: 9 + 1 + 9 + 4 = 23 puntos**
