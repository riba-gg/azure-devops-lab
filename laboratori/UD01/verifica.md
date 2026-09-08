## Parte A — Scelte operative

### 1

In PowerShell `git --version` restituisce `2.53.0`, mentre nel terminale Ubuntu restituisce `2.43.0`. Qual è la spiegazione più corretta?

B. Windows e Ubuntu possono possedere installazioni distinte di Git.  
### 2

Quale comando mostra se la distribuzione Ubuntu sta usando WSL 1 o WSL 2?

C. `wsl --list --verbose`  

### 3

Perché il progetto viene conservato in `~/workspace`?

C. Per lavorare nel file system Linux, più adatto al successivo workflow con Docker e bind mount.  

### 4

Git è presente e la sua versione è compatibile. Qual è l'azione corretta?

C. Verificarne il funzionamento e proseguire senza reinstallazione.  

### 5

Dopo `git commit` la pagina GitHub non mostra la modifica. Quale spiegazione è più probabile?

A. Il commit esiste localmente, ma non è ancora stato eseguito `git push`.  

### 6

Qual è il controllo più diretto per capire quali file entreranno nel prossimo commit?

A. `git status` dopo `git add`  

### 7

Durante `az login --use-device-code` il terminale mostra un codice temporaneo. Che cosa devi fare?

C. Usarlo nella pagina di autenticazione e non conservarlo nel repository.  

### 8

Quale indizio dimostra meglio che VS Code sta operando dentro Ubuntu?

B. L'indicatore `WSL: Ubuntu` e un terminale con percorso Linux.  

### 9

Perché il docente deve essere aggiunto come collaboratore al repository personale pubblico?

C. Per partecipare alle attività di scrittura, revisione e collaborazione previste dal percorso.  

## Parte B — Risposte brevi

### 10

Spiega in non più di quattro righe la differenza fra Git e GitHub.

Git è il sistema di versionamento locale mentre GitHub è il servizio che ospita il repository e che permette la condivisione dei file.


### 11

Scrivi la sequenza minima di comandi che useresti per osservare le modifiche, preparare un singolo file, creare un commit e inviarlo al remote.

git status
git add nome-file
git commit -m "messaggio"
git push

### 12

Si propone di eseguire immediatamente `wsl --update` su tutte le postazioni. Quali due controlli devono precedere la decisione?

wsl --list --verbose per capire se l'aggiornamento è necessario

### 13

Il comando `code .` apre VS Code, ma il terminale integrato mostra un percorso `C:\Users\...`. Quale problema sospetti e quale verifica esegui?

Penso che VSC venga aperto tramite Windows e non Linux controllerei che in basso a sinistra ci sia l'indicatore che mostri WLS

### 14

Hai pubblicato per errore un vero token in un commit e poi hai cancellato la riga con un secondo commit. Perché il problema non è risolto?

Perché il token resta nella cronologia recuperabile

## Parte C — Prova pratica

Nel repository personale:

1. aggiungi in fondo a `laboratori/UD01/nota-operativa.md` una frase che descriva il comando più utile incontrato nell'unità;
2. usa `git diff` per controllare la modifica;
3. prepara soltanto quel file;
4. crea un commit con un messaggio descrittivo;
5. esegui il push;
6. confronta `git log -1 --oneline` con il commit nella pagina GitHub e annota se hash e messaggio coincidono.

La prova è riuscita se sai spiegare l'effetto di ciascun comando, non soltanto se il file compare su GitHub.