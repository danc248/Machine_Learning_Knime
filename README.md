# Machine_Learning_Knime

Ciao,
breve descrizione del workflow di knime:
qui trovate il link di kaggle con la spiegazione del dataset --> https://www.kaggle.com/uciml/caravan-insurance-challenge 

l'ultima colonna CARAVAN è quella che vogliamo classificare (0 non compra la polizza assicurativa, 1 compra la polizza assicurativa)
il dataset e' "unbalanced", ci sono più di 9000 righe classificate come "0" e solo 580 circa classificate come "1"

il primo nodo prende i file csv presenti in questa cartella e li legge con uno script di R (poi ho normalizzato le variabili numeriche con un minimo pari a 0
ed un massimo pari a 1, in caso possiamo valutare se normalizzare tramite distribuzione gaussiana, mean uguale a 0 e standard deviation uguale a 1)
nel nodo 13 (most correlated attributes) ho messo in ordine le variabili più o meno correlate
mentre nel nodo "crosstab" vede il chi-quadro tra le due variabili qualitative di input perchè c'è una forte relazione tra le due variabili (ho etichettato anche la class variable come stringa o factor di R)

in alto vedete un test che ho fatto per trovare le variabili più importanti (non ho ancora usato i metodi di filter e wrapper che ha caricato il prof su elearning)

al centro vedete il test che ho fatto con i vari modelli di classificazione:
nodo partitioning --> ho usato "stratified sampling" per mantenere invariate le proporzioni della variabile CARAVAN
(in questo test ho usato one-hot encoding della variabile "customer_main_type" però sembra che knime accetti le variabili qualitative 
come input per i modelli di classifocazione, ho eliminato anche le variabili che potevano creare problemi di multi-collinearita')

all'interno del metanode "node 38 classification" ho fatto anche un test con un cost-sensitive classifier (cambiando la matrice standard di costi
come ha fatto il prof in un'esercizio del capitolo 4 se non ricordo male)

i modelli di classification tendono ad etichettare tutto come la classe più frequente, dobbiamo rivedere come hanno fatto i ragazzi che hanno
fatto il progetto sul crimine nella città di los angeles (considerando l'unbalanced dataset)
Considerate che il dataset del crimine nella città di los angeles conteneva tantissime righe quindi potevano permettersi di perdere numerose righe con equal size sampling (elimini le righe della classe più frequente, nel nostro caso la classe CARAVAN = 0 )
