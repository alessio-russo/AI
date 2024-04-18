## Reti Neurali

**Reti Neuronali** 

Per la neurofisiologia, un cervello è un organo formato da cellule tra loro connesse che prendono il nome di neuroni. Nel suo complesso, quindi, un cervello è una **rete neuronale**.
Nel caso specifico del cervello umano, normalmente si ritiene che:

- Ogni cervello contenga un numero di neuroni nell'ordine di $10^{11}$
- Ogni cervello contenga poco più di 20 tipi di neuroni 
- Ogni cervello contenga un numero di collegamenti tra neuroni dell'ordine di $10^{14}$

Quindi, la rete neuronale che forma un cervello umano è caratterizzata da un numero enorme di neuroni, quasi tutti uguali tra loro, tra loro collegati mediante un numero relativamente basso di connessioni (in media ogni neurone è collegato a mille altri neuroni). Le connessioni consentono di trasportare **informazioni** attraverso la rete, e ogni neurone _riceve_ e _invia_ informazioni _da_ e _per_ pochi altri neuroni, con un tempo di reazione dell'ordine di 1 ms (quindi, abbastanza lentamente).

![[Neurone.png|600]]

La figura mostra una schematizzazione delle parti principali di un neurone:

- Il **soma** è la struttura cellulare che racchiude il **nucleo** di un neurone
- I **dendridi** sono collegamenti in grado di veicolare informazioni mediante il movimento di ioni (cariche elettriche)
- Le **sinapsi** sono punti di interfaccia tra diversi neuroni, che si trovano nelle parti terminali delle **arborizzazioni** dell'**assone** di ogni neurone

Il trasporto di informazioni, e quindi la comunicazione, tra i neuroni avviene mediante l'interazione tra dendridi e sinapsi di diversi neuroni. Quindi, ogni neurone ha una struttura abbastanza semplice in grado di elaborare le informazioni veicolate dal trasporto di ioni mediante dendridi e sinapsi.

**Reti neurali**

Una rete neurale (o _rete neurale artificiale_, da _Artificial Neural Network_, _ANN_) è uno strumento software in grado di simulare una rete di neuroni che funziona seguendo gli stessi principi della rete neuronale del cervello umano. In generale però:

- Una rete neurale è strutturalmente molto più semplice di una rete neuronale
- I collegamenti tra i neuroni delle reti neurali hanno spesso un'architettura studiata per svolgere un compito specifico

Quindi, sebbene sia possibile dire che una rete neurale è un "simulatore" di un semplice cervello umano, le reti neurali sono progettate per specifici scopi e solo marginalmente sono pensate per riprodurre i fenomeni neurofisiologici.

**Le unità di McCulloch-Pitts**

In particolare, una rete neurale simula il comportamento di una rete neuronale andando a simulare il comportamento dei singoli neuroni. Il simulatore di un neurone viene detto **unità di McCulloch-Pitts**. 

L'unità di McCulloch-Pitts non è altro che un modulo software pensato per simulare il comportamento di un neurone dal punto di vista del trasporto e dell'elaborazione delle informazioni. Infatti, un'unità di McCulloch-Pitts riceve informazioni sotto forma di numeri reali, attraverso una quantità prefissata di canali di comunicazione. Successivamente, l'unità elabora le informazioni ricevute, producendo a sua volta un valore numerico, legato ai valori ricevuti dai canali di comunicazione. 

**Nota.** Spesso le unità di McCulloch-Pitts sono chiamate semplicemente **neuroni**.

In sostanza, un'unità di McCulloch-Pitts non è altro che una funzione reale di $n \in \mathbb{N}_+$
variabili reali, dove $n$ è noto e potenzialmente diverso per ogni neurone simulato. La funzione realizzata da un'unità di McCulloch-Pitts con $n \in \mathbb{N}_+$ ingressi è molto semplice e può essere descritta come segue $$y = g \big( \sum^{n}_{i=1} w_i x_i - w_o \big)$$ 
dove $y \in \mathbb{R}$ è il valore prodotto dall'unità a fronte degli $n$ ingressi reali $(x_i)^n_{i=1}$  utilizzando $n$ coefficienti reali  $(w_i)^n_{i=1}$  detti **pesi**, un coefficiente reale aggiuntivo $w_0$ detto **peso di bias** e una funzione $g: \mathbb{R} \rightarrow \mathbb{R}$  detta **funzione di attivazione**. 

