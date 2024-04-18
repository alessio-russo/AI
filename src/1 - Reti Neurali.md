
## Reti Neuronali

Per la neurofisiologia, un cervello è un organo formato da cellule tra loro connesse che prendono il nome di **neuroni**. Nel suo complesso, quindi, un cervello è una **rete neuronale**.
Nel caso specifico del cervello umano, normalmente si ritiene che:

- Un numero di neuroni stimato nell'ordine di $10^{11}$
- Più di 20 differenti tipi di neuroni, ognuno dei quali svolge funzioni specifiche
- Un numero di connessioni sinaptiche tra i neuroni, che si aggira intorno a $10^{14}$

Quindi, la rete neuronale che forma un cervello umano è caratterizzata da un **enorme numero di neuroni**, per lo più **omogenei** tra loro, connessi da un **numero relativamente basso di sinapsi** ( ogni neurone in media è collegato a circa mille altri). Queste connessioni permettono di trasportare le informazioni attraverso la rete, permettendo a ogni neurone di **ricevere** e **inviare** dati a un limitato numero di neuroni, con un tempo di reazione di circa 1 millisecondo (lento se paragonato alle prestazioni di un calcolatore).

![[Neurone.png|600]]

La figura mostra una schematizzazione delle parti principali di un neurone:

- Il **soma**, il corpo centrale del neurone, che contiene il **nucleo** e le principali componenti cellulari

- I **dendridi**, che sono i collegamenti in grado di veicolare informazioni mediante il movimento di ioni (cariche elettriche)

- Le **sinapsi**, che sono i punti di interfaccia tra diversi neuroni e si trovano nelle parti terminali delle arborizzazioni dell’assone di ogni neurone.

Il trasporto di informazioni, e quindi la comunicazione, tra i neuroni avviene mediante l'interazione tra dendridi e sinapsi di diversi neuroni. Quindi, ogni neurone ha una struttura semplice in grado di elaborare le informazioni veicolate dal trasporto di ioni mediante dendridi e sinapsi.

## Reti Neurali

Le **reti neurali artificiali** (ANN), o semplicemente **reti neurali**, rappresentano una fusione avanzata di hardware (in passato) e software progettata per emulare la complessa rete di neuroni presente nel cervello umano. Benché queste strutture artificiali condividano alcuni principi fondamentali con le reti neuronali biologiche, le reti neurali artificiali tendono ad essere molto più semplificate rispetto al cervello umano. Un aspetto distintivo delle reti neurali artificiali è che la loro architettura di collegamento tra i neuroni è spesso sviluppata con uno scopo ben preciso in mente. Questo le rende strumenti specializzati, configurati per affrontare compiti specifici, piuttosto che tentare di replicare fedelmente tutte le funzionalità del cervello umano.

Le reti neurali artificiali funzionano simulando le dinamiche di una rete neuronale, mimando il comportamento dei neuroni a un livello base. A tal fine, utilizzano moduli noti come unità di McCulloch-Pitts, che agiscono come neuroni artificiali. Ogni unità di McCulloch-Pitts è un componente hardware (in passato) o software calibrato per imitare le funzioni di un neurone dal punto di vista del ricevimento, elaborazione e trasmissione dell'informazione. Queste unità accettano segnali d'input, rappresentati da numeri reali, attraverso canali di comunicazione predefiniti. In seguito, elaborano queste informazioni e generano un output numerico che dipende dai valori in ingresso.

Nel linguaggio comune legato alle reti neurali, le unità di McCulloch-Pitts sono spesso denominate più semplicemente "neuroni".

In termini matematici, un'unità di McCulloch-Pitts è una funzione di $n \in \mathbb{N}_+$ variabili reali, dove $n$ indica il numero di input al neurone, e può variare per ogni neurone simulato nella rete. La funzione svolta da questa unità, data un certo numero di ingressi, è formalizzata attraverso la seguente espressione matematica:
$$y = g \left( \sum^{n}_{i=1} w_i x_i - w_0 \right)$$
In questa formula, $y \in \mathbb{R}$ rappresenta l'output dell'unità di McCulloch-Pitts, basato sugli $n$ input reali $(x_i)^n_{i=1}$ e un insieme corrispondente di $n$ coefficienti reali $(w_i)^n_{i=1}$ denominati **pesi**. Vi è inoltre un coefficiente reale addizionale, $w_0$, conosciuto come **peso di bias**, che aiuta a regolare l'attivazione dell'unità. La **funzione di attivazione** $g: \mathbb{R} \rightarrow \mathbb{R}$ è cruciale per determinare l'output dell'unità in base al risultato della combinazione lineare pesata degli ingressi e del bias.

