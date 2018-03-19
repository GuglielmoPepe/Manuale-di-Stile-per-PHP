# Manuale di Stile per PHP
Guida alla redazione di programmi in PHP (in lavorazione).

## indice

* [Raccomandazione generale](#raccomandazione-generale)
* [Directories](#directories)
* [Files](#files)
* [Tags php](#tags-php)
* [Istruzioni](#istruzioni)
* [Commenti](#commenti)
* [Tipi](#tipi)
* Variabili
* Costanti
* Operatori
* Strutture di controllo
* Funzioni
* Namespaces
* Interfacce
* Traits
* Classi
* Costanti di classe
* Proprietà
* Metodi



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












































































