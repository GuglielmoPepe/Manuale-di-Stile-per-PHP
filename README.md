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



## Formato dei files


## Codifica dei caratteri
> I file devono essere salvati con la codifica Unicode (UTF-8). Il BOM (Byte Order Mark) non deve essere utilizzato. 

A differenza di UTF-16 e UTF-32, non esiste un ordine di byte da indicare in un file con codifica UTF-8 e il BOM (Byte Order Mark) può avere un effetto collaterale negativo nell'invio dell'output, impedendo all'applicazione di impostare le proprie intestazioni.

La codifica può essere dichiarata usando `declare(encoding = 'utf-8');` nella parte superiore del file.


## Indentazione
> Per l'indentazione devono essere utilizzati esclusivamente gli spazi che non devono mai essere mescolati con la tabulazione. 

Ciò aiuta ad evitare problemi con diff, patch, cronologia e annotazioni. L'uso degli spazi rende anche facile inserire una sub-indentazione a grana fine per l'allineamento tra le righe.


## Lunghezza massima delle righe
 > La lunghezza massima di una riga deve essere di 72 caratteri e righe più lunghe devono essere divise in più righe successive di non più di 72 caratteri. Alla fine di una riga non vuota non devono esserci spazi bianchi. 

Limitando la larghezza delle righe a 72 caratteri si migliora la leggibilità del codice.

Un limite di 72 caratteri rende necessario distribuire la logica o le espressioni complesse in funzioni, nonché assegnare nomi più brevi e più espressivi a funzioni ed oggetti.

Limitando la larghezza della finestra dell'editor a 72 caratteri, è possibile avere diversi file aperti fianco a fianco e funziona bene quando si utilizzano gli strumenti di revisione del codice che presentano le due versioni nelle colonne adiacenti.

Il wrapping predefinito nella maggior parte degli strumenti interrompe la struttura visiva del codice, rendendolo più difficile da capire. Il limite è stato scelto per evitare il wrapping degli editor con la larghezza della finestra impostata su 80, anche se lo strumento posiziona un glifo marcatore nella colonna finale quando effettua il wrapping delle linee. Alcuni strumenti basati sul Web potrebbero non offrire affatto il ritorno a capo automatico della linea.


## Fine riga
Le righe dei file PHP devono terminare con un singolo carattere di avanzamento riga Unix LF (linefeed).

La terminazione della riga segue la convenzione del file di testo Unix. I caratteri di avanzamento riga sono rappresentati come numero ordinale 10 oppure come numero esadecimale 0x0A.

Questo è più un problema per gli sviluppatori che lavorano in un ambiente Windows, ma in ogni caso assicurarsi che l'editor di testo sia configurato per salvare i file con interruzioni di riga Unix.


## Tags del codice PHP



## Directories



## Files



## Istruzioni di inclusione



## Costanti



## Variabili



## Istruzioni di controllo



## Operatori logici



## Funzioni



## Namespaces



## Interfacce



## Traits



## Classi astratte



## Classi



## Costanti di classe



## Proprietà



## Metodi


