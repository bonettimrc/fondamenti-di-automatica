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

\begin{align*}
x(t) & =\phi(t, t_0, \alpha x_{0_1}+\beta x_{0_2},\alpha u_1+\beta u_2)\\
& = \alpha \phi(t, t_0, x_{0_1}, u_1) + \beta\phi(t, t_0, x_{0_2}, u_2)
\end{align*}  

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

Dato $\delta x_u(t)=x_u(t)-x(t)$ si dice che il moto di riferimento è stabile rispetto a $\delta u$ se:  

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

### Caso vettoriale omogeneo ($u(t)=0$)  

$$\frac{dx}{dt}(t)=Ax(t);\quad x(0)=x_0; \quad x(t)\in\mathbb{R}^n$$  

Si puo dimostrare che la soluzione dell'equazione differenziale vettoriale è del tipo:  
$$x(t)=e^{At}x_0$$  

> #### Calcolo di $e^{At}$
>
> Per calcolare $e^{At}$, calcolare gli $h$ autovalori di $A$ ed analizzare il grado $l$ del polinomio minimo, poi determinare $\gamma_0, \gamma_1, \cdots,\gamma_{l-1}$ da uno dei seguenti sistemi
>
> - se $h=l$  
>
> $$\begin{pmatrix}
> e^{\lambda_1t}\\
> e^{\lambda_2t}\\
> \vdots\\
> e^{\lambda_ht}\\
> \end{pmatrix}=\begin{pmatrix}
> 1 && \lambda_1 && \lambda_1^2 && \cdots && \lambda_1^{l-1}\\
> 1 && \lambda_2 && \lambda_2^2 && \cdots && \lambda_2^{l-1}\\
> \vdots&&\vdots&&\vdots&&\ddots&&\vdots\\
> 1 && \lambda_h && \lambda_h^2 && \cdots &&\lambda_h^{l-1}\\
> \end{pmatrix}
> \begin{pmatrix}
> \gamma_0\\
> \gamma_1\\
> \vdots\\
> \gamma_{l-1}
> \end{pmatrix}
> $$  
>
> - se $h<l$  
>
> $$\begin{pmatrix}
> e^{\lambda_1t}\\
> te^{\lambda_2t}\\
> \vdots\\
> t^{l_1-1}e^{\lambda_ht}\\
> \hline
> \vdots\\
> \hline
> \vdots\\
> t^{l_h-1}e^{\lambda_ht}
> \end{pmatrix}=\begin{pmatrix}
> 1 && \lambda_1 && \lambda_1^2 && \cdots && \lambda_1^{l-1}\\
> 0 && 1 && \lambda_1 && \cdots && (l-1)\lambda_1^{l-2}\\
> \vdots&&\vdots&&\vdots&&\ddots&&\vdots\\
> 0 && 0 && 0 && \cdots &&\frac{(l-1)!}{(l-l_1)!}\lambda_1^{l-l_1}\\
> \hline
> \vdots && \vdots && \vdots && \ddots && \vdots\\
> \hline
> \vdots && \vdots && \vdots && \ddots && \vdots\\
> 0 && 0 && 0&& \cdots && \frac{(l-1)!}{(l-l_h)!}\lambda_h^{l-l_h}
> \end{pmatrix}
> \begin{pmatrix}
> \gamma_0\\
> \gamma_1\\
> \vdots\\
> \gamma_{l-1}
> \end{pmatrix}
> $$  
>
> Infine, in entrambi i casi:  
>
> $$e^{At}=\sum_{i=0}^{l-1}\gamma_i A^i$$  
>
> ##### Matrici $2\times 2$  
>
> - $A$ ha $2$ autovalori distinti  
>
> $$\begin{pmatrix}
> e^{\lambda_1t}\\
> e^{\lambda_2t}\\
> \end{pmatrix}=\begin{pmatrix}
> 1 && \lambda_1 \\
> 1 && \lambda_2 \\
> \end{pmatrix}
> \begin{pmatrix}
> \gamma_0\\
> \gamma_1\\
> \end{pmatrix}
> $$
>
> - $A$ ha $1$ autovalore con molteplicità $2$  
>
> $$\begin{pmatrix}
> e^{\lambda_1t}\\
> te^{\lambda_2t}\\
> \end{pmatrix}=\begin{pmatrix}
> 1 && \lambda_1 \\
> 0 && 1 \\
> \end{pmatrix}
> \begin{pmatrix}
> \gamma_0\\
> \gamma_1\\
> \end{pmatrix}
> $$
>
> Infine, in entrambi i casi:
> $$e^{At}=\gamma_0 I+\gamma_1 A$$

