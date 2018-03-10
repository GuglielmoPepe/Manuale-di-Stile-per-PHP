# Manuale di Stile per PHP
Guida alla redazione di programmi in PHP (in lavorazione).

* [Qualsiasi raccomandazione del manuale **DEVE** essere violata se migliora la leggibilità](#qualsiasi-raccomandazione-del-manuale-deve-essere-violata-se-migliora-la-leggibilità)
* [Tutti i nomi **DEVONO** essere scritti in inglese](#tutti-i-nomi-devono-essere-scritti-in-inglese)
* [I nomi dei namespaces **DEVONO** contenere solo caratteri alfanumerici ed essere scritti in `CapitalizedWords`](#i-nomi-dei-namespaces-devono-contenere-solo-caratteri-alfanumerici-ed-essere-scritti-in-capitalizedwords)
* [I nomi delle interfacce, dei traits e delle classi **DEVONO** contenere solo caratteri alfanumerici ed essere scritti in `CapitalizedWords`](#i-nomi-delle-interfacce-dei-traits-e-delle-classi-devono-contenere-solo-caratteri-alfanumerici-ed-essere-scritti-in-capitalizedwords)
* [I nomi delle variabili **DEVONO** contenere solo caratteri alfanumerici ed essere scritti in `mixedCase`](#i-nomi-delle-variabili-devono-contenere-solo-caratteri-alfanumerici-ed-essere-scritti-in-mixedcase)
* [Le variabili _generiche_ **DEVONO** avere lo stesso nome del loro tipo](#le-variabili-generiche-devono-avere-lo-stesso-nome-del-loro-tipo)
* [I nomi delle costanti **DEVONO** contenenre solo caratteri alfanumerici, essere tutte in maiuscolo con le parale separate da caratteri di sottolineatura](#i-nomi-delle-costanti-devono-contenenre-solo-caratteri-alfanumerici-essere-tutte-in-maiuscolo-con-le-parale-separate-da-caratteri-di-sottolineatura)
* [I nomi delle funzioni **DEVONO** contenere solo caratteri alfanumerici, essere scritte in `mixedCase` in caso di più parole ed iniziare con un verbo](#i-nomi-delle-funzioni-devono-contenere-solo-caratteri-alfanumerici-essere-scritte-in-mixedcase-in-caso-di-più-parole-ed-iniziare-con-un-verbo)
* [I nomi dei metodi di una classe **DEVONO** contenere solo caratteri alfanumerici, essere scritte in `mixedCase` in caso di più parole ed iniziare con un verbo](#i-nomi-dei-metodi-di-una-classe-devono-contenere-solo-caratteri-alfanumerici-essere-scritte-in-mixedcase-in-caso-di-più-parole-ed-iniziare-con-un-verbo)
* [I nomi dei metodi di una classe **NON DEVONO** contenere il nome della propria classe](#i-nomi-dei-metodi-di-una-classe-non-devono-contenere-il-nome-della-propria-classe)
* [Le abbreviazioni e gli acronimi **NON DEVONO** avere tutte lettere maiuscole se usati come nome](#le-abbreviazioni-e-gli-acronimi-non-devono-avere-tutte-lettere-maiuscole-se-usati-come-nome)
* [I nomi delle directories **DEVONO** contenere solo caratteri alfanumerici ed essere scritti in `CapitalizedWords`](#i-nomi-delle-directories-devono-contenere-solo-caratteri-alfanumerici-ed-essere-scritti-in-capitalizedwords)
* [I nomi dei files **DEVONO** contenere solo caratteri alfanumerici, essere scritti in `CapitalizedWords` e terminare con l'estensione `.php`](#i-nomi-dei-files-devono-contenere-solo-caratteri-alfanumerici-essere-scritti-in-capitalizedwords-e-terminare-con-lestensione-php)
* [I files PHP **DEVONO** usare esclusivamente la codifica dei caratteri UTF-8 senza BOM (Byte Order Mark)](#i-files-php-devono-usare-esclusivamente-la-codifica-dei-caratteri-utf-8-senza-bom-byte-order-mark))
* [I files **DEVONO** usare un'indentazione di quattro spazi](#i-files-devono-usare-unindentazione-di-quattro-spazi)


## Qualsiasi raccomandazione del manuale **DEVE** essere violata se migliora la leggibilità.
> L'obiettivo principale delle raccomandazioni è migliorare la leggibilità e di conseguenza la comprensione, la manutenibilità e la qualità generale del codice. Poichè è impossibile coprire tutti i casi specifici, il programmatore dovrebbe essere flessibile.

##  La lingua utilizzata per scrivere il codice ed i commenti **DEVE** essere l'inglese.
> L'inglese è la lingua preferita per lo sviluppo a livello internazionale.

## I nomi dei namespaces **DEVONO** contenere solo caratteri alfanumerici ed essere scritti in `CapitalizedWords`.
> I numeri sono consentiti nei nomi dei namespaces, ma sono da evitarsi nella maggior parte dei casi.

> Queste raccomandazioni nascono dal fatto che i nomi dei namespaces vengono mappati con i nomi delle directories, creando un collegamento biunivoco con queste ultime.

## I nomi delle interfacce, dei traits e delle classi **DEVONO** contenere solo caratteri alfanumerici ed essere scritti in `CapitalizedWords`.
> I numeri sono consentiti nei nomi dei delle interfacce, dei traits e delle classi, ma sono da evitarsi nella maggior parte dei casi.

> Queste raccomandazioni nascono dal fatto che i nomi delle interfacce, dei traits e delle classi vengono mappati con i nomi dei files che li contengono, creando un collegamento biunivoco con questi ultimi.

## I nomi delle variabili **DEVONO** contenere solo caratteri alfanumerici ed essere scritti in `mixedCase`.
```php
$firstName = 'Mickey';
```

> I numeri sono consentiti nei nomi delle variabili, ma sono da evitarsi nella maggior parte dei casi.

> I nomi delle variabili dovrebbero essere quanto più descrittivi possibile, ma anche quanto più brevi è possibile, quel tanto che basti a descrivere i dati che lo sviluppatore intende memorizzare in essi.

> I nomi di variabili di una sola lettera, come `$i` e `$k`, sono da evitarsi tranne che nei cicli più piccoli. Se un ciclo contiene più di 20 righe di codice, le variabili dell'indice dovrebbero avere nomi più descrittivi.

> Le variabili globali sono da evitarsi.

> Le variabili che fanno riferimento agli oggetti dovrebbero in qualche modo essere associate alla classe di cui la variabile è un oggetto.
> ```php
> $person = new \Person();
> ```

## Le variabili _generiche_ **DEVONO** avere lo stesso nome del loro tipo.
```php
public function connect(\PDO $pdo)
{

}
```

> Riduce la complessità riducendo il numero di termini e nomi utilizzati. Inoltre rende facile dedurre il tipo dato dal nome della variabile.

> Se per qualche motivo questa convenzione non sembra adattarsi, c'è un forte sospetto che il nome del tipo è scelto male.

> Le variabili non generiche hanno un _ruolo_. Queste variabili possono spesso essere nominate combinando il ruolo e il tipo:
> ```php
> public function sendMessage(\Person $fromPerson, \Person $toPerson)
> {
> 
> }
> ```


## I nomi delle costanti **DEVONO** contenenre solo caratteri alfanumerici, essere tutte in maiuscolo con le parale separate da caratteri di sottolineatura.
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

## I nomi delle funzioni **DEVONO** contenere solo caratteri alfanumerici, essere scritte in `mixedCase` in caso di più parole ed iniziare con un verbo.

```php
function getFirstName()
{

}
```
>La verbosità è generalmente incoraggiata. I nomi delle funzioni dovrebbero essere prolissi quanto è pratico per descrivere pienamente il loro scopo e comportamento.

> I numeri sono consentiti nei nomi delle funzioni, ma sono da evitarsi nella maggior parte dei casi.

> Le funzioni _user defined_ nel namespace globale sono da evitarsi nella maggior parte dei casi.

## I nomi dei metodi di una classe **DEVONO** contenere solo caratteri alfanumerici, essere scritte in `mixedCase` in caso di più parole ed iniziare con un verbo.

```php
public function getFirstName()
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

## I nomi dei metodi di una classe **NON DEVONO** contenere il nome della propria classe.
```php
$person->getFirstName();
```
> Come mostrato nell'esempio, si rivela superfluo nell'uso: 
> ```php
> $person->getPersonFirstName(); // bad
> ```

## Le abbreviazioni e gli acronimi **NON DEVONO** avere tutte lettere maiuscole se usati come nome. 
> L'utilizzo di tutte le maiuscole per il nome di base causerà conflitti con le convenzioni di denominazione. Una vatiabile denominata `$pDF` non è molto leggibile. Inoltre quando un nome è composto da più di una parola (`PDFFile`) la leggibilità viene seriamente ridotta, perchè la parola che segue l'acronimo non spicca come dovrebbe.

## I nomi delle directories **DEVONO** contenere solo caratteri alfanumerici ed essere scritti in `CapitalizedWords`.
> I numeri sono consentiti nei nomi delle directories, ma sono da evitarsi nella maggior parte dei casi.

> Queste raccomandazioni nascono dal fatto che i nomi delle directories vengono mappati con i nomi dei namespaces, creando un collegamento biunivoco con questi ultimi.



## I nomi dei files **DEVONO** contenere solo caratteri alfanumerici, essere scritti in `CapitalizedWords` e terminare con l'estensione `.php`.
> I numeri sono consentiti nei nomi dei files, ma sono da evitarsi nella maggior parte dei casi.

> Queste raccomandazioni nascono dal fatto che i nomi dei files vengono mappati con i nomi delle interfacce, dei traits o delle classi, creando un collegamento biunivoco con questi ultimi.

## I files PHP **DEVONO** usare esclusivamente la codifica dei caratteri UTF-8 senza BOM (Byte Order Mark).

> La codifica può essere dichiarata usando `declare(encoding = 'utf-8');` nella parte superiore del file.

> A differenza di UTF-16 e UTF-32, non esiste un ordine di byte da indicare in un file con codifica UTF-8 e il BOM (Byte Order Mark) può avere un effetto collaterale negativo nell'invio dell'output, impedendo all'applicazione di impostare le proprie intestazioni.

## I files **DEVONO** usare un'indentazione di quattro spazi.
> Ciò aiuta ad evitare problemi con diff, patch, cronologia e annotazioni. L'uso degli spazi rende anche facile inserire una sub-indentazione a grana fine per l'allineamento tra le righe.

> Gli spazi non devono mai essere mescolati con la tabulazione. 


## Le righe dei file **DEVONO** avere una lunghezza massima di 72 caratteri e terminare con un singolo carattere di avanzamento riga Unix LF (linefeed).

> Un limite di 72 caratteri rende necessario distribuire la logica o le espressioni complesse in funzioni, nonché assegnare nomi più brevi e più espressivi a funzioni ed oggetti.

> Limitando la larghezza delle righe a 72 caratteri si migliora la leggibilità del codice, evitando peraltro interruzioni di riga involontarie quando si passa un file tra i programmatori.

> Limitando la larghezza della finestra dell'editor a 72 caratteri, è possibile avere diversi file aperti fianco a fianco e funziona bene quando si utilizzano gli strumenti di revisione del codice che presentano le due versioni nelle colonne adiacenti.

> Il wrapping predefinito nella maggior parte degli strumenti interrompe la struttura visiva del codice, rendendolo più difficile da capire. Il limite è stato scelto per evitare il wrapping degli editor con la larghezza della finestra impostata su 80 caratteri, anche se lo strumento posiziona un glifo marcatore nella colonna finale quando effettua il wrapping delle linee. Alcuni strumenti basati sul Web potrebbero non offrire affatto il ritorno a capo automatico della linea.

> La terminazione della riga segue la convenzione del file di testo Unix. I caratteri di avanzamento riga sono rappresentati come numero ordinale 10 oppure come numero esadecimale 0x0A.
> Questo è più un problema per gli sviluppatori che lavorano in un ambiente Windows, ma in ogni caso assicurarsi che l'editor di testo sia configurato per salvare i file con interruzioni di riga Unix.














