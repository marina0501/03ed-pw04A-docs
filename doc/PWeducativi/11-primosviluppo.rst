###########################################
Primo sviluppo semplificato - Versione Alfa
###########################################

Introduzione e BPM
******************
Considerata la complessità di sviluppo e i problemi dovuti alla emergenza che hanno ostacolato il percorso di apprendimento su Bonita, si è optato per la costruzione di una procedura semplificata e resa il più possibile lineare, in cui l’istanza della scuola contiene la richiesta per un solo oggetto: il tal modo il business data model comprende un solo business object in cui sono definiti tutti i campi dei valori da gestire nei successivi tasks necessari per giungere alla fornitura dell’arredo; i campi del business object sono utilizzati e gestiti con l’evoluzione del processo nelle varie attività definite nel diagramma.
Il nuovo processo, disegnato direttamente in BonitaBPM a partire dal digramma Bizagi, si sviluppa su un unico flusso senza subprocessi (PW4A-arredi-semplificato-3.0.bos - https://github.com/Master-MSL/03ed-pw04A-docs/blob/main/doc/PWeducativi/allegatiEDU/PW4A-arredi-semplificato-3.0.bos)

**INSERIRE IMMAGINE**

Business Data Model
*******************
La creazione della struttura della base dati si esegue dalla funzione di “Define”, in Development del Business data model. Deve essere in primo luogo generato il Business data model, definito come New package che può essere rinominato, al quale è immediatamente assegnato una primo Business Object. A questo punto devono essere definiti gli Attributes (o campi) del business object: per questi elementi devono essere indicate la descrizione, la tipologia, obbligatorietà. 

Per ogni business object Bonita definisce un  campo persistenceID con la funzione di identificativo del record presente nel Business object.
É stato pertanto definito il Business data model UPO.arredi1.model e al suo interno un Business Object denominato arredi1 in cui sono presenti i seguenti attributi o campi:

============================= =========== ========= =======================
Name                          Type        Lenght    Mandatory (si/no)
============================= =========== ========= =======================
scuo_autonomia_scolastica     Testo       255       si
scuo_ordine_scolastico        Testo       20        si
scuo_plesso_denominazione     Testo       255       si
scuo_plesso_indirizzo         Testo       255       si
scuo_tipo_gestione            Testo       64        si
scuo_circoscrizione           Intero      255       si
oggetto_descrizione           Testo       255       si
oggetto_tipologia             Testo       30        si
richiesta_tipo                Testo       255       si
richiesta_n_mancante          Integer               si
richiesta_n_in_carico         Integer               si
richiesta_n_esubero           Integer               Si
richiesta_stato_arredo        Testo       20        si
richiesta_data                Data only             si
richiedente                   Testo       255       si
richiesta_note                Testo       512       no
richiesta_repertorio          Testo       64        no
sopralluogo_data              Data only             no
richiesta_esito_data          Data only             no
richiesta_esito               Boolean               no
richiesta_esito_motivazione   Testo       64        no
richiesta_ricezione_corretta  Boolean               no
richiesta_ricezione_esitonote Testo       512       no
oggetto_n_fornitura           Integer               no
oggetto_data_fornitura        Data only             no
============================= =========== ========= =======================

Descrizione BPM
***************

Gli attributes o campi del business object descritto sono stati assegnati ai task che si susseguono in procedura:

**Task 1 Avvio:** ProduzioneDocumentoIstanzaFornitura – Inoltro da parte della scuola (ruolo addetto-scuola) della richiesta di arredi:

+---------------------------+ 
| scuo_autonomia_scolastica |
+---------------------------+
| scuo_ordine_scolastico    |
+---------------------------+
| scuo_plesso_denominazione |
+---------------------------+
| scuo_plesso_indirizzo     |
+---------------------------+
| scuo_tipo_gestione        |
+---------------------------+
| scuo_circoscrizione       |
+---------------------------+
| oggetto_descrizione       |
+---------------------------+
| oggetto_tipologia         |
+---------------------------+
| richiesta_tipo            |
+---------------------------+
| richiesta_n_mancante      |
+---------------------------+
| richiesta_n_in_carico     |
+---------------------------+
| richiesta_n_esubero       |
+---------------------------+
| richiesta_stato_arredo    |
+---------------------------+
| richiesta_data            |
+---------------------------+
| richiedente               |
+---------------------------+
| richiesta_note            |
+---------------------------+

**Task 2:** RicezioneProtocollazioneInserimentoRepertorio – Task di tipo Human - Ricezione dell’istanza con registrazione repertorio da parte dell’addetto-ricezione :

+---------------------------+
| richiesta_repertorio      |
+---------------------------+

**Task 3:** Prime Verifiche Istanza – Task di tipo Human - Verifica correttezza compilazione eseguita dalle due figure addetto-ricezione o addetto-istruttoria:

+-------------------------------+
| richiesta_ricezione_corretta  |
+-------------------------------+
| richiesta_ricezione_esitonote |
+-------------------------------+

**Gateway Documento Corretto?:** Distinzione percorso su esito verifica correttezza (campo booleano richiesta_ricezione_corretta si/no)

====== =====================================
Esito  Azione       
====== =====================================
Si     Verso Task 4A Esecuzione Istruttoria      
No     Verso task 4b Richiesta correzione      
====== =====================================      

**Task 4A:** Esecuzione Istruttoria – Task di tipo Human - Avvio dell’istruttoria sui contenuti dell’istanza riguardo ammissibilità, possibilità e modi fornitura:

+-----------------------+
| richiesta_esito_data  |
+-----------------------+
| richiesta_esito       |
+-----------------------+
| sopralluogo_data      |
+-----------------------+
| oggetto_n_fornitura   |
+-----------------------+
In questa versione semplificata l’addetto alla gestione dell’istruttoria facente parte dell’organizzazione ufficio arredi, compila i campi per giungere alla definizione della fornitura.

**Task 5:** Esito richiesta – Task di tipo Human - al termine dell’istruttoria viene compilato il campo con le motivazioni dell’esito istruttoria d apate del responsabile dell’ufficio (arredi-responsabile)

+-----------------------------+
| richiesta_esito_motivazione |
+-----------------------------+

**Gateway Distribuzione esito:** distinzione dei percorsi delle comunicaizoni per esiti positivi dell’istruttoria con fornitura materiale e esiti negativi in cui la richiesta di fornitura è respinta

====== =============================================
Esito  Azione       
====== =============================================
Si     Verso gateway esito positivo      
No     Verso task 7 Produzione comunicazione esito      
====== =============================================

**Gateway Esito positivo:** gateway parallelo in cui si duplicano informazioni per i due task successivi pe rinvio della comunicazione riguardante l’esecuzione della fornitura a scuola richiedente e ufficio competente 

+---------------------------------------------------+
| Verso task 6B Produzione comunicazione fornitura  |
+---------------------------------------------------+
| Verso task 6A invio ufficio interno               |
+---------------------------------------------------+

**Task 6A:** Invio ufficio interno – task di tipo Service - si produce messaggio e-mail verso ufficio interno per predisposizione delle attività per realizzazione della fornitura verso  Evento finale “Destinatario interno per acquisti”

Il task produce messaggio con Connectors in “comunicaFornituraUfficio” da service mail Google 20037218@studenti.uniupo.it, SMTP host: smtp.gmail.com, SMTP port: 465

**Task 6B:** Produzione comunicazione fornitura – task di tipo Service - si produce messaggio e-mail verso scuola per comunicazione dell’esito postivo della richiesta e della prossima realizzazione fornitura verso Evento finale “Comunicazione fornitura”

Il task produce messaggio con Connectors in “inviaComunicazioneFornitura” da service mail Google 20037218@studenti.uniupo.it, SMTP host: smtp.gmail.com, SMTP port: 465

**Task 7:** Produzione comunicazione esito – task di tipo Service - si produce messaggio e-mail verso scuola per comunicazione dell’esito negativo della richiesta verso Evento finale “Ricezione esito negativo”

Il task produce messaggio con Connectors in “InviaRichiestarespintaEmail” da service mail Google 20037218@studenti.uniupo.it, SMTP host: smtp.gmail.com, SMTP port: 465

**Task 4B:** Richiesta correzione – task di tipo Service - si produce messaggio e-mail verso lane scuola per richiesta integrazione istanza 

Il task produce messaggio con Connectors in “invioRichCorrezioneIstanza” da service mail Google 20037218@studenti.uniupo.it, SMTP host: smtp.gmail.com, SMTP port: 465

**Task 8:** Correzione documento – task di tipo Service - si produce messaggio e-mail verso lane ufficio per risposta a mail richiesta correzione-integrazione istanza

Il task produce messaggio con Connectors in “invioRichCorrezioneIstanza” da service mail Google silvano.rigotti@comune.torino.it, SMTP host: smtp.gmail.com, SMTP port: 465

**Task 9:** Ricezione correzioni – task di tipo Human - da mail ricevuta correzione delle informazioni salvate con presentazione richiesta su form “correzioneRichiesta”

+---------------------------+
| oggetto_descrizione       |
+---------------------------+
| oggetto_tipologia         |
+---------------------------+
| richiesta_tipo            |
+---------------------------+
| richiesta_n_mancante      |
+---------------------------+
| richiesta_n_in_carico     |
+---------------------------+
| richiesta_n_esubero       |
+---------------------------+
| richiesta_stato_arredo    |
+---------------------------+
| richiesta_data            |
+---------------------------+
| richiesta_note            |
+---------------------------+

Organizzazione
##############

Nel progetto è stata definita l’organizzazione “Comune-arredi-semplificato” avente  un unico gruppo “Ufficio arredi” con 4 ruoli 
addetto-scuola, arredi-addetto-istruttoria, arredi-addetto-registrazione, arredi-responsabile.
Questi ruoli sono assegnati a 4 user-utenti:

- user-scuola con ruolo addetto-scuola,
- addetto-istruttoria con ruolo arredi-addetto-registrazione e arredi-addetto-istruttoria,
- addetto-ricezione con ruolo arredi-addetto-registrazione e arredi-addetto-istruttoria,
- arredi-responsabile con ruolo on ruolo arredi-responsabile e arredi-addetto-istruttoria.

L’user arredi-responsabile è anche username per il deploy e amministrazione del pacchetto.

Forms
#####

Per eseguire le gestioni delle attività e dei dati con i tasks descritti di tipo Human sono state generate 6 forms:

- inviorichiesta su start event “ProduzioneDocumentoIstanzaFornitura”
- insrepertorio su task 2 “RicezioneProtocollazioneInserimentoRepertorio”
- verifrichiesta1 su task 3 “Prime Verifiche Istanza”
- esecuzioneIstruttoria su task 4A “Esecuzione Istruttoria”
- fineistruttoria su task 5 “Esito richiesta”
- correzioneRichiesta su task 9 “Ricezione correzioni”

Nelle forms l’utente è abilitato all’aggiornamento dei campi collegati ai tasks presentati nel paragrafo Descrizione BPM. 

Per l’inserimento di alcuni Valori sono stati utilizzati dei widget di tipo “select” con tendina al fine di omogeneizzare l’inserimento di informazioni sui tipi di oggetto e motivazione ella richiesta, ordine scolastico, tipo gestione e circoscrizione del plesso.

Andare oltre la versione semplificata
#####################################

Realizzata la versione alfa con un primo modello semplificato del processo gestione richieste arredi in cui sono gestibili moduli riguardanti un singolo tipo di oggetto oggetto, sarà avviato lo sviluppo della versione disegnata nella BPM Bizagi “PW4A_RIGOTTI-arredi-V2.bpm” - https://github.com/Master-MSL/03ed-pw04A-docs/blob/main/doc/PWeducativi/allegatiEDU/PW4A_RIGOTTI-arredi-v2.bpm -in cui il processo gestirà istanze contenenti richieste riferite a più tipo di oggetti (carrello o lista della spesa) e affidando i diversi task a utenti con profilazione specifica su ruolo.

In questa nuova versione lo sviluppo con Bonita dovrà in primo luogo definire in modo completo il BusinessDataModel seguendo le specifiche descritte nei paragrafi precedenti; il BDM dovrà essere composto da diversi BusinessObject tra loro messi in relazione che dovranno permettere di memorizzare e utilizzare in modo più efficiente ed efficace i dati e le risorse. 
