
## Approssimazione di funzioni

Una rete neurale in avanti (o **feed forward**) è un grafo orientato aciclico pesato, organizzato a strati (o livelli), i cui nodi sono unità di McCulloch-Pitts. In generale, valgono le seguenti proprietà:

- Gli strati sono numerati
- Ogni nodo appartiene ad un solo strato
- I nodi del primo stato non hanno archi entranti e il valore di uscita delle relative unità di McCulloch-Pitts viene fornito dall'esterno 
- Ogni nodo, tranne quelli del primo strato, hanno archi entranti che provengono solo dai nodi dello strato precedente
- I nodi dell'ultimo strato non hanno archi uscenti, e il valore di uscita delle relative unità di McCulloch-Pitts viene fornito all'esterno
- I pesi sugli archi sono i pesi entranti nelle unità di McCulloch-Pitts
- Uno dei valori di ingresso per ogni strato della rete viene fissato al valore di bias -1 e non riceve archi entranti 


![[mlp.png|500]]

Se non viene esplicitamente indicato il contrario, si assume che una rete neurale in avanti abbia il massimo numero di connessioni che le consistono di mantenere la struttura a strati. Si noti che gli strati diversi dal primo e dall'ultimo vengono normalmente chiamati strati nascosti (_hidden layer_). Una rete neurale in avanti viene anche detta _perceptron_ (o _percettrone_) e, quando la struttura della rete non è a strati, spesso si parla di rete neurale _ricorrente_.

#### **Single Layer Perceptron** 

Un **Single Layer Perceptron** ( _SLP_ ) è una rete neurale in avanti con $n \in \mathbb{R}_+$ ingressi reali, nessuno strato nascosto,  $m \in \mathbb{R}_+$ uscite reali e una funzione di attivazione $g : \mathbb{R} \rightarrow \mathbb{R}$. Si utilizza la notazione $(n, m)$-_SLP_ per indicare esplicitamente $n$ e $m$. Un $(n, m)$-_SLP_ si può utilizzare come approssimatore di una funzione $\mathbb{R}^n \rightarrow \mathbb{R}^m$ di cui si conoscano i valori per alcuni vettori. Alcuni dei vettori per cui la funzione è nota sono raccolti in un training set, in modo da poter utilizzare l'addestramento supervisionato per trovare i pesi del _SLP_ in grado di approssimare la funzione oggetto di studio. 

Si consideri un $(n, 1)$-_SLP_ e si ipotizzi che tutti i vettori di $\mathbb{R}^n$ utilizzati come ingressi del _SLP_, compresi raccolti nel training set e nel test set, siano del tipo $$x=(x_1, ..., x_n) \text{ , con } x_n = -1$$
Dato un vettore di ingresso, il valore calcolato dal _SLP_ per un certo vettore dei pesi $w$ è 
$$o(w, x) = g(w \cdot x) = \left( \sum^{n-1}_{i = 1} w_i \cdot x_i - w_n\right) $$
L'addestramento supervisionato ha lo scopo di trovare un vettore dei pesi del _SLP_ in modo da minimizzare la distanza media tra il valore calcolato dal _SLP_ e il corrispondente valore della funzione da approssimare. Si noti che il valore della funzione è noto per tutti i vettori del training set.

Sia $x \in \mathbb{R}^n$ uno dei vettori nel training set, l'errore compiuto dal _SLP_ nell'approssimazione della funzione $f$ in $x$ è dato da 

$\epsilon (w, x) = f(x) -o(w,x) = f(x)-g(w\cdot x)$ 

Si noti che l'approssimazione del _SLP_ della funzione $f$ in $x$ è tanto migliore quanto $|\epsilon (w,x)|$  è piccolo (prossimo a zero). In sintesi, fissato un vettore $x$, il problema di individuare un vettore dei pesi $w$ in grado di approssimare bene $f(x)$ può essere espresso mediante la ricerca di un $w$ che minimizzi $|\epsilon (w,x)|$ .

