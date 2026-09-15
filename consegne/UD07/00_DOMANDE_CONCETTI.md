# UD07 — Risposte alle domande sui concetti

## 1.

**Risposta:** `--query` permette di interrogare direttamente la struttura dei dati JSON e ottenere solo le proprietà necessarie. È preferibile alla ricerca manuale di stringhe perché è più preciso e affidabile, soprattutto nelle procedure automatizzate.

## 2.

**Risposta:** `table` restituisce i dati in una forma leggibile per una persona, mentre `tsv` restituisce valori separati da tabulazioni ed è particolarmente utile per recuperare un singolo valore da riutilizzare in uno script o in un comando successivo.

## 3.

**Risposta:** In PowerShell si lavora con oggetti e non soltanto con testo. Possiamo quindi accedere direttamente alle proprietà dell'oggetto, ad esempio `$rg.Location`, e passare gli oggetti tra i comandi tramite la pipeline.

## 4.

**Risposta:** Una procedura è idempotente quando può essere eseguita più volte senza produrre effetti indesiderati e porta comunque l'ambiente allo stato desiderato.

## 5.

**Risposta:** L'Activity Log registra principalmente le operazioni di gestione delle risorse e della subscription. Le Metrics sono valori numerici osservati nel tempo, come CPU o traffico di rete. I Logs sono record più dettagliati che possono contenere informazioni come timestamp, operazione, stato e identità.

## 6.

**Risposta:** Un Log Analytics workspace è un ambiente nel quale vengono raccolti dati di log e nel quale è possibile interrogarli e analizzarli tramite KQL.

## 7.

**Risposta:** Una diagnostic setting serve a stabilire quali categorie di log o metriche inviare e verso quale destinazione, ad esempio un Log Analytics workspace, uno Storage Account o un Event Hub.

## 8.

**Risposta:** L'Activity Log è il registro degli eventi di gestione di Azure. `AzureActivity` è invece la tabella di Log Analytics nella quale questi eventi possono essere interrogati dopo essere stati instradati al workspace tramite una diagnostic setting.

## 9.

**Risposta:** L'Alert Rule definisce il segnale da monitorare e la condizione che deve essere soddisfatta. L'Action Group definisce invece l'azione da eseguire quando l'alert viene attivato, ad esempio inviare una notifica.

## 10.

**Risposta:** Un alert in stato Fired indica che la condizione configurata è stata soddisfatta, ma non significa automaticamente che esista un incidente reale. La soglia potrebbe essere configurata male oppure il comportamento potrebbe essere previsto.

## 11.

**Risposta:** La correlazione indica che due eventi si verificano in relazione temporale o statistica. La causalità significa invece che un evento è effettivamente la causa dell'altro. La correlazione da sola non dimostra la causalità.

## 12.

**Risposta:** I passaggi essenziali sono: descrivere il sintomo, definire il risultato atteso, raccogliere evidenze, formulare un'ipotesi, verificarla, applicare la modifica minima, ripetere il test e documentare il risultato.
