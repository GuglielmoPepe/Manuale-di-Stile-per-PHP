# Manuale di Stile per PHP
Guida alla redazione di programmi in PHP (in lavorazione).

* [Tags del codice PHP](#tags-del-codice-php)
* [Separazioni delle istruzioni](#separazione-delle-istruzioni)
* [Stringhe](#stringhe)
* [Arrays](#arrays)
* [TRUE, FALSE e NULL](#true-false-e-null)
* [Variabili](#variabili)
* [Costanti](#costanti)
* [Operatori](#operatori)
* [Strutture di controllo](#strutture-di-controllo)

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

```php 
<p>This is going to be ignored by PHP and displayed by the browser.</p>
<?php echo 'While this is going to be parsed.'; ?>
<p>This will also be ignored by PHP and displayed by the browser.</p>
```
## Separazione delle istruzioni
PHP richiede che le istruzioni vengano terminate con un punto e virgola alla fine di ogni istruzione. Il tag di chiusura di un blocco di codice PHP implica automaticamente un punto e virgola.

Sebbene non sia necessario avere un punto e virgola per terminare l'ultima riga di un blocco PHP, le istruzioni devono terminare sempre con un punto e virgola per migliorare la leggibilità del codice oltre che per consistanza nella scrittura dello stesso.

```php

<?php echo 'This is a test' ?> // errato

<?php echo 'This is a test'; ?> // corretto

```


## Stringhe
Le stringhe letterali, quelle che non contengono sostituzioni di variabili, devono essere delimitate dall'apostrofo o "virgoletta singola". Esempio:

```php
$string = 'example string';
```

Quando una stringa letterale contiene apostrofi deve essere delimitata con le virgolette. Questo è particolarmente utile per le istruzioni SQL. Esempio:

```php
$sql = "SELECT `id`, `name` from `people` "
     . "WHERE `name`='Mickey' OR `name`='Minnie'";
```

Questa sintassi è preferibile rispetto agli apostrofi di escape poiché è molto più facile da leggere.
Sempre per migliorare la leggibilità, sono da evitarsi le stringhe contenenti sostituzioni di variabili, preferendo piuttosto la concatenazione di stringhe.

```php
// Poco chiaro
$string = "Hello $name, welcome back!";

$string = "Hello {$name}, welcome back!";

$string = "Hello ${name}, welcome back!";

// Molto meglio
$string = 'Hello ' . $name . ', welcome back!';
```
Le stringhe devono essere concatenate utilizzando l'operatore di concatenzione `.`, che deve essere sempre preceduto e seguito da uno spazio per migliorare la leggibilità del codice. Esempio:

```php
$string = 'Mickey' . ' ' . 'Mouse';
```

Quando si concatenano le stringhe con l'operatore `.`, si consiglia di suddividere l'istruzione in più righe per migliorare la leggibilità. In questi casi, ogni riga successiva deve essere riempita con tanti spazi bianchi, tali che l'operatore di concatenazione `.` sia allineato all'operatore di assegnazione `=`. 

Esempio:
```php
$sql = "SELECT `id`, `name` from `people` "
     . "WHERE `name`='Mickey' OR `name`='Minnie'";
     . "ORDER BY `name` ASC ";
```

## Arrays
Per la dichiarazione di un array usare sempre la sintassi concisa.
```php

  // errato
  $arr = array(
      'foo' => 'bar',
      'bar' => 'foo',
  );

  // corretto
  $arr = [
      'foo' => 'bar',
      'bar' => 'foo',
  ];
```
Gli indici letterali di un array devono essere sempre delimitati da apostrofi (virgolette singole).
```php
$foo[bar] = 'enemy';

echo $foo[bar];

```
Funziona, ma è sbagliato. L'indice nell'array `$foo` viene interpretao come stringa da PHP solo perchè non corrisponde a nessuna costante presente nello script: `bar` in effetti è una costante che PHP sostituirà con la stringa "bar" e la userà. 

Evitare l'uso di numeri negativi come indici di un array a causa di problemi che possono insorgere con alcune funzioni della libreria standard di PHP.

Per migliorare la leggibilità del codice è consigliato far seguire dopo ogni delimitatore `,` di elemento uno spazio. Esempio:

```php
$arr = ['Mickey', 'Minnie', 1, 2, 3];
```

Per migliorare la leggibilità del codice è consigliato far precedere e seguire da uno spazio l'operatore di associazione `=>` di un valore ad una chiave negli array associativi. Esempio:
 
```php
$arr = ['firstKey'  => 'firstValue', 'secondKey' => 'secondValue'];
```

Negli arrays suddivisi su più righe, l'elemento iniziale dell'array deve essere posizionato sulla riga seguente a quella della dichiarazione dell'array. In tal caso, dovrebbe essere riempito a un livello di rientro maggiore della riga contenente la dichiarazione dell'array e tutte le linee successive dovrebbero avere lo stesso rientro. La parentesi di chiusura deve essere su una propria riga allo stesso livello di indentazione della riga contenente la dichiarazione dell'array. Gli operatori di associazione di valore ad una chiave vanno allineati al fine di migliorare la leggibilità. Esempio:

```php
$arr = [
    'firstKey'  => 'firstValue', 
    'secondKey' => 'secondValue',
];
```

Si noti la virgola finale per l'ultimo elemento nell'array: ciò riduce al minimo la possibilità che si verifichino errori di analisi a causa di una virgola mancante per l'aggiunta di nuovi elementi.


## TRUE, FALSE e NULL
Le parole chiave `TRUE`, `FALSE` e `NULL` devono sempre essere completamente maiuscole, come tutte le costanti in PHP.

```php
  if ($foo == TRUE)
  {
    // php code
  }
  
  $bar = FALSE;
  
  function foo($bar = NULL)
  {
    // php code
  }
  
  ```


## Variabili
I nomi delle variabili possono contenere solo caratteri alfanumerici. I caratteri di sottolineatura non sono consentiti. I numeri sono consentiti nei nomi delle variabili, ma sono sconsigliati nella maggior parte dei casi.

Tutte le variabili dovrebbero iniziare con una lettera minuscola e dovrebbero essere scritte in `mixedCase` in caso di più parole.

I nomi delle variabili dovrebbero essere quanto più descrittivi possibile, ma anche quanto più brevi è possibile.  

Le variabili dovrebbero essere sempre prolisse, per descrivere i dati che lo sviluppatore intende memorizzare in essi. I nomi di variabili di una sola lettera, come `$i` e `$k`, sono sconsigliati tranne che nei cicli più piccoli. Se un ciclo contiene più di 20 righe di codice, le variabili dell'indice dovrebbero avere nomi più descrittivi.

Le variabili che fanno riferimento agli oggetti dovrebbero in qualche modo essere associate alla classe di cui la variabile è un oggetto. Esempio:

```php
$person = new Person();
```

Le variabili globali sono fortemente sconsigliate.


## Costanti
Le costanti possono contenere caratteri alfanumerici e caratteri di sottolineatura. I numeri sono consentiti nei nomi delle costanti.

Tutte le lettere utilizzate nel nome di una costante devono essere in maiuscolo, mentre tutte le parole nel nome di una costante devono essere separate da caratteri di sottolineatura. Questo include anche le costanti PHP predefinite come `TRUE`, `FALSE` e `NULL`.

La definizione di costanti nell'ambito globale con la funzione `define` è consentita, ma fortemente sconsigliata.

Le costanti devono essere denominate in modo da indicare il loro scopo e contenuto.

```php

define('PACKAGE_ROOT_PATH', 'package/root/path');

```

## Operatori
In generale gli operatori devono sempre essere preceduti e seguiti da uno spazio bianco. Si notino le eccezioni nei seguenti esempi.

Operatori aritmetici:
```php

$c = $a + $b;
$c = $a - $b;
$c = $a * $b;
$c = $a / $b;
$c = $a % $b;
$c = $a ** $b;
$c = +$a; // eccezione
$c = -$b; // eccezione

```

Operatori di assegnazione:
```php

$a = 3;
$a += 5; // sets $a to 8, as if we had said: $a = $a + 5;
$b = 'Hello ';
$b .= 'There!'; // sets $b to "Hello There!", just like $b = $b . "There!";

```

Operatori bitwise:
```php

$c = $a & $b;
$c = $a | $b;
$c = $a ^ $b;
$c = $a >> $b;
$c = $a << $b;
$c = ~ $a;

```

Operatori di confronto:
```php

$c = $a == $b;
$c = $a === $b;
$c = $a != $b;
$c = $a <> $b;
$c = $a !== $b;
$c = $a < $b;
$c = $a > $b;
$c = $a <= $b;
$c = $a >= $b;
$c = $a <=> $b;

```

Operatore di controllo errore:
```php

// eccezione
$my_file = @file ('non_existent_file') ||
    die ("Failed opening file: error was '$php_errormsg'");
    
```

Operatori di incremento e decremento:
```php

$a = 5;

++$a;
--$a;
$a++;
$a--;

```
Devono essere utilizzati solo l'operatori di incremento `++$a` e l'operatore di decremento `--$a` per motivi di leggibilità.

Operatori logici:
```php

$c = $a and $b;
$c = $a or $b;
$c = $a xor $b;
$c = ! $a;
$c = $a && $b;
$c = $a || $b;


```
Sebben esistano due varianti per gli operatori logici "and" e "or", devono essere utilizzati esclusivamente l'operatore `&&` e `||`.


Operatori su stringhe:
```php

$a = 'Hello ';
$b = $a . 'World!'; // now $b contains "Hello World!"

$a = 'Hello ';
$a .= 'World!';     // now $a contains "Hello World!"

```
Operatori su arrays:
```php

$a = ['a' => 'apple', 'b' => 'banana'];
$b = ['a' => 'pear', 'b' => 'strawberry'], 'c' => 'cherry'];

$c = $a + $b;
$c = $a == $b;
$c = $a === $b;
$c = $a != $b;
$c = $a <> $b;
$c = $a !== $b;

```

Operatore di tipo:
```php

class A { }
class B { }

$a = new A;
$b = new B;
$a2 = new A;

echo $a instanceOf $a; // true
echo $a instanceOf $b; // false
echo $a instanceOf $a2; // true

```


## Strutture di controllo
Le istruzioni di controllo basate sui costrutti `if` e `elseif` devono avere un singolo spazio prima della parentesi tonda di apertura dell'espressione condizionale e un singolo spazio dopo la parentesi tonda di chiusura.

All'interno delle istruzioni condizionali tra parentesi, gli operatori devono essere separati da spazi per la leggibilità. Le parentesi interne sono incoraggiate a migliorare il raggruppamento logico per espressioni condizionali più ampie.

La parentesi graffa di apertura è scritta sulla riga successiva a quella dell'istruzione condizionale. La parentesi di chiusura è sempre scritta su una riga separata. Qualsiasi contenuto all'interno delle parentesi deve essere rientrato utilizzando quattro spazi.
```php
if ($a != 2) 
{
    $a = 2;
}
```

Sebbene sia possibile omettere le parentesi graffe quando queste racchiudano una singola istruzione, il blocco di istruzioni deve essere sempre racchiuso al'interno di parentesi graffe al fine di aumentare la leggibilità oltre che per consistenza nella scrittura del codice.

```php

// errato
if ($a > $b)
  echo 'a is bigger than b';
 
 // corretto
if ($a > $b)
{
  echo 'a is bigger than b';
}
```


Nel caso in cui l'espressione condizionale superi il limite massimo della riga e abbia diverse clausole, deve essere suddivisa su più righe. L'espressione condizionale deve essere interrotta prima di un operatore logico, allineando le altre espressioni condizionali. La parentesi tonda di chiusura sarà posta, con un un livello di indentazione equivalente all'istruzione di controllo di apertura.
```php
if (($a == $b)
    && ($b == $c)
    || (Foo::CONST == $d)
) 
{
    $a = $d;
}
```
Si tenta di prevenire problemi durante l'aggiunta o la rimozione di clausole dall'espressione condizionale durante le revisioni successive.

Per le istruzioni `if` che includono `elseif` o `else`, le convenzioni di formattazione sono simili al costrutto `if`. I seguenti esempi dimostrano una corretta formattazione per le istruzioni `if` con i costrutti `else` e / o `elseif`.
```php

if ($a != 2)
{
    $a = 2;
}
else
{
    $a = 7;
}

if ($a != 2)
{
    $a = 2;
}
elseif ($a == 3)
{
    $a = 4;
}
else
{
    $a = 7;
}

if (($a == $b)
    && ($b == $c)
    || (Foo::CONST == $d)
)
{
    $a = $d;
}
elseif (($a != $b)
        || ($b != $c)
)
{
    $a = $c;
}
else
{
    $a = $b;
}

```
















