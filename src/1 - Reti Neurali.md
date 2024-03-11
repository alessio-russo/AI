## Reti Neuronali e Neurali

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

Una rete neurale (o _rete neurale artificiale_, da _Artificial Neural Network_, _ANN_) è uno strumento hardware/software in grado di simulare una rete di neuroni che funziona con gli stessi principi della rete neuronale del cervello umano, anche se, normalmente, una rete neurale è strutturalmente molto più semplice di un cervello umano. In più, le reti neurali più comuni hanno un'architettura dei collegamenti tra i neuroni progettata per uno specifico scopo. Quindi, anche se è possibile dire che una rete neurale sia un simulatore di un semplice cervello umano, le reti neurali sono progettate per specifici scopi e solo marginalmente sono pensate per riprodurre i fenomeni neurofisiologici.

Una rete neurale simula il comportamento di una rete di neuroni andando a simulare il comportamento dei singoli neuroni. Il simulatore di un neurone viene detto unità di McCulloch-Pitts. L'unità di McCulloch-Pitts non è altro che un modulo hardware/software pensato per simulare il comportamento di un neurone dal punto di vista del trasporto e dell'elaborazione delle informazioni. Infatti. un'unità di McCulloch-Pitts riceve informazioni rappresentate mediante numeri reali tramite una quantità prefissata di canali di comunicazione. Poi. l'unità elabora l'informazione ricevuta, producendo un valore numerico legato ai valori ricevuti dai canali di comunicazione. Si noti che, spesso, quando si parla di reti neurali, le unità di McCulloch-Pitts sono chiamate semplicemente neuroni.

In sostanza, un'unità di McCulloch-Pitts non è altro che una funzione reali di $n \in \mathbb{N}_+$
variabili reali, dove $n$ è noto e potenzialmente diverso per ogni neurone simulato. La funzione realizzata da un'unità di McCulloch-Pitts con $n \in \mathbb{N}_+$ ingressi è molto semplice e può essere descritta come segue $$y = g \cdot \big( \sum^{n}_{i=1} w_i x_i - w_o \big)$$ 
dove $y \in \mathbb{R}$ è il valore prodotto dall'unità a fronte degli $n$ ingressi reali $(x_i)^n_{i=i}$  utilizzando $n$ coefficienti reali  $(w_i)^n_{i=i}$  detti **pesi**, un coefficiente reale aggiuntivo $w_0$ detto **peso di bias** e una funzione $g: \mathbb{R} \rightarrow \mathbb{R}$  detta **funzione di attivazione**. Nell'ambito di una rete neurale, il risultato di un'unità di McCulloch-Pitts viene spesso utilizzato come ingresso di un'altra unità collegata alla rete. In questo modo, una rete neurale è in grado di compiere elaborazioni complesse essenzialmente legate alla struttura della rete e non alle capacità di calcolo delle unità di McCulloch-Pitts. 

Si noti che un'unità di McCulloch-Pitts viene descritta completamente dai pesi, comprensivi del peso di bias, e dalla funzione di attivazione. Normalmente, la funzione di attivazione è fissata per tutta la rete e quindi la descrizione di un'unità di McCulloch-Pitts si riduce all'enumerazione dei pesi. Quindi, spesso, si preferisce estendere gli $n$ ingressi con un ingresso aggiuntivo fissato al valore $-1$ in modo da poter descrivere un'unità di McCulloch-Pitts solo mediante un vettore dei pesi $w= (w_i)^{n+1}_{i=1}$, dove $w_{n+1}$ è il peso di bias $$y=g(x\cdot w)$$
dove $x=(x_i)^{n+1}_{i=1}$ e $x_{n+1}=-1$.


Normalmente, la funzione di attivazione di un'unità di McCulloch-Pitts non è arbitraria funzione reale di variabile reale, ma viene scelta tra una delle seguenti funzioni. La prima possibilità, che è la più semplice e la meno usata, è di scegliere come funzione di attivazione la **funzione identità** $$Id(x) = x$$ e quindi $y = x \cdot w$ . Si noti che questa scelta rende l'unità di McCulloch-Pitts una funzione lineare. 

La seconda possibilità, spesso utilizzata per la sua semplicità realizzativa, è la funzione _ReLU_ (da _Rectifier Linear Unit_) $$R(x) = \max\{0, x\}$$
e quindi $y = \max\{0, x \cdot w\}$. 

La terza possibilità, spesso utilizzata per elaborare valori binari mediante reti neurali, è la _funzione di Heaviside_ (con $H(0) = 1$) $$H(x) = \cases{1 \text{ se } x \ge 0\\0 \text{ se } x < 0}$$
La quarta possibilità, simile alla precedente, è la funzione _signum_ (o segno) $$\text{sgn}(x)= \cases{1 \text{ se } x > 0\\ 0 \text{ se } x = 0\\ -1 \text{ se } x < 0}$$
La quinta possibilità, che è la più frequente perché è non lineare e derivabile ovunque, è la _funzione logistica_ (o _funzione sigmoide_) $$S(x) = \dfrac{1}{1+e^{-x}}$$

![[ReLU-vs-logistic-Sigmoid.png|600]]


Si noti che esistono tante altre funzioni di attivazioni utilizzate per applicazioni reali, ma quelle elencate sono quelle più comunemente utilizzate.

Una rete neurale è quindi un grafo orientato pesato i cui nodi sono unità di McCulloch-Pitts e, per ogni unità, i pesi sugli archi sono i pesi in ingresso dell'unità, comprensivi del peso di bias associato ad un ingresso aggiuntivo fissato a $-1$. Normalmente, non si ammettono autoanelli (collegamenti tra l'uscita dell'unità McCulloch-Pitts e l'ingresso della stessa unità) in una rete neurale, in modo da non dover tenere conto dei ritardi introdotti dalle singole unità di McCulloch-Pitts. In generale, per una rete neurale non è possibile identificare quale sia l'ingresso e quale sia l'uscita di una singola unità di McCulloch-Pitts perché il grafo è orientato. Si noti che è sempre possibile ipotizzare che una rete neurale sia un grafo completamente connesso, eventualmente utilizzando dei pesi nulli per indicare l'assenza di archi tra unità di McCulloch-Pitts.

Data una rete neurale con $n \in \mathbb{N}_+$ neuroni, fissato un qualsiasi istante $t \in \mathbb{R}_{\ge 0}$ , il vettore $s(t) \in \mathbb{R}^n$ formato dalle uscite correnti dei neuroni viene detto _stato della rete_ all'istante $t$. 
Lo stato della rete evolve dinamicamente partendo da uno stato iniziale $s(0)$ che, tipicamente, si assume noto. In generale, però, non è detto che una rete neurale raggiunga uno stato finale.