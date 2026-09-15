# UD07 — Verifica

## Parte A

1. A

2. B

3. B

4. A

5. B

6. B

7. B

8. B

## Parte B

9. Activity Log mostra principalmente le operazioni e gli eventi sulle risorse Azure. Metrics sono valori numerici che permettono di monitorare una risorsa, per esempio utilizzo o latenza. Logs contengono informazioni più dettagliate che possono essere analizzate con KQL.

10. L'idempotenza significa che posso eseguire più volte la stessa operazione senza creare risultati diversi o duplicati. Per esempio, uno script controlla se un Resource Group esiste e lo crea solo se non esiste.

11. table mostra l'output in una tabella leggibile da una persona. tsv restituisce i valori separati da tabulazioni ed è utile quando devo usare un valore dentro un altro comando o in una variabile.

12. Il workspace è il luogo dove possono essere raccolti e analizzati i log. La diagnostic setting invece serve a dire quali dati diagnostici inviare e verso quale destinazione.

13. L'Alert Rule stabilisce quale condizione deve essere controllata. L'Action Group stabilisce cosa fare quando l'alert si attiva, per esempio inviare una notifica.

14. Perché il fatto che due eventi avvengano nello stesso periodo non significa che uno abbia necessariamente causato l'altro. Bisogna controllare altri dati per capire il rapporto tra i due eventi.

## Parte C

15. Posso affermare che alle 10:15 è stata fatta una modifica, alle 10:16 l'operazione write è risultata riuscita, alle 10:20 la metrica è aumentata e alle 10:25 l'alert è passato a Fired.

16. Bisogna controllare la condizione dell'alert, la metrica e i log disponibili nel periodo interessato. Bisogna anche verificare se ci sono state altre modifiche o eventi tra le 10:15 e le 10:25. Solo dopo questi controlli si può capire se la modifica delle 10:15 è stata realmente la causa dell'alert.
