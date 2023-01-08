Otomatik yükleme standartı
==========================

> **Kullanımdan kalktı** - PSR-0 21.10.2014 tarihi itibarı ile kullanımdan
kaldırıldı. Artık alternatif olarak [PSR-4] önerilmektedir.

[PSR-4]: https://www.php-fig.org/psr/psr-4/

# Çeviri
## Çeviri Hakkında
Resmi olmayan bu çeviri php-fig standartları için Türkçe kaynak oluşturmak adına
gönüllülük esaslı hazırlanmıştır. Çeviri kaynaklı hatalar olabileceği veya
çeviri yapıldıktan sonra orijinal dosyanın değiştirilmiş olabileceği dikkate
alınmalıdır. Orijinal dildeki dokümanlar için php-fig tarafından yönetilen
[orijinal depo][figstandards] incelenmelidir.

[figstandards]: https://github.com/php-fig/

Aşağıda, otomatik yükleyici birlikte çalışabilirliği için uyulması gereken
zorunlu gereksinimler açıklanmaktadır.

Zorunlu
-------

* Şu yapıda tam teşekkülü bir alan adı (namespace) ve sınıf adı (class) `\<Tedarikçi Adı>\(<Namespace>\)*<Class Name>`
* Alan adları üst-seviye bir alan adına sahip olmalıdır. ("Tedarikçi Adı").
* Her alan adı istediği kadar alt alan adına sahip olabilir.
* Dosya sisteminden yüklenirken her alan adı ayracı bir `DIRECTORY_SEPARATOR`'e
  dönüştürülür.
* SINIF ADINDAKİ her `_` karakteri bir `DIRECTORY_SEPARATOR`'e dönüştürülür.
  `_` karakterinin alan adı içerisinde özel bir anlamı yoktur.
* Dosya sisteminden yüklenirken tam teşekküllü alan adı ve sınıf adına `.php`
  eklenir.
* Tedarikçi adı, alan adı ve sınıflardaki alfabetik karakterler büyük ve küçük
  harflerin herhangi bir kombinasyonundan oluşabilir.

Örnekler
--------

* `\Doctrine\Common\IsolatedClassLoader` => `/path/to/project/lib/vendor/Doctrine/Common/IsolatedClassLoader.php`
* `\Symfony\Core\Request` => `/path/to/project/lib/vendor/Symfony/Core/Request.php`
* `\Zend\Acl` => `/path/to/project/lib/vendor/Zend/Acl.php`
* `\Zend\Mail\Message` => `/path/to/project/lib/vendor/Zend/Mail/Message.php`

Underscores in Namespaces and Class Names
-----------------------------------------

* `\namespace\package\Class_Name` => `/path/to/project/lib/vendor/namespace/package/Class/Name.php`
* `\namespace\package_name\Class_Name` => `/path/to/project/lib/vendor/namespace/package_name/Class/Name.php`


Burada belirlediğimiz standartlar zahmetsiz bir otomatik yükleyici birlikte
çalışabilirliği için en düşük ortak payda olmalıdır. PHP 5.3 sınıflarını
yükleyebilen bu örnek SplClassLoader uygulamasını kullanarak bu standartlara
uyup uymadığınızı test edebilirsiniz.

Örnek Uygulama
--------------

Aşağıdaki örnek uygulama yukarıdaki standartların basitçe nasıl otomatik
yüklendiğini göstermektedir.

```php
<?php

function autoload($className)
{
    $className = ltrim($className, '\\');
    $fileName  = '';
    $namespace = '';
    if ($lastNsPos = strrpos($className, '\\')) {
        $namespace = substr($className, 0, $lastNsPos);
        $className = substr($className, $lastNsPos + 1);
        $fileName  = str_replace('\\', DIRECTORY_SEPARATOR, $namespace) . DIRECTORY_SEPARATOR;
    }
    $fileName .= str_replace('_', DIRECTORY_SEPARATOR, $className) . '.php';

    require $fileName;
}
spl_autoload_register('autoload');
```

SplClassLoader Uygulaması
-------------------------

Aşağıdaki gist yukarıda teklif edilen otomatik yükleyici birlikte çalışabilirlik
standartlarını uyguladığınızda sınıflarınızı yükleyebilecek olan örnek bir
SplClassLoader uygulamasıdır. Bu standartlara uyan PHP 5.3 sınıflarını yüklemek
için mevcut tavsiye edilen uygulamadır.

* [http://gist.github.com/221634](http://gist.github.com/221634)

