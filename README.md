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


## Note legali

["Manuale di Stile per PHP"](https://guglielmopepe.github.io/Manuale-di-Stile-per-PHP). Copyright &copy; 2018 [Guglielmo Pepe](https://guglielmopepe.github.io). Distribuito con licenza [Creative Commons Attribuzione - Condividi allo stesso modo 4.0 Internazionale](http://creativecommons.org/licenses/by-sa/4.0/legalcode).

Se riproduci, distribuisci o modifichi questo manuale devi fornire un'adeguata attribuzione in base alla licenza.

Se riproduci o distribuisci il manuale senza apportare sostanziali modifiche al suo contenuto, utilizza la seguente riga di attribuzione:

> ["Manuale di Stile per PHP"](https://guglielmopepe.github.io/Manuale-di-Stile-per-PHP). Copyright &copy; 2018 [Guglielmo Pepe](https://guglielmopepe.github.io). Distribuito con licenza [Creative Commons Attribuzione - Condividi allo stesso modo 4.0 Internazionale](http://creativecommons.org/licenses/by-sa/4.0/legalcode). Usato in conformità alla licenza.

Se modifichi il contenuto del manuale, ad esempio per conformarlo alle convenzioni di codifica del tuo team, utilizza questa riga di attribuzione:

> Adattato in conformità alla licenza a partire dal ["Manuale di Stile per PHP"](https://guglielmopepe.github.io/Manuale-di-Stile-per-PHP). Copyright &copy; 2018 [Guglielmo Pepe](https://guglielmopepe.github.io). Distribuito con licenza [Creative Commons Attribuzione - Condividi allo stesso modo 4.0 Internazionale](http://creativecommons.org/licenses/by-sa/4.0/legalcode).

In ogni caso devi includere un collegamento ipertestuale o altro riferimento, collegando "Manuale di Stile per PHP" all'url _https://guglielmopepe.github.io/Manuale-di-Stile-per-PHP_ e "Guglielmo Pepe" all'url _https://guglielmopepe.github.io_.


[vai all'indice ⬆](#indice)

