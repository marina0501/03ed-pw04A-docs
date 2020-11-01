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

A partire dalla descrizione delle attività e dai moduli utilizzati sono state definite 6 tabelle o data-object con i relativi campi riguardanti gli oggetti e le loro proprietà.

Elenco tabelle:
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

Interfacce e output gestionali
******************************

L’utilizzo di Bonita o l’eventuale successiva scelta di sviluppare il pacchetto sulla piattaforma ODOO consentono la realizzazione di una procedura web-online in cui le interfacce sono moduli web per inserimento e gestione di dati residenti su un server.

L’invio delle richieste potrebbe essere anche realizzato attraverso l’inoltro via mail di documenti allegati contenenti le informazioni necessarie per la presentazione dell’istanza: tale modalità potrebbe sembrare più accessibile ed usabile per gli utenti esterni, non porrebbe il problema di gestire autenticazioni e accessi all’applicativo da parte di questi stessi utenti esterni. 
Questa prassi, pur con la definizione di modelli da utilizzare per l’invio in formati standard e la diffusione dettagliata e motivata delle modalità operative da utilizzare, non garantisce dall’utilizzo di modelli non conformi, dall’utilizzo non corretto degli stessi modelli o ancora dalla modifica della struttura dei modelli da parte degli utenti in considerazione delle proprie esigenze e necessità operative. Inoltre questo modello operativo presuppone un’attività di input specifica, manuale o automatizzata: in questo secondo caso implica la scrittura di una funzione per gestire l’acquisizione delle informazioni contenute nei documenti ricevuti.

La web form è dunque la maniera preferibile e maggiormente efficace per la gestione del processo.

Per l’input delle istanze sono dunque stati definiti i requisiti dei dati per 4 modelli corrispondenti alle richieste riguardanti oggetti e/o ordini scolastici differenti

Form Input previste:
    • arredi scuole preobbligo e nido
    • arredi scuole obbligo. 
    • stoviglie
    • copritermo

Nelle form saranno presenti e compilabili i campi utili per l’identificazione della provenienza e della struttura richiedente e le informazioni sugli oggetti di cui si chiede la fornitura o altra attività.
Un’ultima webform di input è stata definita per l’attività di sopralluogo utilizzabile e compilabile dalle addette dell’ufficio. Il dettaglio di queste webform è presente nel file PW4A_RIGOTTI-arredi-modelli-Input.ods - https://github.com/Master-MSL/03ed-pw04A-docs/blob/main/doc/PWeducativi/allegatiEDU/PW4A_RIGOTTI-arredi-modelli-Input.ods

Anche le funzioni di verifica e istruttoria delle istanze possono essere svolte per mezzo di webform, utilizzabili dalle adette e dalle figure responsabili dell’ufficio secondo i loro profili  e ambiti di responsabilità. Queste maschere si compongono di elementi in sola lettura e elementi in aggiornamento, che non potranno o dovranno essere obbligatori per consentire l’esecuzione dell’istruttoria anche in modo parziale o distribuita secondo un iter operativo distribuito in fasi. 

Per le attività di ufficio utili a rendicontazione, reportistica, analisi delle forniture ecc., sono da sviluppare delle webform con la visualizzazione di elenchi riguardanti le richieste, gli oggetti, le forniture, i sopralluoghi. 
Il dettaglio di queste webform per gli uffici è presente nel file PW4A_RIGOTTI-arredi-modelli-Istruttoria.ods - https://github.com/Master-MSL/03ed-pw04A-docs/blob/main/doc/PWeducativi/allegatiEDU/PW4A_RIGOTTI-arredi-modelli-Istruttoria.ods

Considerate le attività definite nella bpm di richiesta e istruttoria rimane da esaminare la chiusura del processo con le comunicazioni degli esiti della richiesta al termine dell’istruttoria. 
Una richiesta giunta al termine dell’iter è sempre origine di una comunicazione all’istituto richiedente di esito dell’istruttoria e di compimento della fornitura a seguito di esito positivo. 

La comunicazione per mezzo di webform non è adeguata alle necessità di avviso sull’esito istanza poiché la scuola utilizza l’applicativo in modo occasionale e rarefatto, dunque dovrebbe essere notificata con qualche altro mezzo la presenza della comunicazione. 
Strumento di comunicazione più efficace nel rapporto con le segreterie ed utilizzabile da Bonita è il messaggio mail, il cui indirizzo è richiesto e presente nella tabella delle scuole. Nella mail inoltre è possibile dettagliare le motivazioni dell’esito dell’istanza e l’eventuale dettaglio di fornitura; oppure è possibile allegare un documento in cui sono esplicitati esiti dell’istruttoria e tutte le informazioni utili per motivare la decisione e comunicare l’avvio della procedura di fornitura.