Nell'ambito di una rete neurale, il risultato di un'unità di McCulloch-Pitts viene spesso utilizzato come ingresso di un'altra unità collegata alla rete. n questo modo, una rete neurale è in grado di compiere elaborazioni complesse, legate alla struttura della rete e non alle capacità di calcolo delle singole unità di McCulloch-Pitts.

Un'unità di McCulloch-Pitts viene descritta completamente dai pesi, comprensivi del peso di bias, e dalla funzione di attivazione. Tuttavia, poiché spesso la funzione di attivazione è fissata per tutta la rete, la descrizione di un'unità di McCulloch-Pitts si riduce all'enumerazione dei pesi. 
Quindi, spesso, si preferisce estendere gli $n$ ingressi con un ingresso aggiuntivo fissato al valore $-1$, in modo da poter descrivere un'unità di McCulloch-Pitts solo mediante un vettore dei pesi $w= (w_i)^{n+1}_{i=1}$, dove $w_{n+1}$ è il **peso di bias**.

Noto $w$, l’elaborazione dell’unità è espressa da $y=g(x\cdot w)$, con $x=(x_i)^{n+1}_{i=1}$ e $x_{n+1}=-1$.

**Funzioni di attivazione**

Normalmente, la funzione di attivazione di un’unità di McCulloch-Pitts non è un’arbitraria funzione reale di variabile reale, ma viene scelta tra una delle seguenti funzioni di uso comune. La prima possibilità, che è la più semplice e la meno usata, è di scegliere come funzione di attivazione la **funzione identità** 
$$Id(x) = x$$
e quindi $y = x \cdot w$ . Si noti che questa scelta rende l'unità di McCulloch-Pitts una funzione lineare.  La seconda possibilità, spesso utilizzata per la sua semplicità realizzativa, è la **funzione ReLU** (da _Rectifier Linear Unit_) 
$$R(x) = \max\{0, x\}$$
e quindi $y = \max\{0, x \cdot w\}$. La terza possibilità, spesso utilizzata per elaborare valori binari mediante reti neurali, è la **funzione di Heaviside** (con $H(0) = 1$) 
$$H(x) = \cases{1 \text{ se } x \ge 0\\0 \text{ se } x < 0}$$
La quarta possibilità, simile alla precedente, è la funzione **signum** (o segno)
$$\text{sgn}(x)= \cases{1 \text{ se } x > 0\\ 0 \text{ se } x = 0\\ -1 \text{ se } x < 0}$$
La quinta possibilità, che è la più frequente perché è non lineare e derivabile ovunque, è la _funzione logistica_ (o **funzione sigmoide**)
$$S(x) = \dfrac{1}{1+e^{-x}}$$

![[ReLU-vs-logistic-Sigmoid.png|400]]


**Nota.** Esistono tante altre funzioni di attivazioni utilizzate per applicazioni reali, ma quelle elencate sono quelle più comunemente utilizzate.

