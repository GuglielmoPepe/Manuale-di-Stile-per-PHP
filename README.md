# Manuale di Stile per PHP
Guida alla redazione di programmi in PHP (in lavorazione).

### Indice
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
### Use `const` for all of your references; avoid using `var`. eslint: [`prefer-const`](https://eslint.org/docs/rules/prefer-const.html), [`no-const-assign`](https://eslint.org/docs/rules/no-const-assign.html)

```javascript
// bad
var a = 1;
var b = 2;

// good
const a = 1;
const b = 2;
```
> Why? This ensures that you can’t reassign your references, which can lead to bugs and difficult to comprehend code.
> Why? This ensures that you can’t reassign your references, which can lead to bugs and difficult to comprehend code.
> Why? This ensures that you can’t reassign your references, which can lead to bugs and difficult to comprehend code.

### Use `const` for all of your references; avoid using `var`. eslint: [`prefer-const`](https://eslint.org/docs/rules/prefer-const.html), [`no-const-assign`](https://eslint.org/docs/rules/no-const-assign.html)

```javascript
// bad
var a = 1;
var b = 2;

// good
const a = 1;
const b = 2;
```
> Why? This ensures that you can’t reassign your references, which can lead to bugs and difficult to comprehend code.
> Why? This ensures that you can’t reassign your references, which can lead to bugs and difficult to comprehend code.
> Why? This ensures that you can’t reassign your references, which can lead to bugs and difficult to comprehend code.
> Why? This ensures that you can’t reassign your references, which can lead to bugs and difficult to comprehend code.
> Why? This ensures that you can’t reassign your references, which can lead to bugs and difficult to comprehend code.

[⬆ vai all'indice](#indice)

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

Esempio per l'istruzione `switch`:
```php
switch ($a)  
{
    case (1): 
        $a = 'foo'; // code php
        $b = 'bar'; // code php
        break;
    case (2): 
        $a = 'bar'; // code php
        $b = 'foo'; // code php
        break;
    default: 
        $a = 'no-foo'; // code php
        $b = 'no-bar'; // code php
        break;
}

```

Esempio per il costrutto `try`, `catch`:
```php
try
{
    $a = 'foo';
}
catch (\Exception $e)
{
    echo $e->getMessage();
}

```


## Funzioni
## Closures
## Namespaces
## Interfacce
Esempio per interfaccia:
```php

namespace 'Foo';

interface Bar
{
    public function execute() : type;
}

```


## Traits
## Classi astratte
Esempio per classe astratta:
```php

namespace 'Foo';

abstract class Baz implements Bar
{
    abstract public function run();

    public function execute() : type
    {
        $a = 'foo';     // code php
        $b = 'baz';     // code php
                        // blank line
        return $type;
    }
}
```


## Classi
## Costanti di classe
## Proprietà
## Metodi
