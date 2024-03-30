# Analisi dei sistemi dinamici  

[[TOC]]

## Definizioni  

Dato un sistema dinamico con modello generale  

$$\frac{dx}{dt}(t)=f(x(t),u(t),t)$$  

ed avente funzione di transizione dello stato:  

$$x(t)=\phi(t, t_0, x(t_0), u)$$  

un movimento o moto è l'insieme delle coppie $(t,x(t))$ ottenute data una certa funzione di ingresso $u$ in $[t_0, t_1]$  

Una traiettoria del sistema è la proiezione del movimento nello spazio degli stati $X$  

Uno stato di equilibrio è un punto $\overline{x}\in X$ per il quale è possibile trovare una funzione di ingresso $u$ tale che:  

$$\overline{x}=\phi(t, t_0, \overline{x}, u)$$  

### Vantaggio della proprietà di linearità  

Nei sistemi lineari vale il principio di sovrapposizione degli effetti, in base al quale le transizioni ottenute con combinazioni lineari tra diversi valori dello stato iniziale e diverse funzioni di ingresso si sommano:  

$$
\begin{align*}
x(t) & =\phi(t, t_0, \alpha x_{0_1}+\beta x_{0_2},\alpha u_1+\beta u_2)\\
& = \alpha \phi(t, t_0, x_{0_1}, u_1) + \beta\phi(t, t_0, x_{0_2}, u_2)
\end{align*}
$$  

Ponendo $\alpha=\beta=1;\quad x_{0_1}=x_0; \quad x_{0_2}=0; \quad u_1=0; \quad u_2=u$ si può scorporare l'effetto dello stato iniziale (moto libero) da quello dell'ingresso (moto forzato)  

$$x(t)=\phi(t,t_0,x_0, u)=\phi(t,t_0,x_0,0)+\phi(t,t_0,0,u)$$  

Analogamente, per la funzione di risposta di un sistema lineare si può scorporare l'effetto dello stato iniziale (risposta libera) da quello dell'ingresso (risposta forzata)  

$$y(t)=\gamma(t,t_0,x_0, u)=\gamma(t,t_0,x_0,0)+\gamma(t,t_0,0,u)$$  

Nei sistemi stazionari, vale la proprietà di traslazione nel tempo di cause ed effetti.  
Cioè, data la funzione di transizione (ed analogamente per la funzione di uscita):  

$$x(t)=\phi(t,t_0,x_0,u)$$  

risulta  

$$x(t+\tau)=\phi(t+\tau,t_0+\tau,x_0,u_{\Delta})=x(t)$$  

con  

$$u_{\Delta}(t)=u(t+\tau)$$  

Come conseguenza della traslazione del tempo ammissibile per i sistemi stazionari:

- L'istante iniziale si puo sempre assumere $t_0=0$  
- Le funzioni di transizione dello stato $\phi$ e della risposta $\gamma$ dipendono dalla differenza $t-t_0$ e non da $t$ e $t_0$ separatamente  

### Definizioni per la stabilità

La stabilità esprime la capacità di un sistema di reagire con variazioni limitate del moto $x$ a perturbazioni limitate dello stato iniziale $x(t_0)$ o dell'ingresso $u$  

moto di riferimento
:  
$$x(t)=\phi(t, t_0, x(t_0), u)$$  

moto perturbato, con perturbazione sullo stato iniziale $\delta x(t_0)$
:  
$$x_p(t)=\phi(t,t_0, x(t_0)+\delta x(t_0), u)$$  

moto perturbato, con perturbazione sull'ingresso $\delta u$
:  
$$x_u(t)=\phi(t, t_0, x(t_0), u+\delta u)$$  

Dato $\delta x_p(t)=x_p(t)-x(t)$ si dice che il moto di riferimento è semplicemente stabile se:  

$$\forall \varepsilon>0 \quad \exists \delta>0,\quad ||\delta x(t_0)||<\delta \implies ||\delta x_p(t)||<\varepsilon\quad \forall t \geq t_0$$  

Si dice che il moto di riferimento è asintoticamente stabile se, oltre alle condizioni per la stabilità semplice, soddisfa la relazione  

$$\lim_{t\to \infty} ||\delta x_p(t)||=0$$  

Dato $\delta x_u(t)=x_u(t)-x(t)$ si dice che il moto di riferimento è stabile rispetto a $\delta u se:  

$$\forall \varepsilon>0 \quad \exists \delta>0,\quad ||\delta u||<\delta \implies ||\delta x_u(t)||<\varepsilon\quad \forall t \geq t_0$$  

## Sistemi lineari stazionari  

Per i sistemi lineari stazionari è possibile calcolare in forma esplicita la funzione di transizione dello stato e la funzione di risposta.  

<!-- Una equazione differenziale scalare e omogenea:  
$$
\begin{cases}
\frac{dx}{dt}(t)=ax(t)\\
x(0)=x_0
\end{cases}
$$  
ha una soluzione del tipo $x(t)=x_0e^{at}$ -->

