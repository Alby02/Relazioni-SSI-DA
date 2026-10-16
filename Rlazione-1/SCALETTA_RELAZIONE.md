# Relazione 1 - Scaletta dettagliata e assegnazione

Scaletta di ricerca per sei persone: indica cosa cercare e come organizzarlo, senza anticipare il testo della relazione. Tema npm confermato: phishing al manutentore di chalk/debug. AUR resta il secondo caso; XZ può comparire soltanto come breve menzione.

## Tema e obiettivo

| Nome del gruppo | Titolo | Breve descrizione | Vincolo del professore |
|---|---|---|---|
| Zero Day Zero Voglia | Supply Chain Attacks: quando la fiducia nelle dipendenze diventa una vulnerabilità | Confrontare il phishing al manutentore npm di chalk/debug dell'8 settembre 2025 e le adozioni/aggiornamenti malevoli in AUR segnalati il 12 giugno 2026. | Concentrarsi su pochi meccanismi/casi concreti di compromissione delle dipendenze, evitando una panoramica troppo ampia sulla supply chain. |

**Domanda guida:** come viene abusata la fiducia nel software di terze parti nei due casi, quali rischi ne derivano e quali misure possono ridurli?

**Obiettivo di lunghezza:** circa 5,5 pagine di contenuto, figure comprese, da verificare rispetto ai 15 minuti di lettura attenta. Bibliografia e metodologia GenAI sono apparati separati.

Le voci di terzo livello qui sotto sono tracce operative per la ricerca. Nella relazione possono diventare brevi paragrafi, senza stampare necessariamente tutti i titoli: in 5-6 pagine un eccesso di intestazioni frammenterebbe il testo.

## Struttura e metodo di analisi

La struttura seguente riprende quella **suggerita, non vincolante, dal PDF**: introduzione, descrizione del tema, analisi tecnica, casi reali, conseguenze e impatti, mitigazioni, conclusioni, bibliografia e allegato GenAI.

**Il Cyber Risk Management è il metodo con cui analizzare il contenuto, non l'indice della relazione.** Le quattro fasi ricordate dal gruppo (framing, assessment, mitigation/respond, monitoring) aiutano a ragionare su contesto, rischi e controlli, ma non diventano quattro capitoli obbligatori. Il PDF chiede soprattutto di collegare contesto e asset, minacce, debolezze, tecniche di attacco, rischi e impatti; le mitigazioni restano sintetiche. Il monitoraggio può comparire tra i comportamenti corretti, senza una sezione estesa dedicata.

## Indice dettagliato della relazione

### 1. Introduzione

**Persona 1 · 0,3 pagina**

#### 1.1 Rilevanza del problema e obiettivo

##### 1.1.1 Perché fidarsi di una dipendenza può esporre a un attacco

- Introdurre il problema con un esempio accessibile, senza una panoramica generale di tutte le minacce supply chain.

##### 1.1.2 Domanda guida e casi selezionati

- Presentare chalk/debug e AUR e spiegare lo scopo del confronto.
- Eventuale menzione di XZ in 2-3 righe, senza aggiungere un terzo caso.

### 2. Descrizione del tema e del contesto

**Persona 1 · 0,5 pagina**

#### 2.1 Dipendenze e confini di fiducia

##### 2.1.1 Dipendenze dirette e transitive in npm

- Definire pacchetto, manutentore e account di pubblicazione; indicare chi si fida di chi.

##### 2.1.2 Ricette di build e installazione in AUR

- Definire PKGBUILD e script di installazione; distinguere AUR dai repository ufficiali Arch.
- Chiarire la differenza tra importare una libreria e utilizzare una ricetta per ottenere software.

#### 2.2 Soggetti e asset interessati

##### 2.2.1 Chi può essere esposto

- Distinguere manutentore, sviluppatore, utilizzatore dell'applicazione e utente del sistema.

##### 2.2.2 Che cosa occorre proteggere

- Individuare account di pubblicazione, integrità del software, ambiente locale e asset degli utenti pertinenti ai due casi.
- Esplicitare il contesto: gli stessi componenti possono comportare rischi diversi secondo utilizzo e condizioni di esecuzione.

### 3. Analisi tecnica: funzionamento e debolezze sfruttate

**Persone 2 e 3 · 1,6 pagine complessive, figure incluse**

#### 3.1 npm: dall'account compromesso alla dipendenza malevola

