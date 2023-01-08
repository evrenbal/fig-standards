# Kodlama Stil Rehberi

> **Kullanımdan Kaldırıldı** - PSR-2 2019-08-10 itibarı ile kullanımdan
kaldırıldı olarak işaretlenmiştir. Artık alternatif olarak [PSR-12]
önerilmektedir.

[PSR-12]: https://github.com/evrenbal/fig-standards/blob/master/accepted/PSR-12.md

Bu spesifikasyon [PSR-1], temel kodlama standartını büyütür ve genişletir.

Bu rehberin amacı farklı yazarların kodlarının taranması sırasında bilişsel
sürtünmeyi azaltmaktır. Bunu, PHP kodunun biçimlendirilmesine dair bir takım
paylaşılan kurallar ve beklentiler sıralayarak yapar.

Buradaki stil kuralları, çeşitli üye projeler arasındaki ortak yönlerden
türetilmiştir. Çeşitli yazarlar birden fazla projede işbirliği yaptığında, tüm
bu projeler arasında kullanılacak bir kılavuz setinin olması yardımcı olur. Bu
nedenle, bu kılavuzun yararı kuralların kendisinde değil, bu kuralların
paylaşılmasındadır.

[PSR-0]: https://github.com/evrenbal/fig-standards/blob/master/accepted/PSR-0.md
[PSR-1]: https://github.com/evrenbal/fig-standards/blob/master/accepted/PSR-1-basic-coding-standard.md

## 0. Çeviri

### 0.1 Çeviri Hakkında
Resmi olmayan bu çeviri php-fig standartları için Türkçe kaynak oluşturmak adına
gönüllülük esaslı hazırlanmıştır. Çeviri kaynaklı hatalar olabileceği veya
çeviri yapıldıktan sonra orijinal dosyanın değiştirilmiş olabileceği dikkate
alınmalıdır. Orijinal dildeki dokümanlar için php-fig tarafından yönetilen
[orijinal depo][figstandards] incelenmelidir.

[figstandards]: https://github.com/php-fig/

### 0.1 Çeviri Notları
- `Specification` kelimesi günlük konuşma dilinde spesifikasyon olarak
  kullanıldığı için `şartname`, `tarif` vb. bir karşılık kullanılmamış,
  spesifikasyon olarak bırakıldığında daha doğru anlaşılacağı düşünülmüştür.
- Php anahtar kelimesi de olarak kullanılan, Türkçe'ye alan adı olarak
  çevrilebilecek `Namespace` terimi, metin içerisinde Türkçe'ye çevrilmeden asıl
  haliyle kullanılacaktır.
- Programlamadaki `Closure` ifadesinin Türkçe karşılığı anlaşılır olmayacağından
  çeviri yapılmamıştır.

## 1. Genel Bakış

- Kodun "kodlama standartı rehberi" PSR [[PSR-1]]'e uygun OLMASI ZORUNLUDUR.

- Kodda girinti için sekme karakteri değil, 4 boşluk KULLANMASI ZORUNLUDUR.

- Satır uzunluğuna ilişkin sabit bir sınır OLMAMASI ZORUNLUDUR. Esnek limitin
  120 karakter OLMASI ZORUNLUDUR; satır uzunluğunun 80 karakter veya altında
  OLMASI ÖNERİLİR.

- `namespace` tanımından ve `use` tanımları bloğundan sonra bir satır boşluk
  OLMASI ZORUNLUDUR.

- Sınıflar için açılış süslü parantezlerinin sonraki satırda, kapanış süslü
  parantezinin ise içerikten hemen sonraki satırda OLMASI ZORUNLUDUR.

- Metotlar için açılış süslü parantezlerinin sonraki satırda, kapanış süslü
  parantezlerinin içerikten sonraki satırda OLMALARI ZORUNLUDUR.

