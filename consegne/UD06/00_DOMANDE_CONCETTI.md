# UD06 — Risposte alle domande sui concetti

## 1.
**Risposta:** Una VM è fatta da diversi pezzi che lavorano insieme: l'Image che dà il sistema operativo di base, la Size che decide quanta potenza di calcolo (CPU e RAM) ho a disposizione, l'OS Disk dove gira il sistema operativo, eventuali Data Disk per metterci i file o i database, e la NIC che collega la macchina alla rete virtuale con il suo indirizzo IP.

## 2.
**Risposta:** Perché l'IP pubblico serve solo a dare un indirizzo valido su Internet, ma poi il traffico deve superare i blocchi dell'NSG, i firewall interni del computer e soprattutto il servizio (come un server web) deve essere acceso e in ascolto su quella specifica porta.

## 3.
**Risposta:** L'Availability Zone separa le macchine su data center fisicamente diversi per proteggerci se cade un intero palazzo. L'Availability Set distribuisce le VM su componenti diversi dello stesso data center per non avere problemi durante le manutenzioni o i guasti hardware. Il VM Scale Set invece gestisce un gruppo di macchine coordinate che possono aumentare o diminuire in base al carico di lavoro.

## 4.
**Risposta:** Lo scale up significa prendere una macchina già esistente e renderla più potente (più CPU o RAM), ma ha dei limiti fisici e se quella macchina muore sei bloccato. Lo scale out vuol dire aggiungere altre macchine uguali che si dividono il lavoro, rendendo il sistema molto più elastico e resistente.

## 5.
**Risposta:** Azure Monitor Autoscale controlla delle metriche e se supera una certa soglia per un po' di tempo, aggiunge o toglie automaticamente le macchine nel Scale Set. I limiti minimo e massimo servono a fare in modo che ci sia sempre almeno una macchina accesa e che il sistema non si metta a crearne troppe all'improvviso facendoci spendere un patrimonio.

## 6.
**Risposta:** L'App Service Plan è l'infrastruttura di base che definisce le risorse disponibili. La Web App è invece l'applicazione vera e propria che carichiamo sopra quel piano e che sfrutta quelle risorse per funzionare.

## 7.
**Risposta:** L'Azure Monitor Autoscale è una regola generale basata su metriche e soglie che configuriamo noi. L'App Service Automatic Scaling è invece un meccanismo più integrato e gestito direttamente dalla piattaforma PaaS che si adatta in modo automatico al traffico web usando metriche specifiche dell'applicazione.

## 8.
**Risposta:** Le Metrics sono numeri che cambiano nel tempo e servono per vedere i trend e far scattare gli avvisi. I Logs sono invece dei file di record dettagliati che possiamo interrogare per capire esattamente che cosa è successo e risalire alla causa di un errore.

## 9.
**Risposta:** Il Recovery Services vault è il contenitore sicuro dove gestiamo i backup. Dentro ci associamo una Backup policy che decide quando fare i salvataggi e per quanto tempo tenerli. I recovery point sono i singoli punti di ripristino concreti che si creano seguendo quella regola e che possiamo usare per recuperare i dati.

## 10.
**Risposta:** L'High Availability serve per far continuare a funzionare il sito se si rompe un pezzo. Il Backup serve se cancello un file per errore e devo recuperare la versione di ieri. Il Disaster Recovery serve se succede un evento catastrofici che distrugge un intero data center e devo riaccendere tutto in un'altra regione geografica.

## 11.
**Risposta:** L'RPO (Recovery Point Objective) misura quanti dati possiamo permetterci di perdere in termini di tempo (es. gli ultimi dati di un'ora fa). L'RTO (Recovery Time Objective) misura invece quanto tempo ci mettiamo a riaccendere e rendere operativo il servizio dopo un guasto. Sono diversi perché uno riguarda la perdita di dati e l'altro il tempo di stop.

## 12.
**Risposta:** Perché quando una VM è semplicemente deallocata non paghiamo più la potenza di calcolo, ma continuano a esistere e a generare costi le risorse che restano salvate o collegate, come i dischi rigidi, gli indirizzi IP pubblici riservati o i backup associati.