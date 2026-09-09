# Consegna UD03 — Laboratorio guidato

## Contesto anonimizzato

- sottoscrizione e tenant verificati: sì (`f6a1c8a7-7d17-4a29-85cf-24350131bc1a`)
- percorso Entra eseguito: A
- resource group temporaneo: `rg-cea-identity-551aae`

## Identità e assegnazione RBAC

| Principal anonimizzato | Ruolo | Scope | Diretta/ereditata | Motivo |
|---|---|---|---|---|
| Gruppo di sicurezza (`grp-cea-readers-551aae`) | Reader | Resource Group (`rg-cea-identity-551aae`) | Diretta | Applicare il minimo privilegio per la sola consultazione del progetto temporaneo |

Descrivi gli oggetti letti o creati, l'autorizzazione necessaria e l'accesso effettivo osservato:
Sono stati creati un utente di test e un gruppo di sicurezza in Microsoft Entra ID (Percorso A). Successivamente è stata creata un'assegnazione RBAC a livello di resource group per concedere i permessi di sola lettura (`Reader`) al gruppo, verificando che il principal erediti i diritti senza disporre di privilegi di scrittura.

## Governance e costi

- tag e significato: `course=cloud-engineer-academy`, `environment=lab`, `deleteAfter` (utilizzati per metadati descrittivi e organizzativi, non per bloccare operazioni).
- lock e operazione impedita: `lock-cea-delete` di tipo `CanNotDelete`, che impedisce l'eliminazione accidentale del resource group.
- stato di Cost Analysis: consultato sullo scope del resource group (inizialmente a zero in assenza di risorse a consumo).
- budget creato o limitazione documentata: `budget-cea-551aae` con soglia di allerta all'80%.
- motivo per cui il budget non blocca la spesa: invia solo notifiche e avvisi ma non ha la funzione tecnica di arrestare servizi o bloccare la creazione di risorse.

## Cleanup

Registra rimozione degli oggetti temporanei e verifica finale del resource group:
- Rimozione del lock via CLI.
- Eliminazione del resource group verificata con `az group exists` (esito `false`).

## Rilevanza professionale

Spiega come distinguere autenticazione, autorizzazione RBAC e blocco di governance:
L'autenticazione verifica l'identità dell'utente che accede al sistema. L'autorizzazione tramite Azure RBAC stabilisce quali azioni specifiche il principal può compiere su un determinato scope. I lock e le policy di governance aggiungono controlli di protezione e conformità che limitano le operazioni a prescindere dai diritti RBAC assegnati.