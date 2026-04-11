# Descrizione
Nella cartella `data` troviamo i dati che il nostro modello andrà ad utilizzare.

Ogni cartella rappresenta un caso distinto e contenuto, seguirà il seguente formato:
- NomeCartella: NN_[Nome_Casistica], es: 00_Print_Log
- File:
    - input.txt, istruzione naturale di esempio
    - output[N].[hpl/hwf], risultato atteso, nel caso di più output attesi si creeranno ulteriori file
    - metadata.json, contiene i tag, difficoltà e tipologia di casistica

Contenuto di metadata.json
- id, Numero Casistica
- difficulty, difficoltà casistica: easy, medium, hard
- type, tipologia dell' output: pipeline, workflow, project
- tags, tag descrittivi della casistica per una migliore identificazione
- description, descrizione della casistica

Infine dataset.json manterrà i metadata in maniera aggregata per una migliore fruizione delle casistiche.