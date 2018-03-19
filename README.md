# Manuale di Stile per PHP
Guida alla redazione di programmi in PHP (in lavorazione).

1. Qualsiasi raccomandazione del manuale **DEVE** essere violata se migliora la leggibilità.
1.  La lingua utilizzata per i nomi **DEVE** essere l'inglese.
1. Le abbreviazioni e gli acronimi **DEVONO** avere tutte lettere in minuscolo eccetto la prima se usati come nome. 
1. Le unità logiche all'interno di un blocco di codice **DEVONO** essere separate da una riga vuota.
1. Per l'indentazione **DEVE** essere utilizzato lo stile Allman.
1. Le parentesi **DEVONO** essere prive si spazi aggiuntivi al loro interno.
1. Le istruzioni **DEVONO** essere tutte su una propria riga.
1. L'error reporting **DEVE** essere impostato con la costante `E_ALL`.
1. Tutto il codice **DEVE** utilizzare le funzionalità avanzate di PHP 7 per la programmazione orientata agli oggetti.
1. Tra la parola chiave di una struttura di controllo e la parentesi aperta **DEVE** esserci uno spazio.


1. I nomi delle directories **DEVONO** contenere solo caratteri alfanumerici ed essere scritti in `CapitalizedWords`.


1. I nomi dei files **DEVONO** contenere solo caratteri alfanumerici, essere scritti in `CapitalizedWords` e terminare con l'estensione `.php`.
1. I files PHP **DEVONO** usare esclusivamente la codifica dei caratteri UTF-8 senza BOM (Byte Order Mark).
1. Le righe dei files **DEVONO** avere una lunghezza massima di 72 caratteri e terminare con un singolo carattere di avanzamento riga Unix LF (linefeed).
1. L'incompletezza di una riga, perchè divisa a causa della sua eccessiva lunghezza, **DEVE** essere resa evidente.
1. I caratteri speciali come TAB e interruzione di pagina devono essere evitati.
1. I files **DEVONO** usare un'indentazione di quattro spazi.
1. Tutti i files sorgente **DEVONO** appartenere a un `namespace` specifico.
1. Tutti i files sorgente files **DEVONO** terminare con una singola riga vuota.
1. I files sorgente che dichiarino interfacce, traits, classi o librerie di funzioni **DEVONO** contenere solo le dichiarazioni di interfaccia, trait, classe o funzione.
1. I files _template_ **DEVONO** distinguere tra indentazione PHP e HTML.
1. Nei files _template_ **DEVE** essere PHP in HTML piuttosto che HTML in PHP.


1. I files sorgente **DEVONO** essere aperti dal tag PHP esteso `<?php` seguito da una riga vuota.
1. Il tag di chiusura **DEVE** essere omesso nei files sorgente.
1. Nei files che mescolano PHP e HTML **DEVONO** essere usati i tag estesi `<?php ?>`.


1. Il codice ingannevole **DEVE** essere riscritto, non commentato.
1. Tutti i commenti **DEVONO** essere scritti in inglese.
1. L'identificatore di commenti `//` **DEVE** essere seguito da uno spazio.
1. I commenti **DEVONO** utilizzare l'identificatore `//`, inclusi i commenti su più righe.
1. I commentisu più righe **DEVONO** essere seguiti da una riga vuota quando sono molto grandi.
1. I commenti **DEVONO** essere indentati allo stesso livello del codice cui si riferiscono.


1. I numeri a virgola mobile **DEVONO** sempre essere scritti con il punto decimale ed almeno un decimale.
1. I numeri a virgola mobile **DEVONO** sempre essere scritti  con una cifra prima del punto decimale.

1. Le stringhe letterali **DEVONO** essere delimitate dalle virgolette singole.
1. Le stringhe che contengono virgolette singole **DEVONO** essere delimitate dalle virgolette doppie.
1. Le stringhe **DEVONO** essere scritte senza variabili da sostituire.
1. La riga **DEVE** essere divisa dopo l'operatore di concatenazione quando l'istruzione è supera il limite di 72 caratteri, allineando la nuova riga con l'inizio dell'espressione sulla riga precedente.

1. Gli arrays **DEVONO** essere dichiarati con la sintassi concisa.
1. Gli arrays **DEVONO** avere indici numerici positivi.
1. I delimitatori degli elementi `,` di un array **DEVONO** essere seguiti da uno spazio.
1. Gli operatori di assegnazione di un valore a una chiave `=>` **DEVONO** essere preceduti e seguiti da uno spazio.
1. Gli array suddivisi su più righe **DEVONO** seguire le seguenti raccomandazioni:
* il primo elemento **DEVE** essere posizionato sulla riga successiva a quella della dichiarazione dell'array;
* ogni elemento **DEVE** essere su una propria riga;
* gli elementi **DEVONO** avere un'indentazione maggiore rispetto alla riga di dichiarazione dell'array;
* gli operatori di assegnazione di un valore a una chiave `=>` **DEVONO** essere allineati;
* l'ultimo elemento **DEVE** essere sempre delimitato da una virgola;
* la parentesi di chiusura **DEVE** essere su una propria riga allo stesso livello di indentazione della riga contenente la dichiarazione dell'array;


