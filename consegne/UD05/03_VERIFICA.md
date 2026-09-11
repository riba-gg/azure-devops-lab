# Consegna UD05 — Verifica

## Parte A — Scelta singola

Per le domande 1–8 riporta risposta e motivazione.

1. B
2. B
3. B
4. A
5. A
6. A
7. B
8. B

## Parte B — Risposte brevi

9. È necessario per accogliere nuove risorse senza esaurire lo spazio IP ed evitare riprogettazioni di rete.

10. NSG: filtra il traffico di rete in base a protocolli, porte e indirizzi IP. Route: definisce il percorso dei pacchetti all'interno o all'esterno della VNet.
DNS: risolve i nomi di dominio in indirizzi IP numerici.

11. Se un pacchetto in entrata è consentito, la risposta di ritorno in uscita viene permessa automaticamente dallo stato della connessione

12. centralizza le regole di sicurezza per tutte le risorse collegate alla subnet, evitando la configurazione su ogni singola NIC.

13. Si possono verificare la configurazione IP, l'associazione alla subnet e la configurazione della risorsa ma manca la verifica delle regole effettive (list-effective-nsg) e la prova di connettività attiva tramite traffico reale

## Parte C — Caso situazionale

14. Azure valuta le regole NSG in base al valore numerico della priorità, dal più piccolo al più grande

15. Modificare la priorità della regola di permesso portandola a un valore inferiore a 150

16. Utilizzare lo strumento IP Flow Verify per verificare quale regola di sicurezza o percorso sta bloccando il traffico verso la macchina virtuale.

