# Ejercicio 9 - La bioinformática te necesita

## Descripción
La universidad ORT acaba de inaugurar su nueva carrera de licenciatura en bioinformática, con el objetivo de convertirse en referente mundial de la ingeniería genética. Para esto, contrató a reconocidos expertos internacionales en biología molecular, quienes desarrollaron un nuevo modelo de análisis genético basado en el algoritmo de Needleman-Wunsch, utilizado tradicionalmente para alinear dos secuencias de ADN. 

Con el nuevo objetivo de encontrar mutaciones genéticas más avanzadas, el equipo se dispone a crear un nuevo algoritmo que le permita comparar tres secuencias distintas. Lamentablemente, la universidad ya se gastó todo su presupuesto en los expertos en biología y ya no puede pagarle a alguien para ayudar con la programación del algoritmo. 

Es por esto que la universidad recurre a ustedes, estudiantes de Algoritmos 2, con gran conocimiento en los algoritmos de programación dinámica. A cambio recibirán, cómo no, su respectiva nota por el trabajo realizado.

## Entrada
La primera línea contiene un entero __N__ (0 < N &le; 10) que representa la cantidad de grupos de secuencias. <br>
Luego se tienen __N__ * 5 líneas de la siguiente forma:<br>
Se recibe __G__ (0 &le; __G__ &le; __L__) que representa la cantidad máxima de **_gaps_** que se pueden utilizar (**Esto no significa que se deban utilizar todos**)<br>
Se recibe __L__ siendo __L__ el largo de las 3 secuencias que se encuentran a continuación <br>
Los posibles caracteres son los siguientes: __A G C #__ siendo __#__ la representación del vacío. <br>


## Salida

un entero que represente el puntaje maximo posible.

## Restricciones

los puntajes se dan de la siguiente manera: <br>
3 iguales = 5 <br>
2 iguales = 2 <br> 
gap (-) = -2 <br>
no match = -1 <br>

## Ejemplo

### Input
2 <br>
1 <br>
3 <br>
AGC <br>
AC# <br>
AGC <br>
0 <br>
3 <br>
AGC <br>
AC# <br>
AGC <br>

### Output

10 <br>
9


### Explicación

posibles puntajes:

(agregando un gap en el medio) <br>
AGC <br>
A-C <br>
AGC <br>
10 = ((2) 3 iguales, (1) 2 iguales, (1) gap)<br>

(no agrego nada nada)<br>
AGC <br>
AC# <br>
AGC <br>
9 = ((1) 3 iguales, (2) 2 iguales, (0) gap)<br>


(agrego gap al comienzo)<br>
AGC <br>
-AC <br>
AGC <br>
7 = ((1) 3 iguales, (2) 2 iguales, (1) gap)<br>

