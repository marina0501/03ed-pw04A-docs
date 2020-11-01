===========================================
Primo sviluppo semplificato - Versione Alfa
===========================================

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

