# Nota operativa — UD01

La cartella di lavoro si trova nel filesystem Linux di WSL 2 ed è stata aperta con Visual Studio Code tramite l'estensione WSL.

Il controllo che ha dimostrato il corretto contesto di esecuzione è:

```bash
pwd
```

L'output indicava un percorso interno alla home Linux e non un percorso `/mnt/c`.

## Nota operativa - Verifica

Il comando più utile incontrato è git status: va lanciato prima e dopo git add per verificare esattamente cosa entrerà nel prossimo commit ed evitare di includere file sbagliati o dimenticare modifiche.