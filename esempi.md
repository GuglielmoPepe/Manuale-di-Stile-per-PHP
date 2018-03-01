Esempio per il tag di apertura in un file con solo codice php:
```
<?php       // blank space
            // blank line
$a = 'foo'; // code php
$b = 'bar'; // code php
            // blank line
```

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
    case (1) : 
        $a = 'foo'; // code php
        $b = 'bar'; // code php
                    // blank line
        break;
        
    case (2) : 
        $a = 'bar'; // code php
        $b = 'foo'; // code php
                    // blank line
        break;
        
    default : 
        $a = 'no-foo'; // code php
        $b = 'no-bar'; // code php
                       // blank line
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

Esempio per interfaccia:
```php

namespace 'Foo';

interface Bar
{
    public function execute() : type;
}

```

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