- Tüm özellik ve metotlar için görünürlük TANIMLANMASI ZORUNLUDUR. `abstract` ve
  `final` tanımlarının görünürlükten önce yapılması, `static` tanımının
  görünürlükten sonra YAPILMASI ZORUNLUDUR.

- Kontrol yapısı kelimelerinden sonra bir boşluk olması, metot ve fonksiyon
  çağrılarından sonra OLMAMASI ZORUNLUDUR.

- Kontrol yapılarının açılış süslü parantezlerinin aynı satırda OLMASI, kapanış
  süslü parantezinin içerikten sonraki satırda OLMASI ZORUNLUDUR.

- Kontrol ypaılarının açılış parantezlerinden sonra, kapanış parantezlerinden
  önce boşluk OLMAMASI ZORUNLUDUR.

### 1.1. Örnek

Aşağıdaki örnek, hızlı bir genel bakış amacıyla kurallardan bazılarını gösterir.

```php
<?php
namespace Vendor\Package;

use FooInterface;
use BarClass as Bar;
use OtherVendor\OtherPackage\BazClass;

class Foo extends Bar implements FooInterface
{
    public function sampleMethod($a, $b = null)
    {
        if ($a === $b) {
            bar();
        } elseif ($a > $b) {
            $foo->bar($arg1);
        } else {
            BazClass::bar($arg2, $arg3);
        }
    }

    final public static function bar()
    {
        // metot gövdesi
    }
}
```

## 2. Genel

### 2.1. Temel Kodlama Standartı

Kod [PSR-1]'de belirtilen tüm kurallara uymalıdır.

### 2.2. Dosyalar

Tüm PHP dpsyaları Unix LF (linefeed) satır sonlandırmasını KULLANMASI ZORUNLUDUR.

Tüm PHP dosyalarının boş bir satırla BİTMESİ ZORUNLUDUR.

Sadece PHP içeren dosyalarda `?>` kapanış etiketinin OLMAMASI ZORUNLUDUR.

### 2.3. Satırlar

Satır uzunluğu ile ilgili sabit bir sınır OLMAMASI ZORUNLUDUR.

Satır uzunluğu esnek limitinin 120 karakter OLMASI ZORUNLUDUR. Otomatik stil
kontrolcülerinin esnek limitte hata değil uyarı VERMELERİ ZORUNLUDUR.

Satırların 80 karakterden uzun OLMAMASI ÖNERİLİR; daha uzun satırların her biri
80 satırdan uzun olmayan satırlara BÖÜLNMESİ ÖNERİLİR.

Boş olmayan satırların sonunda takip eden boşluk karakteri OLMAMASI ZORUNLUDUR.

Okunabilirliği artırmak ve ilişkili kod bloklarını vurgulamak için boş satırlar
BIRAKILMASI MÜMKÜNDÜR.

Bir satıda birden fazla ifade OLMAMASI ZORUNLUDUR.

### 2.4. Girintileme

Kod girintileri için 4 boşluk KULLANILMASI ve sekme karakteri KULLANILMAMASI
ZORUNLUDUR.

> Önemli.: Sadece boşluk kullanmak ve boşlukları sekmelerle karıştırmamak
> diff'ler, yamalar, tarihçe ve açıklamalar ile ilgili sorunları azaltmaya
> yardımcı olur. Boşluk kullanılması satırlar arası girintileme için ince
> ayarlı alt girinti eklemeyi kolaylaştırır.

### 2.5. Anahtar Kelimeler ve True/False/Null

PHP [anahtar kelimeleri][keywords]nin küçük harf OLMASI ZORUNLUDUR.

`true`, `false`, ve `null` PHP sabitlerinin küçük harf OLMASI ZORUNLUDUR.

[keywords]: http://php.net/manual/en/reserved.keywords.php

## 3. Namespace ve Use Tanımları

Var olduğunda `namespace` tanımından sonra boş bir satır OLMASI ZORUNLUDUR.

Var olduklarında tüm `use` tanımlarının `namespace` tanımından sonra GELMELERİ
ZORUNLUDUR.

