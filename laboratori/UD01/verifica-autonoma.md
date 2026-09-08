# Nota Tecnica: Verifica Autonoma Ambiente UD01

## Contesto di Sistema e Configurazione
- **Ambiente:** Ubuntu-24.04 in esecuzione su WSL 2.
- **Percorso Linux:** `/home/sriba/workspace/azure-devops-lab` (verificato tramite `git rev-parse --show-toplevel`).
- **Remote URL:** `https://github.com/ste-riiba/azure-devops-lab` (configurato correttamente su `origin`).
- **Strumenti:** Azure CLI verificata tramite il comando `az version`.
- **Collaborazione:** Stato dell'invito del docente verificato direttamente su GitHub.

## Concetti di Controllo Versione (Git)
- **Working Tree:** L'area di lavoro locale che contiene i file modificati sul filesystem.
- **Staging Area:** L'area di transito intermedia in cui i file vengono selezionati (`git add`) prima di essere consolidati.
- **Commit Locale:** L'istantanea stabile e storicizzata delle modifiche salvata nel database locale (`git commit`).
- **Repository Remoto:** La versione centralizzata del progetto sincronizzata su GitHub (`git push`).

## Gestione del Contesto e Anomalie
- **Errore comune:** Esecuzione di comandi di versionamento al di fuori della struttura di progetto, con conseguente errore `fatal: not a git repository`.
- **Riconoscimento e risoluzione:** L'anomalia viene individuata controllando il percorso corrente con `pwd` e validata verificando la radice tramite `git rev-parse --show-toplevel`.