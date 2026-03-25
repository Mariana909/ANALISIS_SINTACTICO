Actividad Análisis Sintáctico

1. Implementar un analizador sintáctico en Python para la gramática de ejemplo de las diapositivas, generando el árbol sintáctico.
   
   <img width="260" height="211" alt="image" src="https://github.com/user-attachments/assets/d5193a3d-4674-45a5-9f7e-978109a23776" />

   

2. Realizar la comparación del algoritmo CYK con complejidad O(n³) y un algoritmo con complejidad lineal de análisis sintáctico.
   Dentro de los algoritmos de complejidad lineal para el análisis sintáctico se tienen ASD (análisis sintáctico descendente) y ASA (análisis sintáctico ascendente), es decir LL y LR.
   Por lo que dentro de la comparación por el lado de complejidad O(n³) se tendrán los algoritmos CYK y Early, mientras que por el lado de complejidad O(n) se realizará la implementación ASD con pila y tabla M, y ASA versión SLR. Las pruebas se realizarán con la misma gramática del primer punto, pero modificada para que no tenga recursividad por izquierda, pues es problemático para utilizar LL.

   
   
3. Asociatividad y precedencia, realizando modificaciones a una gramática aritmética para hacer asociatividad por derecha, por izquierda, tener la precedencia de operadores definida matemáticamente y el orden inverso, realizar dos pruebas y comparar los resultados obtenidos con la misma cadena en cada una de las versiones de la gramática
   En antlr se tendrán 4 gramáticas, cada una con la modificación necesaria para asociatividad por derecha, asociatividad por izquierda, precedencia usual de operaciones y precedencia inversa.
   La gramática permite realizar operaciones como suma, resta, multiplicación y división entre números racionales. Admitiendo tanto enteros como números de punto flotante con signo. 
