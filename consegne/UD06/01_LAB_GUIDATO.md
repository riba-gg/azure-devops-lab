# UD06 — Consegna laboratorio guidato

## VM

* image: Ubuntu 24 LTS
* size: Standard_B2ts_v2
* private IP: 172.16.0.4
* public IP: 51.12.242.239
* NIC: vm-ud06-linux-nic
* subnet: subnet di default
* OS disk: disco standard Linux

## Accesso e workload

* SSH: riuscito
* Nginx: installato e attivo sulla VM
* test localhost: OK
* test esterno: OK
* IP Flow Verify: Access allowed
* regola responsabile: Allow-HTTP-MyIP

## Azure Monitor

* metrica VM: Percentage CPU, Network In, Network Out
* intervallo: Ultima ora
* aggregazione: Average / Total
* osservazione: CPU stabile vicino allo 0% con minimi flussi; picco di Network In registrato durante i test di connettività e scaricamento pacchetti.

## VMSS / Autoscale

* min: 1
* default: 1
* max: 3
* metrica: Percentage CPU
* soglia: > 70 avg 5m
* azione: scale out 1
* perché serve un max: Protezione da costi imprevedibili, errori di configurazione e scaling eccessivo per picchi anomali.

## App Service

* App Service Plan: non creato
* tier:
* Web App: non creata
* hostname:
* test HTTPS:

## Scaling App Service

| Modalità | Basata su |
| --- | --- |
| Manual | Numero di istanze deciso dall'operatore |
| Azure Monitor Autoscale | Regole e metriche di sistema |
| Automatic Scaling | Gestione nativa e autonoma del servizio PaaS |

## Azure Monitor App Service

* metrica: non eseguite, non disponibile nel piano free
* osservazione:

## Backup

* Recovery Services vault: contenitore logico di protezione
* frequenza ipotizzata: Giornaliera
* retention: 30 giorni
* recovery point: Stato utilizzabile per il ripristino
* backup reale avviato?:

## HA / Backup / DR

* Scenario A: High Availability
* Scenario B: Backup
* Scenario C: Disaster Recovery

## Cleanup

* Resource Group eliminato: rg-ud06-compute
* `az group exists`: false