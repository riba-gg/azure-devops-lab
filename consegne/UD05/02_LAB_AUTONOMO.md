# Consegna UD05 — Laboratorio autonomo

## Inventario iniziale

- **Resource Group:** rg-cea-network-7b4d06 (anonimizzato)
- **Virtual Network:** vnet-lab (10.50.0.0/16)
- **Subnet:** 
  - `snet-web` (10.50.10.0/24)
  - `snet-data` (10.50.20.0/24)
- **Network Security Group:** nsg-lab
- **Network Interfaces (NIC):** 
  - `nic-web-01` collegata a `snet-web`
  - `nic-data-01` collegata a `snet-data`
- **Associazioni NSG:** NSG associato alla subnet `snet-data`
- **Regole NSG iniziali:** `Allow-Web-Postgres` (Priorità 300, Inbound, Allow, TCP 5432, Sorgente `10.50.10.0/24`)

## Guasto e diagnosi

- **regola introdotta:** `Deny-Web-Postgres-Auto` (Priorità 250, Inbound, Deny, TCP 5432, Sorgente `10.50.10.0/24`)
- **ordine di priorità osservato:** Valutazione prioritaria della regola 250 (Deny) rispetto alla regola 300 (Allow)
- **sintomo:** Interruzione del traffico di rete tra la subnet web e la subnet data sulla porta 5432
- **ipotesi:** Presenza di un conflitto di priorità nel Network Security Group in cui la regola di blocco ha precedenza su quella di permesso
- **controllo:** Elenco delle regole tramite `az network nsg rule list` per confermare la coesistenza delle regole in conflitto
- **correzione minima:** Rimozione della regola di blocco `Deny-Web-Postgres-Auto` (Priorità 250)
- **verifica dopo la correzione:** Conferma della presenza esclusiva della regola `Allow-Web-Postgres` tramite `az network nsg rule list`

## Casi ulteriori

### 1. CIDR
- **Fatti osservati:** Spazi di indirizzamento definiti per le subnet (`10.50.10.0/24` e `10.50.20.0/24`).
- **Prove non eseguibili:** Test di connettività inter-subnet tramite pacchetti ICMP senza compute running.

### 2. DNS
- **Fatti osservati:** VNet configurata con risoluzione dei nomi predefinita di Azure.
- **Prove non eseguibili:** Interrogazioni di risoluzione DNS interna con `nslookup` in assenza di macchine virtuali attive.

### 3. Routing
- **Fatti osservati:** Tabella di routing di sistema Azure attiva per il traffico intra-VNet.
- **Prove non eseguibili:** Tracciamento dei saldi di rete con `traceroute` senza interfacce collegate a VM in esecuzione.

### 4. NSG
- **Fatti osservati:** Configurazione, verifica ed eliminazione delle regole di sicurezza tramite CLI e portale.
- **Prove non eseguibili:** Estrazione delle regole effettive (`az network nic list-effective-nsg`) non eseguibile senza VM avviate.

### 5. Servizio non in ascolto
- **Fatti osservati:** Definizione della porta logica (5432) nelle regole di filtraggio dell'NSG.
- **Prove non eseguibili:** Test di handshaking TCP sulla porta del database in assenza del servizio PostgreSQL in esecuzione.

## Cleanup e risultato finale

- **regola autonoma rimossa:** `Deny-Web-Postgres-Auto` eliminata e risorse del laboratorio eliminate tramite cancellazione del Resource Group
- **cleanup verificato:** Conferma dell'eliminazione del gruppo di risorse `$LAB_RG`
- **hash abbreviato e messaggio del commit:** `git commit -m "docs: complete UD05 autonomous lab report"`