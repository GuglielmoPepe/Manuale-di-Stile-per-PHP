# Manuale di Stile per PHP
Guida alla redazione di programmi in PHP (in lavorazione).

#### indice

* [Raccomandazione generale](#raccomandazione-generale)
* [Directories](#directories)
* [Files](#files)
* [Tags php](#tags-php)
* [Istruzioni](#istruzioni)
* [Commenti](#commenti)
* [Tipi](#tipi)
* [Variabili](#variabili)
* [Costanti](#costanti)
* [Operatori](#operatori)
* [Strutture di controllo](#strutture-di-controllo)
* [Funzioni](#funzioni)
* [Namespaces](#namespaces)
* [Interfacce](#interfacce)
* [Traits](#traits)
* [Classi](#classi)
* [Costanti di classe](#costanti-di-classe)
* [Proprietà](#proprietà)
* [Metodi](#metodi)

Questo documento elenca le raccomandazioni per redazione di codice PHP sulla base di standard raccolti da una serie di fonti, esperienze individuali, requisiti/bisogni specifici della comunità PHP.

Ci sono diversi motivi per introdurre nuove raccomandazioni, piuttosto che riferirsi solo a quelli già esistenti. La ragione principale è che queste guide sono troppo generiche nel loro ambito e che devono essere stabilite regole più specifiche (specialmente le regole di denominazione). 

Inoltre, le raccomandazioni presenti in questo manuale sono annotate in modo da facilitarne l'uso, rispetto alla maggior parte delle altre linee guida esistenti. 

In generale, le raccomandazioni di programmazione tendono a mescolare i problemi di stile con le questioni tecniche del linguaggio in un modo alquanto confuso. Il presente documento si concentra principalmente sullo stile di programmazione.

Mentre un dato ambiente di sviluppo (IDE) può migliorare la leggibilità del codice tramite visibilità dell'accesso, codifica a colori, formattazione automatica e così via, il programmatore non dovrebbe mai fare affidamento su tali caratteristiche. Il codice sorgente dovrebbe essere scritto in modo da massimizzare la sua leggibilità indipendentemente da qualsiasi IDE.


Le raccomandazioni sono raggruppate per argomento e seguono questo schema:
> #### Raccomandazione
> ```php
>     $example = 'example'; // example
> ```
> 
> > Motivazione, riferimenti ed informazioni aggiuntive. 

La sezione motivazione è importante. Gli standard e le linee guida di codifica tendono ad avviare "guerre di religione", ed è importante indicare il contesto per la raccomandazione.

Si è scelto di usare solo raccomandazioni _obbligatorie_ per ridurre al minimo il rischio di avere più stili di codifica per singoli elementi di codice.

Questo Manuale di Stile è pensato per essere utilizzato con PHP 7 e successivi, ma nel caso si utilizzi una versione precedente le raccomandazioni possono essere facilmente adattate per una versione precendente di PHP.

[vai all'indice ⬆](#indice)

## Raccomandazione generale

**Qualsiasi raccomandazione del manuale deve essere violata se migliora la leggibilità.**
> L'obiettivo principale delle raccomandazioni è migliorare la leggibilità e di conseguenza la comprensione, la manutenibilità e la qualità generale del codice. Poichè è impossibile coprire tutti i casi specifici, il programmatore dovrebbe essere flessibile.

[vai all'indice ⬆](#indice)

## Directories

**I nomi delle directories devono contenere solo caratteri alfanumerici ed essere scritti in `CapitalizedWords`.**
> I numeri sono consentiti nei nomi delle directories, ma sono da evitarsi nella maggior parte dei casi.

> Queste raccomandazioni nascono dal fatto che i nomi delle directories vengono mappati con i nomi dei namespaces, creando un collegamento biunivoco con questi ultimi e rendendo predicibile la posizione di un namespace.

[vai all'indice ⬆](#indice)



## Files

**I nomi dei files devono contenere solo caratteri alfanumerici, essere scritti in `CapitalizedWords` e terminare con l'estensione `.php`.**
> I numeri sono consentiti nei nomi dei files, ma sono da evitarsi nella maggior parte dei casi.

> Queste raccomandazioni nascono dal fatto che i nomi dei files vengono mappati con i nomi delle interfacce, dei traits o delle classi, creando un collegamento biunivoco con questi ultimi.


**I files PHP devono usare esclusivamente la codifica dei caratteri UTF-8 senza BOM (Byte Order Mark).**

> La codifica può essere dichiarata usando `declare(encoding = 'utf-8');` nella parte superiore del file.

> A differenza di UTF-16 e UTF-32, non esiste un ordine di byte da indicare in un file con codifica UTF-8 e il BOM (Byte Order Mark) può avere un effetto collaterale negativo nell'invio dell'output, impedendo all'applicazione di impostare le proprie intestazioni.


**Le righe dei files devono avere una lunghezza massima di 72 caratteri e terminare con un singolo carattere di avanzamento riga Unix LF (linefeed).**

> Un limite di 72 caratteri rende necessario distribuire la logica o le espressioni complesse in funzioni, nonché assegnare nomi più brevi e più espressivi a funzioni ed oggetti.

> Limitando la larghezza delle righe a 72 caratteri si migliora la leggibilità del codice, evitando peraltro interruzioni di riga involontarie quando si passa un file tra i programmatori.

> Limitando la larghezza della finestra dell'editor a 72 caratteri, è possibile avere diversi file aperti fianco a fianco e funziona bene quando si utilizzano gli strumenti di revisione del codice che presentano le due versioni nelle colonne adiacenti.

> Il wrapping predefinito nella maggior parte degli strumenti interrompe la struttura visiva del codice, rendendolo più difficile da capire. Il limite è stato scelto per evitare il wrapping degli editor con la larghezza della finestra impostata su 80 caratteri, anche se lo strumento posiziona un glifo marcatore nella colonna finale quando effettua il wrapping delle linee. Alcuni strumenti basati sul Web potrebbero non offrire affatto il ritorno a capo automatico della linea.

> Non aggiungere spazi finali alla fine delle righe, ma terminare le righe secondo la convenzione del file di testo Unix. I caratteri di avanzamento riga sono rappresentati come numero ordinale 10 oppure come numero esadecimale 0x0A.
> Questo è più un problema per gli sviluppatori che lavorano in un ambiente Windows, ma in ogni caso assicurarsi che l'editor di testo sia configurato per salvare i file con interruzioni di riga Unix.


**L'incompletezza di una riga, perchè divisa a causa della sua eccessiva lunghezza, deve essere resa evidente.**
```php
$sum = a + b + c +
       d + e;


$obj->method(param1, param2,
             param3);


setText('Long line split' .
        'into two parts.');


for ($tableNo = 0; $tableNo < $nTables;
     $tableNo += $tableStep)
{
    // code
}
```
> Le righe divise si verificano quando un'istruzione supera il limite di 72 caratteri indicato sopra. 

> È difficile dare regole rigide su come le linee dovrebbero essere divise, ma gli esempi sopra dovrebbero dare un suggerimento generale.

> In generale:
> * dividi la riga dopo una virgola;
> * dividi dopo un operatore;
> * allinea la nuova riga con l'inizio dell'espressione sulla riga precedente;


**I caratteri speciali come TAB e interruzione di pagina devono essere evitati.**

> Questi caratteri sono destinati a causare problemi a editor, stampanti, emulatori di terminali o debugger quando vengono utilizzati in un ambiente multi-programmatore e multipiattaforma.


**I files devono usare un'indentazione di quattro spazi.**

> Ciò aiuta ad evitare problemi con diff, patch, cronologia e annotazioni. L'uso degli spazi rende anche facile inserire una sub-indentazione a grana fine per l'allineamento tra le righe.

> Gli spazi non devono mai essere mescolati con la tabulazione. 

> L'indentazione è usata per enfatizzare la struttura logica del codice. L'indentazione di uno spazio è troppo piccola per raggiungere questo risultato. L'indentazione maggiore di quattro spazi rende il codice profondamente annidato e difficile da leggere, aumentando peraltro la possibilità che le righe debbano essere divise.


**Tutti i files sorgente devono appartenere a un `namespace` specifico.**

> L'assegnazione di ogni file ad un `namespace` specifico piuttosto che al `namespace` globale, è un'applicazione delle tecniche di programmazione orientate agli oggetti del linguaggio PHP.


**Tutti i files sorgente devono terminare con una singola riga vuota.**

> Migliora la leggibilità del codice.


**I files sorgente che dichiarino interfacce, traits, classi o librerie di funzioni devono contenere solo le dichiarazioni di interfaccia, trait, classe o funzioni.**

> L'inserimento di codice aggiuntivo che provochi effetti collaterali deve essere evitato, per migliorare la leggibilità, la manutenibilità e la comprensione del codice.


**I files _template_ devono distinguere tra indentazione PHP e HTML.**
```php
<div>

    <?php foreach ($arr as $key => $value) : ?>

        <p><?php echo $value; ?></p>

    <?php endforeach;>

</div>
```
> Ciò rende molto più facile trovare tag di apertura e chiusura corrispondenti, definiti con diversi rientri.


**Nei files _template_ deve essere PHP in HTML piuttosto che HTML in PHP.**
```php
<?php if ( ! $page) : ?>
  <h2><a href="<?php echo $url; ?>"><?php echo $title; ?></a></h2>
<?php endif; ?>

<?php if ($submitted) : ?>
  <span class="submitted"><?php echo $submitted; ?></span>
<?php endif; ?>
```
> Dopotutto, PHP è un linguaggio di scripting incorporato in HTML, e non il contrario.

[vai all'indice ⬆](#indice)

## Tags PHP

**I files sorgente devono essere aperti dal tag PHP esteso `<?php` seguito da una riga vuota.**
```
<?php
            // blank line
$a = 'foo'; // code php
$b = 'bar'; // code php
            // blank line
```
> Devono sempre essere usati esclusivamente i tag PHP estesi `<?php ?>` e mai quelli concisi `<? ?>`. Questo è il modo più portabile per includere codice PHP su diversi sistemi operativi e configurazioni.

> Nei file che contengono esclusivamente codice PHP, il tag di apertura `<?php` deve essere seguito da una singola riga vuota al fine di migliorare la leggibilità del codice.


**Il tag di chiusura deve essere omesso nei files sorgente.**
> Nei file che contengono esclusivamente codice PHP, il tag di chiusura `?>` deve essere sostituito da una singola riga vuota.

> Il tag di chiusura PHP `?>` in un documento PHP é facoltativo per il parser PHP. Tuttavia, se utilizzato, qualsiasi spazio vuoto successivo al tag di chiusura, introdotto dallo sviluppatore, dall'utente o da un'applicazione FTP, può causare output indesiderati, errori PHP o, se questi ultimi vengono soppressi, pagine vuote. Per questo motivo, tutti i file che contengono esclusivamente codice PHP devono omettere il tag di chiusura `?>` e terminare con una singola riga vuota


**Nei files che mescolano PHP e HTML devono essere usati i tag estesi `<?php ?>`.**
```php
<div>

    <?php foreach ($arr as $key => $value) : ?>

        <p><?php echo $value; ?></p>

    <?php endforeach;>

</div>
```
> L'uso del tag esteso `<?php echo` era richiesto nel caso in cui un server non avesse avuto la direttiva INI `short_open_tag` abilitata. 
>Oggi questa esigenza risulta superata dopo che `PHP 5.4` ha reso sempre disponibile l'uso del tag _echo_ breve `<?=` indipendentemente dalla direttiva INI `short_open_tag`. Tuttavia per ragioni di consistenza e leggibilità non deve mai essere usato il tag _echo_ conciso `<?=` preferendogli l'uso esclusivo del tag esteso `<?php echo`.


> Il punto e virgola finale non deve mai essere omesso, neanche quando PHP lo permette, come nell'esempio che segue:
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

## Istruzioni

**La lingua utilizzata per i nomi deve essere l'inglese.**
> L'inglese è la lingua preferita per lo sviluppo a livello internazionale.

**Le abbreviazioni e gli acronimi devono avere tutte lettere in minuscolo eccetto la prima se usati come nome.**
> L'utilizzo di tutte le maiuscole per il nome di base causerà conflitti con le convenzioni di denominazione. Una vatiabile denominata `$pDF` non è molto leggibile. Inoltre quando un nome è composto da più di una parola (`PDFFile`) la leggibilità viene seriamente ridotta, perchè la parola che segue l'acronimo non spicca come dovrebbe.

**Le unità logiche all'interno di un blocco di codice devono essere separate da una riga vuota.**
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
> Introducendo una riga vuota tra le unità logiche correlate, si migliora la leggibilità del codice. Le righe di codice correlate devono essere raggruppate in blocchi, separati gli uni dagli altri per mantenere il più alto grado di leggibilità possibile. La definizione di _correlate_ dipende dal codice. Si noti la poca leggibilità del codice seguente:
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


**Per l'indentazione deve essere utilizzato lo stile Allman.**
```php
function foo($bar)
{
    // code
}
```
> Le parentesi graffe vanno sempre posizionate su una riga da sole e indentate allo stesso livello dell'istruzione che le _possiede_.


**Le parentesi devono essere prive si spazi aggiuntivi al loro interno.**
```php
// no space inside the brackets
function foo($bar)
{

}
```

**Le istruzioni devono essere tutte su una propria riga.**
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

**L'error reporting deve essere impostato con la costante `E_ALL`.**
```php
error\_reporting(E_ALL);
```
> Consente di suggerire le modifiche al codice che garantiscano la migliore interoperabilità e compatibilità all'indietro del codice.

> Il livello di error reporting richiesto è `E_STRICT`, pertanto se viene utilizzata una versione precedente alla `5.4` l'error_reporting deve essere deve essere impostato come segue:
```php
error\_reporting(E_STRICT);
```
> A partire dalla versione `5.4` la costante `E_ALL` include `E_STRICT`;

**Tutto il codice deve utilizzare le funzionalità avanzate di PHP 7 per la programmazione orientata agli oggetti.**
> Ciò significa che non dovrebbero esserci funzioni al di fuori delle classi, se non assolutamente necessario. Se è necessario un _contenitore_ per alcune funzioni di supporto, prendere in considerazione la creazione di una classe statica.

**Tra la parola chiave di una struttura di controllo e la parentesi aperta deve esserci uno spazio.**
```php
// single space following PHP control structures, but not in interior parenthesis
foreach ($arr as $key => $value)
{
    // code
}
```
> Questo è fatto per distinguere le parole chiave di controllo dai nomi di funzioni. Tutte le strutture di controllo devono contenere la loro logica all'interno di parentesi graffe.

[vai all'indice ⬆](#indice)

## Commenti

**Il codice ingannevole deve essere riscritto, non commentato.**
> In generale, l'uso dei commenti dovrebbe essere minimizzato, rendendo il codice autodocumentante mediante scelte di nome appropriate e una struttura logica esplicita.


**Tutti i commenti devono essere scritti in inglese.**
> A livello internazione l'inglese è la lingua preferita per codificare.


**L'identificatore di commenti `//` deve essere seguito da uno spazio.**
```php
// This is a comment
```
> Migliora la leggibilità facendo risaltare il testo.


**I commenti devono utilizzare l'identificatore `//`, inclusi i commenti su più righe.**
```php
// Comment spanning 
// more than one line.
```
> L'uso dell'identificatore `//` per i commenti garantisce che sia sempre possibile commentare intere sezioni di un file usando `/* */` per scopi di debug.


**I commentisu più righe devono essere seguiti da una riga vuota quando sono molto grandi.**
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


**I commenti devono essere indentati allo stesso livello del codice cui si riferiscono.**
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

**I numeri a virgola mobile devono sempre essere scritti con il punto decimale ed almeno un decimale.**
```php
$total = 0.0;

$epsilon = 3.0e8;

$sum = ($a + $b) * 10.0;
```
> Questo enfatizza la diversa natura dei numeri interi e in virgola mobile. Matematicamente sono due concetti completamente diversi e non compatibili.


**I numeri a virgola mobile devono sempre essere scritti  con una cifra prima del punto decimale.**
```php
$total = 0.5;
```
> Il numero ed il sistema di espressione in PHP è preso in prestito dalla matematica e si dovrebbe aderire alle convenzioni matematiche per la sintassi laddove possibile. 

> Inoltre, 0.5 è molto più leggibile di .5 e non c'è modo che possa essere confuso con l'intero 5. Si veda l'esempio seguente:
> ```php
> $total = .5; // bad
> ```

**Le stringhe letterali devono essere delimitate dalle virgolette singole.**
```php
$string = 'example string';
```


**Le stringhe che contengono virgolette singole devono essere delimitate dalle virgolette doppie.**
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


**Le stringhe devono essere scritte senza variabili da sostituire.**
```php
$string = 'Hello ' . $name . ', welcome back!';
```
> Questa sintassi migliora le leggibilità del codice rispetto ai seguenti esempi:
> ```php
> $string = "Hello $name, welcome back!";   // bad
> $string = "Hello {$name}, welcome back!"; // bad
> $string = "Hello ${name}, welcome back!"; // bad
> ```


**La riga deve essere divisa dopo l'operatore di concatenazione quando l'istruzione è supera il limite di 72 caratteri, allineando la nuova riga con l'inizio dell'espressione sulla riga precedente.**
```php
$sql = "SELECT `id`, `name` " . 
       "FROM `people` " . 
       "WHERE `name`='Mickey' OR `name`='Minnie'" . 
       "ORDER BY `name` ASC ";
```
> Quando si concatenano le stringhe con l'operatore `.`, è meglio suddividere l'istruzione in più righe per migliorarne la leggibilità. In questi casi, ogni riga successiva deve essere riempita con tanti spazi bianchi, tali da allinearla con la riga precedente. 


**Gli arrays devono essere dichiarati con la sintassi concisa.**
```php
$arr = [];
```


**Gli arrays devono avere indici numerici positivi.**
> L'uso di numeri negativi come indici di un array può causare problemi con alcune funzioni della libreria standard di PHP.


**I delimitatori degli elementi `,` di un array devono essere seguiti da uno spazio.**
```php
$arr = ['Mickey', 'Minnie', 1, 2, 3];

```
> Migliora la leggibilità del codice.


**Gli operatori di assegnazione di un valore a una chiave, `=>`, devono essere preceduti e seguiti da uno spazio.**
```php
$arr = ['firstKey' => 'firstValue', 'secondKey' => 'secondValue'];

```
> Migliora la leggibilità del codice.


**Gli array suddivisi su più righe devono avere il seguente formato:**
```php
$arr = [
    'firstKey'  => 'firstValue', 
    'secondKey' => 'secondValue',
];
```
> Riepilogando:
> * il primo elemento **DEVE** essere posizionato sulla riga successiva a quella della dichiarazione dell'array;
> * ogni elemento **DEVE** essere su una propria riga;
> * gli elementi **DEVONO** avere un'indentazione maggiore rispetto alla riga di dichiarazione dell'array;
> * gli operatori di assegnazione di un valore a una chiave `=>` **DEVONO** essere allineati;
> * l'ultimo elemento **DEVE** essere sempre delimitato da una virgola;
> * la parentesi di chiusura **DEVE** essere su una propria riga allo stesso livello di indentazione della riga contenente la dichiarazione dell'array;

> L'uso della virgola finale dopo l'ultimo elemento nell'array riduce al minimo la possibilità che si verifichino errori di analisi a causa di una virgola mancante per l'aggiunta di nuovi elementi.

[vai all'indice ⬆](#indice)

## Variabili

**I nomi delle variabili devono contenere solo caratteri alfanumerici ed essere scritti in `mixedCase`.**
```php
$firstName = 'Mickey';
```

> I numeri sono consentiti nei nomi delle variabili, ma sono da evitarsi nella maggior parte dei casi.

> I nomi delle variabili dovrebbero essere quanto più descrittivi possibile, ma anche quanto più brevi è possibile, quel tanto che basti a descrivere i dati che lo sviluppatore intende memorizzare in essi.

> I nomi di variabili di una sola lettera, come `$i` e `$k`, sono da evitarsi tranne che nei cicli più piccoli. Se un ciclo contiene più di 20 righe di codice, le variabili dell'indice dovrebbero avere nomi più descrittivi.

> Le variabili nell'ambito globale sono da evitarsi. Se sono proprio necessarie, si utilizzino le proprietà di classe `static` o le costanti anziché le variabili globali, seguendo il design pattern `factory`.


**Le variabili _generiche_ devono avere lo stesso nome del loro tipo.**
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


**Le variabili devono avere un significato univoco.**

> Migliora la leggibilità, assicurando che tutti i concetti siano rappresentati in modo univoco. Riduce inoltre la possibilità di errore da effetti collaterali.


**Le variabili devono essere mantenute in vita per il minor tempo possibile.**

> Mantenendo le operazioni su una variabile all'interno di un piccolo ambito, è più facile controllare gli effetti collaterali, e non, della variabile.

[vai all'indice ⬆](#indice)

## Costanti

**I nomi delle costanti devono contenere solo caratteri alfanumerici, essere tutte in maiuscolo con le parole separate da caratteri di sottolineatura.**
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


**I nomi delle costanti che rappresentano un concetto comune devono avere un prefisso comune.**
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


**L'istruzione `const` deve essere preferita all'istruzione `define` nella dichiarazione di una costante.**
```php
const COLOR_RED   = '#ff0000';
const COLOR_GREEN = '#00ff00';
const COLOR_BLUE  = '#0000ff';
```
> Si noti che `const` non funziona con le espressioni PHP, pertanto nel caso in cui debba essere definita una costante in maniera condizionale o con un valore non letterale va utilizzata l'istruzione `define`:
> if ( ! defined('MAINTENANCE_MODE'))
> {
>     define('MAINTENANCE_MODE', 'development');
> }

[vai all'indice ⬆](#indice)

## Operatori

**Gli operatori binari devono essere circondati da uno spazio.**
```php
if ($a == $b)
{
    // code
}
```
> Migliora la leggibilità del codice.


**Gli operatori unari devono essere uniti alla variabile cui afferiscono, fatta eccezione per `!`.**
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


**Quando si confrontano una variabile con un'espressione si deve utilizzare la condizione _Yoda_.**
```php
if (TRUE == $foo)
{
    // code
}
```
> Questa raccomandazione evita un'assegnazione accidentale all'interno dell'istruzione condizionale.

> Quando si eseguono confronti logici che coinvolgono variabili, le variabili vanno messe a destra, mentre costanti, letterali o chiamate di funzione sul lato sinistro. Se nessuna delle due parti è una variabile, l'ordine non è importante.

> Se nell'esempio precedente viene omesso un segno di uguale, si avrà un errore di analisi, perché non è possibile assegnare qualcosa ad a una costante come TRUE. Si veda, _a contrario_ l'esempio seguente:
> ```php
> if ($foo = TRUE)
> {
>     // code
> }
> ```
> l'assegnazione è perfettamente valida, generando un bug nel codice.



**L'operatore di concatenazione deve essere preceduto e seguito da un singolo spazio.**
```php
$string = 'Mickey' . ' ' . 'Mouse';
```
> Migliora la leggibilità del codice.


**L'operatore ternario deve essere contenuto su una sola riga.**
```php
$variable = isset($options['variable']) ? $options['variable'] : TRUE;
```
> Opzionalmente le parentesi possono essere utilizzate attorno al controllo delle condizioni del ternario per maggiore chiarezza. Ternari più lunghi dovrebbero essere suddivisi in altre dichiarazioni. 

> Gli operatori ternari non dovrebbero mai essere annidati, come nell'esempio seguente:
> ```php
> // Nested ternaries are bad
> $variable = isset($options['variable']) ? isset($options['othervar']) ? TRUE : FALSE : FALSE;
> ```


**L'operator `@` deve essere evitato assolutamente.**
> L'uso dell'operatore `@` per silenziare i messaggi di errore rende il debug più difficile, oltre a rallentare l'esecuzione del codice.


**Gli operatori di confronto rigorosi devono essere preferiti a tutti gli altri.**
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
> ```php
> if ($foo == $bar) // bad, avoid truthy comparisons
> {
>     // code
> }
> 
> if ($foo != $baz) // bad, avoid falsy comparisons
> {
>     // code
> }
> ```

[vai all'indice ⬆](#indice)

## Strutture di controllo

### if-else

**Le espressioni condizionali complesse devono essere evitate. Introdurre variabili booleane temporanee invece.**
```php
$isFinished = ($elementNo < 0) || ($elementNo > $maxElement);
$isRepeatedEntry = $elementNo == $lastElement; 

if ($isFinished || $isRepeatedEntry)
{
    // code
}
```
> Assegnando le espressioni booleane a delle variabili, lo script si auto-documenta.
> Sarà più facile eseguire il debug oltre che leggere e mantenere lo script.

 
**L'istruzione condizionale deve essere su una riga separata.**
```php
$isFinished = ($elementNo < 0) || ($elementNo > $maxElement);

if ($isFinished)
{
    doExecute();
}
```

> Questa raccomandazione è per scopi di debug. Quando si scrive su una singola riga, non è chiaro se il test sia realmente vero o meno.
> ```php 
> if ($isFinished) doExecute(); // bad
> ```

> Se l'espressione condizionale supera il limite massimo della riga (72 caratteri), la riga va divisa dopo un operatore logico, allineando la nuova riga con l'inizio dell'espressione sulla riga precedente e con la parentesi di chiusura che deve essere sulla stessa riga dell'ultima condizione.
> ```php
> if ($test1 &&
>     $test2 ||
>     $test3)
> {
> 	// code
> }
> ```

> Si segue la regola generale INSERIRE LINK QUI a files.

**Le dichiarazioni eseguibili devono essere evitate nelle istruzioni condizionali.**
```php
$file = fopen($local_file, "r");

if ( ! $file)
{
    // code
}
```

> Le condizioni con istruzioni eseguibili sono semplicemente molto difficili da leggere. Questo è particolarmente vero per i programmatori nuovi in PHP.
> ```php
> if ( ! ($file = fopen($local_file, "r")))
> {
>     // code
> }
> ```

**Il blocco di codice di una struttura di controllo `if-else` deve seguire l'indentazione di Allman.**
```php
if ($condition)
{
    // code block
}

if ($condition)
{
    // code block
}
else
{
    // code block
}

if ($condition)
{
    // code block
}
elseif ($condition)
{
    // code block
}
else
{
    // code block
}
```
> L'approccio scelto è considerato migliore nel modo in cui ogni parte dell'istruzione if-else viene scritta su righe separate del file. Ciò rende più semplice la manipolazione dell'istruzione, ad esempio quando si spostano altre clausole.

**L'istruzione `elseif` deve essere sempre preferita a `else if`.**
> L'istruzione `else if` non è compatibile con la sintassi alternativa dell'istruzione `if else`, pertanto, per consistenza col resto del codice, va utilizzata solo l'istruzione `elseif`.


**L'istruzione singola deve essere scritte con le parentesi.**
```php
if ($condition)
{
    // code block
}
```
> Le parentesi sono superflue su una singola istruzione, ma c'è il rischio che il codice si interrompi se viene aggiunta un'istruzione dimenticando le parentesi, sebbene il codice non dovrebbe mai essere scritto per adattarsi ai cambiamenti che potrebbero insorgere.


**Le parole chiave della struttura di controllo devono essere seguite da uno spazio.**
> Migliora la leggibilità del codice.


**Il corpo di una struttura di controllo deve essere sempre racchiuso tra parentesi graffe.**
> Questo standardizza l'aspetto delle strutture e riduce la probabilità di introdurre errori man mano che nuove linee vengono aggiunte al corpo della struttura di controllo.


**L'espressione condizionale di una struttura di controllo deve essere preceduta e seguita solo ed esclusivamente dalle parentesi tonde.**
> Inutile evidenziare ulteriormente quanto contenuto dalle parentesi tonde di una struttura di controllo.

> Le espressioni che iniziano con l'operatore `!` seguono la raccomandazione generale per gli spazi bianchi intorno agli operatori e pertanto non è un'eccezione alla regola il seguente esempio:
> ```php
> if ( ! $condition)
> {
>     // code
> }
> ```

**Nei files dove PHP è mescolato all'Html deve essere utilizzata la sintassi alternativa per la struttura di controllo `if-else`.**
```php
<div>

    <?php if ($alpha) : ?>

        <p>true alpha condition</p>

    <?php elseif ($beta) : ?>

        <p>true beta condition</p>

    <?php else : ?>

        <p>default condition</p>

    <?php endif;>

</div>
```
> La sintassi alternativa migliora la leggibilità all'interno del codice Html.

> Si notino gli spazi che circondano i due punti `:`.

### while

**Le variabili di loop devono essere inizializzate immediatamente prima del ciclo.**
```php
$i = 0;

while ($i < 10) 
{
    echo ++$i;
}
```


**Il blocco di codice di una struttura di controllo `while` deve seguire l'indentazione di Allman.**
```php
while ($i < 10) 
{
    // code
}
```
> Deriva dalla raccomandazione generale sull'indentazione.


**L'istruzione singola deve essere scritte con le parentesi.**
```php
while ($condition)
{
    // code block
}
```
> Le parentesi sono per definizione superflue su una singola affermazione, ma c'è il rischio che il codice si interrompi se viene aggiunta un'istruzione aggiuntiva senza aggiungere le parentesi, sebbene il codice non dovrebbe mai essere scritto per adattarsi ai cambiamenti che potrebbero insorgere.


### do-while

**L'uso della struttura di controllo `do-while` deve essere evitata.**
```php

$i = 0;

do
{
    echo ++$i;
}
while ($i < 10) 
```
> La struttura di controllo `do-while` è meno leggibile di un `while` ordinario o di un ciclo `for`, perché l'istruzione condizionale si trova nella parte inferiore del ciclo. Il lettore deve eseguire la scansione dell' intero ciclo per comprendere lo scopo del ciclo.

> Inoltre, i cicli `do-while` non sono necessari. Qualsiasi ciclo `do-while` può essere facilmente riscritto in un ciclo `while` o in ciclo `for`. Ridurre il numero di costrutti utilizzati migliora la leggibilità.


**Il blocco di codice di una struttura di controllo `do-while` deve seguire l'indentazione di Allman.**
```php
do
{
    // code
}
while ($condition) 
```
> Deriva dalla raccomandazione generale sull'indentazione.


### for

**Solo le istruzioni di controllo del ciclo devono essere incluse nell'istruzione `for()`.**
```php
$sum = 0;

for ($i = 0; $i < 10; ++$i) 
{
    $sum += $value[$i];
}
```
> Aumenta la manutenibilità e la leggibilità, creando una chiara distinzione tra istruzioni di controllo e istruzioni contenute nel ciclo.


**Il blocco di codice di una struttura di controllo `for` devono seguire l'indentazione di Allman.**
```php
for ($i = 0; $i < 10; ++$i) 
{
    // code
}
```
> Deriva dalla raccomandazione generale sull'indentazione.


**L'istruzione singola deve essere scritte con le parentesi.**
```php
if ($condition)
{
    // code block
}
```
> Le parentesi sono per definizione superflue su una singola affermazione, ma c'è il rischio che il codice si interrompi se viene aggiunta un'istruzione aggiuntiva senza aggiungere le parentesi, sebbene il codice non dovrebbe mai essere scritto per adattarsi ai cambiamenti che potrebbero insorgere.

### foreach

**Il blocco di codice di una struttura di controllo `foreach` deve seguire l'indentazione di Allman.**
```php
foreach ($iterable as $key => $value) 
{
    echo $key . ' => ' . $value;
}

```
> Deriva dalla raccomandazione generale sull'indentazione.

### break

**L'uso di `break` nei cicli deve essere evitata.**
> Questa istruzione dovrebbe essere utilizzata solo se dimostra di essere più leggibile rispetto alle controparti strutturate.


**L'istruzione `break` deve essere indentata allo stesso livello del codice presente all'interno del blocco di codice cui appartiene.
```php
foreach ($iterable as $key => $value) 
{
    echo $key . ' => ' . $value;
    
    if ('foo' === $value)
    {
       break;
    }  
}

```
> All'interno di una struttura `switch` l'istruzione `break` deve essere preceduta e seguita da una riga vuota, come nell'esempio che segue:
> ```php
> switch ($value)  
> {
>     case ($condition) : 
>         $a = 'foo'; 
>         $b = 'bar'; 
>                     // blank line
>         break;
>                     // blank line
>     case ($condition) : 
>         $a = 'bar';
>         $b = 'foo';
>                     // blank line
>         break;
>                     // blank line
>     default : 
>         $a = 'no-foo';
>         $b = 'no-bar';
>                     // blank line
>         break;
>                     // blank line
> }
> ```
> Migliora la leggibilità del codice.


### continue

**L'uso di `continue` nei cicli deve essere evitata.**
> Questa istruzione dovrebbe essere utilizzata solo se dimostra di essere più leggibile rispetto alle controparti strutturate.


### switch

**Il blocco di codice di una struttura di controllo `switch` deve seguire l'indentazione di Allman.**
```php
switch ($value)  
{
    case ($condition) : 
        $a = 'foo'; 
        $b = 'bar'; 
                    // blank line
        break;
                    // blank line
    case ($condition) : 
        $a = 'bar';
        $b = 'foo';
                    // blank line
        break;
                    // blank line
    default : 
        $a = 'no-foo';
        $b = 'no-bar';
                       // blank line
        break;
}
```

> Deriva dalla raccomandazione generale sull'indentazione.


### declare

**Il costrutto `declare` deve essere la prima istruzione nel codice PHP.**
```php
<?php // blank space
            // blank line
declare(encoding = 'utf-8');
declare(strict_types = 1);
            // blank line
```

> Utilizzando il costrutto `declare` a livello globale, tutto il codice che segue sarà interessato da tale istruzione ed evita dimenticanze.

> Il costrutto ```php declare(encoding = 'utf-8')``` consente di evitare effetti collaterali negativi dovuti ad altre codifiche di caratteri.

> Il costrutto ```php declare(strict\_types = 1)``` consente di rendere il codice _autodocumentante_, oltre a renderlo più sicuro.


### return

**L'istruzione `return` deve essere separata dal resto del blocco codice da una riga vuota.**
```php
function bar() : int
{
    $sum = 0;

    for ($i = 0; $i < 11; ++$i)
    {
        $sum += $i;
    }
                    // blank line
    return $sum;
}
```

> Questa raccomandazione migliora la leggibilità del codice.

**Quando una funzione o un metodo restituiscono valori nulli esplicitamente si deve utilizzare `return NULL;`.**
```php
function foo() : null
{
    // code

    return NULL;
}
```
> Migliora la leggibilità del codice.


**Quando una funzione o un metodo restituiscono valori `void` si deve utilizzare `return;`.**
```php
public function setFirstName(string $firstName) : void
{
    $this->firstName = $firstName;
    
    return;
}
```
> Migliora la leggibilità del codice.


**Il valore restituito da `return` deve essere privo di parentesi.**
```php
function bar() : string
{
    // code

    return $bar;
}
```

> Racchiudere il valore restituito da `return` tra parentesi può ostacolare la leggibilità, in aggiunta alla rottura del codice se una funzione o un metodo vengono successivamente modificati per restituire un valore per riferimento.
```php
function bar() : string
{
    // code

    return ($bar); // bad
}
```

 ### try-catch
 
**Il blocco di codice di una struttura di controllo `try-catch` deve seguire l'indentazione di Allman.**
```php
try
{
    // code block
}
catch (\Exception $exception)
{
    // code
}

try
{
    // code block
}
catch (\Exception $exception)
{
    // code
}
finally
{
    // code block
}
```
> Deriva dalla raccomandazione generale sull'indentazione.


### require / require_once / include / include_once

**Per includere un file incondizionatamente deve essere utilizzata l'istruzione `require_once`.**
> L'istruzione va utilizzata nei casi in cui si vuol includere un file sempre e comunque, tipicamente all'inizio di uno script. Un file incluso con `require_once` non sarà incluso di nuovo da `include_once`.


**Per includere un file condizionatamente deve essere utilizzata l'istruzione `include_once`.**
> Laddove l'inclusione di un file sia soggetta a qualche condizione (ad esempio, metodi factory), va usato `include_once`. L'uso di `require_once` e `include_once` assicurerà che i file vengano inclusi solo una volta. Condividono la stessa lista di file, quindi non bisogna preoccuparsi di mescolarli.


**Le istruzioni di inclusione devono essere utilizzate senza parentesi.**
```php
require\_once ROOT_PATH . '/dir/file.php';
```
> Le istruzioni di inclusione `require_once` e `include_once` sono istruzioni del linguaggio e non funzioni, pertanto la corretta formattazione è senza parentesi.


**Le classi devono essere incluse attraverso la funzione `autoload` oppure una soluzione personalizzata.**
```php
$object = new \Namespace\ClassName();
```
> Ciò consente ai pacchetti di funzionare senza modifiche, indipendentemente dal modo in cui sono strutturati su disco, incluso l'esecuzione di un singolo file di grandi dimensioni, all'interno di un archivio `phar` e fornisce la necessaria flessibilità.

> Le classi dovrebbero essere semplicemente utilizzate con il `namespace` completo in modo da documentarne la posizione all'interno del _filesystem_.


### goto
**L'istruzione `goto` deve essere evitata assolutamente.**
> Rende il codice difficile da correggere oltre che difficile da comprendere.

[vai all'indice ⬆](#indice)

## Funzioni

**I nomi delle funzioni devono contenere solo caratteri alfanumerici, essere scritte in `mixedCase` in caso di più parole ed iniziare con un verbo.**
```php
function getFirstName() : string
{

}
```
> La verbosità è generalmente incoraggiata. I nomi delle funzioni dovrebbero essere prolissi quanto è pratico per descrivere pienamente il loro scopo e comportamento.

> I numeri sono consentiti nei nomi delle funzioni, ma sono da evitarsi nella maggior parte dei casi.

> Le funzioni _user defined_ nel namespace globale sono da evitarsi nella maggior parte dei casi.


**Le funzioni devono essere sempre dichiarate in un `namespace`.**
> Migliora l'organizzazione del codice, oltre che la portabilità dello stesso.


**Il corpo di una funzione deve seguire l'indentazione di Allman.**
```php
function getFirstName() : string
{
    // code
}
```
> Deriva dalla raccomandazione generale sull'indentazione.


**Le funzioni devono essere chiamate senza spazio tra il nome della funzione e la parentesi iniziale.**
```php
$var = foo($bar, $bar2, $bar3);
```
> Tra ogni parametro du una funzione c'è uno spazio, come detta la raccomandazione generale.


**Il corpo di una closure deve seguire l'indentazione di Allman.**
```php
$doExecute = function () : mixed
{
    // code
};
```
> Migliora la leggibilità.


**Gli argomenti con valori predefiniti devono essere posti alla fine dell'elenco degli argomenti.**
```php
$var = foo($bar, $baz = 'string', $quux = NULL);
```


**Il costrutto `use` di una closure deve essere preceduto e seguito da uno spazio.**
```php
$doExecute = function () use ($arg) : mixed
{
    // code
};
```
> Migliora la leggibilità.

[vai all'indice ⬆](#indice)

## Namespaces

**I nomi dei namespaces devono contenere solo caratteri alfanumerici ed essere scritti in `CapitalizedWords`.**
> I numeri sono consentiti nei nomi dei namespaces, ma sono da evitarsi nella maggior parte dei casi.

> Queste raccomandazioni nascono dal fatto che i nomi dei namespaces vengono mappati con i nomi delle directories, creando un collegamento biunivoco con queste ultime.


**La definizione del namespace deve essere la prima dichiarazione del file.**
```php
<?php 

namespace MyProject;

const CONNECT_OK = 1;

class Connection
{
    // code
}

function connect() : mixed
{
    // code
}
```

> L'unico costrutto di codice consentito prima che una dichiarazione dello spazio dei nomi sia l'istruzione `declare`, per definire la codifica di un file sorgente. Inoltre, nessun codice non-PHP può precedere una dichiarazione dello spazio dei nomi, inclusi spazi extra:
> ```php
> <html>
> <?php
> namespace MyProject; // fatal error - namespace must be the first statement in the script
> ?>
> ```


**L'importazione di altri `namespace` deve essere effettuata utilizzando l'istruzione `use`.**
```php
<?php 

namespace MyProject;

use \OtherNamespace;

```
> Migliora la leggibilità del codice, oltre a renderlo portabile.

> Se l'importazione di `namespace` crea conflitti tra i nomi, si può usare la parola chiave `as` per creare degli alias. In questo caso l'alias deve essere creato componendo i nomi dei sub-namespace, come nell'esempio che segue:
```php
use Baz\Qux\Quux as BazQuxQuux;
```

> Sempre per migliorare la leggibilità del codice, va utilizzata una sola dichiarazione `use` per riga ed una sola per ogni spazio dei nomi importato.

[vai all'indice ⬆](#indice)

## Interfacce

**I nomi delle interfacce devono contenere solo caratteri alfanumerici ed essere scritti in `CapitalizedWords`.**
> I numeri sono consentiti nei nomi delle interfacce, ma sono da evitarsi nella maggior parte dei casi.

> Queste raccomandazioni nascono dal fatto che i nomi delle interfacce vengono mappati con i nomi dei files, creando un collegamento biunivoco con questi ultimi.


**Le interfacce devono essere dichiarati in singoli file con il nome del file corrispondente al nome della interfaccia con l'aggiunta dell'estensione `.php`.**
> Migliora l'organizzazione del codice.


**Il corpo di un'interfaccia deve seguire l'indentazione di Allman.**
```php
interface Person
{
    // code
}
```
> Deriva dalla raccomandazione generale sull'indentazione.


**La posizione di ciascun elemento all'interno dell'interfaccia deve essere prevedibile.**
```php
interface Person
{
    public function getFirstName() : string;
    public function getLastName() : string;
}
```
> La raccomandazione tenta di ridurre la complessità, rendendo prevedibile la posizione di ciascun elemento dell'interfaccia.

> In generale i metodi vanno ordinati alfabeticamente per nome, ma si veda anche la raccomandazione per ordinare i metodi in base ai modificatori.

[vai all'indice ⬆](#indice)


## Traits

**I nomi dei traits devono contenere solo caratteri alfanumerici ed essere scritti in `CapitalizedWords`.**
> I numeri sono consentiti nei nomi dei traits, ma sono da evitarsi nella maggior parte dei casi.

> Queste raccomandazioni nascono dal fatto che i nomi dei traits vengono mappati con i nomi dei files, creando un collegamento biunivoco con questi ultimi.

**I traits devono essere dichiarati in singoli file con il nome del file corrispondente al nome del trait con l'aggiunta dell'estensione `.php`.**
> Migliora l'organizzazione del codice.

**Il corpo di un `trait` deve seguire l'indentazione di Allman.**
```php
trait Employee
{
    // code
}
```
> Deriva dalla raccomandazione generale sull'indentazione.


[vai all'indice ⬆](#indice)


## Classi

**I nomi delle classi devono contenere solo caratteri alfanumerici ed essere scritti in `CapitalizedWords`.**
> I numeri sono consentiti nei nomi delle classi, ma sono da evitarsi nella maggior parte dei casi.

> Queste raccomandazioni nascono dal fatto che i nomi delle classi vengono mappati con i nomi dei files, creando un collegamento biunivoco con questi ultimi e rendendo predicibile la posizione di un file.


**Le classi devono essere dichiarati in singoli file con il nome del file corrispondente al nome della classe con l'aggiunta dell'estensione `.php`.**
> Migliora l'organizzazione del codice.


**Le classi devono essere sempre dichiarate in un namespace.**
> Migliora l'organizzazione del codice, oltre che la portabilità dello stesso.


**Le classi devono essere dichiarate ognuna in un proprio file sorgente.**
> Migliora l'organizzazione del codice, oltre al fatto che i file sorgenti vanno mappati alle classi.


**Il corpo di una classe deve seguire l'indentazione di Allman.**
```php
class Person extends People implements Employee 
{
    // all contents of class
}
```
> Deriva dalla raccomandazione generale sull'indentazione.

**La posizione di ciascun elemento all'interno della classe deve essere prevedibile.**
```php
abstract class Person
{
    const FEMALE_TITLE = 'Mrs.';
    const MALE_TITLE = 'Mr.';

    private static $gender;

    private $firstName;
    private $lastName;

    abstract public function getFormalName() : string;

    public function __construct(string $firstName, string $lastName, string $gender)
    {
        $self::gender = $gender;

        $this->firstName = $firstName;
        $this->lastName = $lastName;
    }



    public function getFirstName() : string
    {
        return $this->firstName;
    }



    public function getLastName() : string
    {
        return $this->lastName;
    }



    protected function getTitle() : string
    {
        if ('female' == $self::gender)
        {
            return self::FEMALE_TITLE;
        }

        return self::MALE_TITLE;
    }
}
```
> La raccomandazione tenta di ridurre la complessità, rendendo prevedibile la posizione di ciascun elemento della classe.
> Gli elementi della classe vanno raggruppati e, all'interno di ciascun gruppo, ordinati alfabeticamente per nome:
> * costanti;
> * proprietà;
> * metodi;
> si vedano anche le raccomandazioni per ordinare proprietà e metodi.

> Per migliorare la leggibilità il gruppo delle costanti ed il gruppo delle proprietà terminano con una riga vuota. I metodi sono seguiti da tre righe vuote eccetto l'ultimo metodo della classe dove sarebbe superfluo.


**I metodi devono essere separati da tre righe vuote.**
> Separando i metodi con uno spazio più grande di quello utilizzato all'interno degli stessi, i metodi si distingueranno meglio all'interno della classe.


**Le classi che estendono altre classi o che implementano interfacce devono* dichiarare le loro dipendenze sulla stessa riga quando possibile.**
```php
class Person extends People implements Employee 
{
    // all contents of class
    // must be indented four spaces
}
```
> Migliora la leggibilità.

> Nel caso in cui la dichiarazione delle dipendenze di classe comportino il superamento della lunghezza massima della riga, la dihiarazione va interrotta prima delle parole chiave `extends` e / o `implements` applicando un livello di rientro.
> ```php
> class Person
>      extends People
>      implements Employee 
> {
>     // all contents of class
>     // must be indented four spaces
> }
> ```

> Se la classe implementa più interfacce e la dichiarazione supera la lunghezza massima della riga, la dichiarazione va interrotta dopo ogni virgola che separi le interfacce i cui nomi vanno rientrati in modo tale che si allineino.
> ```php
> class Person
>      extends People
>      implements Employee,
>                 Manager
> {
>     // all contents of class
>     // must be indented four spaces
> }
> ```


**Le classi devono essere istanziate utilizzando le parentesi indipendentemente dal numero di argomenti del costruttore.**
```php
$person = new Person();
```
> Migliora la leggibilità del codice, oltre a renderlo consistente.

[vai all'indice ⬆](#indice)

## Costanti di classe

**I nomi delle costanti di classe devono contenere solo caratteri alfanumerici, essere tutte in maiuscolo con le parole separate da caratteri di sottolineatura.**
```php
class Foo
{
 const DATABASE_HOST = 'dbhost';
 const DATABASE_NAME = 'dbname';
 const DATABASE_USER = 'dbuser';
 const DATABASE_PASSWORD = ''dbpwd'';

}
```

> Le costanti devono essere denominate in modo da indicare il loro scopo e contenuto.

> I numeri sono consentiti nei nomi delle costanti, ma sono da evitarsi nella maggior parte dei casi.

> I nomi delle costanti dovrebbero essere quanto più descrittivi possibile, ma anche quanto più brevi è possibile.

[vai all'indice ⬆](#indice)


## Proprietà

**I nomi delle proprietà devono contenere solo caratteri alfanumerici ed essere scritti in `mixedCase`.**
```php
class Person
{
    private $firstName = 'Mickey';
    private $lastName = 'Mouse';
}
```

> I numeri sono consentiti nei nomi delle proprietà, ma sono da evitarsi nella maggior parte dei casi.

> I nomi delle proprietà dovrebbero essere quanto più descrittivi possibile, ma anche quanto più brevi è possibile, quel tanto che basti a descrivere i dati che lo sviluppatore intende memorizzare in essi.

> Le proprietà che fanno riferimento ad oggetti dovrebbero in qualche modo essere associate alla classe di cui la proprietà è un oggetto.
> ```php
> class Manager
> {
>     private $person;
> 
>     public function __construct(\Person $person)
>     {
>         $this->person = $person;
>     }
> }
> ````


**Le proprietà di classe devono essere dichiarate `private` o `protected`.**

> Il concetto di _information hiding_ e incapsulamento è violato dalle proprietà dichiarate `public`. Devono essere invece utilizzate proprietà dichiarate `private` o `protected` e funzioni di accesso a queste proprietà.

> Il costrutto `var` non è permesso.

> Le proprietà della classe vanno raggruppate in base alla visibilità e, all'interno di ciascun gruppo, ordinate alfabeticamente per nome:
> * protected;
> * private;
> la raccomandazione tenta di ridurre la complessità, rendendo prevedibile la posizione di ciascun elemento della classe.

> Per una migliorare le leggibilità, non dovrebbero esserci righe vuote tra le dichiarazioni di proprietà e due righe vuote tra le sezioni di dichiarazione di proprietà e di metodo. È necessario aggiungere una riga vuota tra i diversi gruppi di visibilità.


**La dichiarazione delle proprietà deve seguire il seguente _pattern_: (`protected`|`private`)[`static`]_property name_.**
```php
abstract class Person
{
    const FEMALE_TITLE = 'Mrs.';
    const MALE_TITLE = 'Mr.';

    private static $gender;

    private $firstName;
    private $lastName;

    abstract public function getFormalName() : string;

    public function __construct(string $firstName, string $lastName, string $gender)
    {
        $self::gender = $gender;

        $this->firstName = $firstName;
        $this->lastName = $lastName;
    }

    public function getFirstName() : string
    {
        return $this->firstName;
    }

    public function getLastName() : string
    {
        return $this->lastName;
    }

    protected function getTitle() : string
    {
        if ('female' == $self::gender)
        {
            return self::FEMALE_TITLE;
        }

        return self::MALE_TITLE;
    }
}
```
> La raccomandazione tenta di ridurre la complessità, rendendo prevedibile la posizione di ciascun elemento della dichiarazione di proprietà.


> La lezione più importante qui è rendere obbligatorio il modificatore di visibilità. Tra i possibili modificatori, questo è di gran lunga il più importante e deve sempre esser presente nella dichiarazione di una proprietà. Per gli altri modificatori, l'ordine è meno importante, ma ha senso avere una convenzione fissa.

[vai all'indice ⬆](#indice)


## Metodi

**I nomi dei metodi di una classe devono contenere solo caratteri alfanumerici, essere scritte in `mixedCase` in caso di più parole ed iniziare con un verbo.**

```php
public function getFirstName() : string
{

}
```

> I numeri sono consentiti nei nomi dei metodi, ma sono da evitarsi nella maggior parte dei casi.

> La verbosità è generalmente incoraggiata. I nomi dei metodi dovrebbero essere prolissi quanto è pratico per descrivere pienamente il loro scopo e comportamento.

> Questa raccomandazione segue la prassi comune nella comunità di sviluppo PHP. Anche se la raccomandazione è in pratica identica a quella sui nomi delle funzioni, i metodi in PHP sono già distinguibili dalle funzioni per la loro forma specifica quando vengono invocati:
> ```php
> $person->getFirstName();
>
> getFirstName($person);
> ```


**I nomi dei metodi di una classe non devono contenere il nome della propria classe.**
```php
$person->getFirstName();
```
> Come mostrato nell'esempio, si rivela superfluo nell'uso: 
> ```php
> $person->getPersonFirstName(); // bad
> ```


**Il nome del metodo deve essere immediatamente seguito dalla parentesi di apertura degli argomenti.**
```php
class Person extends People implements Employee 
{
    public function setFirstName(string $firstName) : void
    {
        // code
    }
}
```


**Il corpo di un metodo deve seguire l'indentazione di Allman.**
```php
class Person extends People implements Employee 
{
    public function getFirstName() : string
    {
        // code
    }
}
```
> Deriva dalla raccomandazione generale sull'indentazione

**La dichiarazione dei metodi deve seguire il seguente _pattern_: \[`abstract`|`final`](`public`|`protected`|`private`)\[`static`]_method name_.**
```php
abstract class Person
{
    const FEMALE_TITLE = 'Mrs.';
    const MALE_TITLE = 'Mr.';

    private static $gender;

    private $firstName;
    private $lastName;

    abstract public function getFormalName() : string;

    public function __construct(string $firstName, string $lastName, string $gender)
    {
        $self::gender = $gender;

        $this->firstName = $firstName;
        $this->lastName = $lastName;
    }



    public function getFirstName() : string
    {
        return $this->firstName;
    }



    public function getLastName() : string
    {
        return $this->lastName;
    }



    protected function getTitle() : string
    {
        if ('female' == $self::gender)
        {
            return self::FEMALE_TITLE;
        }

        return self::MALE_TITLE;
    }
}
```
> La raccomandazione tenta di ridurre la complessità, rendendo prevedibile la posizione di ciascun elemento della dichiarazione di metodo.

> I metodi magici precedono all'interno dei singoli gruppi gli altri metodi ordinati alfabeticamente per nome.

> La lezione più importante qui è rendere obbligatorio il modificatore di visibilità. Tra i possibili modificatori, questo è di gran lunga il più importante e deve sempre esser presente nella dichiarazione del metodo. Per gli altri modificatori, l'ordine è meno importante, ma ha senso avere una convenzione fissa.


**Gli argomenti dei metodi devono avere lo stesso nome del loro _tipo_.**
```php
public function connect(\PDO $pdo) : mixed
{

}
```

> Riduce la complessità riducendo il numero di termini e nomi utilizzati. Inoltre rende facile dedurre il tipo dato dal nome della variabile.

> Se per qualche motivo questa convenzione non sembra adattarsi, c'è un forte sospetto che il nome del tipo è scelto male.

> Gli argomenti non _generici_ hanno un _ruolo_. Questi argomenti possono spesso essere denominati combinando il _ruolo_ e il _tipo_:
> ```php
> public function sendMessage(\Person $fromPerson, \Person $toPerson) : mixed
> {
> 
> }
> ```


**L'elenco di argomenti di un metodo deve essere interrotta dopo una virgola, allineando gli argomenti, se la lunghezza massima della riga viene superata.**
```php
class Foo
{
    public function bar($arg1, $arg2, $arg3,
                        $arg4, $arg5, $arg6) : mixed
    {
        // code
    }
}
```
> Un numero di argomenti superiore a tre è indice di codice scritto male. 

[vai all'indice ⬆](#indice)
