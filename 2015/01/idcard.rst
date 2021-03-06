title: ЭЦП, смарткарты, алгоритмы
summary: Технические средства и решаемые иди задачи
pub_date: 2015-01-23
tags: [code, crypto, opressive goverenment]

Крипто и не крипто
==================

Используемые понятия:

* алгоритм - пошаговое решение математической задачи, которое может быть воплощено в программном модуле или аппаратном; примеры: RSA, AES, SHA-1, DH, ДСТУ-4145, ГОСТ-28147-89;
* секретный ключ - набор данных, известный только владельцу, использующийся в работе алгоритма;
* публичный ключ - набор данных, образованный от секретного ключа, распространяемый публично (на визитках, публичных сайтах, справочниках). Получить по публичному ключу приватный невозможно. Одному приватному ключу соответствует один публичный;
* подпись - набор данных, появляющийся в результате работы алгоритма и доказывающий, что модулю, реализующему алгоритм, был известен приватный ключ и документ;
* проверка подписи - работа алгоритма, использующая публичный ключ, документ и подпись, отвечающая на вопрос "действительно ли алгоритму, создающему подпись, был известен именно этот документ и приватный ключ, соответствующий данному публичному ключу". проверка подписи осуществляется для документа, для сертификата и для метки времени;
* центр сертификации — организация чей публичный ключ широко известен и есть доверие, что секретный ключ хорошо защищен, а подписываемые им сертификаты удостоверяют данные реальных субьектов. центр сертификации оказывает услуги по подписанию сертификатов;
* сертификат — подписанный центром сертификации документ, содержащий публичный ключ и заверяющий его связь его с неким субъектом (юрлицо, физлицо), либо объектом (штамп, сервер, кошелек);
* ЭЦП - набор из подписи, документа и сертификата субъекта, имеющий юридические последствия; так же используется для обозначения набора из секретного ключа и сертификата, связывающего публичный ключ с субъектом права;
* общий ключ - одинаковый набор данных, известный двум сторонам некого процесса. Может быть создан одной стороной и передан другой, либо рассчитан двумя сторонами автономно;
* смарткарта - аппаратный модуль, содержащий секретный, либо общий ключ и выполняющий алгоритм, использующий этот ключ. Выдает наружу только результат операции, но не ключ. доступ к запуску алгоритма, использующего ключ, может быть защищен пин-кодом;
* сим-карта - частный случай смарт-карты, использующий общий с оператором ключ для подтверждения владения телефонным номером;
* е-паспорт - частный случай смарт-карты, использующий секретный ключ и связанный с ним сертификат, чтобы подтвердить соответствие личности владельца, как субъекта указанного в сертификате, либо для создания подписи, либо для создания общего с любым другим субъектом ключа;
* формат - четко описанное представление данных (ключа, сертификата, документа), необходимое программе или аппаратному модулю для работы алгоритма и представления результата.

ЭЦП (ключ-сертификат-софт)
--------------------------

Применяется в некоторых процессах в Украине (интернет-банкинг, регистрация ФОП, сдача налоговой отчетности).

* С помощью ЭЦП можно в автоматическом режиме доказать неограниченному кругу лиц, что источником документа в неизменном виде был владелец секретного ключа или кто-либо, имеющий к нему доступ. при правильном поведении сотрудников АЦСК и получателя ключа - это тот же субъект, что записан в сертификате;
* С помощью ЭЦП получатель (не подписант) документа может доказать третьим лицам (например суду), что источником документа в неизменном виде был владелец ключа или кто-либо имеющий к нему доступ;
* С помощью ЭЦП и временной метки (требует наличия доверенного сервера) можно доказать то же и факт существования документа в определенный момент времени (создан не позднее);
* С помощью ЭЦП можно зашифровать файл таким образом, что расшифровать его сможет только владелец определенного приватного ключа (определенный субъект);
* С помощью ЭЦП можно доказать свою личность любому отдельному субъекту из широкого круга;


Данные задачи решаются в случае если все субъекты взаимодействия  имеют доступ к программным или аппаратным средствам, поддерживающим алгоритмы и форматы друг-друга и данный процесс признается государством, как участником данного процесса.

В данный момент в Украине сложилась ситуация, когда:

* широкий круг лиц не имеет доступа к таким программным средствам;
* широкодоступные средства, реализующие популярные алгоритмы не признаются;
* отсутствует какой-либо формат документов;
* сами документы существуют только внутри какой-либо системы; 
* производителями таких систем являются сертификационные центры; 
* не существует общедоступной системы для обмена, регистрации или легализации документов ни построенной на национальных, ни на мировых стандартах;

RSA vs ДСТУ4145
---------------

Вопрос противопоставления RSA и ДСТУ 4145 (и сопутствующих ГОСТов) в контексте аутентификации и идентификации задевает одно звено описанной выше проблемы - широкую доступность средств криптографии и возможность выхода большего количества производителей на рынок. Остальные аспекты данной проблемы должны быть решены независимо от используемого стандарта. В частности совместимость форматов может проверяться стендом, а создание (или лицензирование) общедоступной системы (или стандарта обмена для систем) будет требоваться в любом случае.

