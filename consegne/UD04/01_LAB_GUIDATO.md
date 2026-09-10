# Consegna UD04 — Laboratorio guidato

## Contesto anonimizzato

- resource group: rg-cea-storage-d6065bcd
- storage account: stcead6065bcd
- region: italyorth
- tipo e ridondanza: Standard_LRS

## Servizi e configurazione

| Elemento | Configurazione | Motivazione |
|---|---|---|
| Blob container | documents | per tenere in ordine i file |
| access tier | Hot | per file usati spesso |
| accesso pubblico | Disabilitato | per sicurezza |
| trasferimento/TLS | Solo HTTPS | per cifrare i dati |

## Autorizzazione e lifecycle

- **Ruoli e Scope:** Usato Entra ID con Storage Blob Data Contributor sullo storage account.
- **Entra ID vs Shared Key vs SAS:** La chiave dà accesso totale, la SAS è limitata nel tempo, Entra ID usa gli utenti.
- **Lifecycle Rule:** Regola per cancellare i file in documents/temporary dopo 1 giorno.

## Verifiche, costi e cleanup

- **Esiti essenziali:** Caricati e scaricati file, testato il token SAS.
- **Driver di costo:** Gigabyte salvati e richieste fatte.
- **Rimozione e cleanup:** Cancellato il resource group da Azure.

## Rilevanza professionale

Uso Blob Storage per file sciolti via API e Entra ID o SAS per sicurezza anziché le chiavi fisse.