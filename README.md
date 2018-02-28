# Manuale di Stile per PHP
Guida alla redazione di programmi in PHP (in lavorazione).

* [Formato dei files](#formato-dei-files)
* [Codifica dei caratteri](#codifica-dei-caratteri)
* [Indentazione](#indentazione)
* [Lunghezza massima delle righe](#lunghezza-massima-delle-righe) 
* [Fine riga](#fine-riga) 
* [Tags del codice PHP](#tags-del-codice-php)
* [Directories](#directories)
* [Files](#files)
* [Istruzioni di inclusione](#istruzioni-di-inclusione)
* [Costanti](#costanti)
* [Variabili](#variabili)
* [Istruzioni di controllo](#istruzioni-di-controllo)
* [Operatori logici](#operatori-logici)
* [Funzioni](#funzioni)
* [Namespaces](#namespaces)
* [Interfacce](#interfacce)
* [Traits](#traits)
* [Classi astratte](#classi-astratte)
* [Classi](#classi)
* [Costanti di classe](#costanti-di-classe)
* [Proprietà](#proprietà)
* [Metodi](#metodi)
* [Stringhe](#stringhe)
* [Arrays](#arrays)



## Formato dei files


## Codifica dei caratteri
I file devono essere salvati con la codifica Unicode (UTF-8). Il BOM (Byte Order Mark) non deve essere utilizzato. 

A differenza di UTF-16 e UTF-32, non esiste un ordine di byte da indicare in un file con codifica UTF-8 e il BOM (Byte Order Mark) può avere un effetto collaterale negativo nell'invio dell'output, impedendo all'applicazione di impostare le proprie intestazioni.

La codifica può essere dichiarata usando `declare(encoding = 'utf-8');` nella parte superiore del file.


## Indentazione
Per l'indentazione devono essere utilizzati esclusivamente gli spazi che non devono mai essere mescolati con la tabulazione. 

Ciò aiuta ad evitare problemi con diff, patch, cronologia e annotazioni. L'uso degli spazi rende anche facile inserire una sub-indentazione a grana fine per l'allineamento tra le righe.


## Lunghezza massima delle righe
La lunghezza massima di una riga deve essere di 72 caratteri e righe più lunghe devono essere divise in più righe successive di non più di 72 caratteri. Alla fine di una riga non vuota non devono esserci spazi bianchi. 

Limitando la larghezza delle righe a 72 caratteri si migliora la leggibilità del codice.

Un limite di 72 caratteri rende necessario distribuire la logica o le espressioni complesse in funzioni, nonché assegnare nomi più brevi e più espressivi a funzioni ed oggetti.

Limitando la larghezza della finestra dell'editor a 72 caratteri, è possibile avere diversi file aperti fianco a fianco e funziona bene quando si utilizzano gli strumenti di revisione del codice che presentano le due versioni nelle colonne adiacenti.

Il wrapping predefinito nella maggior parte degli strumenti interrompe la struttura visiva del codice, rendendolo più difficile da capire. Il limite è stato scelto per evitare il wrapping degli editor con la larghezza della finestra impostata su 80, anche se lo strumento posiziona un glifo marcatore nella colonna finale quando effettua il wrapping delle linee. Alcuni strumenti basati sul Web potrebbero non offrire affatto il ritorno a capo automatico della linea.


## Fine riga
Le righe dei file PHP devono terminare con un singolo carattere di avanzamento riga Unix LF (linefeed).

La terminazione della riga segue la convenzione del file di testo Unix. I caratteri di avanzamento riga sono rappresentati come numero ordinale 10 oppure come numero esadecimale 0x0A.

Questo è più un problema per gli sviluppatori che lavorano in un ambiente Windows, ma in ogni caso assicurarsi che l'editor di testo sia configurato per salvare i file con interruzioni di riga Unix.


## Tags del codice PHP
Devono sempre essere usati esclusivamente i tag PHP estesi `<?php ?>` e mai quelli concisi `<? ?>`.

Nei file che contengono esclusivamente codice PHP, il tag di apertura `<?php` deve essere seguito da una singola riga vuota al fine di migliorare la leggibilità del codice.

Nei file che contengono esclusivamente codice PHP, il tag di chiusura `?>` deve essere omesso facendo teminare i files con una singola riga vuota.

Il tag di chiusura PHP `?>` in un documento PHP é facoltativo per il parser PHP. Tuttavia, se utilizzato, qualsiasi spazio vuoto successivo al tag di chiusura, introdotto dallo sviluppatore, dall'utente o da un'applicazione FTP, può causare output indesiderati, errori PHP o, se questi ultimi vengono soppressi, pagine vuote. Per questo motivo, tutti i file PHP devono omettere il tag di chiusura PHP e terminare con una singola riga vuota.

L'uso del tag esteso `<?php echo` era richiesto nel caso in cui un server non avesse avuto `short_open_tag` abilitato. 
Oggi questa esigenza risulta superata dopo che `PHP 5.4` ha reso sempre disponibile l'uso del tag conciso `<?=` indipendentemente dalla direttiva INI `short_open_tag`. Tuttavia per ragioni di consistenza non deve mai essere usato il tag breve `<?=` preferendogli l'uso esclusivo del tag esteso `<?php echo`.


## Directories
I nomi delle directories devono contenere solo caratteri alfanumerici, senza spazi oltre ad avere la prima lettera in maiuscolo. Se il nome di una directory è composto da più di una parola, la prima lettera di ogni nuova parola deve essere in maiuscolo (CapitalizedWords).

Questa esigenza nasce dal fatto che i nomi delle directories vengono mappati con i nomi del `namespace`, creando un collegamento biunivoco tra nome directory e `namespace` (o `sub-namespace`).


## Files
I nomi dei files devono contenere solo caratteri alfanumerici, senza spazi oltre ad avere la prima lettera in maiuscolo. Se il nome di una directory è composto da più di una parola, la prima lettera di ogni nuova parola deve essere in maiuscolo (CapitalizedWords). I nomi dei files devono terminare con l'estensione `.php`.

Questa esigenza nasce dal fatto che i nomi dei files vengono mappati con i nomi delle interfacce, dei traits o delle classi, creando un collegamento biunivoco con questi ultimi.


## Istruzioni di inclusione



## Costanti
Le costanti possono contenere caratteri alfanumerici e caratteri di sottolineatura. I numeri sono consentiti nei nomi delle costanti.

Tutte le lettere utilizzate nel nome di una costante devono essere in maiuscolo, mentre tutte le parole nel nome di una costante devono essere separate da caratteri di sottolineatura. Questo include anche le costanti PHP predefinite come `TRUE`, `FALSE` e `NULL`.

La definizione di costanti nell'ambito globale con la funzione `define` è consentita, ma fortemente sconsigliata.

Le costanti devono essere denominate in modo da indicare il loro scopo e contenuto.


## Variabili
I nomi delle variabili possono contenere solo caratteri alfanumerici. I caratteri di sottolineatura non sono consentiti. I numeri sono consentiti nei nomi delle variabili, ma sono scoraggiati nella maggior parte dei casi.

Tutte le variabili dovrebbero iniziare con una lettera minuscola e dovrebbero essere scritte in `mixedCase` in caso di più parole.

I nomi delle variabili dovrebbero essere quanto più descrittivi possibile, ma anche quanto più brevi è possibile.  

Le variabili dovrebbero essere sempre prolisse, per descrivere i dati che lo sviluppatore intende memorizzare in essi. I nomi di variabili di una sola lettera, come `$i` e `$k`, sono scoraggiati tranne che nei cicli più piccoli. Se un ciclo contiene più di 20 righe di codice, le variabili dell'indice dovrebbero avere nomi più descrittivi.

Le variabili che fanno riferimento agli oggetti dovrebbero in qualche modo essere associate alla classe di cui la variabile è un oggetto. Esempio:

```php
$person = new Person();
```

Le variabili globali sono fortemente scoraggiate.


## Istruzioni di controllo



## Operatori logici



## Funzioni
I nomi delle funzioni devono contenere solo caratteri alfanumerici. I caratteri di sottolineatura non sono consentiti. I numeri sono consentiti nei nomi delle funzioni, ma sono sconsigliati nella maggior parte dei casi.

I nomi delle funzioni devono sempre iniziare con una lettera minuscola. Quando il nome di una funzione è composto da più di una parola, la prima lettera di ogni nuova parola deve essere in maiuscolo (formattazione `mixedCase`).

La verbosità è generalmente incoraggiata. I nomi delle funzioni dovrebbero essere prolissi quanto è pratico per descrivere pienamente il loro scopo e comportamento.

Questo è un esempio di nome accettabile per una funzione:

```php
function longFunctionName()
{

}
```

Le funzioni globali sono fortemente scoraggiate.


## Namespaces
I nomi dei namespaces si mappano direttamente alle directories e possono contenere solo caratteri alfanumerici con la prima lettera in maiuscolo. I numeri sono consentiti nei nomi dei namespaces, ma sono sconsigliati nella maggior parte dei casi.

Se il nome di un namespace è composto da più di una parola, la prima lettera di ogni nuova parola deve essere in maiuscolo (_CapitalizedWords_). Non sono consentite lettere maiuscole successive, ad es. un namespace _"FilePDF"_ non è consentito, mentre _"FilePdf"_ è accettabile.


## Interfacce
I nomi delle interfacce si mappano direttamente ai files in cui sono memorizzate. I nomi delle interfacce possono contenere solo caratteri alfanumerici con la prima lettera in maiuscolo. I numeri sono consentiti nei nomi delle interfacce, ma sono sconsigliati nella maggior parte dei casi.

Se il nome di un'interfaccia è composto da più di una parola, la prima lettera di ogni nuova parola deve essere in maiuscolo (_CapitalizedWords_). Non sono consentite lettere maiuscole successive, ad es. un'interfaccia _"FilePDF"_ non è consentita, mentre _"FilePdf"_ è accettabile.


## Traits
I nomi dei traits si mappano direttamente ai files in cui sono memorizzati. I nomi dei traits possono contenere solo caratteri alfanumerici con la prima lettera in maiuscolo. I numeri sono consentiti nei nomi dei traits, ma sono sconsigliati nella maggior parte dei casi.

Se il nome di un trait è composto da più di una parola, la prima lettera di ogni nuova parola deve essere in maiuscolo (_CapitalizedWords_). Non sono consentite lettere maiuscole successive, ad es. un trait _"FilePDF"_ non è consentito, mentre _"FilePdf"_ è accettabile.


## Classi astratte
I nomi delle classi astratte si mappano direttamente ai files in cui sono memorizzate. I nomi delle classi astratte possono contenere solo caratteri alfanumerici con la prima lettera in maiuscolo. I numeri sono consentiti nei nomi delle classi astratte, ma sono sconsigliati nella maggior parte dei casi.

Se il nome di una classe astratta è composto da più di una parola, la prima lettera di ogni nuova parola deve essere in maiuscolo (_CapitalizedWords_). Non sono consentite lettere maiuscole successive, ad es. una classe astratta _"FilePDF"_ non è consentita, mentre _"FilePdf"_ è accettabile.


## Classi
I nomi delle classi si mappano direttamente ai files in cui sono memorizzate. I nomi delle classi possono contenere solo caratteri alfanumerici con la prima lettera in maiuscolo. I numeri sono consentiti nei nomi delle classi, ma sono sconsigliati nella maggior parte dei casi.

Se il nome di una classe è composto da più di una parola, la prima lettera di ogni nuova parola deve essere in maiuscolo (_CapitalizedWords_). Non sono consentite lettere maiuscole successive, ad es. una classe _"FilePDF"_ non è consentita, mentre _"FilePdf"_ è accettabile.


## Costanti di classe
Le costanti possono contenere caratteri alfanumerici e caratteri di sottolineatura. I numeri sono consentiti nei nomi delle costanti.

Tutte le lettere utilizzate nel nome di una costante devono essere in maiuscolo, mentre tutte le parole nel nome di una costante devono essere separate da caratteri di sottolineatura.

I nomi delle costanti dovrebbero essere quanto più descrittivi possibile, ma anche quanto più brevi è possibile.  


## Proprietà
I nomi delle proprietà possono contenere solo caratteri alfanumerici. I caratteri di sottolineatura non sono consentiti. I numeri sono consentiti nei nomi delle proprietà ma sono scoraggiati nella maggior parte dei casi.

Tutte le proprietà dovrebbero iniziare con una lettera minuscola e dovrebbero essere scritte in `mixedCase` in caso di più parole.

I nomi delle proprietà dovrebbero essere quanto più descrittivi possibile, ma anche quanto più brevi è possibile.  

Le proprietà dovrebbero essere sempre prolisse per descrivere i dati che lo sviluppatore intende memorizzare in essi.

Le proprietà che fanno riferimento agli oggetti dovrebbero in qualche modo essere associate alla classe di cui la proprietà è un oggetto. Esempio:

```php
$this->person = new Person();
```

## Metodi
I nomi dei metodi possono contenere solo caratteri alfanumerici. I caratteri di sottolineatura non sono consentiti. I numeri sono consentiti nei nomi dei metodi ma sono scoraggiati nella maggior parte dei casi.

I nomi dei metodi devono sempre iniziare con una lettera minuscola. Quando il nome di un metodo è composto da più di una parola, la prima lettera di ogni nuova parola deve essere in maiuscolo (formattazione `mixedCase`).

La verbosità è generalmente incoraggiata. I nomi dei metodi dovrebbero essere prolissi quanto è pratico per descrivere pienamente il loro scopo e comportamento.

Questo è un esempio di nome accettabile per un metodo:

```php
public function longMethodName()
{

}
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

Si noti la virgola finale per l'ultimo elemento nell'array. Negli arrays suddivisi su più righe riduce al minimo la possibilità che si verifichino errori di analisi a causa di una virgola mancante per l'aggiunta di nuovi elementi.
