
Una rete neurale **feed-forward** (in avanti) è un modello computazionale avanzato, che si struttura come un grafo orientato aciclico con pesi. Questo modello è organizzato in diversi strati o livelli, dove ogni nodo rappresenta un'unità di McCulloch-Pitts. 

Questa struttura possiede le seguenti caratteristiche:

- Gli strati all'interno della rete sono numerati, per facilitare la loro identificazione e manipolazione

- Ogni nodo è assegnato a un unico strato, garantendo una chiara demarcazione tra i diversi livelli di elaborazione

- I nodi situati nel primo strato si distinguono per l'assenza di connessioni entranti. Il loro input, o segnale di attivazione, deriva direttamente da fonti esterne, sottolineando il loro ruolo come punto di ingresso per l'elaborazione dei dati

- Per ogni nodo, ad eccezione di quelli nel primo strato, esistono connessioni entranti esclusivamente dai nodi dello strato immediatamente precedente. Questo meccanismo garantisce un flusso ordinato e unidirezionale delle informazioni attraverso la rete

- L'ultimo strato della rete si caratterizza per l'assenza di connessioni uscenti. I nodi in questo strato finalizzano il processo di elaborazione, e i loro output vengono trasmessi verso destinazioni esterne alla rete

- I pesi associati a ciascuna connessione rappresentano l'importanza relativa dei segnali in arrivo alle unità di McCulloch-Pitts. Questi pesi sono fondamentali per la modulazione dell'input e per l'addestramento della rete nel riconoscere pattern complessi

- Inoltre, ciascuno strato della rete include un valore di bias fissato a -1, che contribuisce alla regolazione dell'attivazione dei nodi. Questo valore di bias non riceve connessioni entranti


![[mlp.png|500]]


In assenza di indicazioni specifiche, si presume che una rete neurale feed-forward sia configurata per ospitare il numero massimo possibile di connessioni, rispettando al contempo la sua caratteristica struttura stratificata. Questo approccio assicura che ogni nodo (esclusi quelli del primo e dell'ultimo strato) sia pienamente interconnesso con i nodi dello strato precedente, massimizzando le potenzialità di elaborazione e apprendimento della rete.

Gli strati intermedi, situati tra l'ingresso e l'uscita, sono comunemente definiti come strati nascosti. Questi strati svolgono funzioni di elaborazione interna cruciale, manipolando e trasformando l'input ricevuto in modo da estrarre caratteristiche e pattern rilevanti non immediatamente evidenti all'ingresso o all'uscita.

La denominazione "perceptron" o "percettrone" è spesso applicata alle reti neurali feed forward, in particolare quando si riferisce a modelli di rete più semplici con un singolo strato o con pochi strati.

Al contrario, quando la struttura di una rete neurale non segue una disposizione stratificata e presenta connessioni che possono formare cicli, si parla di rete neurale ricorrente. Le reti neurali ricorrenti sono specializzate nella gestione di sequenze di dati e nella memorizzazione di informazioni sullo stato precedente, il che le rende particolarmente adatte per applicazioni come il riconoscimento del linguaggio naturale e la modellazione di serie temporali.

#### Single Layer Perceptron

Il **Single Layer Perceptron** (SLP) rappresenta la forma più basilare di rete neurale feed-forward, che si distingue per la sua struttura semplificata ma efficace nell'eseguire specifici compiti di classificazione e approssimazione. Un SLP è costituito da un singolo strato di nodi di output, senza la presenza di strati nascosti, e viene utilizzato per mappare ingressi reali a uscite reali attraverso una funzione di attivazione. Questa configurazione gli consente di funzionare come un approssimatore di funzione per trasformare input $\mathbb{R}^n$ in output $\mathbb{R}^m$, dove $n$ e $m$ rappresentano rispettivamente il numero di ingressi e il numero di uscite del sistema.

L'uso della notazione $(n, m)$-_SLP_ serve a specificare in modo chiaro le dimensioni dell'input e dell'output del perceptron, evidenziando la sua capacità di trattare vettori di ingresso di dimensione $n$ e di produrre vettori di uscita di dimensione $m$. La funzione di attivazione $g : \mathbb{R} \rightarrow \mathbb{R}$, tipicamente non lineare, è fondamentale per permettere al SLP di apprendere e modellare relazioni complesse tra l'input e l'output.

Per addestrare un SLP, si utilizza un approccio di apprendimento supervisionato, che implica la disponibilità di un training set contenente esempi di input associati ai rispettivi output desiderati. Questi esempi servono per guidare il processo di ottimizzazione dei pesi della rete, affinché la funzione approssimata dal perceptron si avvicini il più possibile alla funzione reale che si vuole modellare. L'obiettivo è trovare il set di pesi che minimizza l'errore tra le uscite calcolate dalla rete e le uscite attese per gli esempi nel training set.

Il SLP, con la sua struttura lineare e senza strati nascosti, mostra eccellenti capacità nell'approssimare funzioni lineari o funzioni non complesse. Tuttavia, la sua semplicità può limitare la sua applicabilità a problemi che richiedono la modellazione di relazioni altamente non lineari o complesse, per i quali sono generalmente preferite reti neurali con architetture più sofisticate, includendo una o più serie di strati nascosti.