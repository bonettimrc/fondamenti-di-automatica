# Calcolo di $e^{At}$  

## metodo analitico del polinomio interpolante  

### Richiamo delle basi teoriche  

#### Definizione. Sia $A\in M_n(\mathbb{R})$. Si dice  

- polinomio caratteristico di $A$  
    : $\Delta_A(\lambda)=\det(\lambda I-A)$  
- equazione caratteristica di $A$  
    : $\Delta_A(\lambda)=0$  
- autovalori di $A$  
    : sono le radici dell'equazione caratteristica
- polinomio annullatore per $A$
    : è un polinomio $p$ che soddisfa la relazione  
    $$p(A)=0$$
- polinomio minimo di $A$
    : è il polinomio annullatore di grado minimo
    $\alpha$

#### Teorema di Cayley-Hamilton  

La matrice $A$ soddisfa l'equazione caratteristica espressa in forma matriciale

#### Proprietà del polinomio minimo  

- È unico se il coefficiente del termine con esponente maggiore è 1
- È un divisore del polinomio caratteristico  

    $$\alpha(\lambda)=\frac{\Delta_A(\lambda)}{b(\lambda)}$$  

    inoltre $b(\lambda)=\gcd\{\operatorname {adj}(\lambda I-A)_{i,j}\}$  
- Essendo divisore del polinomio caratteristico $\Delta_A$ ha come radici tutti gli autovalori di $A$  
- La matrice $(\lambda I -A)^{-1}$ è una matrice i cui elementi sono rapporti tra polinomi in funzione di $\lambda$  
- Il minimo comune multiplo dei denominatori di tale matrice è il polinomio minimo di $A$  
- Il calcolo di questa matrice e del $\operatorname {lcm}$ dei denominatori costituiscono appunto il procedimento per determinare il polinomio minimo di $A$

### Metodo del polinomio interpolante  

Sia $A\in M_n(\mathbb{R})$ e si consideri una funzione $f:\mathbb{R}\to\mathbb{R}$ sviluppabile in serie di potenze:  

$$f(x)=\sum_{i=0}^{\infty} c_i x^i$$  

La corrispondente funzione di matrice $f:\mathbb{R}^n\to\mathbb{R}^n$ è definita:  

$$f(A)=\sum_{i=0}^{\infty} c_i A^i$$  

La funzione di matrice si può però rappresentare senza considerare infiniti termini, questo perchè per A vale il teorema di Cayley-Hamilton.  
Inoltre se il polinomio minima di $A$ è di grado $l$ inferiore al grado $n$ di quello caratteristico, le serie di potenze sono riconducibili al più a $l$ termini.  
Pertanto, le serie infinite considerate diventano, con una opportuna definizione di coefficienti $\gamma_0, \gamma_1, \cdots,\gamma_{l-1}$ delle serie finite, come segue:  

$$f(A)=\sum_{i=0}^{\infty} c_i A^i=\sum_{i=0}^{l-1} \gamma_i A^i$$  

$$f(\gamma_k)=\sum_{i=0}^{\infty} c_i \gamma_k^i=\sum_{i=0}^{l-1} \gamma_i \lambda_k^i\quad \forall k=1,2,\cdots,h$$  

I coefficienti $\gamma_0, \gamma_1, \cdots,\gamma_{l-1}$ che compaiono nell'espressione matriciale e nelle $h$ espressioni scalari sono gli stessi.  
Pertanto, per calcolarli si possono sfruttare come equazioni di vincolo proprio le $h$ espressioni scalari di $f(x)$ ottenute sostituendo a $x$ gli autovalori di $A$.  
Nel caso di interesse, l'obiettivo finale è ottenere  

$$f(x)=e^{xt}\implies f(A)=e^{At}$$  

e i coefficienti $\gamma_0, \gamma_1, \cdots,\gamma_{l-1}$ risulteranno a loro volta funzioni del tempo.  
Una volta determinati i coefficienti $\gamma_0, \gamma_1, \cdots,\gamma_{l-1}$, la matrice $e^{At} si calcola esplicitamente con la sommatoria:  

