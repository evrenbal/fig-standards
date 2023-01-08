# PHP Standard Recommendations

According to the [PSR Workflow Bylaw][workflow] each PSR has a status as it is being worked on. Once a proposal has passed the Entrance Vote it will be listed here as "Draft". Unless a PSR is marked as "Accepted" it is subject to change. Draft can change drastically, but Review will only have minor changes.

As also described in the [PSR Workflow Bylaw][workflow]. The Editor, or editors, of a proposal are the essentially the lead contributors and writers of the PSRs and they are supported by two voting members. Those voting members are the Coordinator who is responsible for managing the review stage and votes; and a second sponsor.

## Index by Status

### Accepted

| Num | Title                                | Maintainer                     |
|:---:|--------------------------------------|--------------------------------|
| 1   | [Basic Coding Standard][psr1]        | _vacant_                       |
| 3   | [Logger Interface][psr3]             | Jordi Boggiano                 |
| 4   | [Autoloading Standard][psr4]         | _vacant_                       |
| 6   | [Caching Interface][psr6]            | Larry Garfield                 |
| 7   | [HTTP Message Interface][psr7]       | Matthew Weier O'Phinney        |
| 11  | [Container Interface][psr11]         | Matthieu Napoli, David Négrier |
| 12  | [Extended Coding Style Guide][psr12] | Korvin Szanto                  |
| 13  | [Hypermedia Links][psr13]            | Larry Garfield                 |
| 14  | [Event Dispatcher][psr14]            | Larry Garfield                 |
| 15  | [HTTP Handlers][psr15]               | Woody Gilk                     |
| 16  | [Simple Cache][psr16]                | Paul Dragoonis                 |
| 17  | [HTTP Factories][psr17]              | Woody Gilk                     |
| 18  | [HTTP Client][psr18]                 | Tobias Nyholm                  |
| 20  | [Clock][psr20]                       | Chris Seufert                  |

### Draft

| Num | Title                                | Editor(s)                      | Sponsor                        |
|:---:|--------------------------------------|--------------------------------|--------------------------------|
| 5   | [PHPDoc Standard][psr5]              | Chuck Burgess                  | Michael Cullum                 |
| 19  | [PHPDoc tags][psr19]                 | Chuck Burgess                  | Michael Cullum                 |
| 21  | [Internationalization][psr21]        | Navarr Barnier                 | Larry Garfield                 |
| 22  | [Application Tracing][psr22]         | Adam Allport                   | Alessandro Chitolina           |

### Abandoned

| Num | Title                                | Editor(s)                      |
|:---:|--------------------------------------|--------------------------------|
| 8   | [Huggable Interface][psr8]           | Larry Garfield                 |
| 9   | [Security Advisories][psr9]          | Michael Hess                   |
| 10  | [Security Reporting Process][psr10]  | Michael Hess                   |

### Deprecated

| Num | Title                                |     |
|:---:|--------------------------------------|-----|
| 0   | [Autoloading Standard][psr0]         |     |
| 2   | [Coding Style Guide][psr2]           |     |

## Numerical Index