Her `use` kelimesinin sadece bir tanım için KULLANILMASI ZORUNLUDUR.

`use` bloğundan sonra boş bir satır OLMASI ZORUNLUDUR.

Örneğin:

```php
<?php
namespace Vendor\Package;

use FooClass;
use BarClass as Bar;
use OtherVendor\OtherPackage\BazClass;

// ... ek PHP kodu ...

```

## 4. Sınıflar, Özellikler ve Metodlar

"class" terimi tüm sınıflar, arayüzler ve trait'leri kapsar.

### 4.1. Extends ve Implements

`extends` ve `implements` anahtar kelimelerinin sınıf adı ile satırda OLMASI
ZORUNLUDUR.

Sınıfın açılış süslü parantezinin kendine ait satırda OLMASI ZORUNLUDUR; kapanış
süslü parantezinin içerikten hemen sonraki satırda OLMASI ZORUNLUDUR.

```php
<?php
namespace Vendor\Package;

use FooClass;
use BarClass as Bar;
use OtherVendor\OtherPackage\BazClass;

class ClassName extends ParentClass implements \ArrayAccess, \Countable
{
    // constants, properties, methods
}
```

`implements` listelerini, her bir bir seviye girintilenmiş birden fazla satıra
BÖLMEK MÜMKÜNDÜR. Bunu yaparken listenin ilk öğesinin sonraki satırda başlaması,
ve her satırda sadece bir arayüz OLMASI ZORUNLUDUR.

```php
<?php
namespace Vendor\Package;

use FooClass;
use BarClass as Bar;
use OtherVendor\OtherPackage\BazClass;

class ClassName extends ParentClass implements
    \ArrayAccess,
    \Countable,
    \Serializable
{
    // constants, properties, methods
}
```

### 4.2. Özellikler

Tüm özellikler için görünürlük TANIMLANMASI ZORUNLUDUR.

Özellik tanımlamak için `var` anahtar kelimesinin KULLANILMAMASI ZORUNLUDUR.

Bir ifadede birden fazla özellik tanımlaması OLMAMASI ZORUNLUDUR.

Özellik isimleri öncesinde korumalı veya özel durumunu belirtmek için alt çizgi
KULLANILMAMASI ÖNERİLİR.

Bir özellik tanımlaması aşağıdaki gibi görünür.

```php
<?php
namespace Vendor\Package;

class ClassName
{
    public $foo = null;
}
```

### 4.3. Metotlar

Tüm metotlarda görünürlük TANIMLANMASI ZORUNLUDUR.

Metot isimleri öncesinde korumalı veya özel durumunu belirtmek için alt çizgi
KULLANILMAMASI ÖNERİLİR.

Metot isimleri tanımlanırken metot ismi sonrasında boşluk OLMAMASI ZORUNLUDUR.
Açılış süslü parantezinin kendi satırında OLMASI ZORUNLUDUR, kapanış süslü
parantezinin içerikten sonraki satıda OLMASI ZORULUDUR. Açılış parantezinden
sonra boşluk OLMAMASI ZORUNLUDUR, kapanış parantezinden önce boşluk OLMAMASI DA
ZORUNLUDUR.

Bir metot tanımı aşağıdaki gibi görünür. Parantezlerin, virgüllerin, boşlukların
ve süslü parantezlerin konumlandırmasına dikkat edin:

```php
<?php
namespace Vendor\Package;

class ClassName
{
    public function fooBarBaz($arg1, &$arg2, $arg3 = [])
    {
        // metot gövdesi
    }
}
```

### 4.4. Methot Argümanları

Argüman listesinde virgüllerden önce boşluk OLMAMASI ZORUNLUDUR, virgüllerden
sonra bir boşluk OLMASI ZORUNLUDUR.

Varsayılan değeri olan metot argümanlarının argüman listesinin en sonunda yer
ALMASI ZORUNLUDUR.

