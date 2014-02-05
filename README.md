Money
=====

Fork from [Mathias Verraes implementation of Fowley's money pattern](https://github.com/mathiasverraes/money).

PHP 5.3+ library to make working with money safer, easier, and fun!

> "If I had a dime for every time I've seen someone use FLOAT to store currency, I'd have $999.997634" -- [Bill Karwin](https://twitter.com/billkarwin/status/347561901460447232)

In short: You shouldn't represent monetary values by a float. Wherever
you need to represent money, use this Money value object.

```php
<?php

use Money\Money;

$fiveEur = Money::EUR(500);
$tenEur = $fiveEur->add($fiveEur);

list($part1, $part2, $part3) = $tenEur->allocate(array(1, 1, 1));
assert($part1->equals(Money::EUR(334)));
assert($part2->equals(Money::EUR(333)));
assert($part3->equals(Money::EUR(333)));
```

The documentation is available at http://money.readthedocs.org


Installation
------------

Install the library using [composer][1]. Add the following to your `composer.json`:

```json
{
    "require": {
        "hemeragestao/money": "dev-master"
    },
    "minimum-stability": "dev"    
}
```

Now run the `install` command.

```sh
$ composer.phar install
```


Added Features
--------------
This fork replaces the maping of currencies from a simple ISO 4217 map from openexchangerates.org with the data contained in [Ruby's Money](https://github.com/RubyMoney) mapping. This allows for a few additional features, including generating formatted output string for the Money objects.

```php
<?php

use Money\Money;

echo Money::EUR(500)->formattedString();
```

Output:
```
€ 5.00
```


Integration
-----------

See [`MoneyBundle`][2] or [`TbbcMoneyBundle`][4] for [Symfony integration][3].

[1]: http://getcomposer.org/
[2]: https://github.com/pink-tie/MoneyBundle/
[3]: http://symfony.com/
[4]: https://github.com/TheBigBrainsCompany/TbbcMoneyBundle
