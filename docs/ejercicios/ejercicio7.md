# Ejercicio 7 - Ranking de Parciales

## Descripción

En la materia **Estructuras de Datos y Algoritmos 2** de nuestra Facultad, el **docente** publica el ranking oficial de los estudiantes según sus notas de parcial (con el formato <Nombre_NroEstudiante>).  
Sin embargo, un **ayudante despistado** publica otro ranking con el mismo conjunto de estudiantes pero en un orden distinto.  

Para medir **qué tan distinto** quedó, queremos calcular **cuántos pares de estudiantes aparecen “invertidos”** entre ambos rankings.  

Un par de estudiantes `(A, B)` está **invertido** si:
- En el ranking oficial: `A` aparece antes que `B`.
- En el ranking del ayudante: `B` aparece antes que `A`.

## Entrada
1. Un entero `n` que representa la cantidad de estudiantes.  
2. Una lista con `n` nombres en el orden del **ranking oficial**.  
3. Una lista con los mismos `n` nombres en el orden del **ranking del ayudante**.  


## Salida
Número de inversiones entre ambos rankings. 

## Restricciones
- Se debe implementar un algoritmo basado en **Divide and Conquer**, con complejidad **O(n log n)**.  


## Ejemplo

**Entrada**

4

Ana_000001

Beto_000002

Carla_000003

Diego_000004

Beto_000002 `comienza la segunda lista`

Ana_000001

Diego_000004

Carla_000003
 
**Salida**

2

### Explicación

- En el ranking oficial: Ana ≺ Beto ≺ Carla ≺ Diego.  
- En el ranking del ayudante: Beto ≺ Ana (inversión), Diego ≺ Carla (inversión).  
- Total: 2 inversiones.