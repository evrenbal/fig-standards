# Loglayıcı Arayüzü

Bu doküman loglama kütüphaneleri için ortak bir arayüz tanımlar.

Ana hedef kütüphanelerin bir `Psr\Log\LoggerInterface` nesnesi kabul ederek
logları basit ve evrensel bir yöntemle ona yazmalarıdır. Frameworkler veya
içerik yönetim sistmeleri bu arayüzü kendi ihtiyaçlarına göre genişletebilirler
fakat bu dokümanla uyumlu kalmaları gerekir. Bu bir uygulamanın kullandığı
üçüncü parti kütüphanelerin merkezileştirilmiş uygulama kayıtlarına
yazabilmesini garanti eder.

Bu dokümandaki `uygulayıcı` loglamaya ilişkin bir kütüphane veya framework
içerisinde `LoggerInterface` uygulayan kişiyi tanımlar. Loglayıcının
kullanıcıları `kullanıcı` olarak tanımlanacaktır.

## 0. Çeviri

### 0.1 Çeviri Hakkında
Resmi olmayan bu çeviri php-fig standartları için Türkçe kaynak oluşturmak adına
gönüllülük esaslı hazırlanmıştır. Çeviri kaynaklı hatalar olabileceği veya
çeviri yapıldıktan sonra orijinal dosyanın değiştirilmiş olabileceği dikkate
alınmalıdır. Orijinal dildeki dokümanlar için php-fig tarafından yönetilen
[orijinal depo][figstandards] incelenmelidir.

[figstandards]: https://github.com/php-fig/

### 0.2 Terimler ve Tarifler
* Log İngilizce bir terimdir ve Türkçeye kayıt, günlük vb. tanımlarla
  çevrilmiştir. Bu terimi kod yazma seviyesinde kullanan teknik kişiler genelde
  orijinal `log` haliyle kullandığı için metin içerisinde tercüme edilmeyecektir.

## 1. Şartname

### 1.1 Temeller

- `LoggerInterface` sekiz farklı seviyedeki kayıtları [RFC 5424][] (debug, info,
  notice, warning, error, critical, alert, emergency) yazmak için sekiz farklı
  metot sağlar.

- Dokuzuncu metod olan `log`, ilk parametre olarak log seviyesini alır. Bu metod
  log seviyelerinden herhangi biri ile çağrıldığında o seviyeye özel metodu
  çağırmakla aynı sonuca ulaşılmalıdır. Metodu bu şartnamede belirtilmeyen bir
  seviye ile çağırmak bir `Psr\Log\InvalidArgumentException` istisnası
  fırlatmalıdır. Eğer uygulama bir seviye ile ilgili bilgi sahibi değilse
  kullanıcılar mevcut uygulamanın bunu desteklediğinden kesinlikle emin olmadan
  özel bir seviye kullanmamalıdır.

[rfc 5424]: http://tools.ietf.org/html/rfc5424

### 1.2 Mesaj

- Her metod string tipinde, veya `__toString()` metoduna sahip bir nesne kabul
  eder. Uygulayıcılar gönderilen nesne ile özel işlemler yapabilir, fakat eğer
  böyle bir ihtiyaç yoksa uygulayıcı nesneyi bir stringe dönüştürmelidir.

