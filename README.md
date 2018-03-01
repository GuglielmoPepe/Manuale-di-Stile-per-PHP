# Manuale di Stile per PHP
Guida alla redazione di programmi in PHP (in lavorazione).

[Tags del codice PHP](#tags-del-codice-php)

## Tags del codice PHP
Quando PHP analizza un file, cerca i tag di apertura `<?php` e di chiusura `?>`, che non fanno altro che indicare a PHP di avviare e interrompere l'interpretazione del codice presente tra di essi. In questo modo PHP può essere incorporato in documenti di diverso tipo, poiché tutto ciò che è esterno a una coppia di tag di apertura e chiusura viene ignorato dal parser PHP.

PHP consente anche un tag aperto breve `<?` (che è sconsigliato dal momento che è disponibile solo se abilitato usando la direttiva del file di configurazione php.ini short_open_tag o se PHP è stato configurato con l'opzione --enable-short-tags).

Devono sempre essere usati esclusivamente i tag PHP estesi `<?php ?>` e mai quelli concisi `<? ?>`.

Nei file che contengono esclusivamente codice PHP, il tag di apertura `<?php` deve essere seguito da uno spazio e da una singola riga vuota al fine di migliorare la leggibilità del codice.

Se un file è puro codice PHP, il tag di chiusura `?>` deve essere omesso, terminando i files con una singola riga vuota.

Il tag di chiusura PHP `?>` in un file con puro codice PHP é facoltativo per il parser PHP. Tuttavia, se utilizzato, qualsiasi spazio vuoto successivo al tag di chiusura, introdotto dallo sviluppatore, dall'utente o da un'applicazione FTP, può causare output indesiderati, errori PHP o, se questi ultimi vengono soppressi, pagine vuote. Per questo motivo, tutti i file PHP devono omettere il tag di chiusura PHP e terminare con una singola riga vuota.

```php
<?php /*php followed by space*/

echo "Hello world";

// ... more code

echo "Last statement";

// the script ends here with no PHP closing tag and blank line

```
Il codice PHP deve essere sempre delimitato dai tag PHP standard completi anche nei file che non contengono solo codice PHP.

L'uso del tag esteso `<?php echo` era richiesto nel caso in cui un server non avesse avuto `short_open_tag` abilitato. 
Oggi questa esigenza risulta superata dopo che `PHP 5.4` ha reso sempre disponibile l'uso del tag conciso `<?=` indipendentemente dalla direttiva INI `short_open_tag`. Tuttavia per ragioni di consistenza non deve mai essere usato il tag breve `<?=` preferendogli l'uso esclusivo del tag esteso `<?php echo`.

