### Caso vettoriale omogeneo (sistema lineare stazionario con $u(t)=0$)  

$$\frac{dx}{dt}(t)=Ax(t);\quad x(0)=x_0; \quad x(t)\in\mathbb{R}^n$$  

Si puo dimostrare che la soluzione dell'equazione differenziale vettoriale è del tipo:  
$$x(t)=e^{At}x_0$$  

>#### Calcolo di $e^{At}$
>
>Per calcolare $e^{At}$, calcolare gli $h$ autovalori di $A$ ed analizzare il grado $l$ del polinomio minimo, poi determinare $\gamma_0, \gamma_1, \cdots,\gamma_{l-1}$ da uno dei seguenti sistemi
 >
 >- se $h=l$  
 >
 >$$\begin{pmatrix}
    >e^{\lambda_1t}\\
    >e^{\lambda_2t}\\
    >\vdots\\
    >e^{\lambda_ht}\\
    >
>\end{pmatrix}=\begin{pmatrix}
    >1 && \lambda_1 && \lambda_1^2 && \cdots && \lambda_1^{l-1}\\
    >1 && \lambda_2 && \lambda_2^2 && \cdots && \lambda_2^{l-1}\\
    >\vdots&&\vdots&&\vdots&&\ddots&&\vdots\\
    >1 && \lambda_h && \lambda_h^2 && \cdots &&\lambda_h^{l-1}\\
>\end{pmatrix}
>\begin{pmatrix}
    >\gamma_0\\
    >\gamma_1\\
    >\vdots\\
    >\gamma_{l-1}
>\end{pmatrix}
>$$  
 >- se $h<l$  
>$$\begin{pmatrix}
    >e^{\lambda_1t}\\
    >te^{\lambda_2t}\\
    >\vdots\\
    >t^{l_1-1}e^{\lambda_ht}\\
    >\hline
    >\vdots\\
    >\hline
    >\vdots\\
    >t^{l_h-1}e^{\lambda_ht}
    >
>\end{pmatrix}=\begin{pmatrix}
    >1 && \lambda_1 && \lambda_1^2 && \cdots && \lambda_1^{l-1}\\
    >0 && 1 && \lambda_1 && \cdots && (l-1)\lambda_1^{l-2}\\
    >\vdots&&\vdots&&\vdots&&\ddots&&\vdots\\
    >0 && 0 && 0 && \cdots &&\frac{(l-1)!}{(l-l_1)!}\lambda_1^{l-l_1}\\
    >\hline
    >\vdots && \vdots && \vdots && \ddots && \vdots\\
    >\hline
    >\vdots && \vdots && \vdots && \ddots && \vdots\\
    >0 && 0 && 0&& \cdots && \frac{(l-1)!}{(l-l_h)!}\lambda_h^{l-l_h}
>\end{pmatrix}
>\begin{pmatrix}
    >\gamma_0\\
    >\gamma_1\\
    >\vdots\\
    >\gamma_{l-1}
>\end{pmatrix}$$  
>Infine, in entrambi i casi:  
>$$e^{At}=\sum_{i=0}^{l-1}\gamma_i A^i$$  
>
>>##### Matrici $2\times 2$  
 >>
 >>- $A$ ha $2$ autovalori distinti  
 >>
 >>$$\begin{pmatrix}
    >>e^{\lambda_1t}\\
    >>e^{\lambda_2t}\\
    >>
>>\end{pmatrix}=\begin{pmatrix}
    >>1 && \lambda_1 \\
    >>1 && \lambda_2 \\
>>\end{pmatrix}
>>\begin{pmatrix}
    >>\gamma_0\\
    >>\gamma_1\\
>>\end{pmatrix}
>>$$
 >>- $A$ ha $1$ autovalore con molteplicità $2$  
>>$$\begin{pmatrix}
    >>e^{\lambda_1t}\\
    >>te^{\lambda_2t}\\
    >>
>>\end{pmatrix}=\begin{pmatrix}
    >>1 && \lambda_1 \\
    >>0 && 1 \\
>>\end{pmatrix}
>>\begin{pmatrix}
    >>\gamma_0\\
    >>\gamma_1\\
>>\end{pmatrix}
>>$$
>>Infine, in entrambi i casi:
>>$$e^{At}=\gamma_0 I+\gamma_1 A$$

L'esponenziale della matrice $At$ è anche chiamata matrice di transizione perchè determina, in assenza di ingresso ($u=0$), il moto libero  

### Caso vettoriale non omogeneo (sistema lineare stazionario con $u(t)\neq 0$)  

$$\frac{dx}{dt}(t)=Ax(t)+Bu(t);\quad x(0)=x_0; \quad x(t)\in\mathbb{R}^n$$  

Si può dimostrare che la soluzione dell'equazione differenziale è data dalla formula di lagrange:  

$$x(t)=e^{At}x_0+\int_0^t e^{A(t-\tau)}Bu(\tau)d\tau$$  
