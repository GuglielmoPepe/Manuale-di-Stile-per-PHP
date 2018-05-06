Le raccomandazioni raccolte in questo manuale aiutano i programmatori a scrivere codice PHP leggibile, aumentandone nel contempo manutenibilità e qualità generale. 

Le raccomandazioni presenti in questo manuale, rispetto alla maggior parte delle altre linee guida esistenti, sono annotate in modo da facilitarne l'uso. 

In generale, le raccomandazioni presenti in altre guide tendono a mescolare i problemi di stile con le questioni tecniche del linguaggio in un modo alquanto confuso. Il presente documento si concentra principalmente sullo stile di programmazione.

Sebbene un dato ambiente di sviluppo (IDE) può migliorare la leggibilità del codice tramite visibilità dell'accesso, codifica a colori, formattazione automatica e così via, il programmatore non dovrebbe mai fare affidamento su tali caratteristiche. Il codice sorgente dovrebbe essere scritto in modo da massimizzare la sua leggibilità indipendentemente da qualsiasi IDE.

Le raccomandazioni sono raggruppate per "elemento" e seguono questo schema:
> **Raccomandazione**
> ```php
> // example
> $example = 'example';
> ```
> 
> > Motivazione, riferimenti ed informazioni aggiuntive. 

La sezione "Motivazione, riferimenti ed informazioni aggiuntive" aiuta ad indicare il contesto per l'uso della raccomandazione evitando che si avviino "guerre di religione" come di solito accade in tema di standard e linee guida di codifica.

Si è scelto di usare solo raccomandazioni "obbligatorie" per ridurre al minimo il rischio di avere più stili di codifica per singoli elementi di codice.

Questo Manuale di Stile è pensato per essere utilizzato con la versione 7 e successive di PHP, ben potendo le raccomandazioni essere facilmente adattate per una versione precendente di PHP.

