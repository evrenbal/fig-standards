# Temel Kodlama Standartı

Standartın bu bölümü, paylaşılan PHP kodları arasında yüksek teknik uyumluluk
sağlamak için gerekli standart kodlama öğeleri olarak düşünülmesi gerekenlerin
neler olduğunu kapsar.

## 0. Çeviri
### 0.1 Çeviri Hakkında
Resmi olmayan bu çeviri php-fig standartları için Türkçe kaynak oluşturmak adına
gönüllülük esaslı hazırlanmıştır. Çeviri kaynaklı hatalar olabileceği veya
çeviri yapıldıktan sonra orijinal dosyanın değiştirilmiş olabileceği dikkate
alınmalıdır. Orijinal dildeki dokümanlar için php-fig tarafından yönetilen
[orijinal depo][figstandards] incelenmelidir.

[figstandards]: https://github.com/php-fig/

### 0.1 Çeviri Notları
Aşağıda yer alan terimler metin içerisinde tercüme edilmeden orijinal halleri
ile bırakılmıştır. Bu terimlerin ne olduğu bilinmiyorsa ayrıca araştırılması
ÖNERİLİR.

- `Class` metin içerisinde sınıf olarak da kullanılmıştır.
- `Function` metin içerisinde fonksiyon olarak da kullanılmıştır.
- `Constant` metin içerisinde sabit olarak da kullanılmıştır.
- `camelCase` ilk kelimenin tüm harfleri küçük, varsa ikinci ve sonraki
kelimelerin yalnızca ilk harfleri büyük, sonraki harfleri küçük şekilde yazılan,
içerisinde boşluk ya da ayraç kullanılmayan kelimeler.
- `PascalCase` Tüm kelimelerin ilk harfleri büyük, sonraki harfleri küçük
şekilde yazılan, içerisinde boşluk ya da ayraç kullanılmayan kelimeler.
- `StudlyCaps` bazı harfleri belirli kurallar çerçevesinde büyük harf
kullanılarak yazılan, içerisinde boşluk ya da ayraç bulunmayan kelimeler.
- `snake_case`, `under_score` tüm harfleri küçük, ayraç olarak alt çizgi
kullanılan kelimeler. 
- `Namespace` benzer amaca hizmet eden özellikler, sınıflar ve fonksiyonların
bir çatı altında toplanarak bu çatıya verilen isimdir.
- `Vendor` sağlayıcı, üretici, kodu yazan kişi ya da organizasyonun benzersiz
adı

## 1. Genel Bakış

- Dosyalarda sadece `<?php` ve `<?=` etiketlerini kullanılması ZORUNLUDUR.

- Dosyalarda, PHP kodu için sadece BOM içermeyen UTF-8 karakter kodlaması
kullanılması ZORULUDUR.

- Dosyaların ya *sadece* sembolleri (sınıf, fonksiyon, sabit, vb.) tanımlaması
*ya da* sadece yan etki (e.g. çıktı üretmek, .ini ayarlarını değiştirmek, vb.)
oluşturması, her ikisini birlikte yapmaması ÖNERİLİR.

- Namespace ve sınıfların bir "otomatik yükleme" PSR'ına [[PSR-0], [PSR-4]]
uygun olmaları ZORUNLUDUR.

- Sınıf isimlerinin `StudlyCaps` şeklinde tanımlanması ZORUNLUDUR.

- Sınıf sabitlerinin tamamı büyük harf ve gerekirse alt çizgiyle ayrılarak
tanımlanması ZORUNLUDUR.

- Metot isimlerinin `camelCase` şeklinde tanımlanması ZORUNLUDUR.

## 2. Dosyalar

### 2.1. PHP Etiketleri

Php kodunda uzun `<?php ?>` etiketleri veya kısa-echo `<?= ?>` etiketlerinin
kullanılması, başka etiket varyasyonlarının kullanılmaması ZORUNLUDUR.

### 2.2. Karakter Kodlaması

PHP kodunın BOM içermeden UTF-8 kullanması ZORUNLUDUR.

