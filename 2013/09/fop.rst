title: Легализация
summary: Рассказ о том, как я зарегистрировался предпринимателем, про электронные отчеты и цифровые подписи
pub_date: 2013-09-07
tags: [opressive government, taxes]


Киев
====

После лета, целиком потраченного на отлипание в Одессе, случилось страшное - прислали предложение работы из Киева. Типа с возможностью удаленки.

После привычно нудных переговоров, интервью по скайпику, телефону и вживую, получил финальное подтверждение и пошел регистрироваться, как физическое лицо-плательщик налогов (aka СПД, ФОП, ЧП, ИП и так далее).

Краткий ликбез
--------------

Какая-то из букв "С" в слове СССР означала социализм. Социализм - это такая замечательная идея, согласно которой государство вас накормит и обогреет, если у вас все плохо (или вам западло работать или работа вообще ненужна). Чтобы накормить и обогреть всех обиженных, надо откуда-то взять деньги.

Если работать на работе согласно Трудового Кодекса и договора о найме, то государство заберет очень много денег, где-то больше половины. Совсем в черную работать тоже нельзя, потомучто деньги приходят из-за границы, налоговая об этом в курсе и просто так забрать их со счета юрлица нельзя. Можно либо что-то купить от имени юрлица, либо заплатить зарплату (трудовой кодекс, привет).

Юридическое лицо
----------------

Что такое вообще юридическое лицо? Юрлицо - это выдуманный персонаж, который вам принадлежит, но который не вы. У юрлица может быть собственность, счет, имущество и обязательства, но это не ваши счета, имущества, собственность и обязательства.

Если юрлицо набрало обязательств, что-то профакапило и не может их выполнить, то при процедуре банкротства злые дяди придут и вынесут все печеньки из офиса, все купленные от имени юрлица ноутбуки и холодильники, но до вашего собственного золотого унитаза не дотянутся.

Слова "ограниченная ответственность" - это как раз лимит, больше которого злые дяди забрать не могут.

То есть это очень полезная штука на самом деле. Примерно как приличные сисадмины создают по виртуальной машине под каждый сервис, так приличные юристы создают по юрлицу под новый проект. Поэтому за слова "фирмы-однодневки" надо бить по морде лица вообще сразу.
Как уже написано выше, чтобы деньги юридического лица стали деньгами его владельца (директора, учередителя, акционера или кого еще) - нужно их явно заплатить по какому-нибудь поводу, провести через бухгалтерию и отчитаться в налоговую.

Если юридическое лицо платит зарплату, вознаграждение, компенсацию физическому лицу, то оно опять же платит *за него* грабительские 15% налога на доходы.

ФОП
----

Все было бы совсем плохо, но существует специально созданная дырка для тех, кто и налоги в таком количестве платить не хочет и работать в черную не может (или не хочет).
Дырка называется "фізична особа - підприємець". Гибрид ежа с ужом, который платит не очень большие налоги, но юридическим лицом не является, разделения собственности и ответственности не происходит. Деньги со своего счета снимаешь (они свои собственные, а не виртуального персонажа), а если накосячил - продавай почку и расплачивайся квартирой.

Чтобы все было совсем хорошо, существует так называемая "упрощенная система". Плательщики разбиваются на пять категорий в зависимости от дохода и вида деятельности и платят только "единый налог" (процент от прибыли) и если хотят - НДС. Плюс конечно платят социальный взнос в пенсионный фонд. Для прогромистов существует "третья группа-пять процентов", но пару лет назад вообще не платили нифига, кроме социального взноса.

Регистрация
-----------

Самый веселый момент в этой истории - регистрацией ФОП занимается не налоговая. Регистрацией и ведением реестра занимается некая "регистрационная служба министерства юстиции".
Следует похвалить нашу кровавую диктатуру - процедура регистрации со временем упрощается.
Раньше нужно было бегать с бумажками в несколько мутных богаделень,
сейчас же (с декабря 2012го) достаточно одной анкеты в эту самую регистрационную службу и квитанции об уплате 34 гривень. Анкета называется "форма 10" заполняются очевидные имя-фамилия-код-адрес, виды деятельности по КВЕД и еще какая-то чушь.

Электронная регистрация
-----------------------

Регистрация даже делается удаленно. Процесс от этого не становится менее муторным и бумажко-ориентированным, к сожалению.

Печальный момент в регистрации по электронке - нужно иметь электронную подпись, а чтобы получить ее, нужно все-таки сходить куда-то и, если это коммерческий сертификационный центр, еще и заплатить 200 гривней.

Паспорт-код-квитанция об оплате и выдают сертификат в стандартном X509 формате на одной болванке и приватный ключ в мутном формате на другой. Чтобы совсем испортить праздник, добавлю, что алгоритм подписи - не RSA+SHA, а какое-то мутное гостово-подобное говно, с пониженнной надеждностью. Штатный OpenSSL ее не понимает.

