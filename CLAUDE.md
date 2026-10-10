# percorsi-site — incubatore dei percorsi clinici (percorsi.ivanferrero.it)

> Creato il 2026-10-07. Questo file è tracciato nel repo (a differenza di quello di `ivanferreroit`, che `.gitignore` escludeva e che si è perso con un nuovo clone) ed è escluso dalla build in `_config.yml`.

## Cosa è

Il terzo sito di Ivan, con un ruolo preciso: **mettere alla prova nicchie cliniche nuove a costo minimo**, una cartella per percorso, prima di dare a ciascuna un sito proprio. `ivanferrero.it` qualifica e non converte (regola sua), `equilibrio.ivanferrero.it` è il verticale che ha già vinto: questo sito sta in mezzo. Decisione del 2026-10-07, motivata così: un sito per nicchia è la cattedrale che rientra dalla finestra; tutto su ivanferrero.it viola la regola del presidio e porta un genitore in ansia su un sito scuro di dashboard.

Filo che lega i percorsi: **si lavora con chi sta accanto al problema** (genitore, partner, familiare), paziente a pieno titolo e mai ingresso secondario verso chi ha il sintomo.

## Regole dell'incubatore

- **Formato e prezzo non cambiano fra una nicchia e l'altra**, cambia solo il contenuto: chiamata di 15 minuti gratuita, incontro di valutazione, pacchetto a sedute contate a €120, misure a metà e alla fine. Il listino sta in `_config.yml` (`prezzo_seduta`, `prezzo_valutazione`, `nota_costi`) e si cambia lì. Motivo: con pochi contatti un esperimento si legge solo se varia una cosa alla volta.
- **Cancello**: 5 contatti clinici qualificati (stesso criterio di Equilibrio, registro CCQ) → la nicchia si guadagna sottodominio e repo propri. Niente contatti nel tempo fissato prima del lancio → la cartella passa in `_archivio/` (esclusa dalla build) e il resto non se ne accorge.
- **Niente cookie, tag, analytics, font esterni**: per questo non c'è banner e `/privacy/` è corta. Se partono annunci su una pagina, prima si aggiunge il tag in `_includes/head.html` con un banner di consenso e si riscrive `/privacy/`, poi si accende la campagna.
- **Il nome del metodo clinico non va in pagina**: i percorsi sono di Ivan e riprendono gli ingredienti dei metodi con evidenza, senza applicarli come marchio (vale per SPACE e NVR sulla pagina genitori; decisione dell'8/10/2026, che sostituisce il «finché manca la formazione ufficiale» del 7/10). Le fonti scientifiche in fondo alla pagina sono pubbliche e restano.
- Linguaggio centrato sulla persona, comunicazione orientata al positivo, nessun rimando ad altri colleghi. Niente «esperto», «specialista», «garantisce», «guarigione».
- **Si lavora in locale e ci si ferma: il push lo fa Ivan a mano.** Si modifica il file originale, niente copie parallele.

## Struttura

| Percorso | Cosa è |
|---|---|
| `index.html` | Home dell'incubatore: elenco dei percorsi attivi + rimando a Equilibrio + modulo |
| `genitori/` | Primo percorso (07/10/2026): genitori di ragazzi 6-17 con ansia o che rifiutano l'aiuto, lavoro con i soli genitori. Riferimenti clinici: schede `space-genitori-ansia.md` e `resistenza-non-violenta.md` in `reference/protocolli_breviario_del_clinico/` |
| `privacy/` | Informativa, cortissima perché il sito raccoglie solo il modulo |
| `_includes/contact-form.html` | Modulo: stesso Apps Script di Equilibrio, parametri `source` (nome pagina) e `chips` (righe separate da `|` che diventano pulsanti facoltativi). Regola ereditata: successo dichiarato solo su `{"ok":true}` dal server |
| `assets/css/main.css` | Foglio unico, palette crema/teal, font di sistema |

## Come si aggiunge un percorso

1. Copia `genitori/index.html` in `<nicchia>/index.html` e riscrivi i contenuti tenendo la stessa sequenza: riconoscimento → perché funziona e dati (con fonti e con «cosa non dicono») → per chi è e cosa viene prima → come funziona (3 passi, prezzi dal config) → nodo etico della nicchia → quando sono la persona giusta → modulo con `source="Percorsi - <Nicchia>"` e chips proprie.
2. Aggiungi la card in `index.html`.
3. Build e controllo a 1280 e 400 px prima di consegnare.

## Stato

- 2026-10-07: repo creato in locale con home, `/genitori/`, `/privacy/`. **Non ancora su GitHub, DNS non ancora puntato.** Prossimi passi di Ivan: creare il repo `percorsi-site` su GitHub (IvanPsy), push, attivare Pages con il CNAME, aggiungere su Aruba il record CNAME `percorsi` → `ivanpsy.github.io`, poi link dalla home di ivanferrero.it. Prima di accendere annunci: preparazione clinica (manuale di Lebowitz, FASA, materiali per i genitori), stimata in due o tre settimane.
- Candidata successiva: familiari di chi gioca d'azzardo (pacchetto prepagato come parte del setting).
- 2026-10-07 sera: sito online su https://percorsi.ivanferrero.it/ con HTTPS forzato (repo su GitHub IvanPsy/percorsi-site, CNAME su Aruba). Lavori successivi affidati a chat separate: link dalla home di ivanferrero.it, preparazione clinica del percorso genitori in `clinica/framework/percorso_genitori/` (da creare), pagina `familiari-gioco/`.
- 2026-10-08: online il link dalla home (card Psicoterapia) e dal footer di ivanferrero.it (commit `f30c4e9` di quel repo) e le tre correzioni di `/genitori/`: totale 1.520, «alcuni ragazzi», regola sul nome dei metodi (`bb9ab46`, `235108b`). Verificato online il 9/10.
- Skill: deciso il 10/10/2026 di estendere `copy-clinico` con un ramo «percorsi» (niente `percorsi-content`). Finché l'estensione non è fatta e registrata in `skill-registry`, nessuna skill copre questo sito.

## Connessioni

- `clinica/framework/dipendenze-sessuali_framework/framework-clinico/de_cartella_lavoro/sito/equilibrio-contatti.gs`: lo script che riceve il modulo (condiviso con Equilibrio; il campo `source` distingue le pagine).
- `clinica/framework/framework-schermi/`: il framework sistemico che questa pagina volutamente NON usa (il paziente qui è l'adulto); se un caso richiede la geometria famiglia-designato, è lì.
- `divulgazione/schede_genitori/`: materiale per i genitori riutilizzabile come oggetto che esce dalla stanza.
