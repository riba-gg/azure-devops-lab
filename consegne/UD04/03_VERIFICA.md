# Consegna UD04 — Verifica

## Parte A — Scelta singola

Per le domande 1–8 riporta risposta e motivazione.

1. A
2. B
3. B
4. B
5. B
6. C
7. B
8. A

## Parte B — Risposte brevi

9. La ridondanza implica il salvare i file su più server, il backup invece permette di tornare indietro in caso di cancellazione o corruzione del file 
10. management plane gestisce la risorsa con az group create, data plane gestisce i file con az storage blob upload
11. permessi minimi, durata breve, scope circoscritto e generazione delegata
12. perché i dati sono offline e il recupero richiede molto tempo
13. perché chiunque li trovi ottiene accesso incontrollato

## Parte C — Caso situazionale

14. uso di un ruolo troppo ampio per l'infrastruttura, uso di account key fisse e sas senza scadenza
15. usare identità entra id con ruoli specifici sui dati e sas con scadenza stretta
16. verificare con autenticazione login e ripulire eliminando il resource group