Per fare ciò, normalmente si assume che la funzione di attivazione $g$ sia di classe $C^\inf(\mathbb{R})$ e si cerca il minimo dell'**errore quadratico**$$e(w,x)= \frac{1}{2}\epsilon^2(w,x)$$
anziché di $|\epsilon (w,x)|$. Naturalmente, un vettore dei pesi $w$ in grado di rendere minimo $e(w,x)$ è anche in grado di rendere minimo $|\epsilon (w,x)|$. 

In sintesi, fissato un vettore $x \in \mathbb{R}^n$, l'errore quadratico è una funzione di $w$ di cui si può cercare il minimo mediante l'algoritmo di discesa del gradiente. Quindi, impostando il problema di approssimare $f$ in questi termini, è necessario esprimere il gradiente di $e(w)$ in modo da utilizzarlo per aggiornare i pesi del _SLP_ mediante la regola $$w \leftarrow w-\epsilon \nabla e(w)$$
dove $\alpha \in \mathbb{R}_+$ prende il nome di **coefficiente di apprendimento** (o _learning rate_).
Per potere applicare l'algoritmo di discesa del gradiente è necessario esprimere il gradiente di $e(w)$ in funzione di $w$ mediante il calcolo delle $n$ derivate parziali di $e(w)$. Quindi, fissato $1 \le i \le n$, quello che interessa è $$\dfrac{\partial e}{\partial w_i}(w) = \frac{1}{2} \cdot 2 \cdot \epsilon (w) \cdot \dfrac{\partial \epsilon}{\partial w_i}(w) = \epsilon(w)\cdot \dfrac{\partial \epsilon}{\partial w_i}(w_i)$$
ma  $$\dfrac{\partial \epsilon}{\partial w_i}(w) = - \dfrac{\partial o}{\partial w_i}(w)$$
perché $f(x)$ non dipende dal vettore dei pesi. Quindi, ricordando che l'uscita del _SLP_ dipende unicamente da $w$ perché $x$ è fissato, si ottiene $$\dfrac{\partial o}{\partial w_i}(w) = \dfrac{\partial g}{\partial w_i}(w\cdot x)=g'(w\cdot x)\dfrac{\partial (w\cdot x)}{\partial w_i} = g'(w \cdot x)x_i$$
perché $$\dfrac{\partial(w \cdot x)}{\partial w_i} = \sum^n_{j=i} x_j \cdot \dfrac{\partial w_j}{\partial w_i} = x_i$$
visto che è semplice constatare che $$\dfrac{\partial w_j}{\partial w_i}=\cases{1 \text{ se } i = j \\ 0 \text{ altrimenti}}$$
Quindi, in sintesi, fissato $x \in \mathbb{R}^n$ nel training set è possibile aggiornare il vettore dei pesi del _SLP_ in modo da spostare i pesi verso un minimo locale dell'errore compiuto nell'approssimazione di $f$ usando la regola $$w_i \leftarrow w_i + \alpha \cdot\epsilon(w) \cdot g'(w \cdot x) \cdot x_i = w_i + \alpha \cdot (f(x)- g(w \cdot x)) \cdot g'(w \cdot x) \cdot x_i$$
per $1 \le i \le n$ e assumendo che l'ultima componente di $x$ valga $-1$. 
Si noti che la formula di aggiornamento dei pesi di un _SLP_ è spesso espressa nell'ipotesi che la funzione di attivazione $g$ sia la funzione sigmoide $$S(x) = \dfrac{1}{1+e^{-x}}$$
perché vale la seguente proprietà della derivata della funzione sigmoide $$S'(x) = S(x) (1-S(x))$$
e quindi $$S'(w \cdot x) = S(w \cdot x) (1-S(w\cdot x))=o(w, x)(1-o(w,x))$$
che permette di aggiornare i pesi senza valutare esplicitamente la derivata della funzione di attivazione.
