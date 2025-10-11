# Ejercicio 9: Alineamiento de Tres Secuencias de ADN

## Descripción

La universidad ORT acaba de inaugurar su nueva carrera de licenciatura en bioinformática, con el objetivo de convertirse en referente mundial de la ingeniería genética. Para esto, contrató a reconocidos expertos internacionales en biología molecular, quienes desarrollaron un nuevo modelo de análisis genético basado en el algoritmo de Needleman-Wunsch, utilizado tradicionalmente para alinear dos secuencias de ADN.

Con el nuevo objetivo de encontrar mutaciones genéticas más avanzadas, el equipo se dispone a crear un nuevo algoritmo que le permita comparar **tres secuencias distintas simultáneamente**. Lamentablemente, la universidad ya se gastó todo su presupuesto en los expertos en biología y ya no puede pagarle a alguien para ayudar con la programación del algoritmo.

Es por esto que la universidad recurre a ustedes, estudiantes de Algoritmos 2, con gran conocimiento en los algoritmos de **programación dinámica**. A cambio recibirán, cómo no, su respectiva nota por el trabajo realizado.

## Entrada

- La primera línea contiene un entero $N$ ($1 \leq N \leq 10$) que representa la cantidad de grupos de secuencias.
- Para cada grupo de secuencias se tienen 5 líneas:
  - $G$ ($0 \leq G \leq L$): cantidad **máxima** de *gaps* que se pueden utilizar (no es obligatorio usar todos)
  - $L$ ($1 \leq L \leq 100$): largo de las 3 secuencias
  - 3 líneas con las secuencias de ADN de longitud $L$ cada una
    - Caracteres posibles: `A`, `G`, `C`, `#`
    - El carácter `#` representa un **espacio vacío** en la secuencia

## Salida

Para cada grupo de secuencias, imprimir un entero que represente el **puntaje máximo** posible al alinear las tres secuencias.

## Restricciones

**Sistema de puntaje por columna:**
- 3 caracteres iguales (sin contar gaps): **+5 puntos**
- 2 caracteres iguales (sin contar gaps): **+2 puntos**
- 1 gap (-): **-2 puntos** (se cuenta por cada gap en la columna)
- 3 caracteres diferentes (no match): **-1 punto**

**Reglas de los gaps:**
- Los *gaps* solo pueden insertarse en secuencias **incompletas** (aquellas que contienen al menos un `#`)
- Un gap puede:
  - **Sustituir** un carácter `#` (vacío)
  - **Empujar** caracteres hacia la derecha, creando espacio
- No se pueden exceder $G$ gaps en total para el grupo
- Los *gaps* se usan para optimizar el alineamiento y maximizar el puntaje

## Complejidad Esperada

Este es un problema de **programación dinámica** que extiende el algoritmo clásico de Needleman-Wunsch de 2 secuencias a 3 secuencias.

- **Tiempo**: $O(L^3 \cdot G)$ por grupo de secuencias
  - $L$ es la longitud de cada secuencia
  - $G$ es el número máximo de gaps permitidos
  - Se requiere explorar estados con índices para las 3 secuencias y cantidad de gaps usados

- **Espacio**: $O(L^3 \cdot G)$ para la tabla de programación dinámica

**Hint**: Considerar un estado de la forma $DP[i][j][k][g]$ donde:
- $i$, $j$, $k$ son las posiciones actuales en cada una de las 3 secuencias
- $g$ es la cantidad de gaps utilizados hasta el momento

## Ejemplo

### Input
```
2
1
3
AGC
AC#
AGC
0
3
AGC
AC#
AGC
```

### Output
```
10
9
```

### Explicación

**Grupo 1** ($G = 1$, $L = 3$):
- Secuencias originales:
  ```
  AGC
  AC#
  AGC
  ```

Posibles alineamientos:

1. **Agregando un gap en el medio de la secuencia 2** (puntaje: 10):
   ```
   AGC
   A-C
   AGC
   ```
   - Columna 1: A, A, A → 3 iguales = +5
   - Columna 2: G, -, G → 2 iguales + 1 gap = +2 - 2 = 0
   - Columna 3: C, C, C → 3 iguales = +5
   - **Total: 5 + 0 + 5 = 10**

2. **Sin agregar gaps** (puntaje: 9):
   ```
   AGC
   AC#
   AGC
   ```
   - Columna 1: A, A, A → 3 iguales = +5
   - Columna 2: G, C, G → 2 iguales = +2
   - Columna 3: C, #, C → 2 iguales = +2
   - **Total: 5 + 2 + 2 = 9**

3. **Agregando un gap al comienzo de la secuencia 2** (puntaje: 7):
   ```
   AGC
   -AC
   AGC
   ```
   - Columna 1: A, -, A → 2 iguales + 1 gap = +2 - 2 = 0
   - Columna 2: G, A, G → 2 iguales = +2
   - Columna 3: C, C, C → 3 iguales = +5
   - **Total: 0 + 2 + 5 = 7**

El máximo es **10** puntos.

**Grupo 2** ($G = 0$, $L = 3$):
- No se pueden usar gaps, por lo que el único alineamiento posible es:
  ```
  AGC
  AC#
  AGC
  ```
- Puntaje: **9** puntos (igual al caso 2 del grupo 1)

