# Consegna UD03 — Domande sui concetti

Per ciascuna domanda 1–8 riporta una risposta motivata.


1. L'autenticazione verifica chi sei, mentre l'autorizzazione stabilisce se hai i permessi per compiere una specifica azione su una risorsa.

2. I ruoli Microsoft Entra gestiscono gli oggetti del tenant, mentre i ruoli Azure RBAC gestiscono le risorse all'interno delle sottoscrizioni e dei resource group.

3. Il principal, la role definition e lo scope.

4. Perché rispetta il principio del minimo privilegio: limita i permessi di lettura al solo progetto interessato ed evita di concedere diritti di scrittura sull'intera sottoscrizione, riducendo l'impatto di eventuali errori.

5. Perché i ruoli ereditati appartengono a uno scope superiore. Per toglierli bisogna modificare l'assegnazione nel punto in cui è stata originariamente creata.

6. i tag sono solo metadati descrittivi utili per organizzare e tracciare le risorse o i costi. Non hanno alcuna funzione di blocco o sicurezza.

7. Il lock CanNotDelete impedisce a chiunque di eliminare la risorsa, ma non blocca le modifiche. Il ruolo Reader, invece, consente solo di leggere e visualizzare le risorse, bloccando qualsiasi modifica o eliminazione tramite RBAC.

8. Perché il budget invia solo notifiche o avvisi al superamento delle soglie impostate; non ha la funzione tecnica di bloccare la creazione di risorse o spegnere i servizi in autonomia.