### 2.3. Yan Etkiler

Bir dosyanın sadece yeni semboller (sınıflar, fonksiyonlar ve semboller)
tanımlaması, başka bir yan etkiye sebep olmaması, veya sadece yan etki
işlevine sahip olması, ikisini aynı anda yapmaması ÖNERİLİR.

"Yan Etkiler", sadece dosyanın dahil edilmesi ile, sınıf, fonksiyon, sabit vb.
tanımlaması yapmadan doğrudan mantıksal ifadelerin çalıştırılmasını ifade eder.

"Yan etkiler" bunlarla sınırlı olmamak üzere şunları kapsar: çıktı oluşturma,
"require" veya "include"in kullanımı, harici hizmetlere bağlanma, ini ayarlarını
 değiştirme, hatalar veya istisnalar oluşturma, genel veya statik değişkenleri
 değiştirme, bir dosyadan okuma veya dosyaya yazma vb.

Aşağıdaki örnek, hem tanımlama hem yan etki içeren bir dosyadır; yani
kaçınılması gereken bir örnektir:

```php
<?php
// yan etki: ini ayarlarını değiştir
ini_set('error_reporting', E_ALL);

// yan etki: bir dosya yükle
include "file.php";

// yan etki: çıktı oluştur
echo "<html>\n";

// tanımlama
function foo()
{
    // fonksiyon içeriği
}
```

Aşağıdak dosya ise yan etki olmadan tanımlama yapılan, yani uygulanması
gereken iyi bir örnektir

```php
<?php
// tanımlama
function foo()
{
    // fonksiyon içeriği
}

// koşulsak tanımlamalar yan etki *değildir*
if (! function_exists('bar')) {
    function bar()
    {
        // fonksiyon içeriği
    }
}
```

## 3. Namespace ve Sınıf İsimleri

Namespace'ler ve sınıflar bir "otomatik yükleme" standartına, PSR: [[PSR-0],
[PSR-4]] uymalıdır.

Her sınıfın kendisine ait bir dosya içerisinde olması ve en azından birinci
seviye derinlikte bir namespace içerisinde: sağlayıcı adından oluşan üst seviye
namespace'de olması ZORUNLUDUR.

Sınıf isimlerinin `StudlyCaps` olarak tanımlanması ZORUNLUDUR.

PHP 5.3 ve sonrasında yazılan kodların resmi namespace tanımını kullanması
ZORUNLUDUR.

Örneğin

```php
<?php
// PHP 5.3 ve sonrası
namespace Vendor\Model;

class Foo
{
}
```

PHP 5.2.x ve öncesi için yazılan kodların takma-namespace  düzenini kullanarak
sınıf isimlerine `Vendor_` ön ekini eklemeleri ÖNERİLİR.

```php
<?php
// PHP 5.2.x ve öncesinde
class Vendor_Model_Foo
{
}
```

## 4. Sınıf Sabitleri, Özellikleri ve Metotları

"Sınıf" terimi, tüm sınıfları, arayüzleri ve özellikleri ifade eder.

### 4.1. Sabitler

Sınıf sabitleri tamamen büyük harf ve gerektiğinde alt çizgi ayracı kullanılarak
tanımlanır.

Örneğin;

```php
<?php
namespace Vendor\Model;

class Foo
{
    const VERSION = '1.0';
    const DATE_APPROVED = '2012-06-01';
}
```

### 4.2. Özellikler

Bu rehber özellik isimleri için `$StudlyCaps`, `$camelCase`, veya `$under_score`
seçeneklerinden birini tavsiye etmekten özellikle kaçınır.

Hangi isimlendirme seçeneği kullanılırsa kullanılsın aynı seçeneğin belirli
kapsam içerisindeki her yerde aynı şekilde kullanılması ÖNERİLİR.
Bu kapsamın üretici seviyesinde, paket seviyesinde, sınıf seviyesinde ve hatta
metot seviyesinde olması TERCİHE BAĞLIDIR.

### 4.3. Metotlar

Metot isimleri `camelCase()` olarak tanımlanmalıdır.