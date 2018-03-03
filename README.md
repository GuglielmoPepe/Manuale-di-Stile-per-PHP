# Manuale di Stile per PHP
Guida alla redazione di programmi in PHP (in lavorazione).

   [Introduzione](#introduzione)
1. [Tags del codice PHP](#tags-del-codice-php)
1. [Separazioni delle istruzioni](#separazione-delle-istruzioni)
1. [Stringhe](#stringhe)
1. [Arrays](#arrays)
1. [TRUE, FALSE e NULL](#true-false-e-null)
1. [Variabili](#variabili)
1. [Costanti](#costanti)
1. [Operatori](#operatori)
1. [Strutture di controllo](#strutture-di-controllo)
1. [Funzioni](#funzioni)
1. [Closures](#closures)
1. [Namespaces](#namespaces)
1. [Interfacce](#interfacce)
1. [Traits](#traits)
1. [Classi astratte](#classi-astratte)
1. [Classi](#classi)
1. [Costanti di classe](#costanti-di-classe)
1. [Proprietà](#proprietà)
1. [Metodi](#metodi)

### Introduzione
PHP richiede che le istruzioni vengano terminate con un punto e virgola alla fine di ogni istruzione. Il tag di chiusura di un blocco di codice PHP implica automaticamente un punto e virgola.

Sebbene non sia necessario avere un punto e virgola per terminare l'ultima riga di un blocco PHP, le istruzioni devono terminare sempre con un punto e virgola per migliorare la leggibilità del codice oltre che per consistanza nella scrittura dello stesso.

1.  ## Usa solo i tags PHP standard completi, anche nei file che non contengono solo codice PHP.
    ```php
    <?php /1.php followed by space1./

    echo "Hello world";

    // ... more code

    echo "Last statement";

    // the script ends here with no PHP closing tag and blank line

    ```

    Il codice PHP deve essere sempre delimitato dai tag PHP standard completi anche nei file che non contengono solo codice PHP.

    L'uso del tag esteso `<?php echo` era richiesto nel caso in cui un server non avesse avuto `short_open_tag` abilitato. 
    Oggi questa esigenza risulta superata dopo che `PHP 5.4` ha reso sempre disponibile l'uso del tag conciso `<?=` indipendentemente dalla direttiva INI `short_open_tag`. Tuttavia per ragioni di consistenza non deve mai essere usato il tag breve `<?=` preferendogli l'uso esclusivo del tag esteso `<?php echo`.
