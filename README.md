# Esercitazione 3 — Data Overview

## Obiettivi didattici

L’esercitazione ha come obiettivo quello di **fornire una visione d’insieme di un intero dataset**, rappresentando ciascun dato attraverso un **glifo** comprensibile.

Attraverso questa attività gli studenti devono dimostrare di sapere:

1. **Caricare e gestire un dataset** in formato CSV.
2. **Disegnare glifi** utilizzando una **funzione dedicata**, in modo da tradurre i dati in forme visive coerenti.
3. **Aggiungere una semplice interazione**, come il cambio di colore o la comparsa di un tooltip al passaggio del mouse.
4. **Creare una legenda** o un sistema di riferimento che aiuti a interpretare la visualizzazione.
5. **Progettare la visualizzazione** in modo che non si limiti a mostrare dati, ma offra anche un **modo per decodificarli**, rendendo esplicite le relazioni tra le variabili e facilitando la comprensione da parte dell’utente.

---

## Descrizione del codice d’esempio

Il codice fornito mostra una possibile implementazione di questi tre obiettivi in p5.js.

- Nella fase di **preload**, il file `assets/data.csv` viene caricato in memoria. Contiene colonne come `latitude`, `longitude`, `value` e `uncertainty`.
- Nel **setup**, vengono calcolati una sola volta i valori minimi e massimi per ciascuna variabile del dataset. Questi valori vengono usati per creare le **scale di mappatura** (coordinate, raggio e sfocatura) e rimangono fissi per tutto il programma.
- Nel **draw**, il programma esegue un ciclo che:
  - rappresenta ogni riga del dataset come un **glifo circolare**, disegnato in una posizione proporzionale a latitudine e longitudine;
  - applica un raggio proporzionale al valore e un livello di **blur** proporzionale all’incertezza;
  - verifica se il **mouse è sopra un glifo** (hover), cambiandone il colore e salvando le informazioni per mostrare il tooltip.
- Al termine del ciclo, se un glifo è stato selezionato, viene mostrato un **tooltip** con il nome del paese e il valore associato.

Sono inoltre presenti **due funzioni dedicate**:

- `drawSun()` — disegna il glifo circolare, applicando il filtro di blur in base al valore di incertezza;
- `drawTooltip()` — mostra il testo del tooltip in prossimità del puntatore del mouse.
