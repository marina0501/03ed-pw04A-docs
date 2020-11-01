==========================
L’analisi dell’applicativo
==========================

Informazioni Generali
*********************

Il progetto, come già in precedenza decritto, si è evoluto e ampliato con aggiunta di nuove informazioni e di caratteristiche non considerate nella scheda di presentazione per l’accesso al master redatta nel mese di novembre (master-progetto-201911-proposta.pdf - https://github.com/Master-MSL/03ed-pw04A-docs/blob/main/doc/PWeducativi/allegatiEDU/master-progetto-201911-proposta.pdf) e nel pitch introduttivo, in cui la decrizione progettuale conservava i tratti e i contenuti della scheda di presentazione.

Fin dal primo colloquio con la Responsabile dell’ufficio e dai moduli acquisiti di richiesta di fornitura materiali si è aggiunto un oggetto nuovo, il copritermo come strumento antinfortunistico, che segue un percorso di fornitura specifico, tempi di richiesta non dettati dalla scansione degli anni scolastici e richiede una valutazione differente.

Successivamente, con lo svolgimento dei colloqui con il personale dell’ufficio, l’attività si è arricchita con la gestione della fornitura delle stoviglie dei refettori, le quali hanno anch’esse come i copitermo tempi di richiesta indipendenti da inizio e fine dell’anno scolastico e per questi oggetti si può compiere il processo inverso di restituzione agli uffici per essere riutilizzate in altri refettori. Questo processo di restituzione può compiersi anche per gli arredi dei plessi in chiusura. 

Il processo di restituzione dei materiali è opposto e complementare alla fornitura: esso richiede la gestione di ulteriori elementi e attività (es. lo stoccaggio del materiale ritirato definendo modi, luoghi e quantità) e per tale motivo non è stato preso in esame nell’evoluzione del progetto che si mantiene nei fatti come gestione delle richieste di fornitura.

Il processo di fornitura, pur inserendo i nuovi oggetti, mantiene una struttura costante di sviluppo che di dipana a partire da invio della richiesta, ricezione e repertoriazione, verifica, istruttoria, valutazione, comunicazione esito e eventuale avvio attività di acquisizione e fornitura materiale. Questa è la traccia che già è stata illustrata e resa nei diagrammi BPMN disegnati con Bizagi e che sarà sviluppata con il pacchetto software scelto per la realizzazione dell’applicativo.

Le informazioni da gestire
**************************

Dalla descrizione del processo è stata rilevata la necessità di gestire e memorizzare le informazioni riguardanti:

Oggetti:
    • arredi-materiali oggetto delle richieste
    • tipologia degli arredi-materiali
    • sedi scolastiche dove i materiali sono richiesti (plesso)
    • istituti comprensivi – circoli didattici comunali
    • ordine scolastico
    • utenti
Eventi o fatti:
    • richiesta
    • sopralluogo
    • istruttoria
    • fornitura

A partire dalla descrizione delle attività e dai moduli utilizzati sono state definite le strutture delle tabelle o data-object con i relativi campi riguardanti gli oggetti e le loro proprietà.

Sono state definite 6 tabelle
    • oggetti_fornitura:
      contiene le informazioni sugli oggetti delle richieste di forniture (tipo, identificativo, descrizione) 
    • plesso
      contiene le informazioni anagrafiche e di struttura riguardanti i punti di servizio scolastico 
    • istituto_circolo
      contiene le informazioni sugli istituti scolastici a cui fanno riferimento i plessi
    • richiesta_scuola
      contiene i dati identificativi della richiesta, la provenienza
    • richiesta_dettaglio
      contiene i dati di dettaglio di ogni richiesta ricevuta ed è strettamente collegata alla tabella “richiesta_scuola”
    • sopralluogo
      contiene i dati identificativi del sopralluogo
    • sopralluogo_dettaglio
      contiene i dati di dettaglio dei sopralluoghi effettuati riguardanti gli oggetti ed è strettamente collegata alla tabella “sopralluogo”
(PW4A_RIGOTTI-arredi-descrizionecampi-V3.ods  https://github.com/Master-MSL/03ed-pw04A-docs/blob/main/doc/PWeducativi/allegatiEDU/PW4A_RIGOTTI-arredi-descrizionecampi-V3.ods)

Tra gli oggetti o fatti da gestire sono compresi anche gli utenti; nel paragrafo iniziale riguardante gli attori del processo sono state definite 5 figure con posizioni operative  differenti che soddisfano i ruoli individuati come necessari per la gestione del processo. 

Il processo non gestisce informazioni riguardanti persone, dunque non è necessario predisporre un archivio degli utenti funzionale al tracciamento delle attività di trattamento dei dati personali. Tuttavia nella definizione dei ruoli operativi è in primo luogo necessario generare utenze e profili di utenza abilitati a svolgere le differenti attività e funzioni del processo componendo un organigramma operativo, realizzato anche nel modello semplificato sviluppato in Bonita che prevede l’organizzazione come una delle componenti costitutive di un’applicazione.

Questa definizione mimimale non è adeguata per la gestione delle richieste provenienti dalle diverse strutture in quanto di ogni richiesta, salvo il fatto di prevedere il campo di indicazione del referente, non si potrebbe conoscere la provenienza. 

Deve dunque essere generato un archivio di utenti, non necessariamente personali ma ad esempio definiti individualmente per struttura o per istituto, in cui la gestione dei flussi informativi sia adeguata a garantire il giusto indirizzamento del pacchetto di dati.

Nel caso di utilizzo dell’applicativo usufruendo del protocollo di accesso al dominio comunale le credenziali sono nominative e pertanto dovrà essere gestito l’archivio nominativo degli utenti abilitati.
Considerando il tipo di informazioni gestite ed il fine dell’attività, la credenziale può essere semplice, formata dai soli user e password, senza necessità di un terzo elemento di controllo (PIN o token) in quanto non deve abilitare all’accesso ad informazioni personali o comunque con profili di riservatezza ed alte esigenze di sicurezza.
