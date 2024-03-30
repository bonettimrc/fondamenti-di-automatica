
# Soluzione di sistemi

Predisponiamo il sistema utilizzando le variabili simboliche

 $$ \left\lbrace \begin{array}{c} \dot{x_1 } +x_2 +c_1 u=0\newline c_2 (x_1 +\dot{x_2 } )=c_3 u \end{array}\right. $$

```matlab
syms x1 x2 c1 c2 c3 x1dot x2dot u;
eqns = [x1dot + x2 + c1*u == 0; c2*(x1 + x2dot) == c3*u];
```

 $$ \dot{x} =\left(\begin{array}{c} \dot{x_1 } \newline \dot{x_2 }  \end{array}\right) $$

```matlab
xdot = [x1dot,x2dot];
```

La funzione `solve(eqns,xdot)` risolve il sistema di equazioni eqns nelle variabili simboliche xdot

```matlab
xdot=solve(eqns,xdot);
```

abbiamo così ottenuto l'espressione di equazioni differenziali accoppiate predisposta per la scrittura del modello di un sistema dinamico nello spazio degli stati

 $$ x=\left(\begin{array}{c} x_1 \newline x_2  \end{array}\right) $$

```matlab
x = [x1,x2];
```

La funzione `equationsToMatix(eqns, x)` restituisce la matrice $A$ e il vettore dei termini noti $b$ del sistema di equazioni eqns tali che $Ax=b$

```matlab
[A,Bu] = equationsToMatrix(xdot,x);
```

Il sistema considerato è nella forma $Ax=Bu$ . Pertanto, il secondo risultato fornito, indicato come vettore Bu nell'esempio precedente, non rappresenta i coefficienti della matrice B nel generico modello nello spazio degli stati, ma rappresenta il prodotto $Bu$ (detta *azione forzante*). Inoltre è a secondo membro, quindi va cambiato di segno per ricavarne i coefficienti della matrice B cercata:

```matlab
B=-Bu/u;
```

## Analisi del sistema dinamico ottenuto

La soluzione dell'equazione differenziale matriciale che descrive il sistema dinamico nello spazio degli stati richiede il calcolo di $e^{At}$ :

```matlab
syms t;
expm(A*t);
```

Nota la matrice esponenziale, è possibile calcolare il valore dello stato di un sistema dinamico noto lo stato iniziale e il tempo intercorso tra i due stati:

 $$ x(3)=\left(\begin{array}{c} 1\newline 0 \end{array}\right) $$

```matlab
x3=[1; 0];
```

 $$ x(4)=e^{A(4-3)} x(3) $$

```matlab
x4=expm(A*(4-3))*x3
```
