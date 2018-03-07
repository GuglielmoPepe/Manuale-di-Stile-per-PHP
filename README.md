# Manuale di Stile per PHP
Guida alla redazione di programmi in PHP.

* [Formattazione dei file PHP](#formattazione-dei-file-php)
  * [Codifica dei caratteri](#codifica-dei-caratteri)
  * [Tags del codice PHP](#tags-del-codice-php)
  * [Indentazione](#indentazione)
  * [Lunghezza massima delle righe](#lunghezza-massima-delle-righe) 
  * [Fine riga](#fine-riga) 
* [Convenzione di denominazione](#convenzione-di-denominazione)
  * [Directories](#directories)
  * [Files](#files)
  * [Costanti](#costanti)
  * [Variabili](#variabili)
  * [Funzioni](#funzioni)
  * [Namespaces](#namespaces)
  * [Interfacce](#interfacce)
  * [Traits](#traits)
  * [Classi astratte](#classi-astratte)
  * [Classi](#classi)
  * [Costanti di classe](#costanti-di-classe)
  * [Proprietà](#proprietà)
  * [Metodi](#metodi)
* [Stili per la codifica](#stili-per-la-codifica)
  * [Stringhe](#stringhe)
  * [Arrays](#arrays)
  * [Strutture di controllo](#strutture-di-controllo)
  * [Funzioni](#funzioni)
  * [Interfacce](#interfacce)
  * [Traits](#traits)
  * [Classi astratte](#classi-astratte)
  * [Classi](#classi)
  * [Proprietà](#proprietà)
  * [Metodi](#metodi)

## Formattazione dei file PHP

### Codifica dei caratteri
```
> Il codice PHP **DEVE** usare esclusivamente la codifica dei caratteri UTF-8 senza BOM (Byte Order Mark).
```

### Indentazione

Il codice PHP **DEVE** usare solo rientri di quattro spazi.

Il codice PHP **NON DEVE** mai usare la tabulazione per i rientri.


### Lunghezza massima delle righe
La lunghezza massima di una riga **DEVONO** essere di 72 caratteri.

Righe più lunghe **DEVONO** essere divise in più righe successive di non più di 72 caratteri.

Alla fine di una riga non vuota non **DEVONO** esserci spazi bianchi. 


### Fine riga
Le righe dei file PHP **DEVONO** terminare con un singolo carattere di avanzamento riga Unix LF (linefeed).

### Tags del codice PHP
I files che contengono solo codice PHP **DEVONO** usare il tag esteso `<?php`.


Il tag di apertura `<?php` **DEVE** essere seguito da una singola riga vuota.

Il tag di chiusura `?>` **DEVE** essere omesso dai files che contengono solo codice PHP.

Il tag breve `<?=` **DEVE** essere utilizzato solo nei file template al posto di `<?php echo `.

Il tag breve `<?=` **DEVE** essere immediatamente seguito da un singolo spazio, dalla variabile o dal valore della funzione da stampare, da un singolo spazio ed infine dal tag di chiusura `?>`.

Tutti i files **DEVONO** terminare con una singola riga vuota.


## Convenzione di denominazione

### Directories
I nomi delle directories **DEVONO** contenere solo caratteri alfanumerici.

I nomi delle directories **NON DEVONO** contenere spazi.

I nomi delle directories **DEVONO** essere tutti in minuscolo.

I nomi delle directories **DEVONO** essere di una sola parola.


### Files
I nomi dei files **DEVONO** contenere solo caratteri alfanumerici.

I nomi dei files **NON DEVONO** contenere spazi.

I nomi dei files **DEVONO** essere tutti in minuscolo.

I nomi dei files **DEVONO** essere di una sola parola.

I nomi dei files **DEVONO** terminare con l'estensione `.php`.


### Costanti
I nomi delle costanti **DEVONO** contenere solo caratteri alfanumerici ed il carattere di sottolineatura (underscore).

Tutte le lettere utilizzate nel nome di una costante **DEVONO** essere in maiuscolo.

Tutte le parole nel nome di una costante **DEVONO** essere separate da caratteri di sottolineatura (underscore).


### Variabili
I nomi delle variabili **DEVONO** contenere solo caratteri alfanumerici.

I nomi delle variabili **DEVONO** iniziare con una lettera minuscola e **DEVONO** essere scritte in `mixedCase` in caso di più parole.


### Funzioni
I nomi delle funzioni **DEVONO** contenere solo caratteri alfanumerici.

I nomi delle funzioni **DEVONO** iniziare con una lettera minuscola e **DEVONO** essere scritte in `mixedCase` in caso di più parole.


### Namespaces
I nomi dei namespace **DEVONO** contenere solo caratteri alfanumerici.

I nomi dei namespace **DEVONO** iniziare con una lettera maiuscola e **DEVONO** essere scritte in `CapitalizedWords` in caso di più parole.

I nomi dei namespace **DEVONO** essere mappati su directories e files.


### Interfacce
I nomi delle interfacce **DEVONO** contenere solo caratteri alfanumerici.

I nomi delle interfacce **DEVONO** iniziare con una lettera maiuscola e **DEVONO** essere scritte in `CapitalizedWords` in caso di più parole.


### Traits
I nomi dei traits **DEVONO** contenere solo caratteri alfanumerici.

I nomi dei traits **DEVONO** iniziare con una lettera maiuscola e **DEVONO** essere scritte in `CapitalizedWords` in caso di più parole.


### Classi astratte
I nomi delle classi astratte **DEVONO** contenere solo caratteri alfanumerici.

I nomi delle classi astratte **DEVONO** iniziare con una lettera maiuscola e **DEVONO** essere scritte in `CapitalizedWords` in caso di più parole.


### Classi
I nomi delle classi **DEVONO** contenere solo caratteri alfanumerici.

I nomi delle classi **DEVONO** iniziare con una lettera maiuscola e **DEVONO** essere scritte in `CapitalizedWords` in caso di più parole.


### Costanti di classe
I nomi delle costanti di classe **DEVONO** contenere solo caratteri alfanumerici ed il carattere di sottolineatura (underscore).

Tutte le lettere utilizzate nel nome di una costante di classe **DEVONO** essere in maiuscolo.

Tutte le parole nel nome di una costante di classe **DEVONO** essere separate da caratteri di sottolineatura (underscore).


### Proprietà
I nomi delle proprietà **DEVONO** contenere solo caratteri alfanumerici.

I nomi delle proprietà **DEVONO** iniziare con una lettera minuscola e **DEVONO** essere scritte in `mixedCase` in caso di più parole.


### Metodi
I nomi dei metodi **DEVONO** contenere solo caratteri alfanumerici.

I nomi dei metodi **DEVONO** iniziare con una lettera minuscola e **DEVONO** essere scritte in `mixedCase` in caso di più parole.


## Stili per la codifica

### Stringhe
Le stringhe letterali **DEVONO** essere delimitate dall'apostrofo.

Le stringhe che contengono apostrofi **DEVONO** essere delimitate dalle virgolette.

Le stringhe **NON DEVONO** contenere variabili da sostituire.

L'operatore di concatenazione **DEVE** essere preceduto e seguito da un singolo spazio.

L'operatore di concatenazione **DEVE** essere allineato all'operatore di assegnazione `=` quando l'istruzione è suddivisa su più righe.

### Arrays
Gli arrays **DEVONO** essere dichiarati con la sintassi concisa.

Gli arrays **NON DEVONO** avere indici numerici negativi.

I delimitatori degli elementi di un array **DEVONO** essere seguiti da uno spazio.

Gli operatori di assegnazione di un valore a una chiave **DEVONO** essere preceduti e seguiti da uno spazio.

In un array suddiviso su più righe il primo elemento **DEVE** essere posizionato sulla riga successiva a quella di dichiarazione dell'array.

Ogni elemento di un array suddiviso su più righe **DEVE** essere su una propria riga.

In un array suddiviso su più righe gli elementi **DEVONO** avere un rientro maggiore rispetto alla riga di dichiarazione dell'array.

In un array suddiviso su più righe gli operatori di assegnazione di un valore a una chiave **DEVONO** essere allineati.

In un array suddiviso su più righe l'ultimo elemento **DEVE** essere sempre delimitato da una virgola.

In un array suddiviso su più righe la parentesi di chiusura **DEVE** essere su una propria riga allo stesso livello di indentazione della riga contenente la dichiarazione dell'array.

### Strutture di controllo
### Funzioni
### Interfacce
### Traits
### Classi astratte

### Classi
Le classi che estendono altre classi o che implementano interfacce **DEVONO** dichiarare le loro dipendenze sulla stessa linea  quando possibile.

La dichiarazione di classe **DEVE** essere suddivisa su più righe se supera la lunghezza massima per una riga (inserire link).

La dichiarazione di classe **DEVE** essere interrotta prima delle parole chiave `extends` e `implements` se supera la lunghezza massima per una riga(inserire link).

Le istruzioni `extends` e `implements` **DEVONO** essere dichiarate su una propria riga e con un livelo di rientro.

L'istruzione `implements` **DEVE** essere interrotta dopo ogni virgola che separa le interfacce se la dichiarazione di classe  supera la lunghezza massima della riga.

I nomi delle interfacce **DEVONO** essere allineate se la dichiarazione di classe  supera la lunghezza massima della riga.

La parentesi di apertura **DEVE** essere su una propria riga.

La parentesi di chiusura **DEVE** essere su una propria riga, successiva al corpo della classe.

### Proprietà
### Metodi
