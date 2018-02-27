# Manuale di Stile per PHP
Guida alla redazione di programmi in PHP.

* [Formattazione dei file PHP](#formattazione-dei-file-php)
  * [Codifica dei caratteri](#codifica-dei-caratteri)
  * [Tags del codice PHP](#tags-del-codice-php)
  * [Indentazione](#indentazione)
  * [Lunghezza massima delle righe](#lunghezza-massima-delle-righe) 
  * [Fine riga](#fine-riga) 
  
  
  
## Formattazione dei file PHP

### Codifica dei caratteri

Il codice PHP **DEVE** usare esclusivamente la codifica dei caratteri UTF-8 senza BOM (Byte Order Mark).


### Tags del codice PHP

I files che contengono solo codice PHP **DEVONO** usare il tag esteso `<?php`.

Il tag di apertura `<?php` **DEVE** essere seguito da una singola riga vuota.

Il tag di chiusura `?>` **DEVE** essere omesso dai files che contengono solo codice PHP.

Il tag breve `<?=` **DEVE** essere utilizzato solo nei file template al posto di `<?php echo `.

Il tag breve `<?=` **DEVE** essere immediatamente seguito da un singolo spazio, dalla variabile o dal valore della funzione da stampare, da un singolo spazio ed infine dal tag di chiusura `?>`.

Tutti i files **DEVONO** terminare con una singola riga vuota.


### Indentazione

Il codice PHP **DEVE** usare solo rientri di quattro spazi.

Il codice PHP **NON DEVE** mai usare la tabulazione per i rientri.


### Lunghezza massima delle righe
La lunghezza massima di una riga **DEVONO** essere di 72 caratteri.

Righe più lunghe **DEVONO** essere divise in più righe successive di non più di 72 caratteri.

Alla fine di una riga non vuota non **DEVONO** esserci spazi bianchi. 


### Fine riga
Le righe dei file PHP **DEVONO** terminare con un singolo carattere di avanzamento riga Unix LF (linefeed).