Una rete neurale è quindi un grafo orientato pesato i cui nodi sono unità di McCulloch- Pitts e, per ogni unità, i pesi sugli archi sono i pesi in ingresso all’unità, comprensivi del peso di bias, associato ad un ingresso aggiuntivo fissato a −1. Normalmente, non si ammettono autoanelli (collegamenti tra l'uscita dell'unità McCulloch-Pitts e l'ingresso della stessa unità) in una rete neurale, in modo da non dover tenere conto dei ritardi introdotti dalle singole unità di McCulloch-Pitts. 

 In generale, se si osserva il grafo che rappresenta la rete neurale, non è possibile identificare quale sia l’ingresso e quale sia l’uscita della rete, anche se è sempre possibile identificare quale sia l’ingresso e quale sia l’uscita della singola unità di McCulloch-Pitts, perché il grafo è orientato. 
 
 **Nota.** E' sempre possibile ipotizzare che una rete neurale sia un grafo completamente connesso, eventualmente utilizzando dei pesi nulli per indicare l’assenza di archi tra unità di McCulloch-Pitts.

Data una rete neurale con $n \in \mathbb{N}_+$ neuroni, fissato un qualsiasi istante $t \in \mathbb{R}_{\ge 0}$ , il vettore $s(t) \in \mathbb{R}^n$ formato dalle uscite correnti dei neuroni viene detto **stato della rete** all'istante $t$. 
Lo stato della rete evolve dinamicamente partendo da uno stato iniziale $s(0)$ che, tipicamente, si assume noto. In generale, però, non è detto che una rete neurale raggiunga uno stato finale.

giunga uno stato finale. Siccome, spesso, le unità di McCulloch-Pitts utilizzate in una rete neurale sono tutte caratterizzate dalla stessa funzione di attivazione, la descrizione della rete si riduce al- l’enumerazione di tutti i pesi associati agli archi del grafo completamente connesso che descrive la rete. Quindi, senza perdere di generalità, pur nell’ipotesi che tutte le unità di McCulloch-Pitts utilizzino la stessa funzione di attivazione, è possibile dire che una rete neurale viene descritta completamente una volta che siano noti i pesi associati agli archi che collegano le unità della rete. 

Inoltre, si noti che, una volta identificati i pesi adeguati, **è** anche **possibile utilizzare una rete** neurale **per realizzare funzioni** dello stato della rete. In questi casi, si ipotizza che **esistano** delle **unità di McCulloch-Pitts** che possano **ricevere valori** da elaborare **dall’esterno**. Coerentemente, si ipotizza che esistano delle **unità di McCulloch-Pitts** i cui **risultati** vengano resi disponibili **verso l’esterno**.

---

**Esempio.** 

Un'unità di McCulloch-Pitts che utilizza la funzione di Heaviside come funzione di attivazione può essere utilizzata per realizzare le funzioni dell'algebra di Boole sull'insieme $\{0,1\}$. Come mostrato nella figura seguente, se la funzione da realizzare ha $n \in \mathbb{N}_+$ ingressi, allora l'unità avrà $n$ ingressi collegati con l'esterno, un ingresso fissato a $-1$ per il peso di bias, e un'uscita collegata con l'esterno.

![[and-or-not.png|450]]

Naturalmente, i pesi indicati in figura non sono gli unici possibili. In generale, se la funzione da realizzare deve associare un ingresso $x = (x_i)^3_{i=1}$ , con $x_3 = -1$ , al valore $1$, allora sarà sufficiente trovare un vettore dei pesi $w = (w_i)^3_{i=1}$ tale che $w \cdot x \ge 0$ . In modo simile, se l'uscita deve valere $0$, allora dovrà essere $w \cdot x < 0$. 

---

Da questo punto di vista, è quindi possibile costruire una rete che abbia un comportamento desiderato andando ad associare un peso adeguato ad ogni arco. Questo approccio, però, pur essendo idealmente percorribile, non è praticabile perché il numero di archi con peso non nullo è normalmente molto elevato. Quindi, per la costruzione di una rete, si ricorre spesso all'**apprendimento**, che prevede che i pesi della rete vengano ottenuti partendo dalle caratteristiche di alcuni esempi. Si dice, quindi, che una rete viene **addestrata** fornendole degli esempi che vengono raccolti in un **training set**.

Si noti che, in base alle caratteristiche degli esempi forniti per l'addestramento, si può parlare di due tipologie principali di addestramento:

- Addestramento **supervisionato**: in cui viene fornito un insieme di esempi e, per ogni esempio, viene anche detto qual'è l'uscita attesa per alcune unità di McCulloch-Pitts della rete che rivestono un particolare interesse

- Addestramento **non supervisionato**: in cui viene fornito un insieme di esempi e, sfruttandone le caratteristiche, si cerca di ottenere un insieme di pesi adeguato.

L'addestramento consente di ottenere un insieme adeguato di pesi in grado di garantire che la rete si comporti bene nei casi d'esempio. Però, per valutare quanto bene la rete si comporti in situazioni non presenti negli esempi forniti, le prestazione di una rete vengono sempre valutate utilizzando un secondo insieme di esempi detto **test set**. Training set e test set devono essere disgiunti ed è possibile dire che una rete **generalizza** se ha un comportamento adeguato anche per gli esempi del test set.

Quindi, come spesso si dice, una rete neurale non viene programmata ma viene addestrata ad avere dei comportamenti. Il **machine learning** (o apprendimento automatico) è quella disciplina che si occupa di studiare questo approccio alla sintesi dei sistemi di calcolo, sia per reti neurali che per altri tipi di sistemi di calcolo. Quando le informazioni imparate mediante le tecniche del machine learning sono di tipo numerico, o riconducibili a tali, allora si parla di intelligenza artificiale subsimbolica.


