# Ejercicio 9 - La bioinformática te necesita

## Descripción
La universidad ORT acaba de inaugurar su nueva carrera de licenciatura en bioinformática, con el objetivo de convertirse en referente mundial de la ingeniería genética. Para esto, contrató a reconocidos expertos internacionales en biología molecular, quienes desarrollaron un nuevo modelo de análisis genético basado en el algoritmo de Needleman-Wunsch, utilizado tradicionalmente para alinear dos secuencias de ADN. 

Con el nuevo objetivo de encontrar mutaciones genéticas más avanzadas, el equipo se dispone a crear un nuevo algoritmo que le permita comparar tres secuencias distintas. Lamentablemente, la universidad ya se gastó todo su presupuesto en los expertos en biología y ya no puede pagarle a alguien para ayudar con la programación del algoritmo. 

Es por esto que la universidad recurre a ustedes, estudiantes de Algoritmos 2, con gran conocimiento en los algoritmos de programación dinámica. A cambio recibirán, cómo no, su respectiva nota por el trabajo realizado.

## Entrada

Se reciben 3 secuencias (strings) donde cada valor se separa por coma (,) 


## Salida

un entero que represente el puntaje maximo posible.

## Restricciones

los puntajes se dan de la siguiente manera:
3 iguales = 5
2 iguales = 2
gap (-) = -2
no match = -1

## Ejemplo

### Input

"A,G,C"
"A,C,#"
"A,G,C"

### Output

10

### Explicación


posibles puntajes:
(si lo dejo como esta)
"A,G,C"
"A,C,#"     = 9 (3 iguales, (2) 2 iguales)
"A,G,C"

(agregando un gap)
"A,G,C"
"A,-,C"     = 10 ((2) 3 iguales, 2 iguales, gap)
"A,G,C"