# UD06 — Consegna laboratorio autonomo

## 1. Baseline

* VM: Running
* Nginx: active (running)
* HTTP: `HTTP/1.1 200 OK`
* regola NSG: `Allow-HTTP`, TCP/80, Allow, priority 310, Source: My IP address

## 2–4. Guasto, diagnosi, ripristino

* regola introdotta: `Deny-HTTP-Auto`, TCP/80, Deny, priority 200, Source: My IP address
* sintomo: HTTP dall'esterno non raggiungibile
* ipotesi: problema del servizio Nginx oppure della configurazione NSG
* controllo: Nginx risultava `active`; `curl -I http://localhost` restituiva `HTTP/1.1 200 OK`
* causa: `Deny-HTTP-Auto` bloccava il traffico TCP sulla porta 80. La regola aveva priorità 200, quindi veniva valutata prima di `Allow-HTTP` con priorità 310
* correzione minima: eliminare `Deny-HTTP-Auto`
* verifica: dopo l'eliminazione di `Deny-HTTP-Auto`, `curl -I http://9.160.105.140` ha restituito `HTTP/1.1 200 OK`


## 5. Monitoring

- metrica: Percentage CPU
- intervallo: Last hour
- aggregazione: Average
- deduzione: nel periodo osservato la VM ha avuto un utilizzo medio della CPU molto basso, circa 0,3044%
- cosa non posso dedurre: da questa sola metrica non posso sapere se l'applicazione funziona correttamente né valutare l'utilizzo di memoria, disco o rete

## 6. VMSS Autoscale

- min: 1
- default: 1
- max: 4
- metrica: Average Percentage CPU
- condizione: CPU media > 70% per 5 minuti
- azione: aggiungere 1 istanza
- perché max=4: per limitare il consumo di risorse e i costi, evitando una crescita illimitata del numero di istanze

## 7. App Service scaling

- A: Scale up — aumentare la potenza della singola istanza scegliendo un piano/SKU più potente
- B: Scale out automatico — aumentare o diminuire il numero di istanze in base a una metrica, ad esempio la CPU
- C: Automatic Scaling — il numero di istanze viene adattato automaticamente in base al carico/traffico
- D: Scale out manuale — aumentare manualmente il numero di istanze, ad esempio da 1 a 2

## 8. Backup policy

- frequenza: giornaliera
- orario: 02:00
- retention: 30 giorni
- motivazione: garantire un punto di ripristino quotidiano mantenendo sotto controllo lo spazio di archiviazione e i costi

## 9. HA / Backup / DR

- A: HA (High Availability) — mantenere il servizio disponibile anche in caso di guasto di una singola istanza
- B: Backup — creare copie dei dati per poterli ripristinare dopo una perdita o cancellazione
- C: DR (Disaster Recovery) — ripristinare il servizio dopo un evento grave che rende indisponibile l'infrastruttura principale

## 10. RPO / RTO

- RPO: 15 minuti
- RTO: 60 minuti
