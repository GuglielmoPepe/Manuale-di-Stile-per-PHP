# Manuale di Stile per PHP
Guida alla redazione di programmi in PHP (in lavorazione).

* [Introduzione](#introduzione)
* [Tags del codice PHP](#tags-del-codice-php)
* [Separazioni delle istruzioni](#separazione-delle-istruzioni)
* [Stringhe](#stringhe)
* [Arrays](#arrays)
* [Variabili](#variabili)
* [Costanti](#costanti)
* [TRUE, FALSE e NULL](#true-false-e-null)
* [Operatori](#operatori)
* [Strutture di controllo](#strutture-di-controllo)
* [Funzioni](#funzioni)
* [Closures](#closures)
* [Namespaces](#namespaces)
* [Interfacce](#interfacce)
* [Traits](#traits)
* [Classi astratte](#classi-astratte)
* [Classi](#classi)
* [Costanti di classe](#costanti-di-classe)
* [Proprietà](#proprietà)
* [Metodi](#metodi)


## Introduzione
## Tags del codice PHP

```
<?php // blank space
            // blank line
$a = 'foo'; // code php
$b = 'bar'; // code php
            // blank line
```


## Separazioni delle istruzioni
## Stringhe
## Arrays
## Variabili
## Costanti
## TRUE, FALSE e NULL
## Operatori
## Strutture di controllo

Esempio per le istruzioni `if`, `elseif` e `else`:
```php

if ($a == 1) 
{
    echo 'one';
}
elseif ($a == 2) 
{
    echo 'two';
}
else
{
    echo 'zero';
}

```

Esempio per l'istruzione `for`:
```php

for ($i = 0; $i < 10; ++$i) 
{
    echo $i;
}

```

Esempio per l'istruzione `foreach`:
```php

foreach ($arr as $key => $value) 
{
    echo $key . ' => ' . $value;
}

```
Esempio per l'istruzione `while`:
```php
$i = 0;

while ($i < 10) 
{
    echo ++$i;
}

```

Esempio per l'istruzione `do-while`:
```php
$i = 0;

do
{
    echo ++$i;
}
while ($i < 10) 

```


## Funzioni
## Closures
## Namespaces
## Interfacce
## Traits
## Classi astratte
## Classi
## Costanti di classe
## Proprietà
## Metodi
