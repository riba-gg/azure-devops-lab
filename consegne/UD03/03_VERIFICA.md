# Consegna UD03 — Verifica

## Parte A — Scelta singola

1. B
2. D
3. C
4. B
5. B
6. C
7. B
8. B

## Parte B — Risposte brevi

9. Assegnare i ruoli ai gruppi è meglio perché gestisci tutto centralmente: se un utente cambia team basta spostarlo nel gruppo senza toccare le assegnazioni su Azure.
10. Il ruolo Microsoft Entra gestisce gli utenti nel tenant, mentre il ruolo Azure gestisce le risorse sulle sottoscrizioni.
11. Ha accesso da Contributor perché vince il permesso più ampio ereditato dalla sottoscrizione rispetto a quello restrittivo sul resource group.
12. Controllo l'account con az account show, verifico i ruoli con az role assignment list, controllo di essere sullo scope giusto e guardo se ci sono lock o policy.
13. Il tag deleteAfter è solo un promemoria testuale, il lock CanNotDelete blocca fisicamente la cancellazione, e il budget manda solo notifiche sui costi senza bloccare nulla.

## Parte C — Caso situazionale

14. Hanno dato Contributor su tutta la sottoscrizione invece di dare solo Reader sulla VNet, violando il minimo privilegio.
15. Ruolo Reader direttamente sul resource group della VNet.
16. Non riesce ad assegnare il ruolo perché Contributor non dà i permessi di gestione accessi, e non riesce a eliminare perché c'è un lock CanNotDelete attivo.