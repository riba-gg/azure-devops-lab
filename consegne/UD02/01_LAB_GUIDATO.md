# Consegna UD02 — Laboratorio guidato

## Contesto verificato

- Azure Portal accessibile: sì, verificato
- Azure CLI autenticata: sì, verificata
- sottoscrizione corretta verificata senza pubblicarne l'ID: sì (`Azure subscription 1`)
- località scelta e motivo: `italynorth`, scelta per vicinanza geografica e disponibilità dei servizi verificata tramite CLI.

## Ambiente creato

| Elemento | Nome tecnico | Tipo | Località | Scopo |
|---|---|---|---|---|
| Resource group | rg-cea-ud02-e9b60a92 | Microsoft.Resources/resourceGroups | italynorth | Contenitore logico per il ciclo di vita del progetto |
| Rete virtuale | vnet-cea-ud02 | Microsoft.Network/virtualNetworks | italynorth | Infrastruttura di rete con subnet `snet-app` (10.20.1.0/24) |
| Storage account | stceae9b60a92 | Microsoft.Storage/storageAccounts | italynorth | Account di archiviazione temporaneo general purpose v2 |

## Decisioni e verifiche

Le risorse appartengono allo stesso resource group perché condividono lo stesso ciclo di vita: consente di gestirle insieme e di eliminarle con un'unica operazione di cleanup. I tag (course, unit, environment, deleteAfter) servono a classificare le risorse e a tracciarne la scadenza. 

**Confronto portale vs CLI:**
- Azure Portal è ideale per la preparazione iniziale e l'esplorazione visiva delle opzioni.
- Azure CLI è più efficiente per interrogare lo stato, estrarre inventari strutturati e anonimizzare i dati in modo ripetibile.

## Cleanup

- operazione di eliminazione: `az group delete --name "$LAB_RG" --yes --no-wait`
- controllo utilizzato: `az group exists --name "$LAB_RG"`
- risultato finale: `false` (risorsa rimossa con successo)
- eventuale anomalia e soluzione: Nessuna anomalia bloccante riscontrata nella fase di pulizia.

## Rilevanza professionale
L'uso dell'inventario tramite CLI, dei tag descrittivi e la verifica puntuale del cleanup garantiscono che gli ambienti di laboratorio o di test siano completamente tracciabili, privi di risorse "orfane" e gestibili in modo automatizzato e ripetibile, riducendo i costi superflui e i rischi di sicurezza.