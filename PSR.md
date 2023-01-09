# Çeviri Hakkında

Resmi olmayan bu çeviri php-fig standartları için Türkçe kaynak oluşturmak adına
gönüllülük esaslı hazırlanmıştır. Çeviri kaynaklı hatalar olabileceği veya
çeviri yapıldıktan sonra orijinal dosyanın değiştirilmiş olabileceği dikkate
alınmalıdır. Orijinal dildeki dokümanlar için php-fig tarafından yönetilen
[orijinal depo][figstandards] incelenmelidir.

# PHP Standart Tavsiyeleri

[PSR İş Akışı Tüzüğü][workflow]ne göre her PSR üzerinde çalışılma aşamasına göre bir duruma sahiptir. Bir teklif giriş oylamasını geçtikten sonra [orijinal PSR depo][figstandards]sunda "Taslak" olarak görüntülenir. Bir PSR kabul edildi olarak işaretlenmedikçe değişebilir. Taslaklar büyük ölçüde değişbilir, inceleme durumundakiler de ufak değişiklikler olacaktır.

Ayrıca yine [PSR İş Akışı Tüzüğü][workflow]nde belirtildiği üzere, bir teklifin editörü veya editörleri, esas olarak PSR'lerin başlıca katkıda bulunanları ve yazarlarıdır ve oy kullanan iki üye tarafından desteklenirler. Oy kullanan üyelerden biri inceleme aşamasını ve oyları yönetmekten sorumlu olan Koordinatör, diğeri isi ikinci bir sponsordur.

## Çalışma Durumuna Göre Sıralanmış Dizin

### Kabul Edilenler

| No  | Başlık                               | Devam Ettirenler               |
|:---:|--------------------------------------|--------------------------------|
| 1   | [Temel Kodalama Standartı][psr1]     | _vacant_                       |
| 3   | [Loglayıcı Arayüzü][psr3]            | Jordi Boggiano                 |
| 4   | Autoloading Standard                 | _vacant_                       |
| 6   | Caching Interface                    | Larry Garfield                 |
| 7   | HTTP Message Interface               | Matthew Weier O'Phinney        |
| 11  | Container Interface                  | Matthieu Napoli, David Négrier |
| 12  | Extended Coding Style Guide          | Korvin Szanto                  |
| 13  | Hypermedia Links                     | Larry Garfield                 |
| 14  | Event Dispatcher                     | Larry Garfield                 |
| 15  | HTTP Handlers                        | Woody Gilk                     |
| 16  | Simple Cache                         | Paul Dragoonis                 |
| 17  | HTTP Factories                       | Woody Gilk                     |
| 18  | HTTP Client                          | Tobias Nyholm                  |
| 20  | Clock                                | Chris Seufert                  |

### Taslaklar

| No | Başlık                               | Editor(ler)                    | Sponsor                        |
|:---:|--------------------------------------|--------------------------------|--------------------------------|
| 5   | PHPDoc Standard                      | Chuck Burgess                  | Michael Cullum                 |
| 19  | PHPDoc tags                          | Chuck Burgess                  | Michael Cullum                 |
| 21  | Internationalization                 | Navarr Barnier                 | Larry Garfield                 |
| 22  | Application Tracing                  | Adam Allport                   | Alessandro Chitolina           |

### Kullanılmıyor

| No | Başlık                               | Editör(ler)                    |
|:---:|--------------------------------------|--------------------------------|
| 8   | Huggable Interface                   | Larry Garfield                 |
| 9   | Security Advisories                  | Michael Hess                   |
| 10  | Security Reporting Process           | Michael Hess                   |

### Kullanımdan Kalktı

| No | Başlık                               |     |
|:---:|-------------------------------------|-----|
| 0   | [Otomatik yükleme standartı][psr0]  |     |
| 2   | [Kodlama Stil Rehberi][psr2]        |     |

## Nümerik Dizin

