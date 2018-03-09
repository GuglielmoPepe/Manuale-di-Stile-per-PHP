# Manuale di Stile per PHP
Guida alla redazione di programmi in PHP (in lavorazione).

* [Directories](#directories)
* [Files](#files)
* [Costanti](#costanti)
* [Variabili](#variabili)
* [Stringhe](#stringhe)
* [Arrays](#arrays)
* [Funzioni](#funzioni)
* [Namespaces](#namespaces)
* [Interfacce](#interfacce)
* [Classi](#classi)
* [Costanti di classe](#costanti-di-classe)


## Directories
### I nomi delle directories **DEVONO** seguire le seguenti raccomandazioni:
* i nomi delle directories **DEVONO** contenere solo caratteri alfanumerici;
* i nomi delle directories **NON DEVONO** contenere spazi;
* i nomi delle directories **DEVONO** essere in formato `CapitalizedWords`;

> Queste raccomandazioni nascono dal fatto che i nomi delle directories vengono mappati con i nomi dei namespaces, creando un collegamento biunivoco con questi ultimi.

## Files
### I nomi dei files **DEVONO** seguire le seguenti raccomandazioni:
* i nomi dei files **DEVONO** contenere solo caratteri alfanumerici;
* i nomi dei files **NON DEVONO** contenere spazi;
* i nomi dei files **DEVONO** essere in formato `CapitalizedWords`;
* nomi dei files **DEVONO** terminare con l'estensione `.php`;

> Queste raccomandazioni nascono dal fatto che i nomi dei files vengono mappati con i nomi delle interfacce, dei traits o delle classi, creando un collegamento biunivoco con questi ultimi.

### Il codice PHP **DEVE** usare esclusivamente la codifica dei caratteri UTF-8 senza BOM (Byte Order Mark).

### Il codice PHP **DEVE** usare solo rientri di quattro spazi.

### Il codice PHP **NON DEVE** mai usare la tabulazione per i rientri.

### La lunghezza massima di una riga **DEVONO** essere di 72 caratteri.

### Righe più lunghe **DEVONO** essere divise in più righe successive di non più di 72 caratteri.

### Alla fine di una riga non vuota **NON DEVONO** esserci spazi bianchi.

### Le righe dei file PHP **DEVONO** terminare con un singolo carattere di avanzamento riga Unix LF (linefeed).

## Tags del codice PHP
### I files che contengono solo codice PHP **DEVONO** usare il tag esteso `<?php`.

### Il tag di apertura `<?php` **DEVE** essere seguito da una singola riga vuota.

### Il tag di chiusura `?>` **DEVE** essere omesso dai files che contengono solo codice PHP.

### Il tag breve `<?=` **NON DEVE** essere utilizzato.

> Migliora la leggibilità oltre che per consistenza.

### Il codice PHP deve essere delimitato dai tags `<?php ... ?>`.
### Il tag esteso `<?php` **DEVE** essere immediatamente seguito da un singolo spazio.
### Il tag di chiusura `?>` **DEVE** essere immediatamente preceduto da un singolo spazio.
### Tutti i files **DEVONO** terminare con una singola riga vuota.


### Ogni file che contiene codice PHP **DEVE** avere un _dockblock_ nella parte superiore del file, che contenga almeno i seguenti tags _phpDocumentor_:
```php
/**
 * Example Framework (http://www.exampleframework.com/)
 *
 * Long description for file (if any)...
 *
 * @link      http://github.com/exampleframework/ for the canonical source repository
 * @copyright Copyright (c) 2005-2013 Example Technologies USA Inc. (http://www.example.com)
 * @license   http://framework.example.com/license/new-bsd New BSD License
 * @since     File available since Release 1.5.0
 */
 
```
> Migliora la documentazione del codice.

## Costanti
### I nomi delle costanti **DEVONO** seguire le seguenti raccomandazioni:
* i nomi delle costanti **DEVONO** contenere solo caratteri alfanumerici ed il carattere di sottolineatura;
* tutte le lettere utilizzate nel nome di una costante **DEVONO** essere in maiuscolo;
* tutte le parole nel nome di una costante **DEVONO** essere separate da caratteri di sottolineatura;
* le costanti devono essere denominate in modo da indicare il loro scopo e contenuto;

```php
define('DATABASE_HOST', 'dbhost');
define('DATABASE_NAME', 'dbname');
define('DATABASE_USER', 'dbuser');
define('DATABASE_PASSWORD', 'dbpwd');

```

> Anche le costanti PHP predefinite come `TRUE`, `FALSE` e `NULL` devono essere tutte in maiuscolo.

> La definizione di costanti nell'ambito globale con la funzione `define` è consentita, ma fortemente sconsigliata. Sono da preferirsi le costanti di classe e se proprio sono necessarie le costanti globali meglio inserirle nel punto di ingresso dello script o meglio ancora in un file separato.

## Variabili
### I nomi delle variabili **DEVONO** seguire le seguenti raccomandazioni:
* i nomi delle variabili **DEVONO** contenere solo caratteri alfanumerici;
* i nomi delle variabili **NON DEVONO** contenere caratteri di sottolineatura non sono consentiti;
* i nomi delle variabili **DEVONO** iniziare con una lettera minuscola;
* i nomi delle variabili **DEVONO** essere scritte in `mixedCase` in caso di più parole;

```php
$firstName = 'Mickey';
```

> I numeri sono consentiti nei nomi delle variabili, ma sono da evitarsi nella maggior parte dei casi.

> I nomi delle variabili dovrebbero essere quanto più descrittivi possibile, ma anche quanto più brevi è possibile.  

> Le variabili dovrebbero essere sempre prolisse, per descrivere i dati che lo sviluppatore intende memorizzare in essi. I nomi di variabili di una sola lettera, come `$i` e `$k`, sono scoraggiati tranne che nei cicli più piccoli. Se un ciclo contiene più di 20 righe di codice, le variabili dell'indice dovrebbero avere nomi più descrittivi.

### Le variabili che fanno riferimento agli oggetti dovrebbero in qualche modo essere associate alla classe di cui la variabile è un oggetto.
```php
$person = new Person();
```
> Migliora la leggibilità del codice.

### Le variabili globali **NON DEVONO** essere usate.

## Stringhe
### Le stringhe letterali **DEVONO** essere delimitate dalle virgolette singole.
```php
$string = 'example string';
```

### Le stringhe che contengono virgolette singole **DEVONO** essere delimitate dalle virgolette doppie.
```php
$str = "That's a 'magic' sock.";
```
> Questa sintassi è preferibile rispetto al carattere di escape `\` poiché è molto più facile da leggere.
> Inoltre è particolarmente utile per le istruzioni SQL:
> ```php
> $sql = "SELECT `id`, `name` "
>      . "FROM `people` "
>      . "WHERE `name`='Mickey' OR `name`='Minnie'";
> ```

### Le stringhe **NON DEVONO** contenere variabili da sostituire.
```php
$string = 'Hello ' . $name . ', welcome back!';
```
> Questa sintassi migliora le leggibilità del codice rispetto ai seguenti esempi:
> ```php
> $string = "Hello $name, welcome back!";
> $string = "Hello {$name}, welcome back!";
> $string = "Hello ${name}, welcome back!";
> ```

### L'operatore di concatenazione **DEVE** essere preceduto e seguito da un singolo spazio.
```php
$string = 'Mickey' . ' ' . 'Mouse';
```
> Migliora la leggibilità del codice.

### L'operatore di concatenazione `.` **DEVE** essere allineato all'operatore di assegnazione `=` quando l'istruzione è suddivisa su più righe.
```php
$sql = "SELECT `id`, `name` "
     . "FROM `people` "
     . "WHERE `name`='Mickey' OR `name`='Minnie'";
     . "ORDER BY `name` ASC ";
```
> Quando si concatenano le stringhe con l'operatore `.`, è meglio suddividere l'istruzione in più righe per migliorarne la leggibilità. In questi casi, ogni riga successiva deve essere riempita con tanti spazi bianchi, tali che l'operatore di concatenazione `.` sia allineato all'operatore di assegnazione `=`. 

## Arrays
### Gli arrays **DEVONO** essere dichiarati con la sintassi concisa.
```php
$arr = [];
```

### Gli arrays **NON DEVONO** avere indici numerici negativi.
> L'uso di numeri negativi come indici di un array può causare problemi con alcune funzioni della libreria standard di PHP.

### I delimitatori degli elementi `,` di un array **DEVONO** essere seguiti da uno spazio.
```php
$arr = ['Mickey', 'Minnie', 1, 2, 3];

```
> Migliora la leggibilità del codice.

### Gli operatori di assegnazione di un valore a una chiave `=>` **DEVONO** essere preceduti e seguiti da uno spazio.
```php
$arr = ['firstKey'  => 'firstValue', 'secondKey' => 'secondValue'];

```
> Migliora la leggibilità del codice.

### Gli array suddivisi su più righe **DEVONO** seguire le seguenti raccomandazioni:
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

## Funzioni
### I nomi delle funzioni **DEVONO** seguire le seguenti raccomandazioni:
* i nomi delle funzioni **DEVONO** contenere solo caratteri alfanumerici;
* i nomi delle funzioni **DEVONO** iniziare con una lettera minuscola;
* i nomi delle funzioni **DEVONO** essere scritte in `mixedCase` in caso di più parole;

```php
function longFunctionName()
{

}

```

> I numeri sono consentiti nei nomi delle funzioni, ma sono da evitarsi nella maggior parte dei casi.

>La verbosità è generalmente incoraggiata. I nomi delle funzioni dovrebbero essere prolissi quanto è pratico per descrivere pienamente il loro scopo e comportamento.

### Le funzioni nel namespace globale **NON DEVONO** essere usate.

## Namespaces
### I nomi dei namespaces **DEVONO** seguire le seguenti raccomandazioni:
* i nomi dei namespaces **DEVONO** contenere solo caratteri alfanumerici;
* i nomi dei namespaces **DEVONO** iniziare con una lettera maiuscola;
* i nomi dei namespaces **DEVONO** essere scritte in `CapitalizedWords` in caso di più parole;

> I numeri sono consentiti nei nomi dei namespaces, ma sono da evitarsi nella maggior parte dei casi.

> Queste raccomandazioni nascono dal fatto che i nomi dei namespaces vengono mappati con i nomi delle directories, creando un collegamento biunivoco con queste ultime.

## Intefacce
### I nomi delle interfacce **DEVONO** seguire le seguenti raccomandazioni:
* i nomi delle interfacce **DEVONO** contenere solo caratteri alfanumerici;
* i nomi delle interfacce **DEVONO** iniziare con una lettera maiuscola;
* i nomi delle interfacce **DEVONO** essere scritte in `CapitalizedWords` in caso di più parole;

> I numeri sono consentiti nei nomi delle interfacce, ma sono da evitarsi nella maggior parte dei casi.

> Queste raccomandazioni nascono dal fatto che i nomi delle interfacce vengono mappati con i nomi dei files che le contengono, creando un collegamento biunivoco con questi ultimi.

## Traits
### I nomi dei traits **DEVONO** seguire le seguenti raccomandazioni:
* i nomi dei traits **DEVONO** contenere solo caratteri alfanumerici;
* i nomi dei traits **DEVONO** iniziare con una lettera maiuscola;
* i nomi dei traits **DEVONO** essere scritte in `CapitalizedWords` in caso di più parole;

> I numeri sono consentiti nei nomi dei traits, ma sono da evitarsi nella maggior parte dei casi.

> Queste raccomandazioni nascono dal fatto che i nomi dei traits vengono mappati con i nomi dei files che li contengono, creando un collegamento biunivoco con questi ultimi.

## Classi
### I nomi delle classi **DEVONO** seguire le seguenti raccomandazioni:
* i nomi delle classi **DEVONO** contenere solo caratteri alfanumerici;
* i nomi delle classi **DEVONO** iniziare con una lettera maiuscola;
* i nomi delle classi **DEVONO** essere scritte in `CapitalizedWords` in caso di più parole;

> I numeri sono consentiti nei nomi delle classi, ma sono da evitarsi nella maggior parte dei casi.

> Queste raccomandazioni nascono dal fatto che i nomi delle classi vengono mappati con i nomi dei files che le contengono, creando un collegamento biunivoco con questi ultimi.

### La dichiarazione di classe **DEVE** seguire le seguenti raccomandazioni:
* le classi che estendono altre classi o che implementano interfacce **DEVONO** dichiarare le loro dipendenze sulla stessa linea  quando possibile;
* la dichiarazione di classe **DEVE** essere suddivisa su più righe se supera la lunghezza massima per una riga (inserire link);
* la dichiarazione di classe **DEVE** essere interrotta prima delle parole chiave `extends` e `implements` se supera la lunghezza massima per una riga(inserire link);
* le istruzioni `extends` e `implements` **DEVONO** essere dichiarate su una propria riga e con un livelo di rientro;
* l'istruzione `implements` **DEVE** essere interrotta dopo ogni virgola che separa le interfacce se la dichiarazione di classe  supera la lunghezza massima della riga;
* i nomi delle interfacce **DEVONO** essere allineate se la dichiarazione di classe  supera la lunghezza massima della riga;
* la parentesi di apertura **DEVE** essere su una propria riga;
* la parentesi di chiusura **DEVE** essere su una propria riga, successiva al corpo della classe;

> Migliora la leggibilità del codice.


## Costanti di classe
### I nomi delle costanti di classe **DEVONO** seguire le seguenti raccomandazioni:
* i nomi delle costanti di classe **DEVONO** contenere solo caratteri alfanumerici ed il carattere di sottolineatura;
* tutte le lettere utilizzate nel nome di una costante di classe **DEVONO** essere in maiuscolo;
* tutte le parole nel nome di una costante di classe **DEVONO** essere separate da caratteri di sottolineatura;
* le costanti devono essere denominate in modo da indicare il loro scopo e contenuto;

```php
class Foo
{
 const DATABASE_HOST = 'dbhost';
 const DATABASE_NAME = 'dbname';
 const DATABASE_USER = 'dbuser';
 const DATABASE_PASSWORD = ''dbpwd'';

}
```

### Proprietà
#### I nomi delle proprietà di una classe **DEVONO** seguire le seguenti raccomandazioni:
* i nomi delle proprietà **DEVONO** contenere solo caratteri alfanumerici;
* i nomi delle proprietà **DEVONO** iniziare con una lettera minuscola; 
* i nomi delle proprietà **DEVONO** essere scritte in `mixedCase` in caso di più parole;


### Metodi
#### I nomi dei metodi di una classe **DEVONO** seguire le seguenti raccomandazioni:
* i nomi dei metodi **DEVONO** contenere solo caratteri alfanumerici;
* i nomi dei metodi **DEVONO** iniziare con una lettera minuscola; 
* i nomi dei metodi **DEVONO** essere scritte in `mixedCase` in caso di più parole;

