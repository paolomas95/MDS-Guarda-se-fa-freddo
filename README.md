<h1> Guarda se fa freddo  :earth_africa: 🐻‍❄️ 🔥</h1>

> Paolo Masella, Luca Merlini, Gloria Tuccillo
***
 Il progetto è stato suddiviso in quattro parti principali:
1. **<h3>Aggiornamento del dataset :battery:</h3>**
    - il dataset originario illustrava i dati fino al **2012-12-01**; attraverso la tecnica del web scraping, utilizzando la libreria *selenium*, sono state estratte le misurazioni mensili di temperatura media per nazione e per città fino al **2020-12-01**
    - le misurazioni sono state estratte dal sito di Berkley Earth 
    - i dati estratti sono stati estrapolati dai file html raccolti utilizzando la libreria *spacy* di NLP e aggiunti al dataset originario con attenzione a far coincidere tutte le variabili e rimuovendo eventuali errori
    
2.  **<h3>Pulizia del dataset 🛠️</h3>** 
    - il dataset presentava diversi problemi tra cui:
        - non tutte le prime osservazioni di ciascuna città coincidevano
        - presenza di osservazioni mancanti
        - latitudine e longitudine erano in formato stringa seguita dala sigla di uno dei punti cardinali 
        - presenza di città con lo stesso nome
    - dopo aver calcolato la prima occorrenza di ogni città, i dati sono stati resi omogenei analizzando solo i dati successivi al **1894-01-01**
    - le poche osservazioni mancanti sono state individuate e stimate tramite interpolazione
    - per le coordinate i dati sono stati trasformati in *float* e la sigla del punto cardinale è diventato il segno del valore
    - non potendo utilizzare la città come riferimento non essendo univoche, è stata creato un codice atomico (**CLL**) dalla combinazione di città, latitudine e longitudine
3. **<h3> Visualizzazione grafica 📈</h3>**
    - per poter visualizzare le variazioni di temperatura sono state calcolate le anomalie di temperatura, definita come differenza tra la media annuale e la media utilizzata come riferimento, per ogni nazione e per ogni città la media di riferimento prendendo in esame il periodo di tempo tra il **1951** e il **1980**, lo stesso sistema di misura utilizzato dal sito di Berkley Earth: <a>http://berkeleyearth.org/</a>
    - calcolate le anomalie per ogni anno è stata creata una mappa choropletica che la visualizza, l'anomalia per nazione è rappresentata da un gradiente di colore e le città che hanno superato una determinata soglia di anomalia fissata a 2°C vengono localizzate da punti rossi 
    - viene inoltre visualizzato un grafico che mostra l'andamento dell'anomalia globale nel tempo
    - tutti i grafici sono stati trattati come frame e uniti in formato GIF per rappresentare al meglio le anomalie nel corso del tempo
4. **<h3>"Viaggiatore freddoloso" :earth_africa: 🥶</h3>**
    - come richiesto è stato sviluppato un algoritmo che per ogni mese calcolasse il percorso da Pechino a Los Angeles tappa dopo tappa spostandosi nella città più calda tra le tre più vicine
    - questa parte del progetto è stata così articolata:
        - in primo luogo sono state calcolate le distanze geodesiche tra ogni città e tutte le altre con longitudine inferiore: dovendosi spostare da Pechino a Los Angeles, il vincolo che si spostasse ad ogni passaggio verso sinistra era necessario per impedire che il viaggiatore tornasse indietro. 
        - per ogni città sono state prelevate le sue tre città più vicine
        - successivamente è stato sviluppato un grafo orientato che avesse come nodi le varie città, gli archi diretti sono stati impostati in modo tale che ogni città sia collegata alle sue tre città più vicine a sinistra
        - i pesi degli archi sono stati progettati successivamente
        - con la programmazione ad oggetti è stato progettato un "viaggiatore" che ricevesse in input il grafo salvato e il dataset ultimato
        - questo oggetto contiene diversi elementi:
            1. il punto di partenza e il punto di arrivo
            2. la funzione per attribuire i vari pesi agli archi del grafo con la temperatura media della città di arrivo a seconda del periodo selezionato
            3. la funzione che faccia scegliere al viaggiatore la città più calda tra le sue opzioni, per ogni tappa, compresa la condizione che giunto a Los Angeles si fermi
            4. la funzione per rappresentare graficamente il percorso con tutte le tappe 
 
 ```{note}
Note: Il codice è stato suddiviso in più file per poter essere maggiormente fruibile.
       Nella repository si trovano tutti i file utili che vengono caricati dal codice.
```

> ## :warning: Il file Data è troppo grande, può essere scaricato al seguente link: <a>https://we.tl/t-o3VMjxG45Q</a>