L'esponenziale della matrice $At$ è anche chiamata matrice di transizione perchè determina, in assenza di ingresso ($u=0$), il moto libero  

#### Sturttura generale di $e^{At}$  

Ogni termine di $e^{At}$ è una combinazione lineare a coefficienti costanti di termini del tipo:

$$e^{\lambda_1t}, te^{\lambda_1t}, \cdots,t^{l_1-1}e^{\lambda_1t}, \cdots, e^{\lambda_ht}, \cdots, t^{l_h-1}e^{\lambda_ht}$$  

Questi termini elementari si chiamano modi di $e^{At}$ e caratterizzano completamente il moto libero del sistema

### Caso vettoriale non omogeneo ($u(t)\neq 0$)  

$$\frac{dx}{dt}(t)=Ax(t)+Bu(t);\quad x(0)=x_0; \quad x(t)\in\mathbb{R}^n$$  

Si può dimostrare che la soluzione dell'equazione differenziale è data dalla formula di lagrange:  

$$x(t)=\underbrace{e^{At}x_0}_{\text{moto libero}}+\underbrace{\int_0^t e^{A(t-\tau)}Bu(\tau)d\tau}_{\text{moto forzato}}$$  

Nel caso di un sistema lineare stazionario, si ottiene facilmente la risposta $y(t)=Cx(t)+Du(t)$:  

$$y(t)=\underbrace{Ce^{At}x_0}_{\text{risposta libera}}+\underbrace{\int_0^t Ce^{A(t-\tau)}Bu(\tau)d\tau+Du(t)}_{\text{risposta forzata}}$$  

La matrice  

$$W(t)=Ce^{At}B$$  

è chiamata risposta impulsiva del sistema

Se $x_0=0$ ed il sistema è puramente dinamico:  

$$y(t)=\int_0^t W(t-\tau)u(\tau)d\tau$$  

ovvero l'uscita è data dall'integrale di convoluzione tra la risposta impulsiva e l'ingresso.  
La risposta impulsiva è così denominata in quanto corrisponde anche alla risposta del sistema nel caso in cui venga applicato ad esso la funzione generallizzata *delta di Dirac* $\delta(t)$:  

$$u(t)=\delta(t)\implies y(t)=\int_0^t W(t-\tau)\delta(\tau)d\tau=W(t)$$  

## Sistemi lineari stazionari a tempo discreto  

### Caso vettoriale omogeneo ($u(t)=0$)

$$x(k+1)=Ax(k);\quad x(0)=x_0;\quad x(k)\in\mathbb{R}^n;\quad  k\in\mathbb{Z}$$  

In tale caso risulta:  

\begin{align*}
x(1)&=Ax_0\\
x(2)&=Ax(1)=A^2x_0\\
&\vdots\\
x(k)&=A^kx_0\\
\end{align*}  

Pertanto nel caso discreto la matrice di transizione, che caratterizza il moto libero è $A^k$.  
A differenza dell'esponenziale di matrice, la potenza di matrice può essere singolare.  

<!-- #### Calcolo di $A^k$  -->

Anche tale matrice può essere calcolata con la teoria delle funzioni di matrice, dalla quale risulta che ogni suo elemento è una combinazione lineare a coefficienti costanti di termini, detti modi di $A^k$, del tipo:  

$$\lambda_1^k, k\lambda_1^{k-1}, \cdots, (l_1-1)!\binom{k}{l_1-1}\lambda_1^{k-l_1+1},\cdots,\lambda_h^k, \cdots, (l_h-1)!\binom{k}{l_h-1}\lambda_h^{k-l_h+1}$$  

### Caso non omogeneo ($k\neq0$)  

$$x(k+1)=Ax(k)+Bu(k);\quad x(0)=x_0;\quad x(k)\in\mathbb{R}^n;\quad k\in\mathbb{Z}$$  

In tale caso risulta:  

