# Consegna UD04 — Domande sui concetti

Per ciascuna domanda 1–8 riporta una risposta motivata.

1. Azure Files serve per condividere file come cartelle di rete con SMB o NFS, mentre Azure Blob è pensato per file non strutturati tramite API e non si monta come disco.

2. Il management plane gestisce la creazione e configurazione delle risorse, mentre il data plane serve per leggere, scrivere e toccare i dati dentro le risorse.

3. Perché Contributor gestisce l'infrastruttura e non i dati, quindi per i file serve un ruolo specifico del data plane come Storage Blob Data Contributor.

4. La geo-ridondanza sposta i dati in un'altra regione per proteggersi da guasti fisici enormi, mentre il backup salva le versioni per recuperare file cancellati per errore o corrotti.

5. Il costo basso di spazio ma alto per riprendere i file, il tempo lungo per riattivarli e il fatto che siano dati da non toccare mai.

6. Perché la chiave dell'account dà accesso totale e illimitato a tutto lo storage, mentre la SAS ha limiti di tempo e permessi ristretti.

7. Dare solo i permessi strettamente necessari, limitarla a una sola risorsa e metterle una scadenza breve.

8. Perché le regole di lifecycle non partono subito ma vengono elaborate da processi automatici di Azure a intervalli lunghi di ore.

