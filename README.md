# Manuale di Stile per PHP
Guida alla redazione di programmi in PHP (in lavorazione).

## indice

* [Raccomandazione generale](#raccomandazione-generale)
* [Directories](#directories)
* [Files](#files)
* PHP tags
* Istruzioni
* Commenti
* Tipi
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

















































