#### Addestramento supervisionato

Aver esplicitato la formula per l'aggiornamento dei pesi di un _SLP_ in modo da cercare di approssimare una funzione $f$ di cui si conoscano alcuni valori permette di esplicitare l'algoritmo di addestramento supervisionato per un _SLP_. Questo algoritmo è descritto sotto e prevede di partire da un vettore dei pesi iniziale, tipicamente casuale, aggiornando questo vettore dei pesi per ogni vettore del training set. In particolare, l'algoritmo lavora su un $(n,1)$-_SLP_ e ha i seguenti parametri: 

- $T$: il training set, formato da coppie $(x, f(x))$
- $\alpha$ : il coefficiente di apprendimento
- $\delta$: la tolleranza accettata sull'errore medio
- $\rho$ : il numero massimo di epoche

L'algoritmo termina producendo un vettore di pesi in grado di approssimare la funzione di cui si conoscono alcuni valori quando:
- L'errore medio calcolato su tutto il training set è sufficientemente piccolo
- E' stato raggiunto un numero massimo di **epoche** (di apprendimento), dove un'epoca non è altro che un'interazione completa dell'algoritmo su tutto il training set

```
function slp_learn(T, alpha, delta, rho):
	randomize w
	for i <= r <= p do
		
```

