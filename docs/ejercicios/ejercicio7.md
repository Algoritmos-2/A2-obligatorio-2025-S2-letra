# Ejercicio 7 - Ranking de Parciales

## Descripción

En la materia **Estructuras de Datos y Algoritmos 2** de nuestra Facultad, el **docente** publica el ranking oficial de los estudiantes según sus notas de parcial (con el formato <Nombre_NroEstudiante>).  
Sin embargo, un **ayudante despistado** publica otro ranking con el mismo conjunto de estudiantes pero en un orden distinto.

Para medir **qué tan distinto** quedó, queremos calcular **cuántos pares de estudiantes aparecen “invertidos”** entre ambos rankings.

Un par de estudiantes `(A, B)` está **invertido** si:

- En el ranking oficial: `A` aparece antes que `B`.
- En el ranking del ayudante: `B` aparece antes que `A`.

## Entrada

La primera línea contiene un entero $N$ ($1 \leq N \leq 10^5$), la cantidad de estudiantes.

Las siguientes $N$ líneas contienen los nombres de los estudiantes en el orden del **ranking oficial**.

Las siguientes $N$ líneas contienen los mismos nombres en el orden del **ranking del ayudante**.

## Salida

Un único entero representando el número de inversiones entre ambos rankings.

## Restricciones

- $1 \leq N \leq 10^5$
- Nombres de hasta 50 caracteres (sin espacios).
- Todos los nombres son únicos.
- Se debe implementar un algoritmo basado en **Divide and Conquer**.

## Complejidad Esperada

- **Tiempo**: $O(N \log N)$
- **Espacio**: $O(N)$

## Ejemplos

### Ejemplo 1

**Entrada**

```
4
Ana_000001
Beto_000002
Carla_000003
Diego_000004
Beto_000002
Ana_000001
Diego_000004
Carla_000003
```

**Salida**

```
2
```

**Explicación**

- En el ranking oficial: Ana ≺ Beto ≺ Carla ≺ Diego.
- En el ranking del ayudante: Beto ≺ Ana ≺ Diego ≺ Carla.
- Inversiones:
  - (Ana, Beto): Ana antes que Beto en oficial, pero Beto antes que Ana en ayudante ✓
  - (Carla, Diego): Carla antes que Diego en oficial, pero Diego antes que Carla en ayudante ✓
- Total: **2 inversiones**.

### Ejemplo 2: Orden Inverso (Máximas inversiones)

**Entrada**

```
4
Ana_000001
Beto_000002
Carla_000003
Diego_000004
Diego_000004
Carla_000003
Beto_000002
Ana_000001
```

**Salida**

```
6
```

**Explicación**

- Ranking oficial: Ana ≺ Beto ≺ Carla ≺ Diego.
- Ranking ayudante: Diego ≺ Carla ≺ Beto ≺ Ana (orden completamente inverso).
- Todas las parejas están invertidas: (Ana,Beto), (Ana,Carla), (Ana,Diego), (Beto,Carla), (Beto,Diego), (Carla,Diego).
- Total: **6 inversiones** = $\frac{N(N-1)}{2}$ con $N=4$.