Дополнительный момент - чтобы заплатить 34 гривни регистрационного сбора, нужно узнать банковские реквизиты, которые так просто не гуглятся и при этом различаются для разных городов (об это дальше).

Taxer
-----

Первая попытка регистрация была через портал taxer.ua. Заполняю красивую формочку, нажимаю "дайте две" и оказывается, что формочка генрирует файл, который нужно распечатать (та самая форма 10, но заполненная заранее), подписать, отсканировать обратно и залить на сервер. Дальше нужно отсканировать квитанцию из банка и ИНН.

После этого сканы нужно подписать уже электронной подписью. Это делается прямо на сайте, а поскольку закон запрещает передавать приватный ключ, то с сайта грузится жава-апплет, считает подписи локально и на сервер грузит только результат.

Дальше таксер выплевывает невразумительную ошибку, я звоню им в техсаппорт и оказывается, что у них ничего не работает, "у проблемы два уровня - технический и организационный" и когда починится - неизвестно. Ну хотябы высылают PDF с инструкцией о том, как сделать все то же самое на государственном портале.

Регистрационный портал
----------------------

Регистрационный портал - это очень страшный сайт по адресу http://rp.irc.gov.ua. В отличии от таксера, там даже не жава-апплет, а целый силверлайтовый ад, который требует поставить в систему дополнительные библиотеки и только после этого работает. Конечно же - только под виндами и только после трех ребутов.

Кроме технологического ада, сайт страшен сам по себе, хотя и сделан на бутстрапе (силверлайт там нужен только для электронной подписи). Нужно на пяти экранах заполнять все то же самое, что уже написано в электронном сертификате и на таксере помешается в одну маленькую форму. При этом заполняемые данные полностью дублируют бумажную анкету (которую надо подписать руками И цифровой подписью). Данные о себе, включая имя, ИНН и адрес, нужно заполнять два раза - один раз о том, на кого регистрируется ФОП, второй раз о том, кто подает заявление.

В оправадание можно сказать, что на сайте есть оплата регистрационного сбора с банковской карточки, что могло бы сэкономить поход в банк. В целом юзабилити вполне на уровне плинтуса, как и у предыдущего госсайта, где я бодался с реэкспортом криптографии из США.

Отправка заявления
------------------

Заявление заполнено, файлы загружены и подписаны, кнопочка нажата, после чего анкета идет по электронке все туда же - на Арнаутскую 25. В прямую и деревянную логику современного технофашизма вторгается юридическая реальность, согласно которой Украина делится на кучу областей и городов, в каждом из которых существует местный бюджет (куда и платяться налоги) и территориальное отделение регистрационной службы.

Отправляя заявление, предприниматель регистрируется не просто "в Украине", а в конкретном территориальном отделении по месту прописки. Территориальные отделения - это не разные окошки одной и той же системы, а вполне автономные сущности, имеющие собственные счета, но при этом подчиняющиеся одним законам и имеющие доступ к единому реестру.

На следующий день после отправки заявление вернули (оставили без рассмотрения) с пометкой о том, что я подал недостаточное количество документов. Позвонил в эту богадельню по телефону, чтобы выяснить, что происходит - спрашивают, какой у меня регистратор (заявления обрабатывают несколько сотрудников, хотя вообще непонятно зачем там человек). Поскольку интерфейс сделан абсолютно адски, я ищу эту информацию минут 15 и в итоге нахожу под пунктом "посмотреть документы", где лежит полный ответ на мою заявку в виде rtf файлика и указано имя.

Перезваниваю и выясняю, что кроме трех сканов бумажек, нужен еще и четвертый - опись, где написан список предыдущих трех. Бумажная опись документов при электронной регистрации ага.

Ответ
-----

На следующий день после повторной отправки у заявки меняется статус на "зарегистрировано", при этом никаких документов в ответ не загружено, даже кнопки этой нет. При этом в базе ФОП я уже есть, судя по `поиску в ЕДР`_, но выписку еще не сделали.

Еще один прекрасный момент - сайт электронной регистрации не шлет на мыло никаких уведомлений о смене статуса заявки. Другой прекрасный момент - даже для того, чтобы на сайт зайти, нужно использовать электронную подпись (что работает только в виндах).

Второй рабочий день после подачи, статус заявки висит все тот же - звоню еще раз. Поскольку документы в ответ не загружены, имя регистратора я опять не знаю. Добравшись до нужной сотрудницы, нажимающей ответственную кнопочку, выясняю, что они ждут ответа от налоговой, которую они сами уведомляют о моей регистрации. Хорошо, что не надо лишний раз ходить, но могли бы и писать на сайте что происходит. По закону, на заявление должны ответить в течении трех дней, а это уже второй.

