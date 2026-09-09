# Consegna UD03 — Laboratorio autonomo

## Analisi dell'accesso

| Principal anonimizzato | Ruolo | Scope | Origine | Accesso effettivo |
|---|---|---|---|---|
| Gruppo FinOps (`grp-cea-readers-551aae`) | Reader | Resource Group (`rg-cea-identity-551aae`) | Diretta | Vedono solo le risorse e i costi, zero permessi di scrittura. |
| Owner Sottoscrizione | Owner | Sottoscrizione | Ereditata | Gestione totale ereditata dall'alto. |

**Perché ho scelto Reader**: 
Al team FinOps serve solo leggere i dati e i costi, quindi il ruolo Reader basta e avanza (minimo privilegio). Non metto Contributor sennò possono modificare le cose, e nemmeno Owner perché non devono toccare i permessi o fare danni con gli accessi.

## Diagnosi dei casi

### Caso A
- **Causa probabile**: Non hai una sessione attiva sulla CLI o è scaduta.
- **Controllo**: `az account show`
- **Rimedio minimo**: Eseguire `az login`.

### Caso B
- **Causa probabile**: Stai provando a scrivere o modificare qualcosa ma hai solo permessi di lettura (es. ruolo Reader).
- **Controllo**: `az role assignment list --include-inherited`
- **Rimedio minimo**: Usare un account con un ruolo adeguato (es. Contributor) sullo scope.

### Caso C
- **Causa probabile**: Stai cercando di cancellare un resource group che ha un blocco attivo.
- **Controllo**: `az lock list --resource-group "<nome-rg>"`
- **Rimedio minimo**: Rimuovere il lock con `az lock delete` prima di procedere alla cancellazione.

## Budget, lock e cleanup

- **Cosa fanno**: 
  - Il RBAC dà i permessi ma non ferma i danni da cancellazione.
  - Il Lock protegge fisicamente il gruppo se provi a cancellarlo per sbaglio.
  - Il Budget manda solo le mail di avviso ma non blocca la spesa se sfori.
- **Ordine di pulizia**:
  1. Tolgo il lock (`az lock delete`).
  2. Cancello il resource group (`az group delete`).
  3. Controllo che sia zero (`az group exists`).

## Risultato finale

- output usati: quelli della CLI per ruoli e lock.
- cleanup: verificato con `az group exists` che dà `false`.