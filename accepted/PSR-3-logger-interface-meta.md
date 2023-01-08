# Loglayıcı Meta Dokümanı

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

## 1. Özet

Loglama arayüzü, bir uygulama ya da kütüphaneden gelen sistem mesajlarının
tutulması için ortak bir arayüz tanımlar.

PSR-3 standartı meta-dokümanları standart uygulama haline gelmeden önce
yayınlandığı için bu meta dokümanı sonradan yazılmıştır.

## 2. Tasarım Kararları

### Statik Log Mesajları

Bu şartnamenin amacı bir loglama metoduna iletilen mesajın her zaman statik bir
değer olmasıdr. Herhangi bir bağlama özgü değişkenlikler (örneğin kullanıcı adı,
zaman damgası veya diğer bilgiler ) sadece `$context` dizisi ile sağlanmalı ve
metinde bunlara atıfta bulunan yer tutucular bulunmalıdır.

Bu tasarımın amacı iki yönlüdür. Birincisi, mesaj daha sonra günlük mesajlarının
yerelleştirilmiş sürümlerini oluşturmak için çeviri sistemleri tarafından
kolayca kullanılabilir. İkincisi, bağlama özgü veriler, kullanıcı girişi
içerebilir ve bu nedenle temizlik yapılmasını gerektirir. Günlük iletisi daha
sonra HTML'de işlenmek üzere bir veritabanında saklanıyorsa, JSON'a seri hale
getirildiyse, bir syslog mesaj dizisine serileştirildiyse vb. temizlik buna göre
farklılaşacaktır. Kullanıcıya gösterilen "$context" verilerinin uygun şekilde
temizlenmesi loglama uygulamasının sorumluluğundadır.

## 3. İnsanlar

### 3.1 Düzenleyici(ler)

* Jordi Boggiano

### 3.2 Türkçe'ye Çeviri

* [Evren Bal][@benevrenbal]

[@benevrenbal]: https://www.linkedin.com/in/evrenbal
## 4. Oylama

[Kabul oyu](https://groups.google.com/g/php-fig/c/d0yPC7jWPAE/m/rhexAfz2T_8J)

## 5. Yazım Hataları

### 5.1 Tip Eklemeleri

"psr/log" paketinin 2.0 sürümü, skaler parametre tiplerini içerir. Paketin 3.0
sürümü dönüş türlerini içerir. Bu yapı, kademeli bir yükseltme işlemine izin
vermek için PHP 7.2 kovaryans desteğinden yararlanır, ancak tür uyumluluğu için
PHP 8.0 gerektirir.

Uygulayıcılar, aşağıdakilerin sağlanması koşuluyla, kendi takdirine bağlı olarak
kendi paketlerine dönüş tipleri EKLEYEBİLİR:

* dönüş türleri 3.0 paketindekilerle eşleşmelidir.
* uygulama, PHP 8.0.0 veya sonraki bir sürümü asgari sürüm olarak belirtmelidir.

Uygulayıcılar, yeni bir ana sürümde, dönüş tipleri ile birlikte veya ayrı bir
sürüm olarak parametre tiplerini de EKLEYEBİLİRLER. Bunun için aşağıdaki
şartların da sağlanması gerekir:

* parametre tipleri 2.0 paketindekilerle eşleşmelidir.
* uygulama, PHP 8.0.0 veya sonraki bir sürümü asgari sürüm olarak belirtmelidir.
* uygulama `"psr/log": "^2.0 || ^3.0"` sürümlerine bağlı olmalı, tip içermeyen
  1.0 sürümünü dışlamalıdır.

Uygulayıcılar, paketlerini mümkün olan en kısa sürede paketin 3.0 sürümüne
geçirmeleri için teşvik edilse de bunun yapılması gerekli değildir.