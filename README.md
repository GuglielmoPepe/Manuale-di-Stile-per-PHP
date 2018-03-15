# Manuale di Stile per PHP
Guida alla redazione di programmi in PHP (in lavorazione).

#### Indice


* [Raccomandazioni generali](#raccomandazioni-generali)
   * [Qualsiasi raccomandazione del manuale **DEVE** essere violata se migliora la leggibilità](#qualsiasi-raccomandazione-del-manuale-deve-essere-violata-se-migliora-la-leggibilità)

* [Tags PHP](#tags-php)
   * [I files sorgente **DEVONO** essere aperti dal tag PHP esteso `<?php` seguito da una riga vuota](#i-files-sorgente-devono-essere-aperti-dal-tag-php-esteso-<?php-seguito-da-una-riga-vuota)
   * [Il tag di chiusura **DEVE** essere omesso nei files sorgente](#il-tag-di-chiusura-deve-essere-omesso-nei-files-sorgente)
   * [Nei files che mescolano PHP e HTML **DEVONO** essere usati i tag estesi `<?php ?>`](#nei-files-che-mescolano-php-e-html-devono-essere-usati-i-tag-estesi-<?php-?>)

## Raccomandazioni generali

#### Qualsiasi raccomandazione del manuale **DEVE** essere violata se migliora la leggibilità.
> L'obiettivo principale delle raccomandazioni è migliorare la leggibilità e di conseguenza la comprensione, la manutenibilità e la qualità generale del codice. Poichè è impossibile coprire tutti i casi specifici, il programmatore dovrebbe essere flessibile.

####  La lingua utilizzata per i nomi **DEVE** essere l'inglese.
> L'inglese è la lingua preferita per lo sviluppo a livello internazionale.

#### Le abbreviazioni e gli acronimi **DEVONO** avere tutte lettere in minuscolo eccetto la prima se usati come nome. 
> L'utilizzo di tutte le maiuscole per il nome di base causerà conflitti con le convenzioni di denominazione. Una vatiabile denominata `$pDF` non è molto leggibile. Inoltre quando un nome è composto da più di una parola (`PDFFile`) la leggibilità viene seriamente ridotta, perchè la parola che segue l'acronimo non spicca come dovrebbe.

#### Le unità logiche all'interno di un blocco di codice **DEVONO** essere separate da una riga vuota.
```php
if ($condition1)
{
    // code
}

if ($condition2)
{
    // code
}

if ($condition3)
{
    // code
}
```
> Introducendo una riga vuota tra le unità logiche correlate, si migliora la leggibilità del codice. Le righe di codice correlate devono essere raggruppate in blocchi, separati gli uni dagli altri per mantenere il più alto grado di leggibilità possibile. La definizione di _correlate_ dipende dal codice.
> ```php
> if ($condition1)
> {
>     // code
> }
> if ($condition2)
> {
>    // code
> }
> if ($condition3)
> {
>     // code
> }
> ```

#### Per l'indentazione **DEVE** essere utilizzato lo stile Allman.
```php
function foo($bar)
{
    // code
}
```
> Le parentesi graffe vanno sempre posizionate su una riga da sole e indentate allo stesso livello dell'istruzione che le _possiede_.

#### Le parentesi **DEVONO** essere prive si spazi aggiuntivi al loro interno.
```php
// no space inside the brackets
function foo($bar)
{

}
```

#### Le istruzioni **DEVONO** essere tutte su una propria riga.
```php
$foo = 'this';
$bar = 'that';
$bat = str_replace($foo, $bar, $bag);
```
> Mai combinare più istruzioni su una stessa riga come nell'esempio seguente:
> ```php
> $foo = 'this'; $bar = 'that'; $bat = str_replace($foo, $bar, $bag);
> ```

> I valori ed i commenti vanno allineati quando ciò è appropriato, come nell'esempio seguente:
> ```php
> $var        = ''; // do each on its own line
> $other_var  = ''; // do each on its own line
> ```

#### L'error reporting **DEVE** essere impostato con la costante `E_ALL`.
```php
error\_reporting(E_ALL);
```
> Consente di suggerire le modifiche al codice che garantiscano la migliore interoperabilità e compatibilità all'indietro del codice.

> Il livello di error reporting richiesto è `E_STRICT`, pertanto se viene utilizzata una versione precedente alla `5.4` l'error_reporting deve essere deve essere impostato come segue:
```php
error\_reporting(E_STRICT);
```
> A partire dalla versione `5.4` la costante `E_ALL` include `E_STRICT`;


#### Tutto il codice **DEVE** utilizzare le funzionalità avanzate di PHP 7 per la programmazione orientata agli oggetti.
> Ciò significa che non dovrebbero esserci funzioni al di fuori delle classi, se non assolutamente necessario. Se è necessario un _contenitore_ per alcuni metodi di supporto, prendere in considerazione la creazione di una classe statica.


[vai all'indice ⬆](#indice)

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
> L'uso del tag esteso `<?php echo` era richiesto nel caso in cui un server non avesse avuto la direttiva INI `short_open_tag` abilitata. 
>Oggi questa esigenza risulta superata dopo che `PHP 5.4` ha reso sempre disponibile l'uso del tag _echo_ breve `<?=` indipendentemente dalla direttiva INI `short_open_tag`. Tuttavia per ragioni di consistenza e leggibilità non deve mai essere usato il tag _echo_ breve `<?=` preferendogli l'uso esclusivo del tag esteso `<?php echo`.

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

[vai all'indice ⬆](#indice)


## Commenti

#### Il codice ingannevole **DEVE** essere riscritto, non commentato.
> In generale, l'uso dei commenti dovrebbe essere minimizzato, rendendo il codice autodocumentante mediante scelte di nome appropriate e una struttura logica esplicita.

#### Tutti i commenti **DEVONO** essere scritti in inglese.
> A livello internazione l'inglese è la lingua preferita per codificare.

#### L'identificatore di commenti `//` **DEVE** essere seguito da uno spazio.
```php
// This is a comment
```
> Migliora la leggibilità facendo risaltare il testo.

#### I commenti **DEVONO** utilizzare l'identificatore `//` per tutti i commenti non in formato _phpDocumentor_, inclusi i commenti su più righe.
```php
// Comment spanning 
// more than one line.
```
> L'uso dell'identificatore `//` per i commenti garantisce che sia sempre possibile commentare intere sezioni di un file usando `/* */` per scopi di debug.

#### I commentisu più righe **DEVONO** essere seguiti da una riga vuota quando sono molto grandi.
```php
// Comment single line
$foo = 'bar';

// Comment long
// Comment too long
// Comment very long
// Comment very very long
// Comment really too long

$baz = $object->foo($bar);

```
> Migliora la leggibilità del codice. E del commento.

#### I commenti **DEVONO** essere indentati allo stesso livello del codice cui si riferiscono.
```php
while (TRUE) 
{
    // Do something
    doSomething();
}

```
> Questo per evitare che i commenti interrompano la struttura logica del programma.

[vai all'indice ⬆](#indice)


## Tipi

#### I numeri a virgola mobile **DEVONO** sempre essere scritti con il punto decimale ed almeno un decimale.
```php
$total = 0.0;

$epsilon = 3.0e8;

$sum = ($a + $b) * 10.0;
```
> Questo enfatizza la diversa natura dei numeri interi e in virgola mobile. Matematicamente sono due concetti completamente diversi e non compatibili.


#### I numeri a virgola mobile **DEVONO** sempre essere scritti  con una cifra prima del punto decimale.
```php
$total = 0.5;
```
> Il numero ed il sistema di espressione in PHP è preso in prestito dalla matematica e si dovrebbe aderire alle convenzioni matematiche per la sintassi laddove possibile. 

> Inoltre, 0.5 è molto più leggibile di .5 e non c'è modo che possa essere confuso con l'intero 5. Si veda l'esempio seguente:
> ```php
> $total = .5; // bad
> ```


[vai all'indice ⬆](#indice)


## Strutture di controllo

## Tra la parola chiave di una struttura di controllo e la parentesi aperta **DEVE** esserci uno spazio.
```php
// single space following PHP control structures, but not in interior parenthesis
foreach ($arr as $key => $value)
{
    // code
}
```
> Questo è fatto per distinguere le parole chiave di controllo dai nomi di funzioni. Tutte le strutture di controllo devono contenere la loro logica all'interno di parentesi graffe.



[vai all'indice ⬆](#indice)

