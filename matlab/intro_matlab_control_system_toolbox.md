
# Control System Toolbox

La funzione ss(A,B,C,D) crea l'oggetto rappresentativo del modello nello spazio degli stati a partire dalle matrici A,B,C,D in formato numerico

 $$ A=\left(\begin{array}{cc} -1 & 4\newline -4 & -1 \end{array}\right);~B=\left(\begin{array}{c} 1\newline 0 \end{array}\right);~C=\left(\begin{array}{cc} 0 & 1 \end{array}\right);~D=\left(\begin{array}{c} 2 \end{array}\right) $$

```matlab
sys=ss([-1 4; -4 -1], [1;0], [0 1], 2);
```

La funzione `lsim(sys,u,t,x0)` simula l'evoluzione dello stato del sistema a partire dalle condizioni iniziali e ne restituisce uscita, tempo simulato e stato

 $$ t\in \lbrace 0,0.1,0.2,\ldots,10\rbrace $$

```matlab
t=0:0.01:10;
```

 $$ u=\underset{\# t}{\underbrace{\left(\begin{array}{cccc} 0 & 0 & \cdots  & 0 \end{array}\right)} } $$

```matlab
u=zeros(size(t));
```

 $$ x_0 =\left(\begin{array}{c} 1\newline 0 \end{array}\right) $$

```matlab
x0=[1,0];
```

La chiamata senza assegnazione, apre una finestra di analisi grafica per sistemi

```matlab
lsim(sys, u, t, x0)
```

Con la seguente opzione di chiamata, si ottiene invece il vettore di stato completo. In questo caso il sistema è di ordine 2, quindi il grafico in due dimensioni ne rappresenta la traiettoria

```matlab
[y, tout, x]=lsim(sys, u, t, x0);
plot(x(:,1),x(:,2))
```

Nota anche la derivata dello stato, si può visualizzare la direzione della traiettoria

```matlab
xn=x(1:5:end,:);
un=u(1:5:end);
```

 $$ v=\dot{x} =Ax+Bu $$

```matlab
% non funziona
v=(sys.A*xn+sys.B*un);
```

```matlab
hold on
quiver(xn(:,1), xn(:,2), v(:,1),v(:,2))

```