**Persona 2 · 0,8 pagina**

##### 3.1.1 Phishing e abuso dell'autorità di pubblicazione

- Cercare il pretesto e i passaggi del phishing; collegare la debolezza sfruttata al controllo dell'account.
- Distinguere compromissione del publisher e compromissione dell'intero registro.

##### 3.1.2 Percorso dalla release al browser

- Ricostruire account compromesso → versione malevola → dipendenza integrata → bundle browser → comportamento malevolo.
- Definire bundle e verificare le condizioni di attivazione; distinguere browser e server/CLI secondo F1.
- Usare debug@4.4.2 come esempio circoscritto; eventuale diagramma compatto, senza codice di exploit.

#### 3.2 AUR: dalla modifica della ricetta all'esecuzione

**Persona 3 · 0,8 pagina**

##### 3.2.1 Abuso della manutenzione della ricetta

- Cercare come viene ottenuto il controllo nel singolo esempio: non presumere furto di account o phishing.
- Identificare la modifica malevola e il passaggio di fiducia abusato.

##### 3.2.2 Ambiente di esecuzione e privilegi

- Ricostruire ricetta modificata → recupero/esecuzione di codice → asset esposti.
- Distinguere build e installazione, utente e privilegi; non assumere automaticamente permessi amministrativi.

### 4. Casi reali: ricostruzione degli episodi

**Persone 2 e 3 · 1 pagina complessiva**

#### 4.1 chalk/debug, 8 settembre 2025

**Persona 2 · 0,5 pagina**

##### 4.1.1 Cronologia essenziale e componenti coinvolti

- Documentare scoperta, versione esemplificativa coinvolta e comunicazioni del progetto usando F1 e le fonti originali collegate.

##### 4.1.2 Risposta effettivamente adottata

- Riassumere rimozione delle versioni e indicazioni agli utilizzatori, senza anticipare un catalogo di contromisure.

#### 4.2 AUR, segnalazione del 12 giugno 2026

**Persona 3 · 0,5 pagina**

##### 4.2.1 Un esempio documentato entro l'ondata

- Partire da F2 e cercare un solo esempio con segnalazione originale e modifica verificabile.
- Non estendere il lavoro al censimento di tutti i pacchetti.

##### 4.2.2 Evidenze disponibili e risposta del progetto

- Documentare gli interventi attestati e i limiti della ricostruzione.
- Se il singolo esempio non è verificabile, limitarsi al meccanismo attestato dall'avviso, dichiarandolo; non inventare payload, vittime o danni.

**Distinzione tra capitoli 3 e 4:** nel 3 spiegare come funziona l'attacco e quali debolezze sfrutta; nel 4 raccontare brevemente l'episodio documentato, con date e risposta. Non ripetere due volte lo stesso percorso tecnico.

### 5. Conseguenze, impatti e confronto dei rischi

**Persona 4 · 0,9 pagina**

#### 5.1 Dal comportamento malevolo al danno

##### 5.1.1 Rischi e impatti nel caso npm

- Collegare il comportamento documentato agli asset e alle transazioni in criptovalute.
- Separare download, presenza nel progetto, esecuzione e perdite provate; i download non sono vittime.

##### 5.1.2 Rischi e impatti nel caso AUR

- Collegare ambiente e privilegi verificati alle possibili conseguenze su dati e sistema.
- Separare impatti osservati e potenziali; non attribuire all'intera ondata il comportamento di un solo esempio.

#### 5.2 Lettura comparativa secondo il Cyber Risk Management

##### 5.2.1 Collegamento tra asset, minaccia, debolezza e impatto

- Preparare una sola tabella: caso → asset → minaccia → debolezza → tecnica → condizioni di esposizione → rischio/impatto.
- Formulare scenari di rischio motivati, senza percentuali o punteggi arbitrari.

##### 5.2.2 Differenze e incertezze

- Confrontare il passaggio di fiducia abusato e la portata delle conseguenze, senza confronti numerici non omogenei.
- Esplicitare quali conclusioni sono sostenute dalle fonti e quali restano ipotesi.

### 6. Mitigazioni e comportamenti corretti

**Persona 5 · 0,7 pagina**

#### 6.1 Ridurre il rischio prima dell'incidente

##### 6.1.1 Controllo degli account e delle modifiche