\begin{align*}
x(1)&=Ax_0+Bu(0)\\
x(2)&=Ax(1)+Bu(1)=A^2x_0+ABu(0)+Bu(1)\\
&\vdots\\
x(k)&=\underbrace{A^kx_0}_{\text{moto libero}}+\underbrace{\sum_{i=0}^{k-1}A^{k-1-i}Bu(i)}_{\text{moto forzato}}\\
\end{align*}  

Si ottiente facilmente la risposta:  

$$
y(k)=\underbrace{CA^kx_0}_{\text{risposta libera}}+\underbrace{\sum_{i=0}^{k-1}CA^{k-1-i}Bu(i)+Du(k)}_{\text{risposta forzata}}
$$  

La matrice  

$$W(k)=CA^{k-1}B$$  

è la risposta impulsiva per il caso discreto, determinabile applicando come ingresso  

$$u(k)=\begin{cases}
1 & k=0\\
0& k\neq 0
\end{cases}$$  

## Stabilità di un moto con stato iniziale perturbato  

moto di riferimento:  

$$x(t)=e^{At}x_0+\int_0^t e^{A(t-\tau)}Bu(\tau)d\tau$$  

moto perturbato rispetto allo stato iniziale:  

$$x_p(t)=e^{At}(x_0+\delta x_0)+\int_0^t e^{A(t-\tau)}Bu(\tau)d\tau$$  

$$\implies \delta x_p(t)=x_p(t)-x(t)=e^{At}\delta x_0$$  

La differenza tra il moto di riferimento e quello perturbato corrisponde a un moto libero del sistema con stato iniziale $\delta x(0)$  

Per poter raggiungere la stabilità asintotica, ovvero perchè sia:  

$$\lim_{t\to\infty}\delta x_p(t)=0$$  

occorre che tutti gli elementi di $e^{At}$ tendano a $0$ per $t\to\infty$  

### Caso discreto  

moto di riferimento:  

$$x(k)=A^kx_0+\sum_{i=0}^{k-1}A^{k-1-i}Bu(i)$$  

moto perturbato:  

$$x_p(k)=A^k(x_0+\delta x_0)+\sum_{i=0}^{k-1}A^{k-1-i}Bu(i)$$  

$$\implies \delta x_p(k)=x_p(k)-x(k)=A^k\delta x_0$$  

## Stabilità e stati di equilibrio dei sistemi lineari tempo stazionari  

Uno stato di equilibrio è un punto $\overline{x}\in X$ per il quale è possibile trovare una funzione di ingresso $u$ tale che:  

$$\overline{x}=\phi(t, t_0, \overline{x}, u)$$  

Se $A$ è invertibile, il punto di equilibrio è unico:  

$$A\overline{x}+B\overline{u}=0 \implies \overline{x}=-A^{-1}B\overline{u}$$  

Notare che se $\overline{u}=0$ allora $\overline{x}=0$  

L'unico movimento di interesse per la stabilità è il movimento libero, le cui caratteristiche dipendono da $e^{At}$ (o $A^k$ nel caso discreto), cioè dipendono solo dagli autovalori di $A$.

## Rappresentazioni equivalenti  

Si osservi che non esiste un modo unico di scegliere le variabili di stato per rappresentare un sistema dinamico, o anche per ordinarle nel vettore di stato.  
Un sistema lineare tempo stazionario una volta scelte le variabili di stato è rappresentato da:  

$$\begin{cases}
\dot{x}(t)=Ax(t)+Bu(t)\\
y(t)=Cx(t)+Du(t)
\end{cases}$$  

Considerando una matrice $T\in M_n(\mathbb{R})$ costante e non singolare, è possibile effettuare un cambio di variabili e definire un nuovo vettore di stato $z$ come:  

$$x=Tz\iff z=T^{-1}x$$  

Sostituendo nelle equazioni di partenza si ottiene:  

$$\begin{cases}
\dot{z}(t)=\hat{A}z(t)+\hat{B}u(t)\\
y(t)=\hat{C}x(t)+\hat{D}u(t)
\end{cases}$$  

Dove:  

$$\begin{cases}
\hat{A}=T^{-1}AT\\
\hat{B}=T^{-1}B\\
\hat{C}=CT\\
\hat{D}=D\\
\end{cases}$$  

