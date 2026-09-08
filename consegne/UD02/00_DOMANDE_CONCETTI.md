# Consegna UD02 — Domande sui concetti

Per ciascuna domanda 1–8 riporta una risposta motivata.

1. Perché con una VM è l'utente a gestire tutta la macchina mentre con App Service Microsoft si occupa di sistema operativo e runtime, lasciando all'utente solo codice, configurazione del servizio e dati.

2. Tenant è la directory che contiene identità e oggetti dell'organizzazione, sottiscrizione è un confine di fatturazione contenuta nel tenant e il resource group è un contenitore logico dentro la sottoscrizione che raggruppa risorse

3. La località del resource group indica solo dove Azure conserva i suoi metadati amministrativi, non è un vincolo tecnico sulle risorse contenute.

4. Una region è un'area geografica con dei datacenter, un'availability zone è un gruppo di datacenter indipendenti dentro la stessa region, pensato per ridurre il rischio che un singolo guasto interrompa tutto.

5. Perché un comando eseguito nella sottoscrizione sbagliata crea una risorsa, ma nel posto sbagliato.

6. Perché i tag sono semplici coppie chiave valore informative, non regolano permessi o accesso.

7. Un comando CLI è riproducibile, può essere salvato, confrontato, versionato e riutilizzato in uno script o pipeline.

8. Perché lanciare il comando di eliminazione avvia solo il processo. bisogna verificare che Azure confermi che il resource group non esiste più, altrimenti delle risorse possono restare attive e generare costi anche dopo il comando.

