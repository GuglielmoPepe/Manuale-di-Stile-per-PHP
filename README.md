# Manuale di Stile per PHP
Guida alla redazione di programmi in PHP (in lavorazione).

* [Qualsiasi raccomandazione del manuale **DEVE** essere violata se migliora la leggibilità](#qualsiasi-raccomandazione-del-manuale-deve-essere-violata-se-migliora-la-leggibilità)
* [Tutti i nomi **DEVONO** essere scritti in inglese](#tutti-i-nomi-devono-essere-scritti-in-inglese)
* [I nomi dei namespaces **DEVONO** contenere solo caratteri alfanumerici ed essere scritti in `CapitalizedWords`](#i-nomi-dei-namespaces-devono-contenere-solo-caratteri-alfanumerici-ed-essere-scritti-in-capitalizedwords)
* [I nomi delle interfacce, dei traits e delle classi **DEVONO** contenere solo caratteri alfanumerici ed essere scritti in `CapitalizedWords`](#i-nomi-delle-interfacce-dei-traits-e-delle-classi-devono-contenere-solo-caratteri-alfanumerici-ed-essere-scritti-in-capitalizedwords)
* [I nomi delle variabili **DEVONO** contenere solo caratteri alfanumerici ed essere scritti in `mixedCase`](#i-nomi-delle-variabili-devono-contenere-solo-caratteri-alfanumerici-ed-essere-scritti-in-mixedcase)
* [Le variabili _generiche_ **DEVONO** avere lo stesso nome del loro tipo](#le-variabili-generiche-devono-avere-lo-stesso-nome-del-loro-tipo)
* [I nomi delle costanti **DEVONO** contenenre solo caratteri alfanumerici, essere tutte in maiuscolo con le parale separate da caratteri di sottolineatura](#i-nomi-delle-costanti-devono-contenenre-solo-caratteri-alfanumerici-essere-tutte-in-maiuscolo-con-le-parale-separate-da-caratteri-di-sottolineatura)
* [I nomi dei metodi di una classe **DEVONO** contenere solo caratteri alfanumerici, essere scritte in `mixedCase` in caso di più parole ed iniziare con un verbo](#i-nomi-dei-metodi-di-una-classe-devono-contenere-solo-caratteri-alfanumerici-essere-scritte-in-mixedcase-in-caso-di-più-parole-ed-iniziare-con-un-verbo)



## Qualsiasi raccomandazione del manuale **DEVE** essere violata se migliora la leggibilità.
> L'obiettivo principale delle raccomandazioni è migliorare la leggibilità e di conseguenza la comprensione, la manutenibilità e la qualità generale del codice. Poichè è impossibile coprire tutti i casi specifici, il programmatore dovrebbe essere flessibile.

##  Tutti i nomi **DEVONO** essere scritti in inglese.
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

## I nomi dei metodi di una classe **DEVONO** contenere solo caratteri alfanumerici, essere scritte in `mixedCase` in caso di più parole ed iniziare con un verbo.

```php
public function getFirstName()
{

}
```

> I numeri sono consentiti nei nomi dei metodi, ma sono da evitarsi nella maggior parte dei casi.

> La verbosità è generalmente incoraggiata. I nomi dei metodi dovrebbero essere prolissi quanto è pratico per descrivere pienamente il loro scopo e comportamento.

> Questa raccomandazione segue la prassi comune nella comunità di sviluppo PHP. Anche se la raccomandazione è in pratica identica a quella sui nomi delle variabili, i metodi in PHP sono già distinguibili dalle variabili per la loro forma specifica quando vengono invocati.