$$e^{At}=\sum_{i=0}^{l-1} \gamma_i A^i$$  

Le equazioni di vincolo per calcolare $\gamma_0, \gamma_1, \cdots,\gamma_{l-1}$ dalla funzione scalare si possono esprimere come segue:  

$$
\begin{pmatrix}
    f(\lambda_1)\\
    f(\lambda_2)\\
    \vdots\\
    f(\lambda_h)\\
\end{pmatrix}
=
\begin{pmatrix}
    1 && \lambda_1 && \lambda_1^2 && \cdots && \lambda_1^{l-1}\\
    1 && \lambda_2 && \lambda_2^2 && \cdots && \lambda_2^{l-1}\\
    \vdots&&\vdots&&\vdots&&\ddots&&\vdots\\
    1 && \lambda_h && \lambda_h^2 && \cdots &&\lambda_h^{l-1}\\
\end{pmatrix}
\begin{pmatrix}
    \gamma_0\\
    \gamma_1\\
    \vdots\\
    \gamma_{l-1}
\end{pmatrix}
$$  

Nel caso di interesse, cioè per calcolare $f(A)=e^{At}$ risulta il seguente sistema di vincoli, determinato dai valori delgi autovalori di $A$:  

$$
\begin{pmatrix}
    e^{\lambda_1t}\\
    e^{\lambda_2t}\\
    \vdots\\
    e^{\lambda_ht}\\
\end{pmatrix}
=
\begin{pmatrix}
    1 && \lambda_1 && \lambda_1^2 && \cdots && \lambda_1^{l-1}\\
    1 && \lambda_2 && \lambda_2^2 && \cdots && \lambda_2^{l-1}\\
    \vdots&&\vdots&&\vdots&&\ddots&&\vdots\\
    1 && \lambda_h && \lambda_h^2 && \cdots &&\lambda_h^{l-1}\\
\end{pmatrix}
\begin{pmatrix}
    \gamma_0\\
    \gamma_1\\
    \vdots\\
    \gamma_{l-1}
\end{pmatrix}
$$  

A questo punto, si possono presentare due casi a seconda della molteplicità degli autovalori nel polinomio minimo:  

 1. $h=l$
 2. $h<l$

#### $h=l$  

Il sistema di equazioni ha soluzione unica, essendo la matrice dei coefficienti invertibile per costruzione

#### $h<l$  

Il sistema non ha soluzione univoca, quindi occore fare ulteriori considerazioni.
Anzitutto, si noti che, dato un qualunque altro polinomio $h(x)$ per il quale valga:  

$$
\begin{align*}
&g(A)=h(A)\\
\implies& g(A)-h(A)=0
\end{align*}
$$  

Il che significa che il polinomio minimo $\alpha$ è un divisore di $g(x)-h(x)$, cioè esiste un polinomio $\beta(x)$ tale che:  

$$g(x)-h(x)=\alpha(x)\beta(x)$$  

Inoltre, essendo il polinomio minimo $\alpha$ fattorizabile rispetto agli autovalori nei punti di interesse per la variabile scalare $x$, il polinomio minimo ha anche derivate rispetto a $x$ nulle fino all'ordine pari alla molteplicità dell'autovalore considerato:  

$$0=\alpha(\lambda_k)=\frac{d\alpha}{dx}(\lambda_k)=\frac{d^{l_k-1}\alpha}{dx^{l_k-1}}(\lambda_k)\quad \forall k=1,2,\cdots,h$$  

Tutti i polinomi e le loro derivate fino alla $l_k-1$ esima assumono gli stessi valore in $\lambda_k \forall k=1,2,\cdots,h$  
In base a questi risultati si può estendere il problema di calcolo dei coefficienti $\gamma_0, \gamma_1, \cdots,\gamma_{l-1}$ impostando un sistema di equazioni basato su una matrice di Vandermonde generalizzata, la qui struttura ha:

