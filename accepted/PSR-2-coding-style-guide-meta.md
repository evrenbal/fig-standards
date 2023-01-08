# PSR-2 Meta Dokümanı

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

## 1. Özet

Bu rehberin amacı farklı yazarların kodlarının taranması sırasında bilişsel
sürtünmeyi azaltmaktır. Bunu, PHP kodunun biçimlendirilmesine dair bir takım
paylaşılan kurallar ve beklentiler sıralayarak yapar.

Buradaki stil kuralları, çeşitli üye projeler arasındaki ortak yönlerden
türetilmiştir. Çeşitli yazarlar birden fazla projede işbirliği yaptığında, tüm
bu projeler arasında kullanılacak bir kılavuz setinin olması yardımcı olur. Bu
nedenle, bu kılavuzun yararı kuralların kendisinde değil, bu kuralların
paylaşılmasındadır.

## 2. Oylama

- **Kabul Oylaması:** [ML](https://groups.google.com/d/msg/php-fig/c-QVvnZdMQ0/TdDMdzKFpdIJ)

## 3. Yazım Hataları ve Düzeltmeler

### 3.1 - Çok satırlı argümanlar (09/08/2013)

Birden fazla satırdan oluşan argümanlar kullanmak ( örneğin diziler veya anonim
fonksiyonlar) argüman listesini bölmek anlamına gelmez, bu nedenle bölüm 4.6
otomatik olarak zorunlu hale gelir. Diziler ve anonim fonksiyonlar birden fazla
satıra bölünebilirler.

Aşağıdaki örnekler PSR-2 açısından mükkemmel doğrulukta değerlendirilir.

```php
<?php
somefunction($foo, $bar, [
  // ...
], $baz);

$app->get('/hello/{name}', function ($name) use ($app) {
    return 'Merhaba '.$app->escape($name);
});
```

### 3.2 - Birden Çok Aayüzü genişletme (10/17/2013)

Birden fazla arayüz genişletilirken `extends` listesi bölüm 4.1'de açıklanan 
`implements` listesi gibi değerlendirilir.

## 4. Kişiler

### 4.1 Editör

* Paul M. Jones

### 4.2 Türkçe'ye Çeviri

* [Evren Bal][@benevrenbal]

[@benevrenbal]: https://www.linkedin.com/in/evrenbal