#######################
Evoluzione del progetto
#######################
Nel mese di febbraio è stato redatto un gannt per la programmazione, sviluppo e verifica del progetto in cui erano state considerate 5 fasi a partire dall’avvio, comprendente le attività di analisi iniziale fino alla realizzazione del software e deployment ( obbligo-di-da-arredare-V3.pod  - https://github.com/Master-MSL/03ed-pw04A-docs/blob/main/doc/PWeducativi/allegatiEDU/obbligo-di-da-arredare-V3.pod).

*Il gannt citato ed il successivo sono stati realizzato con ProjectLibre v.1 1.9, applicativo OS con licenza CPAL.; esso permette di rappresentare la gestione di un progetto con riferimenti temporali, di costo, risorse  e oggetti.*

Quanto indicato nel gannt iniziale, a seguito dell’emergenza covid che ha impedito molte delle attività necessarie e previste, non è stato realizzato secondo l’originaria programmazione: il PW ed il relativo cronoprogramma è stato oggetto di un profondo riesame sia nella definizione delle attività che nei tempi di realizzazione, poiché molte delle azioni previste erano programmate in presenza ma la chiusura degli uffici, della sede universitaria e l’assenza dal servizio del personale degli uffici ha impedito la loro realizzazione.

E’ stato dunque costruito un nuovo gannt in cui le attività di sviluppo del pw erano ridefinite alla luce del momento emergenziale ( PW4A_RIGOTTI-arredi-gannt-V2.pod - https://github.com/Master-MSL/03ed-pw04A-docs/blob/main/doc/PWeducativi/allegatiEDU/PW4A_RIGOTTI-arredi-gannt-V2.pod ).

Il nuovo progetto ed il gannt ridefinito non prevedono più la realizzazione del pacchetto applicativo ma la sola analisi del processo e dell’applicativo, l’individuazione delle risorse necessarie e la produzione di una versione alfa iniziale semplificata.

A partire dalle informazioni raccolte nel momento di presentazione del pw per l’accesso al master è stato condotto un primo approfondimento con la responsabile dell'ufficio in Posizione Organizzativa per mezzo di colloqui telefonici o con internet calls; a seguito di questi scambi sono astati acquisiti alcuni modelli oggi in uso per documentazione di progetto.
(PW4A_RIGOTTI-arredi-moduli.zip - https://github.com/Master-MSL/03ed-pw04A-docs/blob/main/doc/PWeducativi/allegatiEDU/PW4A_RIGOTTI-arredi-moduli.zip )

Da questi primi elementi sono state redatti due documenti iniziali di analisi: 

- una prima scheda riguardante i dati da gestire con tipo e formato delle informazioni. (PW-4A_descrizionecampi-arrediscolastici.ods - https://github.com/Master-MSL/03ed-pw04A-docs/blob/main/doc/PWeducativi/allegatiEDU/PW-4A_descrizionecampi-arrediscolastici-V1.ods)

- successivamente è stata sviluppata una rappresentazione grafica bpm del processo tramite Bizagi in cui sono stati rappresentati il processo principale ed i cinque subprocessi che lo compongono (pw4A_RIGOTTI-arredi-V2.bpm -
 https://github.com/Master-MSL/03ed-pw04A-docs/blob/main/doc/PWeducativi/allegatiEDU/PW4A_RIGOTTI-arredi-v2.bpm)

*I due diagrammi sono stati realizzati con la versione base di Bizagi Modeler, applicativo con licenza tipo FREEMIUM,  che prevede di offrire gratuitamente una versione di base di un prodotto proprietario (prevalentemente software proprietario) ed eventualmente nel proporre a pagamento funzionalità aggiuntive.*

Passo successivo è stata la ricerca e individuazione del software gestionale adeguato per lo sviluppo del pacchetto di gestione del processo oggetto del pw.
In considerazione del contenuto del master sono stati considerati due prodotti: Bonita BPM e ODOO.

BONITA BPM
----------

Bonita BPM è un software open source in cui sono riunite la funzione di modellazione dei processi BPMN e la funzione di LCPD (Low-Code Development Platform) che permette di sviluppare applicazioni da semplici interfaccia grafiche combinate al modello di processo. 
Esso è stato sviluppato nel 2001, è di proprietà della società francese Bonitasoft ed è attiva una community sia di condivisione di progetti che di sviluppo.
Bonita è scritto in Java su piattaforma di sviluppo open source Eclipse (licenza EPL); comprende componenti scritte con Groovy (o *JSR 241*), linguaggio di programmazione a oggetti per la piattaforma Java che usa una sintassi a parentesi graffe simile a Java
Bonita è suddiviso in più componenti
    • Studio, interfaccia di creazione dei diagrammi, multi-piattaforma ed è il pacchetto scaricato dal sito di Bonitasoft; permette di creare collegamenti con sistema informativo con servizi mail, gestione dei contenuti, database. 
    • BPM Engine che gestisce e coordina, esegue le attività del processo, permette i collegamenti con i db esterni tramite le API esposte e per il suo ruolo di interconnessione con pacchetti esterni è rilasciato con licenza LGPL; sviluppato in Angular JS 
    • Bonita Portal, applicazione web con interfacce grafiche costruite in base alla differente modalità di utilizzo (utente finale o amministratore), è il destinatario dei processi che attraverso di esso divengono gestibili dagli utenti;
    • UI Designer, strumento per comporre le interfacce grafiche, sviluppato in Bootstrap e Angular JS
    • Continuus delivery, componente di provisioning automatico sui servizi server di Amazon (AWS)
In Bonita è presente un db relazionale su cui sviluppare query sql gestito tramite la componente Engine e può essere collegato anche a differenti db esterni (es. PostgreSQL, My SQL; SQLserver)

*Scheda descrittiva pacchetto applicativo*

===================================== ===============================================================================================================
===================================== ===============================================================================================================
**Denominazione**                     Bonita
**Corporation**                       Bonitasoft
**Licenza**                           GPL2 - LGPL per componente Bonita Engine
**Risorse – requisiti installazione** Multipiattaforma 
** **                                 Windows 32 o 64 bit
** **                                 Linux 32 o 64 bit
** **                                 MacOS 64 bit
** **                                 Necessita di 8 gb di RAM
** **                                 Compatibile con Browser Mozilla, Chrome, Explorer, Edge
**Formato file standard**             .proc
**Formati output-export**             **.bos** – esporta il progetto su singole parti o complessivamente da utilizzare su altre istanze Bonita
** **                                 **.xml** – esporta gli schemi delle organizzazioni
** **                                 **.png** – file immagine di un singolo diagramma
** **                                 **.bpmn** - Business Process Model and Notation
===================================== ================================================================================================================
