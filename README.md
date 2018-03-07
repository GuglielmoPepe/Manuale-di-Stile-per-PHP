# Manuale di Stile per PHP
Guida alla redazione di programmi in PHP (in lavorazione).


## Arrays

* ### Usare la sintassi concisa per la dichiarazione di un array
```php

$arr = [];

```

* ### Il delimitatore di elemento `,` deve essere seguito da uno spazio.
```php

$arr = ['Mickey', 'Minnie', 1, 2, 3];

```

* ### Mai usare numeri negativi come indici.
L'uso di numeri negativi come indici può causare dei problemi con alcune funzioni della libreria standard di PHP.


* ### L'operatore di associazione di un valore ad una chiave `=>` deve essere preceduto e seguito da uno spazio.
```php

$arr = ['firstKey'  => 'firstValue', 'secondKey' => 'secondValue'];

```
Migliora la leggibilità del codice.