- Mesaj uygulayıcıların `context` dizisindeki değerlerle değiştirebileceği yer
  tutucular içerebilir.

  Yer tutucu isimleri `context` dizisindeki anahtarlarla uyumlu olmalıdır.

  Yer tutucu isimleri süslü parantez `{` ve ters süslü parantez `}` ile
  sınırlandırılır. Sınırlandırıcılar ve yer tutucu isimleri arasında boşluk
  olmamalıdır.

  Yer tutucu isimlerinin `A-Z`, `a-z`, `0-9`, alt çizgi `_`, ve noktadan `.`
  oluşması önerilir. Diğer karakterlerin kullanımı yer tutucu kuralları ile
  ilgili gelecekte yapılacak değişiklikler için saklı tutulmuştur.

  Uygulayıcılar yer tutucuları çeşitli temizlik stratejileri uygulamak ve loglar
  görüntülenirken tercüme edilmesi amacıyla kullanabilir. Kullanıcılar yer
  tutuculara ayrıca temizleme işlemi uygulamamalıdır çünkü hangi bağlamda
  gösterileceğini bilemezler.

  Aşağıda, yer tutucu enterpolasyonu için yalnızca referans amacıyla sağlanan
  örnek bir uygulama yer almaktadır:

  ```php
  <?php

  /**
   * Bağlam değerlerini mesaj yer tutucuları içine yerleştirir
   */
  function interpolate($message, array $context = array())
  {
      // bağlam anahtarlarının etrafına süslü parantezler koyarak bir değiştirme
      // dizisi oluştur
      $replace = array();
      foreach ($context as $key => $val) {
          // Değerin stringe dönüştürülebileceğini doğrula
          if (!is_array($val) && (!is_object($val) || method_exists($val, '__toString'))) {
              $replace['{' . $key . '}'] = $val;
          }
      }

      // Değiştirme değerlerini mesajın içerisine yerleştir ve geri döndür
      return strtr($message, $replace);
  }

  // süslü parantez ile sınırlandıırlmış yer tutucu isimleri içeren bir mesaj
  $message = "User {username} created";

  // yer tutucu isimleri => değiştirilecek değerler içeren bir bağlam dizisi
  $context = array('username' => 'bolivar');

  //  "User bolivar created" metnini ekrana yazar.
  echo interpolate($message, $context);
  ```

### 1.3 Bağlam

- Her metod bağlam verisi olarak bir dizi kabul eder. Bu, bir strgine tam olarak
  uymayan herhangi bir yabancı bilgiyi tutmak içindir. Dizi her şeyi içerebilir.
  Uygulayıcılar, bağlam verilerini mümkün olduğunca müsmahalı bir şekilde ele
  aldıklarından emin OLMALIDIR. Bağlamdaki belirli bir değer, bir istisna
  FIRLATMAMALI veya herhangi bir php hatası, uyarı veya not OLUŞTURMAMALIDIR.

- Bağlam dizisi içerisine bir `Exception` nesnesi gönderildiyse bu,
  `'exception'` anahtarı içinde OLMALIDIR. İstisna durumları loglamak yaygın bir
   modeldir ve log backendi desteklediğinde uygulayıcılara istisna durumundaki
   yığın ağacını görme imkanı sağlar. Uygulayıcılar `'exception'` anahtarının
   bir `Exception` olarak kullanmadan önce öyle olduğundan emin OLMALIDIR.

### 1.4 Yardımcı Sınıflar ve Arayüzler

- `Psr\Log\AbstractLogger` sınıfı `LoggerInterface`
  arayüzünü genişletip jenerik `log` metodunu dahil ederek (implement) kolayca
  uyarlamanıza olanak taır. Diğer sekiz metod mesajı ve bağlamı ona iletir.

- Benzer şekilde `Psr\Log\LoggerTrait` sadece jenerik `log` metodunu
  oluşturmanızı gerektirir. Trait'ler arayüzleri dahil edemeyecekleri
  (implement) için hala `LoggerInterface` ayrıca dahil edilmelidir.

- `Psr\Log\NullLogger` arayüz ile birlikte sağlanır. Kendilerine herhangi bir
  kaydedici verilmediği takdirde, arayüz kullanıcıları tarafından bir son çare
  "kara delik" uygulaması sağlamak için KULLANILABİLİR. Ancak, bağlam verisi
  oluşturma masraflı olması durumunda koşullu loglama daha iyi bir yaklaşım
  olabilir.

- `Psr\Log\LoggerAwareInterface` sadece
  `setLogger(LoggerInterface $logger)` metodu içerir ve frameworkler tarafından
  isteğe bağlı oluşturulan örnekleri bir loglayıcı ile otomatik bağlamak için
  kullanılır.

- `Psr\Log\LoggerAwareTrait` eşdeğer arayüzü bir sınıf içerisinde kolayca dahil
  etmek (implement) için kullanılır. Bu `$this->logger` şeklinde kullanıma erişim
  sağlar.

- `Psr\Log\LogLevel` sınıfı sekiz log seviyesi için sabitleri saklar.

## 2. Paket

