## Piano di indirizzamento

| Elemento | CIDR | Scopo | Sovrapposizioni |
|---|---|---|---|
| VNet | `10.50.0.0/16` | Rete principale del laboratorio | Nessuna |
| subnet web | `10.50.10.0/24` | Segmento per risorse frontend | Nessuna |
| subnet data | `10.50.20.0/24` | Segmento per risorse database | Nessuna |

## NSG e associazioni

| NSG | Scope associato | Regola | Priorità | Origine | Porta | Esito |
|---|---|---|---:|---|---|---|
| `nsg-data` | Subnet `snet-data` | `Allow-Web-Postgres` | 300 | `10.50.10.0/24` | `5432` | Allow |

## Verifica effettiva

Ho creato le interfacce di rete `nic-web-01` e `nic-data-01` collegandole alle rispettive subnet. Dalle verifiche ho preso nota del fatto che l'interrogazione delle regole effettive tramite `az network nic list-effective-nsg` restituisce un errore se la NIC non è associata a una macchina virtuale attiva. Ho comunque verificato la corretta associazione dell'NSG e la presenza della regola e delle route di sistema, ma per validare il traffico effettivo sarà necessario attendere la creazione di un workload.

## Costi e cleanup

Ho creato le risorse di rete nel resource group di test. Poiché non sono state avviate macchine virtuali, i costi sono stati nulli. Alla fine ho eseguito il comando di eliminazione per ripulire completamente l'ambiente.

## Rilevanza professionale

Ho scelto di procedere definendo prima il piano CIDR e le regole di sicurezza perché prevenire conflitti di indirizzamento e configurare i perimetri di rete prima del deployment evita modifiche strutturali complesse in seguito.