#### indice
* [Raccomandazione generale](#raccomandazione-generale)
* [Directories](#directories)
* [Files](#files)
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
* [Note legali](#note-legali)

## Raccomandazione generale

**Qualsiasi raccomandazione del manuale deve essere violata se migliora la leggibilità.**
> L'obiettivo principale delle raccomandazioni è migliorare la leggibilità e di conseguenza la comprensione, la manutenibilità e la qualità generale del codice. Poichè è impossibile coprire tutti i casi specifici, il programmatore deve essere flessibile.



[vai all'indice ⬆](#indice)



## Directories

**I nomi delle _directories_ devono contenere solo caratteri alfanumerici ed essere scritti in `CapitalizedWords`.**
> I numeri sono consentiti nei nomi delle _directories_, ma sono da evitarsi nella maggior parte dei casi.

> Questa raccomandazione nasce dal fatto che i nomi delle _directories_ vengono mappati con i nomi dei _namespaces_, creando un collegamento biunivoco con questi ultimi e rendendo predicibile la posizione di un _namespace_.



[vai all'indice ⬆](#indice)



## Files

**I nomi dei _files_ devono contenere solo caratteri alfanumerici, essere scritti in `CapitalizedWords` e terminare con l'estensione `.php`.**
> I numeri sono consentiti nei nomi dei _files_, ma sono da evitarsi nella maggior parte dei casi.

> Questa raccomandazionie nasce dal fatto che i nomi dei _files_ vengono mappati con i nomi delle interfacce, dei _traits_ o delle classi, creando un collegamento biunivoco con questi ultimi e rendendo predicibile la posizione delle interfacce, dei _traits_, delle classi, delle librerie o dei _files templates_.


**Nei _files_ deve essere utilizzata esclusivamente la codifica dei caratteri UTF-8 senza BOM (Byte Order Mark).**

> La codifica può essere dichiarata usando `declare(encoding = 'utf-8');` nella parte superiore del _file_.

> A differenza di UTF-16 e UTF-32, non esiste un ordine di byte da indicare in un _file_ con codifica UTF-8 e il BOM (Byte Order Mark) può avere un effetto collaterale negativo nell'invio dell'output, impedendo all'applicazione di impostare le proprie intestazioni.


**Le righe dei _files_ devono avere una lunghezza massima di 72 caratteri e terminare con un singolo carattere di avanzamento riga Unix LF (_linefeed_).**

> Un limite di 72 caratteri rende necessario distribuire la logica o le espressioni complesse in funzioni e/o metodi, nonché assegnare nomi più brevi e più espressivi a funzioni e classi.

> Limitando la larghezza delle righe a 72 caratteri si migliora la leggibilità del codice.

> Limitando la larghezza della finestra dell'editor a 72 caratteri, è possibile avere diversi _files_ aperti fianco a fianco e funziona bene quando si utilizzano gli strumenti di revisione del codice che presentano le due versioni nelle colonne adiacenti.

> Il _wrapping_ predefinito nella maggior parte degli strumenti interrompe la struttura visiva del codice, rendendolo più difficile da capire. Il limite è stato scelto per evitare il _wrapping_ degli editor con la larghezza della finestra impostata su 80 caratteri, anche se lo strumento posiziona un glifo marcatore nella colonna finale quando effettua il _wrapping_ delle linee. Alcuni strumenti basati sul Web potrebbero non offrire affatto il ritorno a capo automatico della linea.

> Non aggiungere spazi finali alla fine delle righe, ma terminare le righe secondo la convenzione dei file di testo Unix. I caratteri di avanzamento riga sono rappresentati come numero ordinale 10 oppure come numero esadecimale 0x0A.
> Questo è più un problema per gli sviluppatori che lavorano in ambiente Windows, ma in ogni caso assicurarsi che l'editor di testo sia configurato per salvare i _files_ con interruzioni di riga Unix.


> **Nota sulla terminologia:** il _line-wrapping_ avviene quando il codice che potrebbe occupare in altro modo regolarmente una singola riga è diviso in più righe.


**L'incompletezza di una riga, perchè divisa a causa della sua eccessiva lunghezza, deve essere resa evidente.**
```php
$sum = $a + $b + $c +
       $d + $e;


$obj->method($param1, $param2,
             $param3);


setText('Long line split' .
        'into two parts.');


for ($tableNo = 0; $tableNo < $nTables;
     $tableNo += $tableStep)
{
    // code
}
```
> Le righe vanno divise quando un'istruzione supera il limite di 72 caratteri indicato sopra. 

> È difficile dare regole rigide su come le righe dovrebbero essere divise, ma gli esempi sopra dovrebbero dare un suggerimento generale.

> In generale:
> * dividi la riga dopo una virgola;
> * dividi dopo un operatore;
> * allinea la nuova riga con l'inizio dell'espressione sulla riga precedente;


**I caratteri speciali come _TAB_ e interruzione di pagina devono essere evitati.**
> Questi caratteri sono destinati a causare problemi a editor, stampanti, emulatori di terminali o debugger quando vengono utilizzati in un ambiente multi-programmatore e/o multipiattaforma.


**I _files_ devono usare un'indentazione di quattro spazi.**
> Ciò aiuta ad evitare problemi con _diff_, _patch_, cronologia e annotazioni. L'uso degli spazi rende anche facile inserire una sub-indentazione a grana fine per l'allineamento tra le righe.

> Gli spazi non devono mai essere mescolati con la tabulazione. 

> L'indentazione è usata per enfatizzare la struttura logica del codice. L'indentazione di uno spazio è troppo piccola per raggiungere questo risultato. L'indentazione maggiore di quattro spazi rende il codice profondamente annidato e difficile da leggere, aumentando peraltro la possibilità che le righe debbano essere divise.


**Tutti i _files_ sorgente devono appartenere ad un `namespace` specifico.**
> L'assegnazione di ogni _file_ ad un `namespace` specifico piuttosto che al `namespace` globale, è una conseguenza dell'applicazione delle tecniche di programmazione orientate agli oggetti del linguaggio PHP.


**I _files_ sorgente devono essere aperti dal tag PHP esteso `<?php` seguito da una riga vuota.**
```
<?php
            // blank line
$a = 'foo'; // code php
$b = 'bar'; // code php
            // blank line
```
> Devono sempre essere usati esclusivamente i tag PHP estesi `<?php ?>` e mai quelli concisi `<? ?>`. Questo è il modo più portabile per includere codice PHP su diversi sistemi operativi e configurazioni.

> Nei _files_ che contengono esclusivamente codice PHP, il tag di apertura `<?php` deve essere seguito da una singola riga vuota al fine di migliorare la leggibilità del codice.


**Il _tag_ di chiusura deve essere omesso nei _files_ sorgente.**
> Nei _files_ che contengono esclusivamente codice PHP, il _tag_ di chiusura `?>` deve essere sostituito da una singola riga vuota.

> Il _tag_ di chiusura PHP `?>` in un documento PHP é facoltativo per il parser PHP. Tuttavia, se utilizzato, qualsiasi spazio vuoto successivo al tag di chiusura, introdotto dallo sviluppatore, dall'utente o da un'applicazione FTP, può causare _output_ indesiderati, errori PHP o, se questi ultimi vengono soppressi, pagine vuote. Per questo motivo, tutti i _files_ che contengono esclusivamente codice PHP devono omettere il _tag_ di chiusura `?>` e terminare con una singola riga vuota


**I _files_ sorgente che dichiarino interfacce, _traits_, classi o librerie di funzioni devono contenere solo le dichiarazioni di interfaccia, _trait_, classe o funzioni.**
> L'inserimento di codice aggiuntivo che provochi effetti collaterali deve essere evitato, per migliorare la leggibilità, la manutenibilità e la comprensione del codice.


**I _files template_ devono distinguere tra indentazione PHP e HTML.**
```php
<div>

    <?php foreach ($arr as $key => $value) : ?>

        <p><?php echo $value; ?></p>

    <?php endforeach;>

</div>
```
> Ciò rende molto più facile trovare tag di apertura e chiusura corrispondenti, definiti con diversi rientri.


**Nei _files template_ deve essere PHP in HTML piuttosto che HTML in PHP.**
```php
// bad
if ($isSubmitted)
{
    echo '<span class="isSubmitted">' . $isSubmitted . '</span>';
}

// good
<?php if ($isSubmitted) : ?>
  <span class="isSubmitted"><?php echo $isSubmitted; ?></span>
<?php endif; ?>
```
> Dopotutto, PHP è un linguaggio di scripting incorporato in HTML, e non il contrario.


**Nei _files template_ devono essere usati i _tags_ estesi `<?php ?>`.**
```php
<div>

    <?php foreach ($arr as $key => $value) : ?>

        <p><?php echo $value; ?></p>

    <?php endforeach;>

</div>
```
> L'uso del _tag echo_ esteso `<?php echo` era richiesto nel caso in cui un server non avesse avuto la direttiva INI `short_open_tag` abilitata. 
> Oggi questa esigenza risulta superata dopo che `PHP 5.4` ha reso sempre disponibile l'uso del _tag echo_ conciso `<?=` indipendentemente dalla direttiva INI `short_open_tag`. Tuttavia per ragioni di consistenza e leggibilità non deve mai essere usato il _tag echo_ conciso `<?=` preferendogli l'uso esclusivo del _tag_ esteso `<?php echo`.

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


## Note legali

["Manuale di Stile per PHP"](https://guglielmopepe.github.io/Manuale-di-Stile-per-PHP). Copyright &copy; 2018 [Guglielmo Pepe](https://guglielmopepe.github.io). Distribuito con licenza [Creative Commons Attribuzione - Condividi allo stesso modo 4.0 Internazionale](http://creativecommons.org/licenses/by-sa/4.0/legalcode).

Se riproduci, distribuisci o modifichi questo manuale devi fornire un'adeguata attribuzione in base alla licenza.

Se riproduci o distribuisci il manuale senza apportare sostanziali modifiche al suo contenuto, utilizza la seguente riga di attribuzione:

> ["Manuale di Stile per PHP"](https://guglielmopepe.github.io/Manuale-di-Stile-per-PHP). Copyright &copy; 2018 [Guglielmo Pepe](https://guglielmopepe.github.io). Distribuito con licenza [Creative Commons Attribuzione - Condividi allo stesso modo 4.0 Internazionale](http://creativecommons.org/licenses/by-sa/4.0/legalcode). Usato in conformità alla licenza.

Se modifichi il contenuto del manuale, ad esempio per conformarlo alle convenzioni di codifica del tuo team, utilizza questa riga di attribuzione:

> Adattato in conformità alla licenza a partire dal ["Manuale di Stile per PHP"](https://guglielmopepe.github.io/Manuale-di-Stile-per-PHP). Copyright &copy; 2018 [Guglielmo Pepe](https://guglielmopepe.github.io). Distribuito con licenza [Creative Commons Attribuzione - Condividi allo stesso modo 4.0 Internazionale](http://creativecommons.org/licenses/by-sa/4.0/legalcode).

In ogni caso devi includere un collegamento ipertestuale o altro riferimento, collegando "Manuale di Stile per PHP" all'url _https://guglielmopepe.github.io/Manuale-di-Stile-per-PHP_ e "Guglielmo Pepe" all'url _https://guglielmopepe.github.io_.


[vai all'indice ⬆](#indice)

