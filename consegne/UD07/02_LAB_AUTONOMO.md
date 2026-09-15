# UD07 — Consegna laboratorio autonomo

## 1. Script CLI idempotente

* **logica:** controllo se il Resource Group esiste. Se non esiste lo creo, se esiste lo riutilizzo. Poi imposto i tag `ManagedBy=Autonomo` e `UD=07` e mostro le informazioni principali.

* **prima esecuzione:** il Resource Group non esisteva, quindi è stato creato.

* **seconda esecuzione:** il Resource Group esisteva già, quindi è stato riutilizzato.

* **verifica:** lo stato finale è risultato `Succeeded`.

## 2. PowerShell equivalente

* **controllo esistenza:** ho controllato se `rg-ud07-auto-ps` esisteva già usando `Get-AzResourceGroup`.

* **modifica:** se non esisteva veniva creato. Ho poi aggiunto i tag `ManagedBy=Autonomo` e `UD=07`.

* **output:** il Resource Group è stato creato correttamente e lo stato era `Succeeded`.

## 3. Activity Log

* **operazione:** Update resource group

* **status:** Succeeded

* **timestamp:** 2026-09-15T14:54:50.6641704Z

## 4. KQL

1. Le righe aggregate sono 2.

2. Lo stato con la latenza media maggiore è WARN, con 470 ms.

3. summarize raggruppa i dati e calcola dei valori, quindi non mostra più tutte le righe originali ma un risultato più sintetico.

## 5. Metrics

* **metrica:** UsedCapacity

* **unità:** Bytes

* **aggregazione:** Average

* **dato presente:** sì, è stato trovato un dato.

* **interpretazione:** indica quanto spazio viene utilizzato dallo Storage Account.

## 6. Alert

* **scope:** Storage Account del laboratorio autonomo.

* **condition:** Transactions maggiore di 0, con aggregazione Total.

* **severity:** 3

* **evaluation frequency:** 5 minuti

* **Action Group:** presente

* **Enabled vs Fired:** Enabled significa che l'alert è attivo e controlla la condizione. Fired significa invece che la condizione si è verificata. Quindi un alert può essere Enabled senza essere Fired.

## 7. Guasto amministrativo

* **sintomo:** il Resource Group non è stato trovato.

* **errore:** ResourceGroupNotFound

* **ipotesi:** il nome potrebbe essere sbagliato oppure il Resource Group potrebbe non esistere nella subscription attuale.

* **controllo:** controllare la subscription e il nome del Resource Group.

* **correzione:** usare il nome corretto del Resource Group. Non ho creato quello inesistente usato per la prova.

* **verifica:** ripetere il comando con il nome corretto.

## 8. Runbook

### Sintomo

Una risorsa o un Resource Group non viene trovato.

### Contesto

Può essere dovuto al nome sbagliato oppure al fatto di essere nella subscription sbagliata.

### Controlli

Controllare prima account e subscription, poi il nome del Resource Group e della risorsa.

### Comandi

Per vedere la subscription: az account show --output table

Per controllare il Resource Group: az group exists --name NOME_RG

Per visualizzarlo: az group show --name NOME_RG --output table

Per controllare l'Activity Log: az monitor activity-log list --resource-group NOME_RG --offset 30m --output table

### Interpretazione

Se il Resource Group non viene trovato bisogna controllare se il nome è corretto e se si sta usando la subscription giusta.

### Correzione minima

Usare il nome corretto oppure cambiare subscription se necessario. Non creare una nuova risorsa senza aver prima controllato.

### Verifica

Ripetere il comando e controllare che la risorsa venga trovata.

### Cleanup

Eliminare le risorse create per il laboratorio e controllare che siano state eliminate.

## 9. Cleanup

* **rg-ud07-auto:** eliminato. `az group exists` ha restituito `false`.

* **rg-ud07-auto-ps:** eliminato. `az group exists` ha restituito `false`.