Tanımlanan arabirimler ve sınıfların yanı sıra ilgili istisna sınıfları ve
uygulamanızı doğrulamak için bir test paketi [psr/log] paketinin bir parçası
olarak sağlanır.

[psr/log]: https://packagist.org/packages/psr/log

## 3. `Psr\Log\LoggerInterface`

```php
<?php

namespace Psr\Log;

/**
 * Bir logger örneğini tanımlar
 *
 * Mesaj bir string ya da __toString() uyarlaması olan bir nesne olmalıdır.
 *
 * Mesaj şu formata uygun yer tutucular içerebilir: {foo}
 * bağlam verisi içindeki "foo" anahtarlı veriyle değiştirilir.
 *
 * Bağlam dizisi rasgele veriler içerebilir, uygulayıcı tarafından yapılabilecek
 * tek varsayım eğer bir yığın ağacı oluşturmak için bir Exception örneği
 * verilecekse bu "exception" anahtarı ile verilmiş OLMALIDIR.
 *
 * Arayüz şartnamesinin tamamını görmek için See https://github.com/php-fig/fig-standards/blob/master/accepted/PSR-3-logger-interface.md inceleyiniz
 */
interface LoggerInterface
{
    /**
     * System kullanılamaz
     *
     * @param string $message
     * @param array $context
     * @return void
     */
    public function emergency($message, array $context = array());

    /**
     * Hemen eyleme geçilmelidir.
     *
     * Örneğin: Tüm web sitesi çöktü, veritabanı ulaşılamaz vb.
     * Bu SMS alarmını etkin hale getirip sizi uyandırmalı
     *
     * @param string $message
     * @param array $context
     * @return void
     */
    public function alert($message, array $context = array());

    /**
     * Kritik durumlar
     *
     * Örneğin: Uygulama bileşeni mevcut değil, beklenmeyen istisna
     *
     * @param string $message
     * @param array $context
     * @return void
     */
    public function critical($message, array $context = array());

    /**
     * Çalışma zamanı hataları genellikle anında eylem gerektirmez fakat genel
     * olarak loglanıp izlenmeleri gerekir.
     *
     * @param string $message
     * @param array $context
     * @return void
     */
    public function error($message, array $context = array());

    /**
     * Hata olmayan ististna durumlar
     *
     * Örneğin: Kullanım ömrü dolmuş bir API kullanılması, bir API'nin yanlış
     * kullanımı, yanlış olması gerekmeyen ama istenmeyen şeyler.
     *
     * @param string $message
     * @param array $context
     * @return void
     */
    public function warning($message, array $context = array());

    /**
     * Normal ama önemli olaylar
     *
     * @param string $message
     * @param array $context
     * @return void
     */
    public function notice($message, array $context = array());

    /**
     * İlgilenilen olaylar
     *
     * Örneğin: Kullanıcı giriş yaptı, SQL logları
     *
     * @param string $message
     * @param array $context
     * @return void
     */
    public function info($message, array $context = array());

    /**
     * Detaylı hata ayıklama kayıtları
     *
     * @param string $message
     * @param array $context
     * @return void
     */
    public function debug($message, array $context = array());

    /**
     * Herhangi bir seviyedeki loglar
     *
     * @param mixed $level
     * @param string $message
     * @param array $context
     * @return void
     */
    public function log($level, $message, array $context = array());
}
```

## 4. `Psr\Log\LoggerAwareInterface`

```php
<?php

namespace Psr\Log;

/**
 * Logger Aware örneğini tanımlar.
 */
interface LoggerAwareInterface
{
    /**
     * Nesne üzerinde bir logger örneği tanımlar
     *
     * @param LoggerInterface $logger
     * @return void
     */
    public function setLogger(LoggerInterface $logger);
}
```

## 5. `Psr\Log\LogLevel`

```php
<?php

namespace Psr\Log;

/**
 * Log seviyelerini tanımlar
 */
class LogLevel
{
    const EMERGENCY = 'emergency';
    const ALERT     = 'alert';
    const CRITICAL  = 'critical';
    const ERROR     = 'error';
    const WARNING   = 'warning';
    const NOTICE    = 'notice';
    const INFO      = 'info';
    const DEBUG     = 'debug';
}
```