- tanti blocchi quanti sono gli autovalori di $A$  
- la prima riga di ogni blocco analoga a quelle della matrice di Vandermonde base  
- le righe seguenti di ogni blocco formulate come le derivate successive rispetto a $x$ della prima riga e calcolate in $\lambda_i$, fino all'ordine di derivata pari alla molteplicità nel polinomio minimo di $\lambda_i$ stesso  

## Riassunto

Per calcolare $e^{At}$, calcolare gli $h$ autovalori di $A$ ed analizzare il grado $l$ del polinomio minimo, poi determinare $\gamma_0, \gamma_1, \cdots,\gamma_{l-1}$ da uno dei seguenti sistemi

- se $h=l$  

$$\begin{pmatrix}
    e^{\lambda_1t}\\
    e^{\lambda_2t}\\
    \vdots\\
    e^{\lambda_ht}\\
\end{pmatrix}
=
\begin{pmatrix}
    1 && \lambda_1 && \lambda_1^2 && \cdots && \lambda_1^{l-1}\\
    1 && \lambda_2 && \lambda_2^2 && \cdots && \lambda_2^{l-1}\\
    \vdots&&\vdots&&\vdots&&\ddots&&\vdots\\
    1 && \lambda_h && \lambda_h^2 && \cdots &&\lambda_h^{l-1}\\
\end{pmatrix}
\begin{pmatrix}
    \gamma_0\\
    \gamma_1\\
    \vdots\\
    \gamma_{l-1}
\end{pmatrix}
$$  

- se $h<l$  

$$\begin{pmatrix}
    e^{\lambda_1t}\\
    te^{\lambda_2t}\\
    \vdots\\
    t^{l_1-1}e^{\lambda_ht}\\
    \hline
    \vdots\\
    \hline
    \vdots\\
    t^{l_h-1}e^{\lambda_ht}
\end{pmatrix}
=
\begin{pmatrix}
    1 && \lambda_1 && \lambda_1^2 && \cdots && \lambda_1^{l-1}\\
    0 && 1 && \lambda_1 && \cdots && (l-1)\lambda_1^{l-2}\\
    \vdots&&\vdots&&\vdots&&\ddots&&\vdots\\
    0 && 0 && 0 && \cdots &&\frac{(l-1)!}{(l-l_1)!}\lambda_1^{l-l_1}\\
    \hline
    \vdots && \vdots && \vdots && \ddots && \vdots\\
    \hline
    \vdots && \vdots && \vdots && \ddots && \vdots\\
    0 && 0 && 0&& \cdots && \frac{(l-1)!}{(l-l_h)!}\lambda_h^{l-l_h}
\end{pmatrix}
\begin{pmatrix}
    \gamma_0\\
    \gamma_1\\
    \vdots\\
    \gamma_{l-1}
\end{pmatrix}$$  

Infine, in entrambi i casi:  

$$e^{At}=\sum_{i=0}^{l-1}\gamma_i A^i$$  

### Matrici $2\times 2$  

 - $A$ ha $2$ autovalori distinti  

$$\begin{pmatrix}
    e^{\lambda_1t}\\
    e^{\lambda_2t}\\
\end{pmatrix}
=
\begin{pmatrix}
    1 && \lambda_1 \\
    1 && \lambda_2 \\
\end{pmatrix}
\begin{pmatrix}
    \gamma_0\\
    \gamma_1\\
\end{pmatrix}
$$

- $A$ ha $1$ autovalore con molteplicità $2$  

$$\begin{pmatrix}
    e^{\lambda_1t}\\
    te^{\lambda_2t}\\
\end{pmatrix}
=
\begin{pmatrix}
    1 && \lambda_1 \\
    0 && 1 \\
\end{pmatrix}
\begin{pmatrix}
    \gamma_0\\
    \gamma_1\\
\end{pmatrix}
$$  

Infine, in entrambi i casi:  

$$e^{At}=\gamma_0 I+\gamma_1 A$$