| No | Başlık                               | Editör(ler) / Devam Ettirenler | Durum                |
|:---:|--------------------------------------|--------------------------------|----------------------|
| 0   | [Otomatik yükleme standartı][psr0]   |                                | Kullanımdan Kalktı   |
| 1   | [Temel Kodalama Standartı][psr1]     | _vacant_                       | Kabul Edildi         |
| 2   | [Kodlama Stil Rehberi][psr2]         |                                | Kullanımdan Kalktı   |
| 3   | [Loglayıcı Arayüzü][psr3]            | Jordi Boggiano                 | Kabul Edildi         |
| 4   | Autoloading Standard                 | _vacant_                       | Kabul Edildi         |
| 5   | PHPDoc Standard                      | Chuck Burgess                  | Taslak               |
| 6   | Caching Interface                    | Larry Garfield                 | Kabul Edildi         |
| 7   | HTTP Message Interface               | Matthew Weier O'Phinney        | Kabul Edildi         |
| 8   | Huggable Interface                   | Larry Garfield                 | Durduruldu           |
| 9   | Security Advisories                  | Michael Hess                   | Durduruldu           |
| 10  | Security Reporting Process           | Michael Hess                   | Durduruldu           |
| 11  | Container Interface                  | Matthieu Napoli, David Négrier | Kabul Edildi         |
| 12  | Extended Coding Style Guide          | Korvin Szanto                  | Kabul Edildi         |
| 13  | Hypermedia Links                     | Larry Garfield                 | Kabul Edildi         |
| 14  | Event Dispatcher                     | Larry Garfield                 | Kabul Edildi         |
| 15  | TTP Handlers                         | Woody Gilk                     | Kabul Edildi         |
| 16  | Simple Cache                         | Paul Dragoonis                 | Kabul Edildi         |
| 17  | HTTP Factories                       | Woody Gilk                     | Kabul Edildi         |
| 18  | HTTP Client                          | Tobias Nyholm                  | Kabul Edildi         |
| 19  | PHPDoc tags                          | Chuck Burgess                  | Taslak               |
| 20  | Clock                                | Chris Seufert                  | Kabul Edildi         |
| 21  | Internationalization                 | Navarr Barnier                 | Taslak               |
| 22  | Application Tracing                  | Adam Allport                   | Taslak               |

[workflow]: https://github.com/php-fig/fig-standards/blob/master/bylaws/002-psr-workflow.md
[figstandards]: https://github.com/php-fig/
[psr0]: https://github.com/evrenbal/fig-standards/blob/master/accepted/PSR-0.md
[psr1]: https://github.com/evrenbal/fig-standards/blob/master/accepted/PSR-1-basic-coding-standard.md
[psr2]: https://github.com/evrenbal/fig-standards/blob/master/accepted/PSR-2-coding-style-guide.md
[psr3]: https://github.com/evrenbal/fig-standards/blob/master/accepted/PSR-3-logger-interface.md
[psr4]: https://github.com/evrenbal/fig-standards/blob/master/accepted/PSR-4-autoloader-meta.md
[psr5]: https://github.com/evrenbal/fig-standards/blob/master/proposed/phpdoc.md
[psr6]: https://github.com/evrenbal/fig-standards/blob/master/accepted/PSR-6-cache.md
[psr7]: https://github.com/evrenbal/fig-standards/blob/master/accepted/PSR-7-http-message.md
[psr8]: https://github.com/evrenbal/fig-standards/blob/master/proposed/psr-8-hug/
[psr9]: https://github.com/evrenbal/fig-standards/blob/master/proposed/security-disclosure-publication.md
[psr10]: https://github.com/evrenbal/fig-standards/blob/master/proposed/security-reporting-process.md
[psr11]: https://github.com/evrenbal/fig-standards/blob/master/accepted/PSR-11-container.md
[psr12]: https://github.com/evrenbal/fig-standards/blob/master/accepted/PSR-12-extended-coding-style-guide.md
[psr13]: https://github.com/evrenbal/fig-standards/blob/master/accepted/PSR-13-links.md
[psr14]: https://github.com/evrenbal/fig-standards/blob/master/accepted/PSR-14-event-dispatcher.md
[psr15]: https://github.com/evrenbal/fig-standards/blob/master/accepted/PSR-15-request-handlers.md
[psr16]: https://github.com/evrenbal/fig-standards/blob/master/accepted/PSR-16-simple-cache.md
[psr17]: https://github.com/evrenbal/fig-standards/blob/master/accepted/PSR-17-http-factory.md
[psr18]: https://github.com/evrenbal/fig-standards/blob/master/accepted/PSR-18-http-client.md
[psr19]: https://github.com/evrenbal/fig-standards/blob/master/proposed/phpdoc-tags.md
[psr20]: https://github.com/evrenbal/fig-standards/blob/master/accepted/PSR-20-clock.md
[psr21]: https://github.com/evrenbal/fig-standards/blob/master/proposed/internationalization.md
[psr22]: https://github.com/evrenbal/fig-standards/blob/master/proposed/tracing.md