```php
<?php
namespace Vendor\Package;

class ClassName
{
    public function foo($arg1, &$arg2, $arg3 = [])
    {
        // methot gövdesi
    }
}
```

Argüman listesinin her biri bir defa girintilenmiş birden fazla satıra BÖLÜNMESİ
MÜMKÜNDÜR. Bu yapılırken argüman listesindeki ilk öğenin sonraki satırda OLMASI,
ve her satırda bir argüman OLMASI ZORUNLUDUR.

Argüman listesi birden fazla satıra bölündüğünde kapanış parantezi ve açılış
süslü parantezi aralarında bir boşluk olacak şekilde kendilerine ait bir satırda
OLMALARI ZORUNLUDUR.

```php
<?php
namespace Vendor\Package;

class ClassName
{
    public function aVeryLongMethodName(
        ClassTypeHint $arg1,
        &$arg2,
        array $arg3 = []
    ) {
        // metot gövdesi
    }
}
```

### 4.5. `abstract`, `final`, ve `static`

`abstract` ve `final` tanımlamaları bulunduğunda görünürlük tanımlarından önce
gelmeleri ZORUNLUDUR. 

`static` tanımı bulunduğunda görünürlük tanımından sonra gelmesi ZORUNLUDUR.

```php
<?php
namespace Vendor\Package;

abstract class ClassName
{
    protected static $foo;

    abstract protected function zim();

    final public static function bar()
    {
        // metot gövdesi
    }
}
```

### 4.6. Methot ve Fonksiyon Çağrıları

Metot veya fonksiyon çağrısı yapıldığında metot veya fonksiyon adı ile açılış
parantezi arasında boşluk OLMAMASI ZORUNLUDUR, açılış parantezinden sonra ve
kapanış parantezinden önce boşluk olmaması ZORUNLUDUR. Argüman listesinde
virgüllerden önce boşluk olmaması, virgüllerden sonra bir boşluk OLMASI
ZORUNLUDUR.

```php
<?php
bar();
$foo->bar($arg1);
Foo::bar($arg2, $arg3);
```

Argüman listesinin her biri bir defa girintilenmiş birden fazla satıra BÖLÜNMESİ
MÜMKÜNDÜR. Bunu yaparken listedeki ilk öğenin sonraki satıra gelmesi ve her
satırda yalnızca bir argüman OLMASI ZORUNLUDUR.

```php
<?php
$foo->bar(
    $longArgument,
    $longerArgument,
    $muchLongerArgument
);
```

## 5. Kontrol Yapıları

Kontrol yapıları için genel stil kuralları aşağıdaki gibidir:

- Kontrol yapısı kelimesinden sonra bir boşluk OLMASI ZORUNLUDUR.
- Açılış parantezinden sonra boşluk OLMAMASI ZORUNLUDUR.
- Kapanış parantezinden önce boşluk OLMAMASI ZORUNLUDUR.
- Kapanış parantezi ve açılış süslü parantezi arasında bir boşluk OLMASI
  ZORUNLUDUR.
- Yapı gövdesinin bir defa GİRİNTİLENMESİ ZORUNLUDUR.
- Kapanış süslü parantezinin içerikten sonraki satırda OLMASI ZORUNLUDUR.

Her yapının gövdesi süslü parantezler içerisinde eolmalıdır. Bu yapıların
görünümünü standartlaştırır, ve içeriğe yeni satırlar eklendiğinde hata ile
karşılaşma olasılığını azaltır
### 5.1. `if`, `elseif`, `else`

Bir `if` yapısı aşağıdaki gibi görünür. Parantezlerin, boşlukların, süslü
parantezlerin yerleşimlerine, `else` ve `elseif` kelimelerinin önceki gövdesinin
kapanış süslü parantezi ile aynı satırda olmasına dikkat edin.

```php
<?php
if ($expr1) {
    // if gövdesi
} elseif ($expr2) {
    // elseif gövdesi
} else {
    // else gövdesi;
}
```