На третий день заявка уже принята, на сайт загруежен RTF файл с "выпиской", где указана куча циферок под которыми я записан в налоговой, пенсионном и статистичеком. Моего ИНН им мало, поэтому в каждой из трех служб (миндоходов aka налоговой, пенсионном и статистическом) мне присвоили еще один номер.

Выписка
-------

Получив электронную выписку, прохожу следующий круг ада - получаю электронную подпись уже на ФОП (еще за 200 гривней), открываю счет в банке (банку нужны циферки из выписки, что спалить в налоговую, что я открыл счет). Дальше я все-таки иду в налоговую, чтобы зарегистрировать книгу учета доходов. Такую бумажную, прошнурованную и с пломбой на шнуровке.

Кроме книжечки, в налоговую нужно подать заявление на переход на упрощенную систему налогообложения и единый налог, причем сделать это в течении 10 дней иначе включится "общая система  налогообложения" и будет адский ад. Форму я опять заполняю на таксере, но ее адски корежит и приходится покупать в налоговой два бланка по 2 гривни и заполнять руками.

Во все три места - банк, налоговую и сертификационный центр я принес распечатку выписки, обычный RTF файл без подписей и печатей. В налоговой больше интересовались тем, чтобы я купил им канцтоваров - папочку, в которую эту выписку подшили.

Налоговая
---------

В налоговой, которую сейчас называют "миндоходов" все чистенько-приятненько, очередей не видел, торгуют канцтоварами по адскому прайсу. Само здание очень годно поремонтировано, снаружи скамеечки-газончики, никакого ОВИР-стайл. Торчат в середине района, а к главной улице сделали дорожку из плитки, что вообще удивительно.

Как и с регистрационным отделом, все территориальные органы - это отдельные сущности с собственными счетами. Регистраируясь "в налоговой", предприниматель регистрируется в конкретном отделении и прикреплется к конкретному налоговому инспектору, которому и нужно подавать документы (документы потом нужно все равно нести в окно входящей корреспонденции). Этой же конкретной налоговой он и перечисляет деньги на ее счета, а отчеты сдает конкретному инспектору (хотя отчеты в бумажном виде сдают только лохи).

Единый налог
------------

Заявление на единый налог нужно подать в течении 10 дней после регистрации, иначе предприниматель останется на "общей системе". Заявление на единый налог нельзя подать по электронке и с ним нужно ходить ногами в налоговую.

Что радует - положительная динамика сохраняется и на неделе приняли новый закон о том, чтобы выбор упрощенной системы и единого налога указывался прямо в регистрационной карточке и не нужно было ходить лишний раз.

После подачи заявления на единый налог нужно получить еще и свидетельство плательщика, которое почему-то делают 10 дней вместе с опечатываением книги. Свидетельство плательшика нужно бухгалтерии контрагента чтобы там знали, что выплаты делаются не физическому лицу и контрагент не должен платить с них грабительские 15% (см начало текста).

Электронная отчетность
----------------------

Отчетность в пенсионный и налоговую тоже сдается по электронке
для чего нужно заключить с обеими конторами договора о признании электронных сертификатоф. В пенсионный он отправляется практически одной кнопкой (которую в таксере умудриись сломать, не заметив просроченный сертификат) и на которую отвечает робот в течении получаса.

Для налоговой нужно указывать еще и имя начальника территориального отделения для чего звонить туда по телефону. Имя начальника достаточно просто гуглится, но данные устаревают и в каких-то отделениях такие договора почему-то подписывает не начальник, а заместитель и это занимает день.

Итого
-----

- начал 21го августа, тогда же получил подпись.
- 22го пришел первый отлуп
- 23го зарегистрировали, 24-26 выходные
- 28го зарегистрировали в налоговой и ПФ, получил выписку в электронной форме
- 29го подал заявление в налоговую на ЕН и книжечку, получил подпись ФОП и открыл счет в банке
- 31го на почту пришла бумажная выписка на бланке.
- 2го отправил электронное заявление о признанни ключей в ПФ и сразу получил ответ
- 4го отправил такое же в налоговую
- 5го получил ответ из налоговой
- где-то девятого-десятого получу свидетельство ЕН

Сходить пришлось за подписью (два раза), в банк (два раза), в налоговую один раз и еще один раз схожу забрать книгу и свидетельство ЕН

Интерфейсы дурацкие, подпись нестандартная, электронный документооборот дублируется бумажным, а феодально-территориальная система прорывется наружу. В идеале тут должно быть достаточно одной кнопки, списка КВЕДов и группы ЕН в одной форме, а бумажек не должно быть вообще.

Банк
----

И еще - в банке выдают еще одну электронную подпись. Чтобы пользоваться интернет-банкингом, существует отдельный (не тот, что у просто физлиц) веб-интерфейс, целиком сделанный из жава-апплета.

.. _поиску в ЕДР: http://irc.gov.ua/ua/Poshuk-v-YeDR.html