Questa struttura consente alla rete neurale di effettuare elaborazioni complesse, che dipendono più dall'interconnessione tra le unità che dalle singole capacità computazionali di ciascuna unità di McCulloch-Pitts. È importante notare che l'identità di un'unità di McCulloch-Pitts è definita dai suoi pesi, inclusi quelli di bias, e dalla sua funzione di attivazione. Comunemente, per semplificare, la funzione di attivazione è standardizzata in tutta la rete, facendo sì che la caratterizzazione di un'unità di McCulloch-Pitts si concentri sulla configurazione dei suoi pesi.

Per ulteriore semplificazione, è frequente estendere gli $n$ input con un ingresso aggiuntivo impostato a $-1$, consentendo di descrivere un'unità di McCulloch-Pitts esclusivamente tramite un vettore di pesi $w= (w_i)^{n+1}_{i=1}$, con $w_{n+1}$ rappresentante il peso di bias. Di conseguenza, l'output dell'unità può essere espresso come:
$$y=g(x\cdot w)$$
dove $x=(x_i)^{n+1}_{i=1}$ e $x_{n+1}=-1$. 

Le funzioni di attivazione rivestono un ruolo cruciale nel definire il comportamento e le capacità di apprendimento delle unità di McCulloch-Pitts all'interno delle reti neurali artificiali. Queste funzioni determinano come l'input ricevuto da un neurone viene trasformato in un output, influenzando direttamente la capacità della rete di gestire problemi non lineari e la sua efficacia nell'apprendimento. Vediamo nello specifico le funzioni di attivazione più comuni:

 **Funzione Identità**:
   $$Id(x) = x$$
La scelta della funzione identità come funzione di attivazione rende l'unità di McCulloch-Pitts essenzialmente lineare, dove l'output è direttamente proporzionale all'input. Sebbene questa semplicità possa avere vantaggi in termini di calcolo, limita la capacità della rete di modellare relazioni complesse non lineari.

**ReLU (Rectified Linear Unit)**:
   $$R(x) = \max\{0, x\}$$
La funzione ReLU è ampiamente utilizzata per la sua efficacia nell'accelerare la convergenza dell'algoritmo di apprendimento. La sua semplicità computazionale la rende una scelta popolare per molte architetture di reti neurali.

**Funzione di Heaviside**:
   $$H(x) = \begin{cases}1 & \text{se } x \ge 0\\0 & \text{se } x < 0\end{cases}$$
La funzione di Heaviside è utile per applicazioni che richiedono output binari. È un tipo di funzione di attivazione "step", che fornisce un cambio netto da 0 a 1. È particolarmente utile per classificazioni binarie.

**Funzione Signum**:
   $$\text{sgn}(x) = \begin{cases}1 & \text{se } x > 0\\0 & \text{se } x = 0\\-1 & \text{se } x < 0\end{cases}$$
La funzione signum estende la funzione di Heaviside introducendo la possibilità di un output negativo, offrendo una rappresentazione più ricca di relazioni binarie e ternarie.

**Funzione Logistica (Sigmoide)**:
   $$S(x) = \frac{1}{1+e^{-x}}$$

La funzione sigmoide è stata una delle prime funzioni di attivazione non lineari utilizzate in reti neurali per la sua capacità di mappare input arbitrari in un intervallo $(0,1)$, rendendola adatta per probabilità e classificazioni. La sua natura non lineare e derivabile ovunque permette una maggiore flessibilità nel modellare relazioni complesse.

![[ReLU-vs-logistic-Sigmoid.png|600]]


Esistono poi molte altre funzioni di attivazione utilizzate nelle reti neurali per specifiche applicazioni, ognuna con i propri vantaggi e contesti d'uso ideali.

Una rete neurale può essere efficacemente descritta come un grafo orientato pesato, dove ciascun nodo rappresenta un'unità di McCulloch-Pitts, ovvero un neurone artificiale. I collegamenti tra questi nodi, o neuroni, sono rappresentati dagli archi del grafo, con i pesi su questi archi che corrispondono ai pesi di input di ciascuna unità, inclusi i pesi di bias. Quest'ultimo è associato a un input supplementare, tipicamente fissato a $-1$, per semplificare la rappresentazione matematica delle interazioni tra i neuroni.