`else if` yerine `elseif` kelimesinin KULLANILMASI ÖNERİLİR, böylece tüm anahtar
kelimeler tek kelime gibi görüncektir.

### 5.2. `switch`, `case`

Bir `switch` yapısı aşağıdaki gibi görünür. Parantezlerin, boşlukların ve süslü
parantezlerin yerleşimlerine dikkat edin. `case` ifadesinin `switch`e göre bir
defa girintilenmesi, `break` anahtar kelimesinin (veya diğer sonlandırma
kelimesinin) `case` gövdesi ile aynı seviyede OLMASI ZORUNLUDUR. Boş olmayan bir
`case` ifadesi sonrasında bir sonraki ifadeye düşme bilinçli olarak yapıldıysa
`// no break` gibi bir yorum satırı OLMASI ZORUNLUDUR.

```php
<?php
switch ($expr) {
    case 0:
        echo 'break içeren ilk seçenek';
        break;
    case 1:
        echo 'sonrakine geçiş yapan ikinci seçenek';
        // no break
    case 2:
    case 3:
    case 4:
        echo 'break değil return içeren üçüncü seçenek';
        return;
    default:
        echo 'Varsayılan seçenek';
        break;
}
```

### 5.3. `while`, `do while`

Bir `while` ifadesi aşağıdaki gibi gözükür. Parantezlerin, boşlukların ve süslü
parantezlerin konumlarına dikkat edin.

```php
<?php
while ($expr) {
    // yapı gövdesi
}
```

Benzer şekilde bir `do while` ifadesi de aşağıdaki gibi görünür. Parantezlerin,
boşlukların ve süslü parantezlerin konumlarına dikkat edin.

```php
<?php
do {
    // yapı gövdesi
} while ($expr);
```

### 5.4. `for`

Bir `for` ifadesi aşağıdaki gibi görünür. Parantezlerin, boşlukların ve süslü
parantezlerin konumlarına dikkat edin.

```php
<?php
for ($i = 0; $i < 10; $i++) {
    // for gövdesi
}
```

### 5.5. `foreach`

Bir `foreach` ifadesi aşağıdaki gibi görünür. Parantezlerin, boşlukların ve
süslü parantezlerin konumlarına dikkat edin.

```php
<?php
foreach ($iterable as $key => $value) {
    // foreach gövdesi
}
```

### 5.6. `try`, `catch`

Bir `try catch` ifadesi aşağıdaki gibi görünür. Parantezlerin, boşlukların ve
süslü parantezlerin konumlarına dikkat edin.

```php
<?php
try {
    // try gövdesi
} catch (FirstExceptionType $e) {
    // catch gövdesi
} catch (OtherExceptionType $e) {
    // catch gövdesi
}
```

## 6. Closure'lar

Closure'ların `function` anahtar kelimesinden sonra bir boşluk, `use`
kelimesinden önce ve sonra bir boşluk bırakılarak TANIMLANMASI ZORUNLUDUR.

Açılış süslü parantezinin aynı satır, kapanış süslü parantezinin gövdeden sonraki
satırda OLMASI ZORUNLUDUR.

Argüman listesi veya değişken listesinin açılış paranezinden sonra ve kapanış
parantezinden önce boşluk OLMAMASI ZORUNLUDUR. 

Argüman listesi ve değişken listesinde virgüllerden önce boşluk OLMAMASI,
virgüllerden sonra boşluk OLMASI ZORUNLUDUR.

Varsayılan değeri olan Closure argümanlarının argüman listesinin en sonunda yer
ALMASI ZORUNLUDUR.

Bir closure tanımlaması aşağıdaki gibi görünür. Parantezlerin, boşlukların ve
süslü parantezlerin konumlarına dikkat edin.

```php
<?php
$closureWithArgs = function ($arg1, $arg2) {
    // body
};

$closureWithArgsAndVars = function ($arg1, $arg2) use ($var1, $var2) {
    // body
};
```