1. I nomi delle variabili **DEVONO** contenere solo caratteri alfanumerici ed essere scritti in `mixedCase`.
1. Le variabili _generiche_ **DEVONO** avere lo stesso nome del loro tipo.
1. Le variabili **DEVONO** avere un significato univoco.
1. Le variabili **DEVONO** essere mantenute in vita per il minor tempo possibile.


1. I nomi delle costanti **DEVONO** contenere solo caratteri alfanumerici, essere tutte in maiuscolo con le parole separate da caratteri di sottolineatura.
1. I nomi delle costanti che rappresentano un concetto comune **DEVONO** avere un prefisso comune.
1. L'istruzione `const` **DEVE** essere preferita all'istruzione `define` nella dichiarazione di una costante.


1. Gli operatori binari **DEVONO** essere circondati da uno spazio.
1. Gli operatori unari **DEVONO** essere uniti alla variabile cui afferiscono, fatta eccezione per `!`.
1. Quando si confrontano una variabile con un'espressione si **DEVE** utilizzare una condizione _Yoda_.
1. L'operatore di concatenazione **DEVE** essere preceduto e seguito da un singolo spazio.
1. L'operatore ternario **DEVE** essere contenuto su una sola riga.
1. L'operator `@` **DEVE** essere evitato assolutamente.
1. Gli operatori di confronto rigorosi **DEVONO** essere preferiti a tutti gli altri.


1. L'uso di `break` nei cicli **DEVE** essere evitata.
1. L'istruzione `break` **DEVE** essere rientrata allo stesso livello del codice presente all'interno dell'istruzione `case` e deve essere preceduta e seguita da una riga vuota.

1. L'uso di `continue` nei cicli **DEVE** essere evitata.

1. Il costrutto `declare` **DEVE** essere la prima istruzione nel codice PHP.

1. L'uso della struttura di controllo `do-while` **DEVE** essere evitata.
1. Il blocco di codice di una struttura di controllo `do-while` **DEVE** seguire l'indentazione di Allman.

1. Solo le istruzioni di controllo del ciclo **DEVONO** essere incluse nell'istruzione `for()`.
1. Il blocco di codice di una struttura di controllo `for` **DEVE** seguire l'indentazione di Allman.
1. L'istruzione singola **DEVE* essere scritte con le parentesi.

1. Il blocco di codice di una struttura di controllo `foreach` **DEVE** seguire l'indentazione di Allman.

1. Le espressioni condizionali complesse **DEVONO** essere evitate. Introdurre variabili booleane temporanee invece.
1. L'istruzione condizionale **DEVE** essere su una riga separata.
1. Le dichiarazioni eseguibili **DEVONO** essere evitate nelle istruzioni condizionali.
1. Il blocco di codice di una struttura di controllo `if-else` **DEVE** seguire l'indentazione di Allman.
1. L'istruzione `elseif` **DEVE** essere sempre preferita a `else if`.
1. L'istruzione singola **DEVE* essere scritte con le parentesi.
1. Le parole chiave della struttura di controllo **DEVONO** essere seguite da uno spazio.
1. Il corpo di una struttura di controllo **DEVE** essere sempre racchiuso tra parentesi graffe. 
1. L'espressione condizionale di una struttura di controllo **DEVE** essere preceduta e seguita solo ed esclusivamente dalle parentesi tonde.
1. Nei files dove PHP è mescolato all'Html **DEVE** essere utilizzata la sintassi alternativa per la struttura di controllo `if-else`.

1. L'istruzione `return` **DEVE** essere separata dal resto del blocco codice da una riga vuota.
1. Quando una funzione o un metodo restituiscono valori nulli esplicitamente si **DEVE** utilizzare `return NULL;`.
1. Quando una funzione o un metodo restituiscono valori `void` si **DEVE** utilizzare `return;`.
1. Il valore restituito da `return` **DEVE** essere privo di parentesi. 

1. Il blocco di codice di una struttura di controllo `switch` **DEVE** seguire l'indentazione di Allman.
 
1. Il blocco di codice di una struttura di controllo `try-catch` **DEVE** seguire l'indentazione di Allman.

1. Le variabili di loop **DEVONO** essere inizializzate immediatamente prima del ciclo.
1. Il blocco di codice di una struttura di controllo `while` **DEVE** seguire l'indentazione di Allman.
1. L'istruzione singola **DEVE* essere scritte con le parentesi.

1. Per includere un file incondizionatamente **DEVE** essere utilizzata l'istruzione `require_once`.
1. Per includere un file condizionatamente **DEVE** essere utilizzata l'istruzione `include_once`.
1. Le istruzioni di inclusione **DEVONO** essere utilizzate senza parentesi.
1. Le classi **DEVONO** essere incluse attraverso la funzione `autoload` oppure una soluzione personalizzata.