Per mantenere la struttura della rete neurale semplificata e gestibile, di solito si evitano i collegamenti ricorsivi o autoanelli, dove l'output di un'unità potrebbe servire come uno dei suoi stessi input. Questa restrizione aiuta a prevenire complicazioni legate alla gestione dei tempi di ritardo che tali feedback potrebbero introdurre, garantendo che il flusso di informazioni attraverso la rete sia unidirezionale e senza auto-riferimenti.

La concezione di una rete neurale come un grafo completamente connesso, dove l'assenza di un collegamento diretto tra due neuroni è semplicemente indicata da un peso nullo, facilita la comprensione della struttura e della dinamica della rete. In questo modello, ogni neurone può potenzialmente comunicare con ogni altro neurone, direttamente o indirettamente, a seconda della configurazione dei pesi.

Ogni **stato della rete** neurale in un dato istante di tempo $t$, rappresentato dal vettore $s(t)$ che contiene gli output correnti di tutti i neuroni, riflette l'insieme delle informazioni processate dalla rete fino a quel momento. Questo stato evolverà dinamicamente nel tempo a partire da uno stato iniziale $s(0)$, solitamente noto o definito dall'utente. Tuttavia, non è garantito che la rete neurale converga verso uno stato finale stabile, poiché la sua evoluzione dipende fortemente dalla struttura della rete, dai valori dei pesi, dalle funzioni di attivazione utilizzate e dalle condizioni iniziali.

La standardizzazione della funzione di attivazione per tutte le unità di McCulloch-Pitts semplifica notevolmente la struttura e l'analisi della rete. Se ogni neurone artificiale adotta la stessa funzione di attivazione, la descrizione completa della rete si focalizza primariamente sulla configurazione dei pesi associati ai collegamenti tra i neuroni. In pratica, ciò significa che il comportamento complessivo della rete può essere interamente definito e modificato attraverso l'aggiustamento di questi pesi, rendendo il processo di "apprendimento" della rete una questione di ottimizzazione dei pesi stessi in funzione dell'output desiderato.

La realizzazione di funzioni dello stato della rete diventa possibile grazie a questo schema organizzativo. Le reti neurali sono concepite per avere unità di input, che ricevono dati dall'esterno, e unità di output, le cui elaborazioni vengono rese disponibili al mondo esterno. Le unità di input sono configurate per accogliere i segnali esterni e iniziare il processo di elaborazione, trasmettendo l'informazione attraverso la rete mediante i loro collegamenti ponderati. Allo stesso modo, le unità di output fungono da terminali attraverso cui la rete comunica i risultati del suo processo elaborativo.

La capacità di una rete di eseguire specifici compiti dipende non solo dalla scelta dei pesi ma anche dalla sua architettura, ovvero dal modo in cui i neuroni sono organizzati e interconnessi.

#### Apprendimento Automatico

Il processo di apprendimento in una rete neurale artificiale rappresenta un pilastro fondamentale per il suo sviluppo e la sua efficacia. Sebbene teoricamente sia possibile progettare una rete neurale assegnando manualmente i pesi a ogni collegamento in modo da ottenere un comportamento specifico, questa pratica è impraticabile a causa dell'enorme numero di connessioni presenti anche nelle reti di dimensioni moderate. Ogni connessione, o arco, tra unità di McCulloch-Pitts ha un peso che influisce sul modo in cui le informazioni vengono elaborate e trasferite attraverso la rete. Man mano che la complessità della rete cresce, il numero di questi pesi diventa rapidamente vasto, rendendo la loro configurazione manuale un compito estremamente complesso e poco efficiente.

Per superare questa sfida, si fa affidamento all'**apprendimento automatico**, un metodo attraverso il quale i pesi della rete sono adattati e ottimizzati basandosi su un insieme di dati noto come **training set**. Il training set consiste in esempi che la rete utilizza per imparare, contenendo input specifici e gli output desiderati corrispondenti. Durante il processo di addestramento, la rete elabora questi esempi e aggiusta i pesi dei suoi collegamenti in modo da minimizzare la differenza tra l'output prodotto dalla rete e quello desiderato indicato nel training set.