Argüman listesi ve değişken listesinin her biri birer girintili birden fazla
satıra BÖLÜNMESİ MÜMKÜNDÜR.Bu yapılırken listedeki ilk öğenin sonraki satırda
OLMASI ve her satırda bir argüman veya değişken OLMASI ZORUNLUDUR.

Bitiş listesi (ister argüman ister değişken olsun) birden çok satıra
bölündüğünde, kapanış parantezi ve açılış süslü parantezinin aralarında bir
boşluk olacak şekilde kendi satırlarına YERLEŞTİRİLMELERİ ZORUNLUDUR.

Aşağıdakiler argüman ve değişken listesi var ve var olmaksızın birden fazla
satıra bölünmesinin örnekleridir.

```php
<?php
$longArgs_noVars = function (
    $longArgument,
    $longerArgument,
    $muchLongerArgument
) {
    // gövde
};

$noArgs_longVars = function () use (
    $longVar1,
    $longerVar2,
    $muchLongerVar3
) {
    // gövde
};

$longArgs_longVars = function (
    $longArgument,
    $longerArgument,
    $muchLongerArgument
) use (
    $longVar1,
    $longerVar2,
    $muchLongerVar3
) {
    // gövde
};

$longArgs_shortVars = function (
    $longArgument,
    $longerArgument,
    $muchLongerArgument
) use ($var1) {
    // gövde
};

$shortArgs_longVars = function ($arg) use (
    $longVar1,
    $longerVar2,
    $muchLongerVar3
) {
    // gövde
};
```

Biçimlendirme kurallarının, closure doğrudan bir işlev veya yöntem çağrısında
değişken olarak doğrudan kullanıldığında da geçerli olduğunu unutmayın.

```php
<?php
$foo->bar(
    $arg1,
    function ($arg2) use ($var1) {
        // gövde
    },
    $arg3
);
```

## 7. Sonuç

Bu kılavuzda kasıtlı olarak atlanan birçok stil ve uygulama öğesi vardır.
Bunlar şunları içerir ancak bunlarla sınırlı değildir:

- Global değişkenler ve global sabitlerin tanımlanması

- Fonksiyonların tanımlanması

- Operatör ve atamalar

- Satır içi hizalama

- Yorumlar ve dokümantasyon blokları

- Sınıf ismi ön ekleri ve son ekleri

- En iyi uygulamalar

Gelecekteki tavsiyeler, bunlar veya diğer stil ve uygulama öğelerini ele almak
için bu kılavuzu gözden geçirmesi ve genişletmesi MÜMKÜNDÜR.

## Ek A. Anket

Grup, bu stil kılavuzunu yazarken ortak uygulamaları belirlemek için üye
projeler arasında bir anket yaptı. Anket, gelecek nesiller için burada
saklanmaktadır.

