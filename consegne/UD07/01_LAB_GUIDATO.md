# UD07 — Consegna laboratorio guidato

## CLI

* prima esecuzione script: il Resource Group `rg-ud07-cli-test` non esisteva, quindi è stato creato.
* seconda esecuzione: il Resource Group esisteva già ed è stato riutilizzato.
* comportamento idempotente: eseguendo lo script una seconda volta non viene creata una nuova risorsa e l'ambiente rimane nello stato previsto.
* esempio JMESPath: `{Name:name,Location:location,State:properties.provisioningState,Tags:tags}`
* quando usare `tsv`: quando serve ottenere un singolo valore da usare in un altro comando o script.

## PowerShell

* `Get-AzContext` verificato: sì.
* Resource Group test: `rg-ud07-ps-test`
* prima esecuzione: il Resource Group è stato creato e sono stati aggiunti i tag.
* seconda esecuzione: il Resource Group esisteva già e non è stato ricreato.
* perché il controllo `if` è utile: serve a controllare se la risorsa esiste già prima di crearla.

## Log Analytics

* workspace: `law-ud07-15374`
* regione: `northeurope`
* query `print`: ha restituito `Course=AZ104`, `UD=7` e `Status=OK`.
* query `datatable`: ha creato alcuni dati di esempio con `API`, `DB` e `WEB`.
* risultato sintetico: 2 componenti con stato `OK` e 1 con stato `WARN`.

## Activity Log

* evento osservato: `Update resource group`
* status: `Succeeded`
* timestamp: `2026-09-15T12:47:48.2194571Z`
* dati personali omessi: sì

## Diagnostic Setting

* esito: creata correttamente e poi eliminata durante il cleanup.
* destinazione: Log Analytics workspace.
* AzureActivity disponibile: no.
* fallback usato, se necessario: sì, il workspace è stato creato in `northeurope` perché `westeurope` non permetteva la creazione di nuove risorse in quel momento.

## Metrics

* Storage Account: `stud0789474940`
* metrica: `UsedCapacity`
* unità: `Bytes`
* aggregazione: `Average`
* punto dati disponibile: sì
* interpretazione: indica quanto spazio viene utilizzato dallo Storage Account.

## Alert

* nome: `alert-ud07-storage-transactions`
* scope corretto: sì
* condition: `Transactions`, `Total`, maggiore di `0`, con finestra di 5 minuti.
* severity: `3 - Informational`
* Action Group: presente (`ag-ud07`)
* perché non è necessario che sia Fired: perché dovevamo verificare che l'alert fosse configurato e attivo. Non era necessario aspettare che la condizione si verificasse.

## Correlazione

* modifica osservata: è stato modificato il tag dello Storage Account.
* evento Activity Log: è comparso un evento `Create/Update Storage Account` con stato `Succeeded`.
* la correlazione prova causalità?: no.
* motivazione: il fatto che due eventi avvengano nello stesso periodo non significa automaticamente che uno sia la causa dell'altro.

## Cleanup

* diagnostic setting rimossa: sì
* RG CLI test eliminato: sì
* RG PowerShell test eliminato: sì
* RG principale eliminato: sì
