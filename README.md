# Machine_Learning_Knime

Ciao,
breve descrizione del workflow di knime:
qui trovate il link di kaggle con la spiegazione del dataset --> https://www.kaggle.com/uciml/caravan-insurance-challenge 

l'ultima colonna CARAVAN è quella che vogliamo classificare (0 non compra la polizza assicurativa, 1 compra la polizza assicurativa)
il dataset e' "unbalanced", ci sono più di 9000 righe classificate come "0" e solo 580 circa classificate come "1"

il primo nodo prende i file csv presenti in questa cartella e li legge con uno script di R (dobbiamo decidere se dobbiamo normalizzare i dati, magari trasformando la legenda presente su kaggle nei dati originali e poi usando il nodo "normalizer")
nel nodo 13 (most correlated attributes) ho messo in ordine le variabili più o meno correlate
mentre nel nodo "crosstab" vede il chi-quadro tra le due variabili qualitative di input perchè c'è una forte relazione tra le due variabili (ho etichettato anche la class variable come stringa o factor di R)

in alto vedete un test che ho fatto per trovare le variabili più importanti (possiamo anche cancellare quel gruppo di nodi, stessa cosa per il nodo #70 "r-smote")

al centro vedete il test che ho fatto con i vari modelli di classificazione:
nodo partitioning --> ho usato "stratified sampling" per mantenere invariate le proporzioni della variabile CARAVAN
(in questo test ho usato one-hot encoding della variabile "customer_main_type" però sembra che knime accetti le variabili qualitative 
come input per i modelli di classifocazione, ho eliminato anche le variabili che potevano creare problemi di multi-collinearita')


