
# Esempio completo

Modello semplificato della dinamica longitudinale di un aereo

 $$ \begin{array}{l} \dot{\alpha} =-2\alpha +C_q q+2\delta \newline \dot{q} =-\alpha -4q+\delta \newline \dot{\theta} =C_q q\newline x_1 =\alpha ;~x_2 =q;~x_3 =\theta ;~u=\delta ;~y=\theta  \end{array} $$

Si determini l'uscita $y$ all'istante $t=10$ data la condizione iniziale $x_0 =\left(\begin{array}{c} 1\newline 0\newline 0 \end{array}\right);~t_0 =0$ con $C_q =1$

## Soluzione

```matlab
syms x1dot x1 Cq x2 u x2dot x3dot x3;
eqns=[x1dot==-2*x1+Cq*x2+2*u, x2dot==-x1-4*x2+u, x3dot==Cq*x2];
xdot=[x1dot; x2dot; x3dot];
[x1dot, x2dot, x3dot]=solve(eqns, xdot);
xdot=[x1dot; x2dot; x3dot];
x=[x1; x2; x3];
[A, Bu]=equationsToMatrix(xdot, x)
B=-Bu/u;
tf=10;
x0=[1;0;0];
t0=0;
Cq=1;
A=subs(A);
xf=expm(A.*(tf-t0))*x0;
C=[0 0 1];
yf=C*xf
vpa(yf)
```