- Selezionare poche misure: autenticazione resistente al phishing per i publisher, revisione delle release e delle modifiche a PKGBUILD/script.
- Collegare ogni misura a una debolezza analizzata e indicare chi deve adottarla.
- Accennare ai limiti di firme, checksum e lockfile presi isolatamente.

##### 6.1.2 Attendere prima di adottare nuove release

- Proporre almeno **24 ore dalla pubblicazione per gli aggiornamenti ordinari**, controllando nel frattempo gli avvisi: vedi F3.
- Chiarire che l'attesa riduce l'esposizione iniziale ma non garantisce sicurezza; prevedere eccezioni motivate per patch urgenti.

#### 6.2 Reagire e continuare a controllare

##### 6.2.1 Risposta proporzionata all'esposizione

- Distinguere recupero dell'account del publisher e risposta degli utilizzatori.
- Per npm, richiamare le indicazioni documentate su versioni, cache e ricostruzione dei bundle; per AUR, collegare verifica e ripristino al comportamento del caso scelto.

##### 6.2.2 Controllo degli avvisi e dei cambiamenti

- Accennare al monitoraggio di nuove release, modifiche alle ricette, cambi di manutentore e avvisi ufficiali.
- Indicare chi verifica e quale anomalia richiede una nuova valutazione o una risposta. Integrare il monitoring qui, senza trasformarlo in un capitolo autonomo.

### 7. Conclusioni e discussione

**Persona 6 · 0,5 pagina**

#### 7.1 Risultati dell'analisi

##### 7.1.1 Risposta alla domanda guida

- Riassumere cosa mostrano i due casi sulla fiducia nell'identità del manutentore e nel codice distribuito, usando i risultati già esposti.

##### 7.1.2 Limiti e rischio residuo

- Richiamare le incertezze delle fonti e ciò che le misure non risolvono.
- Chiudere con una riflessione critica, senza introdurre nuovi casi o ripetere tutte le contromisure.

### 8. Bibliografia e sitografia

**Tutti forniscono le proprie fonti; Persona 6 coordina.**

- Inserire in references.bib solo le fonti utilizzate e citarle nei passaggi pertinenti.
- Registrare date di consultazione e distinguere fonti primarie, analisi e deduzioni del gruppo.

### Allegato A. Gestione della GenAI

**Tutti documentano i propri usi; Persona 6 raccoglie i contributi.**

- A.1 Attività supportate e strumenti utilizzati, inclusa questa pianificazione.
- A.2 Prompt significativi effettivamente utilizzati.
- A.3 Verifiche svolte e responsabilità degli autori.

## Assegnazione a sei persone

| Persona | Nome | Parti assegnate | Budget | Integrazione | Stato |
|---|---|---|---|---|---|
| 1 | __________ | 1 e 2: introduzione e descrizione del tema | 0,8 pagina | Perimetro, termini e contesto comune | Da iniziare |
| 2 | __________ | 3.1 e 4.1: tecnica ed episodio npm | 1,3 pagine | Fonti npm e diagramma | Da iniziare |
| 3 | __________ | 3.2 e 4.2: tecnica ed episodio AUR | 1,3 pagine | Verifica dell'esempio e delle condizioni | Da iniziare |
| 4 | __________ | 5: conseguenze e analisi comparativa dei rischi | 0,9 pagina | Collegamenti asset-minaccia-debolezza-impatto | Da iniziare |
| 5 | __________ | 6: mitigazioni e comportamenti corretti | 0,7 pagina | Collegamento delle misure ai rischi | Da iniziare |
| 6 | __________ | 7: conclusioni; bibliografia e allegato | 0,5 pagina | Raccordo finale, apparati e leggibilità | Da iniziare |

**Totale: 5,5 pagine**, apparati esclusi. Ogni autore consegna fonti, date di consultazione e dubbi aperti; la persona 6 coordina gli apparati, non verifica da sola tutto il lavoro.

## Collegamento con i file LaTeX

Questa scaletta aggiorna l'organizzazione della ricerca. I file LaTeX attuali hanno ancora titoli provvisori; la struttura suggerita dal PDF richiede di adattarli quando si imposta l'indice definitivo.

