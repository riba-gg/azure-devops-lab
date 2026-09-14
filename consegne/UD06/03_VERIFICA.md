## Parte A

1. A
2. B
3. B
4. A
5. B
6. B
7. A
8. B

## Parte B

9. L'Availability Zone mette le istanze in datacenter fisicamente separati ma dentro la stessa regione, quindi se un intero datacenter ha un problema le altre zone restano su. L'Availability Set invece lavora dentro lo stesso datacenter, ma separa le VM su hardware diverso e su cicli di aggiornamento diversi, così non si spengono tutte insieme per un guasto o una manutenzione. Il VM Scale Set è pensato per gestire tante istanze uguali insieme, e in più permette di farle crescere o ridurre automaticamente in base al carico.

10. Scale up vuol dire dare più potenza alla stessa macchina. Scale out invece vuol dire aggiungere altre macchine, quindi il carico si divide tra più istanze invece che stare tutto su una sola.

11. Con l'Autoscale di App Service sei tu a impostare le regole. Con l'Automatic Scaling invece è la piattaforma stessa che si regola da sola in base al traffico, senza che tu debba configurare soglie.

12. La High Availability serve a far sì che il servizio resti su anche se un pezzo si rompe. Il Backup serve a tornare indietro nel tempo se perdi o rovini dei dati. Il Disaster Recovery invece entra in gioco quando il problema è grosso e serve a far ripartire tutto altrove.

13. Il Recovery Services vault è il posto dove Azure tiene organizzati tutti i backup. La Backup policy è la regola che dice ogni quanto fare il backup e per quanto tempo tenerlo. Il Recovery point è uno punto preciso nel tempo a cui puoi tornare quando fai un ripristino.

14. L'RPO ti dice quanti dati puoi permetterti di perdere, misurato in tempo. L'RTO ti dice invece quanto tempo puoi stare fermo prima che il servizio torni su.

## Parte C

15. Qui vince la regola Deny-HTTP perché ha priorità 100 contro 300 e in Azure il numero più basso viene controllato per primo. Quindi il traffico HTTP viene bloccato.

16. Per sistemarlo basta cambiare la priorità di Allow-HTTP mettendola più bassa di 100, così viene valutata prima di quella che blocca. Per controllare che funzioni davvero, userei IP Flow Verify di Network Watcher per vedere se Azure dice Allowed.