Проблемы широкой доступности средств криптографии (а скорее конечных продуктов) могут быть решены без смены стандарта (но с возможностью перейти на RSA или другой перспективный алгоритм впоследствии). Например возможно:

выкупить или создать криптобиблиотеку стандарта ДСТУ 4145, провести ее сертификацию и опубликовать для свободного использования;
лицензировать библиотеку и создать общедоступный сервисы аутентификации (далее портал) и сервис обмена документами, как объекты цифровой инфраструктуры для внутреннего использования в госорганах и как сервис для бизнеса;

Одним из действительных преимуществ RSA или ECDSA является его поддержка браузерами в виде сертификатов и виде Web Crypto API (http://www.w3.org/2012/webcrypto/webcrypto-next-workshop/papers/Using_the_W3C_WebCrypto_API_for_Document_Signing.html). При использовании RSA-сертификатов, аутентификацию (но не подписание документов) можно выносить на канальный уровень (SSL aka TLS aka HTTPS), где она тривиально настраивается в конфигурации веб-сервера, а подписание реализовывать средствами Web Crypto API браузера.

Ограничения и предположения
---------------------------

При использовании ЭЦП все субъекты полагаются на то (доверяют), что каждый АЦСК сертифицирует ключи только тем субъектам, личность которых записывает в сертификат, а владелец ключа не разглашает его или разглашает только лицам, которых уполномочивает выступать от своего имени (например бухгалтеру).

Выдача текстового пароля
------------------------

Выдача текстового пароля через ЦНАПы или другие органы власти может решить проблему идентификации субъекта онлайн без применения ЭЦП и необходимости использовать сертифицированные средства криптографической защиты.

Текстовые пароли используются для доступа к большинству ресурсов в интернете, включая интернет-банкинг для физлиц в Украине. В некоторых ситуациях используется два пароля (двухфакторная авторизация, например пароль+код из смс).

* пароль позволяет доказать сервису, выдавшему пароль, что субъект обращающийся к сервису в какой-то момент времени имел доступ к пин-конверту или знает текст пароля. при правильном поведении оператора и получателя конверта - это тот же субъект, что и получатель пин-конверта;
* при онлайн-доступе, такое доказательство может быть проверено порталом авторизации с выдачей токена подтверждения для широкого круга сервисов, доверяющих порталу в процедуре аутентификации;
* портал, проверяющий пароль, не может доказать личность пользователя третьим лицам иначе, чем административно;
* пароль не может использоваться для прямого доказательства своей личности широкому кругу субъектов;
* пароль не может использоваться для доказательства неизменности документа или времени его создания;

Процедура выдачи пароля может быть основана на пин-конвертах, используемых в банковской сфере. Оператор, проверяет личность человека, желающего получить конверт, записывает проверенную идентичность в систему аккаунтов вместе с номером пин-конверта, который портал может связать с самим паролем.

При использовании пароля все субъекты полагаются на то, что портал аутентификации корректно проверяет пароль, а операторы корректно проверяют личность при выдаче пин-конверта;

Аутентификация по смс (one time password) является разновидностью аутентификации по паролю, обладает теми же свойствами и может ее дополнять. Дополнительная гарантия - смс могут приходить только на один телефон и их нельзя заранее скопировать, как пароль. Для использования аутентификации по смс-паролю, оператор должен вместо (или вместе с) выдачей пин-конверта проверить и записать номер телефона идентифицируемого лица.

Портал может комбинировать разные способы аутентификации (пароль, otp, ЭЦП) не требуя внедрения ЭЦП на каждом использующем его сервисе. Это поможет плавно перейти от простого (выдача конвертов) к сложному (ЭЦП) и одновременно сэкономить на лицензиях, не лицензируя криптобиблиотеку для каждого отдельного ресурса. При этом портал будет использовать ЭЦП только для подтверждения личности, но не для подписи документов, шифрования и прочего. Для такой схемы достаточно шифрования с общим ключем и выдачи нумерованных смарт-карт, как более безопасного аналога пин-конвертов.

Смарт-карта
------------

Смарта-карта, содержащая приватный ключ и сертификат может выдаваться, как отдельное устройство, может быть совмещена с сим-картой телефона или может быть встроена в паспорт.

Использование смарт-карты, реализующей ЭЦП, позволяет решить все те же задачи, что ЭЦП как таковое, но при это дополнительно защищает владельца ключа от несанкционированного доступа к нему.

Встраивание смарт-карты в паспорт позволяет государству ограничить передачу ключа третьим лицам с санкции или без санкции владельца. Чтобы эта гарантия работала, нужно так же запретить использование ключей не встроенных в паспорт, то есть организовать государственную монополию на ЭЦП.