### A.1. Anketi Verisi

    url,http://www.horde.org/apps/horde/docs/CODING_STANDARDS,http://pear.php.net/manual/en/standards.php,http://solarphp.com/manual/appendix-standards.style,http://framework.zend.com/manual/en/coding-standard.html,https://symfony.com/doc/2.0/contributing/code/standards.html,http://www.ppi.io/docs/coding-standards.html,https://github.com/ezsystems/ezp-next/wiki/codingstandards,http://book.cakephp.org/2.0/en/contributing/cakephp-coding-conventions.html,https://github.com/UnionOfRAD/lithium/wiki/Spec%3A-Coding,http://drupal.org/coding-standards,http://code.google.com/p/sabredav/,http://area51.phpbb.com/docs/31x/coding-guidelines.html,https://docs.google.com/a/zikula.org/document/edit?authkey=CPCU0Us&hgd=1&id=1fcqb93Sn-hR9c0mkN6m_tyWnmEvoswKBtSc0tKkZmJA,http://www.chisimba.com,n/a,https://github.com/Respect/project-info/blob/master/coding-standards-sample.php,n/a,Object Calisthenics for PHP,http://doc.nette.org/en/coding-standard,http://flow3.typo3.org,https://github.com/propelorm/Propel2/wiki/Coding-Standards,http://developer.joomla.org/coding-standards.html
    voting,yes,yes,yes,yes,yes,yes,yes,yes,yes,yes,yes,yes,yes,yes,yes,no,no,no,?,yes,no,yes
    indent_type,4,4,4,4,4,tab,4,tab,tab,2,4,tab,4,4,4,4,4,4,tab,tab,4,tab
    line_length_limit_soft,75,75,75,75,no,85,120,120,80,80,80,no,100,80,80,?,?,120,80,120,no,150
    line_length_limit_hard,85,85,85,85,no,no,no,no,100,?,no,no,no,100,100,?,120,120,no,no,no,no
    class_names,studly,studly,studly,studly,studly,studly,studly,studly,studly,studly,studly,lower_under,studly,lower,studly,studly,studly,studly,?,studly,studly,studly
    class_brace_line,next,next,next,next,next,same,next,same,same,same,same,next,next,next,next,next,next,next,next,same,next,next
    constant_names,upper,upper,upper,upper,upper,upper,upper,upper,upper,upper,upper,upper,upper,upper,upper,upper,upper,upper,upper,upper,upper,upper
    true_false_null,lower,lower,lower,lower,lower,lower,lower,lower,lower,upper,lower,lower,lower,upper,lower,lower,lower,lower,lower,upper,lower,lower
    method_names,camel,camel,camel,camel,camel,camel,camel,camel,camel,camel,camel,lower_under,camel,camel,camel,camel,camel,camel,camel,camel,camel,camel
    method_brace_line,next,next,next,next,next,same,next,same,same,same,same,next,next,same,next,next,next,next,next,same,next,next
    control_brace_line,same,same,same,same,same,same,next,same,same,same,same,next,same,same,next,same,same,same,same,same,same,next
    control_space_after,yes,yes,yes,yes,yes,no,yes,yes,yes,yes,no,yes,yes,yes,yes,yes,yes,yes,yes,yes,yes,yes
    always_use_control_braces,yes,yes,yes,yes,yes,yes,no,yes,yes,yes,no,yes,yes,yes,yes,no,yes,yes,yes,yes,yes,yes
    else_elseif_line,same,same,same,same,same,same,next,same,same,next,same,next,same,next,next,same,same,same,same,same,same,next
    case_break_indent_from_switch,0/1,0/1,0/1,1/2,1/2,1/2,1/2,1/1,1/1,1/2,1/2,1/1,1/2,1/2,1/2,1/2,1/2,1/2,0/1,1/1,1/2,1/2
    function_space_after,no,no,no,no,no,no,no,no,no,no,no,no,no,no,no,no,no,no,no,no,no,no
    closing_php_tag_required,no,no,no,no,no,no,no,no,yes,no,no,no,no,yes,no,no,no,no,no,yes,no,no
    line_endings,LF,LF,LF,LF,LF,LF,LF,LF,?,LF,?,LF,LF,LF,LF,?,,LF,?,LF,LF,LF
    static_or_visibility_first,static,?,static,either,either,either,visibility,visibility,visibility,either,static,either,?,visibility,?,?,either,either,visibility,visibility,static,?
    control_space_parens,no,no,no,no,no,no,yes,no,no,no,no,no,no,yes,?,no,no,no,no,no,no,no
    blank_line_after_php,no,no,no,no,yes,no,no,no,no,yes,yes,no,no,yes,?,yes,yes,no,yes,no,yes,no
    class_method_control_brace,next/next/same,next/next/same,next/next/same,next/next/same,next/next/same,same/same/same,next/next/next,same/same/same,same/same/same,same/same/same,same/same/same,next/next/next,next/next/same,next/same/same,next/next/next,next/next/same,next/next/same,next/next/same,next/next/same,same/same/same,next/next/same,next/next/next