| Num | Title                                | Editor(s) / Maintainers        | Status     |
|:---:|--------------------------------------|--------------------------------|------------|
| 0   | [Autoloading Standard][psr0]         |                                | Deprecated |
| 1   | [Basic Coding Standard][psr1]        | _vacant_                       | Accepted   |
| 2   | [Coding Style Guide][psr2]           |                                | Deprecated |
| 3   | [Logger Interface][psr3]             | Jordi Boggiano                 | Accepted   |
| 4   | [Autoloading Standard][psr4]         | _vacant_                       | Accepted   |
| 5   | [PHPDoc Standard][psr5]              | Chuck Burgess                  | Draft      |
| 6   | [Caching Interface][psr6]            | Larry Garfield                 | Accepted   |
| 7   | [HTTP Message Interface][psr7]       | Matthew Weier O'Phinney        | Accepted   |
| 8   | [Huggable Interface][psr8]           | Larry Garfield                 | Abandoned  |
| 9   | [Security Advisories][psr9]          | Michael Hess                   | Abandoned  |
| 10  | [Security Reporting Process][psr10]  | Michael Hess                   | Abandoned  |
| 11  | [Container Interface][psr11]         | Matthieu Napoli, David Négrier | Accepted   |
| 12  | [Extended Coding Style Guide][psr12] | Korvin Szanto                  | Accepted   |
| 13  | [Hypermedia Links][psr13]            | Larry Garfield                 | Accepted   |
| 14  | [Event Dispatcher][psr14]            | Larry Garfield                 | Accepted   |
| 15  | [HTTP Handlers][psr15]               | Woody Gilk                     | Accepted   |
| 16  | [Simple Cache][psr16]                | Paul Dragoonis                 | Accepted   |
| 17  | [HTTP Factories][psr17]              | Woody Gilk                     | Accepted   |
| 18  | [HTTP Client][psr18]                 | Tobias Nyholm                  | Accepted   |
| 19  | [PHPDoc tags][psr19]                 | Chuck Burgess                  | Draft      |
| 20  | [Clock][psr20]                       | Chris Seufert                  | Accepted   |
| 21  | [Internationalization][psr21]        | Navarr Barnier                 | Draft      |
| 22  | [Application Tracing][psr22]         | Adam Allport                   | Draft      |

[workflow]: https://github.com/php-fig/fig-standards/blob/master/bylaws/002-psr-workflow.md
[psr0]: https://github.com/php-fig/fig-standards/blob/master/accepted/PSR-0.md
[psr1]: https://github.com/php-fig/fig-standards/blob/master/accepted/PSR-1-basic-coding-standard.md
[psr2]: https://github.com/php-fig/fig-standards/blob/master/accepted/PSR-2-coding-style-guide.md
[psr3]: https://github.com/php-fig/fig-standards/blob/master/accepted/PSR-3-logger-interface.md
[psr4]: https://github.com/php-fig/fig-standards/blob/master/accepted/PSR-4-autoloader-meta.md
[psr5]: https://github.com/php-fig/fig-standards/blob/master/proposed/phpdoc.md
[psr6]: https://github.com/php-fig/fig-standards/blob/master/accepted/PSR-6-cache.md
[psr7]: https://github.com/php-fig/fig-standards/blob/master/accepted/PSR-7-http-message.md
[psr8]: https://github.com/php-fig/fig-standards/blob/master/proposed/psr-8-hug/
[psr9]: https://github.com/php-fig/fig-standards/blob/master/proposed/security-disclosure-publication.md
[psr10]: https://github.com/php-fig/fig-standards/blob/master/proposed/security-reporting-process.md
[psr11]: https://github.com/php-fig/fig-standards/blob/master/accepted/PSR-11-container.md
[psr12]: https://github.com/php-fig/fig-standards/blob/master/accepted/PSR-12-extended-coding-style-guide.md
[psr13]: https://github.com/php-fig/fig-standards/blob/master/accepted/PSR-13-links.md
[psr14]: https://github.com/php-fig/fig-standards/blob/master/accepted/PSR-14-event-dispatcher.md
[psr15]: https://github.com/php-fig/fig-standards/blob/master/accepted/PSR-15-request-handlers.md
[psr16]: https://github.com/php-fig/fig-standards/blob/master/accepted/PSR-16-simple-cache.md
[psr17]: https://github.com/php-fig/fig-standards/blob/master/accepted/PSR-17-http-factory.md
[psr18]: https://github.com/php-fig/fig-standards/blob/master/accepted/PSR-18-http-client.md
[psr19]: https://github.com/php-fig/fig-standards/blob/master/proposed/phpdoc-tags.md
[psr20]: https://github.com/php-fig/fig-standards/blob/master/accepted/PSR-20-clock.md
[psr21]: https://github.com/php-fig/fig-standards/blob/master/proposed/internationalization.md
[psr22]: https://github.com/php-fig/fig-standards/blob/master/proposed/tracing.md
