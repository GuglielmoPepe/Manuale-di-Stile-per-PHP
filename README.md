# Manuale di Stile per PHP
Guida alla redazione di programmi in PHP.

* [Codifica dei caratteri](#codifica-dei-caratteri)
* [Indentazione](#indentazione)
* [Lunghezza massima delle righe](#lunghezza-massima-delle-righe) 
* [Fine riga](#fine-riga) 
* [Tags del codice PHP](#tags-del-codice-php)
* [Directories](#directories)
* [Files](#files)
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

## Codifica dei caratteri
I file **DEVONO** essere salvati con la codifica Unicode (UTF-8). Il BOM (Byte Order Mark) **NON DEVE** essere utilizzato. A differenza di UTF-16 e UTF-32, non esiste un ordine di byte da indicare in un file con codifica UTF-8 e il BOM (Byte Order Mark) può avere un effetto collaterale negativo nell'invio dell'output, impedendo all'applicazione di impostare le proprie intestazioni.

La codifica può essere dichiarata usando `declare(encoding = 'utf-8');` nella parte superiore del file.
