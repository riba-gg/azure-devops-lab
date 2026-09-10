# Consegna UD04 — Laboratorio autonomo

## Scelta del servizio e della ridondanza

* requisito: file non strutturati accessibili via api
* servizio: azure blob storage
* ridondanza: standard_lrs
* motivazione: soluzione economica e adatta a carichi di test

## Operazioni e verifica

* container documents creato
* file di prova caricato e scaricato con verifica cmp
* sas limitata generata con scadenza e testata con curl

## Diagnosi

* sintomo: authorizationpermissionmismatch
* piano: data plane
* causa: mancanza del ruolo di autorizzazione sui dati
* controllo: verifica assegnazioni iam
* correzione: assegnato storage blob data contributor

## Lifecycle, costi e cleanup

* prefisso: delimita la cartella o i file soggetti a policy
* driver di costo: spazio occupato e numero di richieste
* cleanup: resource group eliminato e verificato con az group exists

## Risultato finale

* nessun segreto pubblicato: confermato
* hash abbreviato e messaggio del commit: completato