### A.2. Anket lejantı

Anket lejantı Türkçe'ye çevrilmemiş. Destekte bulunmak isterseniz çeviriye katkıda bulunabilirsiniz.

`indent_type`:
The type of indenting. `tab` = "Use a tab", `2` or `4` = "number of spaces"

`line_length_limit_soft`:
The "soft" line length limit, in characters. `?` = not discernible or no response, `no` means no limit.

`line_length_limit_hard`:
The "hard" line length limit, in characters. `?` = not discernible or no response, `no` means no limit.

`class_names`:
How classes are named. `lower` = lowercase only, `lower_under` = lowercase with underscore separators, `studly` = StudlyCase.

`class_brace_line`:
Does the opening brace for a class go on the `same` line as the class keyword, or on the `next` line after it?

`constant_names`:
How are class constants named? `upper` = Uppercase with underscore separators.

`true_false_null`:
Are the `true`, `false`, and `null` keywords spelled as all `lower` case, or all `upper` case?

`method_names`:
How are methods named? `camel` = `camelCase`, `lower_under` = lowercase with underscore separators.

`method_brace_line`:
Does the opening brace for a method go on the `same` line as the method name, or on the `next` line?

`control_brace_line`:
Does the opening brace for a control structure go on the `same` line, or on the `next` line?

`control_space_after`:
Is there a space after the control structure keyword?

`always_use_control_braces`:
Do control structures always use braces?

`else_elseif_line`:
When using `else` or `elseif`, does it go on the `same` line as the previous closing brace, or does it go on the `next` line?

`case_break_indent_from_switch`:
How many times are `case` and `break` indented from an opening `switch` statement?

`function_space_after`:
Do function calls have a space after the function name and before the opening parenthesis?

`closing_php_tag_required`:
In files containing only PHP, is the closing `?>` tag required?

`line_endings`:
What type of line ending is used?

`static_or_visibility_first`:
When declaring a method, does `static` come first, or does the visibility come first?

`control_space_parens`:
In a control structure expression, is there a space after the opening parenthesis and a space before the closing parenthesis? `yes` = `if ( $expr )`, `no` = `if ($expr)`.

`blank_line_after_php`:
Is there a blank line after the opening PHP tag?

`class_method_control_brace`:
A summary of what line the opening braces go on for classes, methods, and control structures.

### A.3. Anket Sonuçları

    indent_type:
        tab: 7
        2: 1
        4: 14
    line_length_limit_soft:
        ?: 2
        no: 3
        75: 4
        80: 6
        85: 1
        100: 1
        120: 4
        150: 1
    line_length_limit_hard:
        ?: 2
        no: 11
        85: 4
        100: 3
        120: 2
    class_names:
        ?: 1
        lower: 1
        lower_under: 1
        studly: 19
    class_brace_line:
        next: 16
        same: 6
    constant_names:
        upper: 22
    true_false_null:
        lower: 19
        upper: 3
    method_names:
        camel: 21
        lower_under: 1
    method_brace_line:
        next: 15
        same: 7
    control_brace_line:
        next: 4
        same: 18
    control_space_after:
        no: 2
        yes: 20
    always_use_control_braces:
        no: 3
        yes: 19
    else_elseif_line:
        next: 6
        same: 16
    case_break_indent_from_switch:
        0/1: 4
        1/1: 4
        1/2: 14
    function_space_after:
        no: 22
    closing_php_tag_required:
        no: 19
        yes: 3
    line_endings:
        ?: 5
        LF: 17
    static_or_visibility_first:
        ?: 5
        either: 7
        static: 4
        visibility: 6
    control_space_parens:
        ?: 1
        no: 19
        yes: 2
    blank_line_after_php:
        ?: 1
        no: 13
        yes: 8
    class_method_control_brace:
        next/next/next: 4
        next/next/same: 11
        next/same/same: 1
        same/same/same: 6
