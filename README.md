# Manuale di Stile per PHP
Guida alla redazione di programmi in PHP (in lavorazione).

#### Indice
* [Tags PHP](#tags-php)
    * [I files sorgente **DEVONO** essere aperti dal tag PHP esteso `<?php` seguito da una riga vuota](#i-files-sorgente-devono-essere-aperti-dal-tag-php-esteso-<?php-seguito-da-una-riga-vuota)
    * [Il tag di chiusura **DEVE** essere omesso nei files sorgente](#il-tag-di-chiusura-deve-essere-omesso-nei-files-sorgente)
    * [Nei files che mescolano PHP e HTML **DEVONO** essere usati i tag estesi `<?php ?>`](#nei-files-che-mescolano-php-e-html-devono-essere-usati-i-tag-estesi-<?php-?>)




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

#### Nei files che mescolano PHP e HTML **DEVONO** essere usati i tag estesi `<?php ?>`.
```php
<div>

    <?php foreach ($arr as $key => $value) : ?>

        <p><?php echo $value; ?></p>

    <?php endforeach;>

</div>
```
> L'uso del tag esteso `<?php echo` era richiesto nel caso in cui un server non avesse avuto `short_open_tag` abilitato. 
>Oggi questa esigenza risulta superata dopo che `PHP 5.4` ha reso sempre disponibile l'uso del tag conciso `<?=` indipendentemente dalla direttiva INI `short_open_tag`. Tuttavia per ragioni di consistenza e leggibilità non deve mai essere usato il tag breve `<?=` preferendogli l'uso esclusivo del tag esteso `<?php echo`.

> Il punto e virgola finale non deve mai essere omesso anche quando PHP lo permette, come nell'esempio che segue:
> ```php
> <div>
> 
>     <?php foreach ($arr as $key => $value) : ?>
> 
>         <p><?php echo $value ?></p> // bad
> 
>     <?php endforeach;>
> 
> </div>
> ```



**[vai all'indice ⬆](#indice)**