| Contenuto | Destinazione proposta |
|---|---|
| Introduzione | File esistente chapters/01_introduzione.tex |
| Descrizione del tema | File dedicato da predisporre |
| Analisi tecnica | Adattare chapters/02_primo_punto.tex |
| Casi reali | File dedicato da predisporre |
| Conseguenze e impatti | File dedicato da predisporre |
| Mitigazioni e comportamenti corretti | Adattare chapters/03_secondo_punto.tex |
| Conclusioni | File esistente chapters/04_conclusioni.tex |
| Bibliografia | references.bib e chapters/05_bibliografia.tex |
| Allegato GenAI | File dedicato da predisporre |

I nomi attuali non stabiliscono la numerazione finale. Nel LaTeX usare section, subsection e, solo dove utile, subsubsection; la numerazione è automatica. In questa modifica non vengono cambiati i sorgenti della relazione.

## Fonti di partenza

- **[F1] [Advisory del progetto debug: GHSA-4x49-vf9v-38px](https://github.com/advisories/GHSA-4x49-vf9v-38px):** fonte primaria per il phishing dell'8 settembre 2025, debug@4.4.2, condizioni di esposizione browser e indicazioni di risposta. Persone 2, 4 e 5.
- **[F2] [Arch Linux, Active AUR malicious packages incident, 12 giugno 2026](https://archlinux.org/news/active-aur-malicious-packages-incident/):** fonte primaria per adozioni/aggiornamenti malevoli e invito a controllare PKGBUILD e script. Non documenta da sola tutti i payload o gli impatti; non prova lo stato dell'incidente a ottobre. Persone 3, 5 e 6.
- Per AUR, cercare nella documentazione ufficiale Arch le voci su AUR, PKGBUILD e makepkg; per il singolo esempio cercare segnalazione originale e modifiche associate. Per npm, seguire dall'advisory la discussione originale del progetto e le analisi dei ricercatori citate. Registrare URL, data e affermazione supportata.

Non confrontare il numero di vittime dei due casi senza dati omogenei. Distinguere sempre impatto osservato, comportamento documentato e scenario potenziale. Ogni persona consegna fonti, data di consultazione e dubbi aperti; inserire in references.bib soltanto le fonti effettivamente utilizzate. La scaletta non è una fonte tecnica.

**[F3] [pnpm, Supply chain security](https://pnpm.io/supply-chain-security):** documentazione del controllo minimumReleaseAge per ritardare l'adozione delle nuove versioni. Usarla per motivare la misura, distinguendo il meccanismo dalla scelta del gruppo di una finestra di 24 ore. Persona 5.

## Indicazioni del professore da tenere presenti

Dal PDF “2026_DidatticaAttiva_Relazione1.pdf”:

- Pubblico con familiarità con Internet e dispositivi, senza competenze specifiche di cybersecurity: spiegare acronimi e passaggi tecnici.
- Seguire il ragionamento del Cyber Risk Management: contesto e asset → minacce → debolezze → tecniche di attacco → rischi e impatti → mitigazioni. Non è necessario trasformare ogni voce in un capitolo.
- Dare priorità all'analisi di attacco, debolezze e impatti; trattare le mitigazioni in modo sintetico.
- Documentare le informazioni con fonti affidabili; distinguere le evidenze dalle ipotesi e verificare i contenuti suggeriti dalla GenAI.
- Stimare circa 15 minuti di lettura attenta; le 3-6 pagine indicate dal docente sono un riferimento, non il criterio principale. Bibliografia, sitografia e metodologia GenAI sono escluse dalla stima del tempo di lettura.
- Dichiarare e documentare l'uso della GenAI in un allegato, riportando metodologia, attività supportate e prompt significativi. Registrare anche questo uso per organizzare la scaletta; ogni componente aggiunge i propri usi effettivi.

**Nota sulle scadenze:** questo PDF riporta ancora la consegna del 16 ottobre; la pianificazione v2 già usata per il README riporta il 19 ottobre. Questa scaletta non modifica le scadenze del repository.

## Revisione dei contributi

1. Compilare i nomi e concordare i termini comuni.
2. Le persone 2 e 3 separano spiegazione tecnica e cronologia per evitare ripetizioni tra capitoli 3 e 4.
3. La persona 4 usa i risultati dei casi per costruire l'analisi dei rischi; la persona 5 vi collega le misure.
4. La persona 6 scrive le conclusioni dopo gli altri contributi; tutti controllano fonti e correttezza delle proprie parti.
5. Verificare che il risk management sia presente nei collegamenti logici dell'analisi, senza imporre le sue fasi come indice.
6. Compilare e controllare tempo di lettura, spazio delle figure e budget complessivo.
