# ForgeAI
ForgeAI è un tool AI per la trasformazione del linguaggio naturale in WorkFlow e Pipeline ApacheHop

## Obiettivo
ForgeAI è un chatbot che permette di generare Workflow e Pipeline Apache Hop da linguaggio naturale.
La macchina verrà allenata sulla documentazione di Apache Hop, progetti di esempio creati ad hoc e progetti reali utilizzati in azienda.

Il primo obiettivo sarà quello di creare Pipeline e Workflow semplici con istruzioni semplici.
Il secondo obiettivo sarà quello di gestire Pipeline e Workflow più complessi con istruzioni e gestioni custom.
L'obiettivo finale sarà quello di creare Workflow completi con Pipeline innestati.

L'input principale sarà linguaggio naturale, ma potrebbe anche riceve in input un Workflow/Pipeline parziale o completo in formato XML, la macchina dovrà poi controllare la richiesta e modificare il flusso allegato secondo le richieste.

## Apache Hop

Apache Hop è un framework open source per la progettazione e l'esecuzione di pipeline di trasformazione dati e workflow.

Un progetto Apache Hop è costituito da questi elementi:

- **Pipeline** (`.hpl`): sequenza di *transform* collegati da *hop* (frecce). Ogni transform esegue un'operazione sui dati (lettura, filtro, join, scrittura...). L'esecuzione è tipicamente parallela e orientata agli stream.

- **Workflow** (`.hwf`): sequenza di *action* collegate da *hop* condizionali (successo/fallimento). Servono per orchestrare più pipeline, controllare file, inviare notifiche, gestire errori.

Entrambi i tipi di file sono serializzati in XML, la struttura base è:
  ```xml
  <pipeline>
    <info> ... </info>        <!-- metadati -->
    <order> ... </order>      <!-- hop: connessioni tra transform -->
    <transform> ... </transform>  <!-- definizione di ogni step -->
  </pipeline>
  ```

## DataSet
Il dataset è stato costruito ad hoc per questo progetto, è costituito da coppie `(istruzione naturale → file XML Apache Hop atteso)`, ogni casistica è stata progettata per coprire pattern reali.

La difficoltà è distribuita su tre livelli:

- **Easy**: pipeline lineari con 1-2 transform, nessuna logica condizionale
- **Medium**: pipeline con filtri, lookup, aggregazioni, o workflow semplici
- **Hard**: pattern avanzati (SCD2, incremental load, job queue, multi-sorgente)

Il dataset contiene solo 20 casistiche, è stato deciso un approccio dove il dataset ha una minore mole di dati ma di migliore qualità.