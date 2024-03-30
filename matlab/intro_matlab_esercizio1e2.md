
# Esercizio 1

Si ricavino le matrici del modello di un carrello elevatore a trazione elettrica in modalità di frenatura:

 $$ \begin{array}{l} m\ddot{p} +b\dot{p} +\frac{k_m^2 }{R_a +R_f }\dot{p} =0\newline x_1 =p;~x_2 =\dot{p} \newline  \end{array} $$

## Soluzione

```matlab
syms m km Ra Rf b;
syms x1 x2 x1dot x2dot u y t;
```

 $$ x=\left(\begin{array}{c} x_1 \newline x_2  \end{array}\right) $$

```matlab
x=[x1;x2];
```

 $$ \dot{x} =\left(\begin{array}{c} \dot{x_1 } \newline \dot{x_2 }  \end{array}\right) $$

```matlab
xdot=[x1dot;x2dot];
```

 $$ \left\lbrace \begin{array}{c} \dot{x_1 } =x_2 \newline m\dot{x_2 } +bx_2 +\frac{k_m^2 }{R_a +R_f }x_2 =0 \end{array}\right. $$

(l'equazione $\dot{x_1 } =x_2$ la otteniamo TODO)

```matlab
eqns = [x1dot==x2; m*x2dot+b*x2+(km^2/(Ra+Rf))*x2==0];
```

Risolviamo il sistema di equazioni per $\dot{x_1 }$ e $\dot{x_2 }$ usando solve

```matlab
[x1dot,x2dot]=solve(eqns,xdot);
xdot = [x1dot;x2dot];
```

Ricaviamo le matrici $A$ e $B$ usando equationsToMatrix

```matlab
[A,Bu]=equationsToMatrix(xdot,x)
```

```matlab
B=-Bu/u
```

# Esercizio 2

Dati i seguenti valori numerici:

 $$ m=1000;~b=100;~R_a =10;~R_f =90;~k_m =300 $$

Si determini  lo spazio percorso e la velocità raggiunta in 12 secondi dal veicolo (ovvero $x(t=12)$ ) in modalità di frenata, considerando una velocità iniziale di $5\frac{m}{s}$ , vale a dire:

 $$ x(0)=\left(\begin{array}{c} 0\newline 5 \end{array}\right) $$

Ricaviamo la matrice $A$ in forma numerica

 $$ m=1000;~b=100;~R_a =10;~R_f =90;~k_m =300 $$

```matlab
m=1000;
b=100;
Ra=10;
Rf=90;
km=300;

A=subs(A);
```

Ricaviamo l'esponenziale di matrice $e^{At}$ in forma simbolica

```matlab
eAt=expm(A*t);
```

Risolviamo ora l'esercizio in forma numerica

 $$ x(0)=\left(\begin{array}{c} 0\newline 5 \end{array}\right) $$

```matlab
x0=[0;5];
```

 $$ t_{\textrm{finale}} =12 $$

```matlab
tf=12;
```

 $$ x(t_{\textrm{finale}} )=x(12)=e^{12A} x(0) $$

```matlab
x12=expm(A*tf)*x0
```

Approssimazione numerica:

```matlab
var = vpa(x12)
```

Grafico di funzioni simboliche:

```matlab
fplot(eAt*x0, [0,12])
legend("x_1 (posizione)", "x_2 (velocità)")
```
