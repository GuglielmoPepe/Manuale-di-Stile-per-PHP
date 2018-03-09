# Manuale di Stile per PHP
Guida alla redazione di programmi in PHP (in lavorazione).

* [Directories](#directories)
* [Files](#files)

## Directories
#### I nomi delle directories **DEVONO** seguire le seguenti raccomandazioni:
* i nomi delle directories **DEVONO** contenere solo caratteri alfanumerici;
* i nomi delle directories **NON DEVONO** contenere spazi;
* i nomi delle directories **DEVONO** essere in formato `CapitalizedWords`;

> Queste raccomandazioni nascono dal fatto che i nomi delle directories vengono mappati con i nomi dei namespaces, creando un collegamento biunivoco con questi ultimi.

> I numeri sono consentiti nei nomi delle directories, ma sono da evitarsi nella maggior parte dei casi.

## Files
#### I nomi dei files **DEVONO** seguire le seguenti raccomandazioni:
* i nomi dei files **DEVONO** contenere solo caratteri alfanumerici;
* i nomi dei files **NON DEVONO** contenere spazi;
* i nomi dei files **DEVONO** essere in formato `CapitalizedWords`;
* nomi dei files **DEVONO** terminare con l'estensione `.php`;

> Queste raccomandazioni nascono dal fatto che i nomi dei files vengono mappati con i nomi delle interfacce, dei traits o delle classi, creando un collegamento biunivoco con questi ultimi.

> I numeri sono consentiti nei nomi dei files, ma sono da evitarsi nella maggior parte dei casi.

#### I files **DEVONO** essere memorizzati come testo ASCII.

#### I files PHP **DEVONO** usare esclusivamente la codifica dei caratteri UTF-8 senza BOM (Byte Order Mark).

> La codifica può essere dichiarata usando `declare(encoding = 'utf-8');` nella parte superiore del file.

> A differenza di UTF-16 e UTF-32, non esiste un ordine di byte da indicare in un file con codifica UTF-8 e il BOM (Byte Order Mark) può avere un effetto collaterale negativo nell'invio dell'output, impedendo all'applicazione di impostare le proprie intestazioni.

#### I files **DEVONO** usare un'indentazione di quattro spazi.
> Ciò aiuta ad evitare problemi con diff, patch, cronologia e annotazioni. L'uso degli spazi rende anche facile inserire una sub-indentazione a grana fine per l'allineamento tra le righe.
> Gli spazi non devono mai essere mescolati con la tabulazione. 

#### Le righe dei file **DEVONO** seguire le seguenti raccomandazioni:
  * la lunghezza massima di una riga **DEVE** essere di 72 caratteri;
  * righe più lunghe di 72 caratteri devono essere divise in più righe successive;
  * alla fine di una riga non vuota non devono esserci spazi bianchi;
  * le righe dei file PHP **DEVONO** terminare con un singolo carattere di avanzamento riga Unix LF (linefeed);
  
> Limitando la larghezza delle righe a 72 caratteri si migliora la leggibilità del codice.

> Un limite di 72 caratteri rende necessario distribuire la logica o le espressioni complesse in funzioni, nonché assegnare nomi più brevi e più espressivi a funzioni ed oggetti.

> Limitando la larghezza della finestra dell'editor a 72 caratteri, è possibile avere diversi file aperti fianco a fianco e funziona bene quando si utilizzano gli strumenti di revisione del codice che presentano le due versioni nelle colonne adiacenti.

> Il wrapping predefinito nella maggior parte degli strumenti interrompe la struttura visiva del codice, rendendolo più difficile da capire. Il limite è stato scelto per evitare il wrapping degli editor con la larghezza della finestra impostata su 80, anche se lo strumento posiziona un glifo marcatore nella colonna finale quando effettua il wrapping delle linee. Alcuni strumenti basati sul Web potrebbero non offrire affatto il ritorno a capo automatico della linea.