Ultima attività necessaria è la produzione degli output necessari ai vari uffici competenti per avviare le attività utili al soddisfacimento delle richieste approvate: acquisto, fornitura, riparazione, ritiro. 
Per la fornitura degli elementi di arredo la comunicazione deve essere distinta tra

    • le richieste di arredo, raggruppate secondo criteri di data, tipologia o di altro genere secondo le esigenze degli uffici; per esse deve prodursi elenco delle richieste approvate con i dati degli oggetti da acquisire (tipo, descrizione e quantità) ed i dati dei beneficiari utili per la distribuzione:
    • fornitura, sostituzione o riparazione di copritermosifoni, devono produrre un ordine puntuale sulla richiesta poiché le richeiste sono occasionali e devono essere soddifatte con il termine dell’istruttoria essendo dispositivi di protezione e la loro mancanza o non regolarità potrebbe determinare l’impossibilità di fruire di spazi o svolgimento di attività.

Output simile a quello prodotto per richieste di fornitura arredi è l’elenco delle riparazioni; come nelle forniture anche le riparazioni sono raggruppate in un documento che deve essere considerato l’esplicitazione e dettaglio dell’ordine indirizzato all’affidatario del servizio.

I documenti descritti devono essere trasmessi a diversi destinatari con finalità differenti ma per tutti deve garantirsi accessibilità e usabilità: quindi ogni documento, sia esso un elenco o un ordine singolo, deve essere predisposto in formato standard interoperabile, utilizzabile ed elaborabile su altri applicativi o software; in ogni caso il documento dovrà contenere sia i dati degli oggetti da acquisire che i dati dei beneficiari dell’attività. 

Gli output di dati aperti
*************************

Nei pochi incontri o colloqui avuti con la responsabile e con le addette dell’ufficio è stato introdotto l’argomento sulla reportistica di tipo informativo ma non è stato approfondito nel merito; attualmente l’ufficio realizza reportistiche per il management interno sulle attività di fornitura arredi per programmazione attività e acquisti. Considerando le prassi operative attuali, per la produzione di questa reportistica è necessaria un’attività di composizione di informazioni distribuite in differenti documenti e supporti. 
Sono invece mancanti reportistiche con standard open data. 

Nel corso dello sviluppo dell’applicativo sarà indispensabile pertanto affrontare questo argomento con la nuova responsabile dell’ufficio e con le addette: a beneficio di tutte sarà necessario in primo luogo introdurre l’argomento illustrando natura e funzioni dei dati aperti, le prassi del Comune di Torino in questo ambito e l’importanza di predisporre e rendere pubbliche le informazioni dell’attività; secondo e più importante confronto riguarderà i dati da rendere pubblici ed in quali modalità.

In questo stato del progetto posso solo ipotizzare un panorama di sviluppo nel quale le attività e le informazioni gestite possano essere rese pubbliche sotto forma di dati aperti.
Come descritto nella sezione riguardante le informazioni gestite, il progetto tratta dati riguardanti oggetti di arredo, istituzioni scolastiche e plessi, documenti e iter di istruttoria e utenti; la specifica attività dell’ufficio riguarda la fornitura degli arredi e di altri oggetti alle scuole.
I report potrebbero dunque essere dedicati a rendere pubbliche le informazioni sull’entità delle forniture di materiali per ogni anno scolastico ed essere dettagliati per tipo gestione, plesso, autonomia scolastica, tipologia di oggetto, tipo di fornitura realizzata, motivazioni, ecc.

Non è opportuno invece che dalle informazioni gestite dall’ufficio siano prodotti dataset con elenchi di scuole. Le istituzioni scolastiche ed i plessi sono argomento specifico di altri uffici della Divisione Servizi Educativi che si occupano di dimensionamento e gestione del patrimononio immobiliare scolastico. I dati in possesso dell’ufficio Acquisto Beni sono i soli dati utili per la propria attività gestionale, mentre le informazioni native dell’ufficio che si occupa del dimensionamento e del patrimonio scolastico sono più complete, dettagliate ed adeguate alla pubblicazione. 

Da Bonita e anche nel caso di adozionedi ODOO, possono essere estratti report in formati adeguati per la pubblicazione aventi caratteristiche di dato aperto come il csv.
Questi dataset in formato open data saranno licenziati CC BY 4.0 https://creativecommons.org/licenses/by/4.0/legalcode.it che è lo standard scelto dall’ente per la pubblicazione dei suoi open data sul repository comunale raggiungibili dalla url:  http://aperto.comune.torino.it/  

Dei dataset sarà predisposta la scheda descrittiva con i metadati seguendo il modello cittadino reperibile alla url: http://aperto.comune.torino.it/dataset/dataset-di-prova

Questa soluzione produce data set di livello “3 stars” della Tim Berners-Lee scale.
Il file csv è un formato pubblico (OL), elaborabile (RE) ed aperto (OF): un dataset csv adeguatamente corredato dei metadati di supporto, consente l’elaborazione dei dati in esso contenuti tramite un eleboratore previo intervento umano per la scrittura del programma destinato all’utilizzo delle informazioni.

