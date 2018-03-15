# Manuale di Stile per PHP
Guida alla redazione di programmi in PHP (in lavorazione).


## Tags PHP

#### I files sorgente **DEVONO** essere aperti dal tag PHP esteso `<?php` seguito da una riga vuota.
```
<?php
            // blank line
$a = 'foo'; // code php
$b = 'bar'; // code php
            // blank line
```
> Devono sempre essere usati esclusivamente i tag PHP estesi `<?php ?>` e mai quelli concisi `<? ?>`. Questo è il modo più portabile per includere codice PHP su diversi sistemi operativi e configurazioni.

> Nei file che contengono esclusivamente codice PHP, il tag di apertura `<?php` deve essere seguito da una singola riga vuota al fine di migliorare la leggibilità del codice.

#### Il tag di chiusura **DEVE** essere omesso nei files sorgente.
> Nei file che contengono esclusivamente codice PHP, il tag di chiusura `?>` deve essere sostituito da una singola riga vuota.

> Il tag di chiusura PHP `?>` in un documento PHP é facoltativo per il parser PHP. Tuttavia, se utilizzato, qualsiasi spazio vuoto successivo al tag di chiusura, introdotto dallo sviluppatore, dall'utente o da un'applicazione FTP, può causare output indesiderati, errori PHP o, se questi ultimi vengono soppressi, pagine vuote. Per questo motivo, tutti i file che contengono esclusivamente codice PHP devono omettere il tag di chiusura `?>` e terminare con una singola riga vuota.