Questo processo di addestramento si basa su algoritmi di ottimizzazione, come la discesa gradiente e sue varianti, che modificano iterativamente i pesi della rete per ridurre un'indicazione quantitativa dell'errore, nota come funzione di costo o funzione di perdita. Attraverso ripetute iterazioni su questo set di dati, la rete "impara" a riconoscere pattern e relazioni tra gli input e gli output, ottimizzando i suoi pesi per eseguire il compito per cui è stata addestrata con maggiore precisione.

L'apprendimento può avvenire in diversi modi:

**Addestramento Supervisionato (Supervised Learning)**

Nell'addestramento supervisionato, la rete neurale viene addestrata su un insieme di dati etichettato, che include esempi di input con i corrispondenti output attesi. Questo approccio è particolarmente utile per compiti di classificazione e regressione, dove l'obiettivo è prevedere l'output corretto a partire da un nuovo input basandosi sull'apprendimento da esempi precedenti. L'addestramento supervisionato consente alla rete di imparare valutando le sue prestazioni attraverso una funzione di perdita, che misura la differenza tra l'output previsto dalla rete e l'output reale (atteso) fornito nel training set. L'obiettivo dell'addestramento è minimizzare questa funzione di perdita, ottimizzando i pesi attraverso tecniche quali la discesa del gradiente.

**Addestramento Non Supervisionato (Unsupervised Learning)**

L'addestramento non supervisionato non si basa su esempi etichettati. Invece, la rete è fornita di un insieme di dati senza output specificati e deve trovare da sola struttura o pattern nei dati. Questo tipo di addestramento è utile per scoprire raggruppamenti nascosti (cluster), ridurre la dimensionalità o per la generazione di nuovi dati che siano coerenti con quelli osservati. In questo caso, la rete cerca di organizzare o rappresentare i dati in un modo che rifletta le loro caratteristiche intrinseche, spesso attraverso la minimizzazione di una funzione di perdita che, ad esempio, misura la distanza tra i punti dati e i loro rappresentanti (centroidi, nel caso dei problemi di clustering)

**Addestramento per Rinforzo (Reinforcement Learning)**

L'addestramento per rinforzo è un paradigma di apprendimento in cui la rete (o agente) impara a prendere decisioni ottimizzando le ricompense accumulate nel tempo. Questo approccio è diverso dall'apprendimento supervisionato e non supervisionato in quanto non si basa su un set di esempi con output noti, ma piuttosto su un processo di interazione con un ambiente dal quale l'agente riceve feedback sotto forma di ricompense o punizioni. L'obiettivo è apprendere una politica, ossia una mappatura da stati (o percezioni) a azioni, che massimizzi la somma delle ricompense future. Questo tipo di addestramento è particolarmente adatto per compiti che richiedono la pianificazione di una sequenza di azioni, come nei giochi, nella navigazione di robot o in qualsiasi contesto dove le decisioni attuali influenzano gli esiti futuri.



L'addestramento di una rete neurale è cruciale per insegnarle a compiere determinati compiti, ma la vera misura della sua efficacia è la capacità di **generalizzare**, ovvero di applicare ciò che ha imparato a nuovi dati mai visti durante la fase di addestramento. Questa capacità è valutata attraverso l'uso di un **test set**, un insieme di esempi che la rete non ha mai incontrato durante l'addestramento. È fondamentale che training set e test set siano disgiunti per assicurare una valutazione onesta delle prestazioni della rete. Se una rete neurale mostra buone prestazioni sia sul training set che sul test set, si dice che ha **generalizzato** bene il problema.

La distinzione tra training set e test set riflette un principio fondamentale nel campo del machine learning: l'abilità di un modello di generalizzare da un insieme limitato di dati a un contesto più ampio è più importante della sua capacità di memorizzare i dati su cui è stato addestrato. Questa capacità di generalizzazione distingue i modelli che hanno imparato pattern genuini e utili dai modelli che hanno semplicemente memorizzato i dati di addestramento, un fenomeno noto come **overfitting**, dove il modello performa bene sui dati di addestramento ma poveramente su dati nuovi o non visti.

Il concetto di machine learning si basa su questo processo di apprendimento e adattamento, piuttosto che sulla programmazione esplicita delle regole che il modello deve seguire. Nel contesto dell'**intelligenza artificiale subsimbolica**, i modelli apprendono e operano su rappresentazioni numeriche dei dati, piuttosto che su simboli o regole esplicite. 