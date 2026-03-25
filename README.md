Actividad Análisis Sintáctico

1. Implementar un analizador sintáctico en Python para la gramática de ejemplo de las diapositivas, generando el árbol sintáctico.
   
   <img width="260" height="211" alt="image" src="https://github.com/user-attachments/assets/d5193a3d-4674-45a5-9f7e-978109a23776" />

   

2. Realizar la comparación del algoritmo CYK con complejidad O(n³) y un algoritmo con complejidad lineal de análisis sintáctico.
3. 
   Dentro de los algoritmos de complejidad lineal para el análisis sintáctico se tienen ASD (análisis sintáctico descendente) y ASA (análisis sintáctico ascendente), es decir LL y LR.
   
   Por lo que dentro de la comparación por el lado de complejidad O(n³) se tendrán los algoritmos CYK y Early, mientras que por el lado de complejidad O(n) se realizará la implementación ASD con pila y tabla M, y ASA versión SLR. Las pruebas se realizarán con la misma gramática del primer punto, pero modificada para que no tenga recursividad por izquierda, pues es problemático para utilizar LL.
   
   E → T E'
   E' → opsuma T E' | ε
   T → F T'
   T' → opmul F T' | ε
   F → id
   F → num
   F → pari E pard

   Terminales: opsuma, opmul, pari, pard, id, num, $ (fin de cadena)
   No terminales: E'', E, E', T, T', F

   SLR
   Como primer paso, obtenemos la gramática aumentada.
   E'' → E
   E → T E'
   E' → opsuma T E'
   E' → ε
   T → F T'
   T' → opmul F T'
   T' → ε
   F → id
   F → num
   F → pari E pard

   Ahora necesitamos obtener los conjuntos PRIMERO(X) y SIGUIENTE(A)

   Reglas para calcular PRIMERO

   1. Si X es terminal → PRIMERO(X) = { X }
   2. Si existe X → ε → agregar ε a PRIMERO(X)
   3. Si existe X → Y₁ Y₂ ... Yₖ → agregar PRIMERO(Y₁) sin ε. Si ε ∈ PRIMERO(Y₁), agregar PRIMERO(Y₂) sin ε, y así sucesivamente. Si todos derivan ε, agregar ε.

      PRIMERO(F) = {id, num, pari}
   
      PRIMERO(T') = {opmul, ε}
   
      PRIMERO(T) = {id, num, pari}
   
      PRIMERO(E') = {opsuma, ε}
   
      PRIMERO(E) = {id, num, pari}
   
      PRIMERO(E'') = {id, num, pari}

      Reglas para calcular SIGUIENTE
      
      1. $ ∈ SIGUIENTE(S') donde S' es el símbolo inicial aumentado
      2. Si existe A → α B β → agregar PRIMERO(β) - {ε} a SIGUIENTE(B)
      3. Si existe A → α B o A → α B β con ε ∈ PRIMERO(β) → agregar SIGUIENTE(A) a SIGUIENTE(B)
     
      SIGUIENTE(E'') = {$}

      SIGUIENTE(E) = {$, pard}

      SIGUIENTE(E') = {$, pard}

      SIGUIENTE(T) = {opsuma, $, pard}

      SIGUIENTE(T') = {opsuma, $, pard}

      SIGUIENTE(F) = {opmul, opsuma, $, pard}

      
      
   
5. Asociatividad y precedencia, realizando modificaciones a una gramática aritmética para hacer asociatividad por derecha, por izquierda, tener la precedencia de operadores definida matemáticamente y el orden inverso, realizar dos pruebas y comparar los resultados obtenidos con la misma cadena en cada una de las versiones de la gramática
   En antlr se tendrán 4 gramáticas, cada una con la modificación necesaria para asociatividad por derecha, asociatividad por izquierda, precedencia usual de operaciones y precedencia inversa.
   La gramática permite realizar operaciones como suma, resta, multiplicación y división entre números racionales. Admitiendo tanto enteros como números de punto flotante con signo. 