1. I nomi delle funzioni **DEVONO** contenere solo caratteri alfanumerici, essere scritte in `mixedCase` in caso di più parole ed iniziare con un verbo.
1. Le funzioni **DEVONO** essere sempre dichiarate in un namespace.
1. Il corpo di una funzione **DEVE** seguire l'indentazione di Allman.
1. Le funzioni **DEVONO** essere chiamate senza spazio tra il nome della funzione e la parentesi iniziale. 
1. Il corpo di una closure **DEVE** seguire l'indentazione di Allman.
1. Gli argomenti con valori predefiniti **DEVONO** essere posti alla fine dell'elenco degli argomenti.
1. Il costrutto `use` di una closure **DEVE** essere preceduto e seguito da uno spazio.


1. I nomi dei namespaces **DEVONO** contenere solo caratteri alfanumerici ed essere scritti in `CapitalizedWords`.
1. La definizione del namespace **DEVE** essere la prima dichiarazione del file. 
1. L'importazione di altri `namespace` **DEVE** essere effettuata utilizzando l'istruzione `use`.

1. I nomi delle interfacce **DEVONO** contenere solo caratteri alfanumerici ed essere scritti in `CapitalizedWords`.
1. Le interfacce **DEVONO** essere dichiarati in singoli file con il nome del file corrispondente al nome della interfaccia con l'aggiunta dell'estensione `.php`.
1. Il corpo di una'interfaccia **DEVE** seguire l'indentazione di Allman.
1. La posizione di ciascun elemento all'interno dell'interfaccia **DEVE** essere prevedibile.

1. I nomi dei traits **DEVONO** contenere solo caratteri alfanumerici ed essere scritti in `CapitalizedWords`.
1. I traits **DEVONO** essere dichiarati in singoli file con il nome del file corrispondente al nome del trait con l'aggiunta dell'estensione `.php`.

1. I nomi delle classi **DEVONO** contenere solo caratteri alfanumerici ed essere scritti in `CapitalizedWords`.
1. Le classi **DEVONO** essere dichiarati in singoli file con il nome del file corrispondente al nome della classe con l'aggiunta dell'estensione `.php`.
1. Le classi **DEVONO** essere sempre dichiarate in un namespace.
1. Le classi **DEVONO** essere dichiarate ognuna in un proprio file sorgente.
1. Il corpo di una classe **DEVE** seguire l'indentazione di Allman.
1. La parentesi graffa di apertura per le classi **DEVE** andare sulla riga successiva alla dichiarazione di classe, e la parentesi graffa di chiusura **DEVE** andare sulla riga successiva dopo il corpo della classe.
1. La posizione di ciascun elemento all'interno della classe **DEVE** essere prevedibile.
1. I metodi **DEVONO** essere separati da tre righe vuote.
1. Le classi che estendono altre classi o che implementano interfacce **DEVONO** dichiarare le loro dipendenze sulla stessa riga quando possibile.
1. Le classi **DEVONO** essere istanziate utilizzando le parentesi indipendentemente dal numero di argomenti del costruttore.

1. I nomi delle costanti di classe **DEVONO** contenere solo caratteri alfanumerici, essere tutte in maiuscolo con le parole separate da caratteri di sottolineatura.

1. I nomi delle proprietà **DEVONO** contenere solo caratteri alfanumerici ed essere scritti in `mixedCase`.
1. Le proprietà di classe **DEVONO** essere dichiarate `private` o `protected`.
1. La dichiarazione delle proprietà **DEVE** seguire il seguente _pattern_: (`protected`|`private`)[`static`]_property name_.

1. I nomi dei metodi di una classe **DEVONO** contenere solo caratteri alfanumerici, essere scritte in `mixedCase` in caso di più parole ed iniziare con un verbo.
1. I nomi dei metodi di una classe **NON DEVONO** contenere il nome della propria classe.
1. Il nome del metodo **DEVE** essere immediatamente seguito dalla parentesi di apertura degli argomenti.
1. Il corpo di un metodo **DEVE** seguire l'indentazione di Allman.
1. La dichiarazione dei metodi **DEVE** seguire il seguente _pattern_: [`abstract`|`final`](`public`|`protected`|`private`)[`static`]_method name_.
1. Gli argomenti dei metodi **DEVONO** avere lo stesso nome del loro _tipo_.
1. L'elenco di argomenti di un metodo **DEVE** essere interrotta dopo una virgola, allineando gli argomenti, se la lunghezza massima della riga viene superata.






[vai all'indice ⬆](#indice)



## Directory

**I nomi delle directories devono contenere solo caratteri alfanumerici ed essere scritti in `CapitalizedWords`.**
> I numeri sono consentiti nei nomi delle directories, ma sono da evitarsi nella maggior parte dei casi.

> Queste raccomandazioni nascono dal fatto che i nomi delle directories vengono mappati con i nomi dei namespaces, creando un collegamento biunivoco con questi ultimi e rendendo predicibile la posizione di un namespace.





