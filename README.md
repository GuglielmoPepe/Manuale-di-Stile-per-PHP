# Manuale di Stile per PHP
Guida alla redazione di programmi in PHP (in lavorazione).

#### Indice


* [Qualsiasi raccomandazione del manuale **DEVE** essere violata se migliora la leggibilità](#qualsiasi-raccomandazione-del-manuale-deve-essere-violata-se-migliora-la-leggibilità)
* [ La lingua utilizzata per i nomi **DEVE** essere l'inglese](#-la-lingua-utilizzata-per-i-nomi-deve-essere-l'inglese)
* [Le abbreviazioni e gli acronimi **DEVONO** avere tutte lettere in minuscolo eccetto la prima se usati come nome](#le-abbreviazioni-e-gli-acronimi-devono-avere-tutte-lettere-in-minuscolo-eccetto-la-prima-se-usati-come-nome)
* [Le unità logiche all'interno di un blocco di codice **DEVONO** essere separate da una riga vuota](#le-unità-logiche-all'interno-di-un-blocco-di-codice-devono-essere-separate-da-una-riga-vuota)
* [Per l'indentazione **DEVE** essere utilizzato lo stile Allman](#per-l'indentazione-deve-essere-utilizzato-lo-stile-allman)
* [Le parentesi **DEVONO** essere prive si spazi aggiuntivi al loro interno](#le-parentesi-devono-essere-prive-si-spazi-aggiuntivi-al-loro-interno)
* [Le istruzioni **DEVONO** essere tutte su una propria riga](#le-istruzioni-devono-essere-tutte-su-una-propria-riga)
* [L'error reporting **DEVE** essere impostato con la costante `E_ALL`](#l'error-reporting-deve-essere-impostato-con-la-costante-eall)
* [Tutto il codice **DEVE** utilizzare le funzionalità avanzate di PHP 7 per la programmazione orientata agli oggetti](#tutto-il-codice-deve-utilizzare-le-funzionalità-avanzate-di-php-7-per-la-programmazione-orientata-agli-oggetti)

* [I files sorgente **DEVONO** essere aperti dal tag PHP esteso `<?php` seguito da una riga vuota](#i-files-sorgente-devono-essere-aperti-dal-tag-php-esteso-php-seguito-da-una-riga-vuota)
* [Il tag di chiusura **DEVE** essere omesso nei files sorgente](#il-tag-di-chiusura-deve-essere-omesso-nei-files-sorgente)
* [Nei files che mescolano PHP e HTML **DEVONO** essere usati i tag estesi `<?php ?>`](#nei-files-che-mescolano-php-e-html-devono-essere-usati-i-tag-estesi-)

* [Il codice ingannevole **DEVE** essere riscritto, non commentato](#il-codice-ingannevole-deve-essere-riscritto,-non-commentato)
* [Tutti i commenti **DEVONO** essere scritti in inglese](#tutti-i-commenti-devono-essere-scritti-in-inglese)
* [L'identificatore di commenti `//` **DEVE** essere seguito da uno spazio](#l'identificatore-di-commenti-//-deve-essere-seguito-da-uno-spazio)
* [I commenti **DEVONO** utilizzare l'identificatore `//` per tutti i commenti non in formato _phpDocumentor_, inclusi i commenti su più righe](#i-commenti-devono-utilizzare-l'identificatore-//-per-tutti-i-commenti-non-in-formato-phpdocumentor,-inclusi-i-commenti-su-più-righe)
* [I commenti su più righe **DEVONO** essere seguiti da una riga vuota quando sono molto grandi](#i-commenti-su-più-righe-devono-essere-seguiti-da-una-riga-vuota-quando-sono-molto-grandi)
* [I commenti **DEVONO** essere indentati allo stesso livello del codice cui si riferiscono](#i-commenti-devono-essere-indentati-allo-stesso-livello-del-codice-cui-si-riferiscono)

* [I numeri a virgola mobile **DEVONO** sempre essere scritti con il punto decimale ed almeno un decimale](#i-numeri-a-virgola-mobile-devono-sempre-essere-scritti-con-il-punto-decimale-ed-almeno-un-decimale)
* [I numeri a virgola mobile **DEVONO** sempre essere scritti con una cifra prima del punto decimale](#i-numeri-a-virgola-mobile-devono-sempre-essere-scritti--con-una-cifra-prima-del-punto-decimale)

* [Le stringhe letterali **DEVONO** essere delimitate dalle virgolette singole](#le-stringhe-letterali-devono-essere-delimitate-dalle-virgolette-singole)
* [Le stringhe che contengono virgolette singole **DEVONO** essere delimitate dalle virgolette doppie](#le-stringhe-che-contengono-virgolette-singole-devono-essere-delimitate-dalle-virgolette-doppie)
* [Le stringhe **DEVONO** essere scritte senza variabili da sostituire](#le-stringhe-devono-essere-scritte-senza-variabili-da-sostituire)
* [La riga **DEVE** essere divisa dopo l'operatore di concatenazione quando l'istruzione è supera il limite di 72 caratteri, allineando la nuova riga con l'inizio dell'espressione sulla riga precedente](#la-riga-deve-essere-divisa-dopo-l'operatore-di-concatenazione-quando-l'istruzione-è-supera-il-limite-di-72-caratteri,-allineando-la-nuova-riga-con-l'inizio-dell'espressione-sulla-riga-precedente)

* [Gli arrays **DEVONO** essere dichiarati con la sintassi concisa](#gli-arrays-devono-essere-dichiarati-con-la-sintassi-concisa)
* [Gli arrays **DEVONO** avere indici numerici positivi](#gli-arrays-devono-avere-indici-numerici-positivi)
* [I delimitatori degli elementi `,` di un array **DEVONO** essere seguiti da uno spazio](#i-delimitatori-degli-elementi-,-di-un-array-devono-essere-seguiti-da-uno-spazio)
* [Gli operatori di assegnazione di un valore a una chiave `=>` **DEVONO** essere preceduti e seguiti da uno spazio](#gli-operatori-di-assegnazione-di-un-valore-a-una-chiave-=>-devono-essere-preceduti-e-seguiti-da-uno-spazio)

* [Tra la parola chiave di una struttura di controllo e la parentesi aperta **DEVE** esserci uno spazio](#tra-la-parola-chiave-di-una-struttura-di-controllo-e-la-parentesi-aperta-deve-esserci-uno-spazio)


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
error_reporting(E_ALL);
```
> Consente di suggerire le modifiche al codice che garantiscano la migliore interoperabilità e compatibilità all'indietro del codice.

> Il livello di error reporting richiesto è `E_STRICT`, pertanto se viene utilizzata una versione precedente alla `5.4` l'error_reporting deve essere deve essere impostato come segue:
```php
error_reporting(E_STRICT);
```
> A partire dalla versione `5.4` la costante `E_ALL` include `E_STRICT`;


#### Tutto il codice **DEVE** utilizzare le funzionalità avanzate di PHP 7 per la programmazione orientata agli oggetti.
> Ciò significa che le funzioni dovrebbero essere ridotte al minimo e non dovrebbero essercene al di fuori di `namespace`, se non assolutamente necessario. Se è necessario un _contenitore_ per alcune funzioni di supporto, prendere in considerazione la creazione di una classe statica.


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

#### I commenti su più righe **DEVONO** essere seguiti da una riga vuota quando sono molto grandi.
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


#### Le stringhe letterali **DEVONO** essere delimitate dalle virgolette singole.
```php
$string = 'example string';
```

#### Le stringhe che contengono virgolette singole **DEVONO** essere delimitate dalle virgolette doppie.
```php
$str = "That's a 'magic' sock.";
```
> Questa sintassi è preferibile rispetto al carattere di escape `\` poiché è molto più facile da leggere.
> Inoltre è particolarmente utile per le istruzioni SQL:
> ```php
> $sql = "SELECT `id`, `name` " . 
>        "FROM `people` " . 
>        "WHERE `name`='Mickey' OR `name`='Minnie'";
> ```

#### Le stringhe **DEVONO** essere scritte senza variabili da sostituire.
```php
$string = 'Hello ' . $name . ', welcome back!';
```
> Questa sintassi migliora le leggibilità del codice rispetto ai seguenti esempi:
> ```php
> $string = "Hello $name, welcome back!";   // bad
> $string = "Hello {$name}, welcome back!"; // bad
> $string = "Hello ${name}, welcome back!"; // bad
> ```

#### La riga **DEVE** essere divisa dopo l'operatore di concatenazione quando l'istruzione è supera il limite di 72 caratteri, allineando la nuova riga con l'inizio dell'espressione sulla riga precedente.
```php
$sql = "SELECT `id`, `name` " . 
       "FROM `people` " . 
       "WHERE `name`='Mickey' OR `name`='Minnie'" . 
       "ORDER BY `name` ASC ";
```
> Quando si concatenano le stringhe con l'operatore `.`, è meglio suddividere l'istruzione in più righe per migliorarne la leggibilità. In questi casi, ogni riga successiva deve essere riempita con tanti spazi bianchi, tali da allinearla con la riga precedente. 


#### Gli arrays **DEVONO** essere dichiarati con la sintassi concisa.
```php
$arr = [];
```

#### Gli arrays **DEVONO** avere indici numerici positivi.
> L'uso di numeri negativi come indici di un array può causare problemi con alcune funzioni della libreria standard di PHP.

#### I delimitatori degli elementi `,` di un array **DEVONO** essere seguiti da uno spazio.
```php
$arr = ['Mickey', 'Minnie', 1, 2, 3];

```
> Migliora la leggibilità del codice.

#### Gli operatori di assegnazione di un valore a una chiave `=>` **DEVONO** essere preceduti e seguiti da uno spazio.
```php
$arr = ['firstKey' => 'firstValue', 'secondKey' => 'secondValue'];

```
> Migliora la leggibilità del codice.

#### Gli array suddivisi su più righe **DEVONO** seguire le seguenti raccomandazioni:
* il primo elemento **DEVE** essere posizionato sulla riga successiva a quella della dichiarazione dell'array;
* ogni elemento **DEVE** essere su una propria riga;
* gli elementi **DEVONO** avere un'indentazione maggiore rispetto alla riga di dichiarazione dell'array;
* gli operatori di assegnazione di un valore a una chiave `=>` **DEVONO** essere allineati;
* l'ultimo elemento **DEVE** essere sempre delimitato da una virgola;
* la parentesi di chiusura **DEVE** essere su una propria riga allo stesso livello di indentazione della riga contenente la dichiarazione dell'array;

```php
$arr = [
    'firstKey'  => 'firstValue', 
    'secondKey' => 'secondValue',
];
```
> L'uso della virgola finale dopo l'ultimo elemento nell'array riduce al minimo la possibilità che si verifichino errori di analisi a causa di una virgola mancante per l'aggiunta di nuovi elementi.



[vai all'indice ⬆](#indice)


## Variabili

#### I nomi delle variabili **DEVONO** contenere solo caratteri alfanumerici ed essere scritti in `mixedCase`.
```php
$firstName = 'Mickey';
```

> I numeri sono consentiti nei nomi delle variabili, ma sono da evitarsi nella maggior parte dei casi.

> I nomi delle variabili dovrebbero essere quanto più descrittivi possibile, ma anche quanto più brevi è possibile, quel tanto che basti a descrivere i dati che lo sviluppatore intende memorizzare in essi.

> I nomi di variabili di una sola lettera, come `$i` e `$k`, sono da evitarsi tranne che nei cicli più piccoli. Se un ciclo contiene più di 20 righe di codice, le variabili dell'indice dovrebbero avere nomi più descrittivi.

> Le variabili nell'ambito globale sono da evitarsi. Se sono proprio necessarie, si utilizzino le proprietà di classe `static` o le costanti anziché le variabili globali, seguendo il design pattern `factory`.


#### Le variabili _generiche_ **DEVONO** avere lo stesso nome del loro tipo.
```php
$person = new \Person();
```

> Riduce la complessità riducendo il numero di termini e nomi utilizzati. Inoltre rende facile dedurre il tipo dato dal nome della variabile.

> Se per qualche motivo questa convenzione non sembra adattarsi, c'è un forte sospetto che il nome del _tipo_ è scelto male.

> Le variabili non generiche hanno un _ruolo_. Queste variabili possono spesso essere nominate combinando il _ruolo_ e il _tipo_:
> ```php
> function sendMessage(\Person $fromPerson, \Person $toPerson)
> {
> 
> }
> ```


#### Le variabili **DEVONO** avere un significato univoco.

> Migliora la leggibilità, assicurando che tutti i concetti siano rappresentati in modo univoco. Riduce inoltre la possibilità di errore da effetti collaterali.


#### Le variabili **DEVONO** essere mantenute in vita per il minor tempo possibile.

> Mantenendo le operazioni su una variabile all'interno di un piccolo ambito, è più facile controllare gli effetti collaterali, e non, della variabile.

[vai all'indice ⬆](#indice)


## Costanti

#### I nomi delle costanti **DEVONO** contenere solo caratteri alfanumerici, essere tutte in maiuscolo con le parole separate da caratteri di sottolineatura.
```php
define('DATABASE_HOST', 'dbhost');
define('DATABASE_NAME', 'dbname');
define('DATABASE_USER', 'dbuser');
define('DATABASE_PASSWORD', 'dbpwd');
```

> Le costanti devono essere denominate in modo da indicare il loro scopo e contenuto.

> Anche le costanti PHP predefinite come `TRUE`, `FALSE` e `NULL` devono essere tutte in maiuscolo.

> I numeri sono consentiti nei nomi delle costanti, ma sono da evitarsi nella maggior parte dei casi.

> I nomi delle costanti dovrebbero essere quanto più descrittivi possibile, ma anche quanto più brevi è possibile.

> La definizione di costanti nell'ambito globale con la funzione `define` è consentita, ma fortemente sconsigliata. Sono da preferirsi le costanti di classe e, se proprio sono necessarie, è meglio inserire le costanti globali nel punto di ingresso dello script o meglio ancora in un file separato.



#### I nomi delle costanti che rappresentano un concetto comune **DEVONO** avere un prefisso comune.
```php
define('COLOR_RED', '#ff0000');
define('COLOR_GREEN', '00ff00');
define('COLOR_BLUE', '0000ff');
```
> Ciò indica che le costanti appartengono allo stesso insieme, e quale concetto rappresentino.

> Un'alternativa a questo approccio consiste nel mettere le costanti all'interno di un'interfaccia in modo da utilizzare il nome dell'interfaccia come prefisso:
> ```php
> interface Color
> {
>   const RED   = '#ff0000';
>   const GREEN = '#00ff00';
>   const BLUE  = '#0000ff';
> }
> ```


#### L'istruzione `const` **DEVE** essere preferita all'istruzione `define` nella dichiarazione di una costante.
```php
const COLOR_RED   = '#ff0000';
const COLOR_GREEN = '#00ff00';
const COLOR_BLUE  = '#0000ff';
```
> Si noti che `const` non funziona con le espressioni PHP, pertanto nel caso in cui debba essere definita una costante in maniera condizionale o con un valore non letterale va utilizzata l'istruzione `define`:
> ```php
> if ( ! defined('MAINTENANCE_MODE'))
> {
>     define('MAINTENANCE_MODE', 'development');
> }
> ```

[vai all'indice ⬆](#indice)

## Operatori

#### Gli operatori binari **DEVONO** essere circondati da uno spazio.
```php
if ($a == $b)
{
    // code
}
```
> Migliora la leggibilità del codice.

#### Gli operatori unari **DEVONO** essere uniti alla variabile cui afferiscono, fatta eccezione per `!`.
```php
@fopen('file/path');
```
> Migliora la leggibilità del codice.

> L'operator `!` deve essere diviso dalla variabile cui afferisce da uno spazio, per migliorare la leggibilità del codice, soprattuto quando si trova nelle espressioni condizionali come nel caso che segue:
> ```php
> if ( ! $condition)
> {
>     // code
> }
> ```

> Gli operatori unari di incremento `++` e decremento `--` vanno posizionati prima della variabile piuttosto che successivamente, per ragioni di efficienza.

#### Quando si confrontano una variabile con un'espressione si **DEVE** utilizzare una condizione _Yoda_.
```php
if (TRUE == $foo)
{
    // code
}
```
> Questa raccomandazione evita un'assegnazione accidentale all'interno dell'istruzione condizionale.

> Quando si eseguono confronti logici che coinvolgono variabili, le variabili vanno messe a destra, mentre costanti, letterali o chiamate di funzione sul lato sinistro. Se nessuna delle due parti è una variabile, l'ordine non è importante.

> Se nell'esempio precedente viene omesso un segno di uguale, si avrà un errore di analisi, perché non è possibile assegnare qualcosa ad a una costante come TRUE. Si veda, _a contrario_ l'esempio seguente:
```php
> if ($foo = TRUE)
> {
>     // code
> }
> ```
> l'assegnazione è perfettamente valida, generando un bug nel codice.



## L'operatore di concatenazione **DEVE** essere preceduto e seguito da un singolo spazio.
```php
$string = 'Mickey' . ' ' . 'Mouse';
```
> Migliora la leggibilità del codice.



#### L'operatore ternario **DEVE** essere contenuto su una sola riga.
```php
$variable = isset($options['variable']) ? $options['variable'] : TRUE;
```
> Opzionalmente le parentesi possono essere utilizzate attorno al controllo delle condizioni del ternario per maggiore chiarezza. Ternari più lunghi dovrebbero essere suddivisi in altre dichiarazioni. 

> Gli operatori ternari non dovrebbero mai essere annidati, come nell'esempio seguente:
> ```php
> // Nested ternaries are bad
> $variable = isset($options['variable']) ? isset($options['othervar']) ? TRUE : FALSE : FALSE;
> ```


#### L'operator `@` **DEVE** essere evitato assolutamente.
L'uso dell'operatore `@` per silenziare i messaggi di errore rende il debug più difficile, oltre a rallentare l'esecuzione del codice.


#### Gli operatori di confronto rigorosi **DEVONO** essere preferiti a tutti gli altri.
```php
if ($foo === $bar)
{
    // code
}

if ($foo !== $baz)
{
    // code
}
```
> Gli operatori di confronto rigorosi vanno preferiti ogni volta che è possibile, per evitare problemi con valori booleani che potrebbero portare ad un comportamento diverso da quello che ci si aspetta, come nei seguenti casi:
```php
if ($foo == $bar) // bad, avoid truthy comparisons
{
    // code
}

if ($foo != $baz) // bad, avoid falsy comparisons
{
    // code
}
```
[vai all'indice ⬆](#indice)






## Strutture di controllo

#### Tra la parola chiave di una struttura di controllo e la parentesi aperta **DEVE** esserci uno spazio.
```php
// single space following PHP control structures, but not in interior parenthesis
foreach ($arr as $key => $value)
{
    // code
}
```
> Questo è fatto per distinguere le parole chiave di controllo dai nomi di funzioni. Tutte le strutture di controllo devono contenere la loro logica all'interno di parentesi graffe.



[vai all'indice ⬆](#indice)

