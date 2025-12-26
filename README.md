# Fratina - Guida al Progetto

Questo documento descrive l'architettura e le modalità di gestione dei contenuti per il progetto Fratina. Il sistema è progettato per essere modulare e facile da aggiornare senza dover intervenire sulla logica di programmazione profonda.

## Funzionamento di Astro

Astro è il framework utilizzato per costruire questo sito web. Funziona secondo il principio della "Isola di Componenti": la maggior parte del sito viene generata come HTML statico per garantire la massima velocità di caricamento, mentre le parti interattive vengono caricate solo se necessario.

A differenza di altri sistemi, Astro separa nettamente la struttura della pagina dai dati, rendendo il sito estremamente performante e ottimizzato per i motori di ricerca.

## Styling con Tailwind CSS

Per la gestione grafica viene utilizzato Tailwind CSS. Invece di scrivere fogli di stile esterni complicati, Tailwind permette di applicare classi predefinite direttamente negli elementi del codice. Questo garantisce coerenza visiva in tutto il sito e permette di modificare l'aspetto dei componenti in modo rapido e prevedibile.

## Struttura dei Contenuti

Il cuore dei dati del sito si trova nella cartella `src/content/`. Il sistema è tipizzato per evitare errori nell'inserimento delle informazioni.

### Schemi e Validazione

Il file `src/content.config.ts` contiene le definizioni degli oggetti. Qui sono descritti i campi obbligatori e facoltativi per ogni elemento del sito (come titoli, descrizioni, immagini o date). Se un dato inserito non rispetta lo schema definito in questo file, il sistema segnalerà un errore durante la fase di build.

### Collezioni (Catalogo ed Eventi)

All'interno di `src/content/` sono presenti due cartelle principali:
  - catalogo: Contiene i prodotti o gli articoli del catalogo.
  - eventi: Contiene le iniziative e gli eventi in programma.

Ogni file creato all'interno di queste cartelle (ad esempio `nome-evento.json`) rappresenta una singola "entry" (una riga o un elemento) della collezione corrispondente. Modificare o aggiungere un file in queste cartelle aggiornerà automaticamente le pagine del sito che visualizzano tali contenuti.

## Pagine e Layout
### Aggiungere Nuove Pagine

Le pagine del sito si trovano in `src/pages/`. Ogni file `.astro` creato in questa cartella corrisponde a un indirizzo URL del sito. Ad esempio, creando `src/pages/chi-siamo.astro`, il contenuto sarà raggiungibile all'indirizzo `/chi-siamo`.

### Layout Principale

Il file `src/layouts/Layout.astro` funge da guscio per tutte le pagine del sito. Questo file gestisce:
  - Metadati: Titoli, Favicon, descrizioni SEO e configurazioni per i social network.
  - Header: La barra di navigazione superiore presente in ogni pagina.
  - Footer: La sezione informativa a fondo pagina.

Tutte le nuove pagine dovrebbero essere avvolte da questo componente per mantenere coerenza visiva e funzionale.

### Configurazione Variabili d'Ambiente

Le informazioni di contatto globali sono gestite tramite il file `.env`. Questo permette di aggiornare i recapiti senza modificare il codice sorgente.

Per modificare i contatti, apri il file .env nella cartella principale e aggiorna i seguenti valori:
Snippet di codice
```
PUBLIC_CONTACT_EMAIL=info@lafratina.it
PUBLIC_CONTACT_PHONE=+39 333 123 4567
PUBLIC_CONTACT_WHATSAPP=393331234567
PUBLIC_CONTACT_INSTAGRAM=la_fratina_vintage
PUBLIC_CONTACT_FACEBOOK=la_fratina_vintage
```

Nota: I cambiamenti effettuati in questo file si rifletteranno automaticamente in tutto il sito (Header, Footer e pagine di contatto).