Il sistema rappresentato da queste equazioni è equivalente al sistema di partenza, nel senso che per un ingresso $u(t)$ e due stati iniziali legati dalla condizione  

$$z_0=T^{-1}$$  

Le funzioni dello stato $x(t)$ e $z(t)$ sono legate dalla relazione  

$$z(t)=T^{-1}x(t)\quad \forall t\geq 0$$  

e le uscite sono identiche per entrambi i modelli.  

Le matrici $A$ e $\hat{A}$ sono matrici simili, aventi lo steso polinomio caratteristico, lo stesso polinomio minimo e gli stessi autovalori:  

\begin{align*}
|\lambda I - \hat{A}|&=|\lambda T^{-1}T - T^{-1}AT|\\
&=|T^{-1}(\lambda I - \hat{A})T|\\
&=\frac{1}{|T|}|\lambda I - \hat{A}||T|=|\lambda I - A|\end{align*}  

Risulta inoltre:  

$$\hat{A}^2=T^{-1}ATT^{-1}AT=T^{-1}A^2T$$  

$$e^{\hat{A}t}=\sum_{i=0}^\infty\hat{A}\frac{t^i}{i!}=\sum_{i=0}^\infty T^{-1}AT\frac{t^i}{i!}=T^{-1}e^{At}T$$  

$$\hat{C}e^{\hat{A}t}\hat{B}=CTT^{-1}e^{At}TT^{-1}B=Ce^{At}B$$  

La risposta impulsiva $W(t)$ rimane quindi invariata  

La scelta delle variabili di stato però influisce sulla forma delle matrici $A$, $B$ e $C$. Ciò permette, con opportune trasformazioni dello stato, di rendere più evidenti alcuni parametri numerici del sistema, in quiesto caso si parla di sistemi in forma canonica  

## Stabilità dei sistemi lineari stazionari  

Teorema
: un sistema lineare stazionario a tempo continuo è semplicemente stabile se e solo se tutti gli autovalori di $A$ hanno parte reale negativa o nulla, e quelli a parte reale nulla hanno molteplicità unitaria nel polinomio minimo di $A$  

Teorema
: Un sistema lineare stazionario a tempo continuo è asintoticamente stabile se e solo se tutti gli autovalori di $A$ hanno parte reale negativa  

Teorema
: Un sistema lineare stazionario a tempo discreto è semplicemente stabile se e solo se tutti gli autovalori di $A$ hanno modulo minore o uguale a $1$, e quelli a modulo unitario hanno molteplicità unitaria nel polinomio minimo di $A$  

Teorema
: Un sistema lineare stazionario a tempo discreto è asintoticamente stabile se e solo se tutti gli autovalori di $A$ hanno modulo minore di $1$  

## Proprietà strutturali dei sistemi lineari stazionari, raggiungibilità e controllabilità  

Sono proprietà di un sistema che descrivono la possibilità di influire sul suo moto $x$ agendo opportunamente sulla funzione di ingresso $u$  

Come la stabilità, tali proprietà sono strutturali, cioè non dipendono dalla scelta delle variabili di stato  

Inoltre non sono modificabili tramite il controllo  

### Raggiungibilità

Definizione
: Lo stato $x_1$ di un sistema dinamico è raggiungibile da $x_0$ nell'intervallo di tempo $[t_0, t_1]$ con $t_0<t_1$ se esiste una funzione di ingresso $u\in U_f$ tale che:  

$$x_1=x(t_1)=\phi(t_1,t_0,x_0,u)$$  

L'insieme degli stati raggiungibili all'istante $t_1$ a partire dall'evento $(t_0,x_0)$ è indicato con  

$$\mathcal{R}^+ (t_0,t_1,x_0)$$  

### Controllabilità  

Definizione
: Lo stato $x_0$ di un sistema dinamico è controllabile a $x_1$ nell'intervallo di tempo $[t_0, t_1]$ con $t_0<t_1$ se esiste una funzione di ingresso ammissibile $u\in U_f$ tale che:  

$$x_1=x(t_1)=\phi(t_1,t_0,x_0,u)$$  

L'insieme degli stati controllabili all'evento $(t_1,x_1)$ a partire dall'istante $t_0$ è indicato con  

$$\mathcal{R}^- (t_0,t_1,x_1)$$  