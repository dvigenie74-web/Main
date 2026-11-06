# TBC Bank (Грузия): кто может получить онлайн-эквайринг. Требования к нерезидентам, юридическая форма, KYC, налоги

> Методология и ограничения: собрано 2026-11-06. В этой облачной сессии WebFetch не работал: хосты `tbcbank.ge`, `developers.tbcbank.ge`, `manageripgeorgia.atlassian.net`, `travelask.ru` не резолвились, поэтому полные тексты страниц прочитать не удалось. Всё ниже основано на выдаче WebSearch, то есть на фрагментах страниц и их пересказе поисковой моделью. Формулировки из официальных документов TBC (FAQ по e-commerce, договор мерчанта, страница о санкциях) взяты из этих фрагментов. Перед публикацией их стоит перепроверить по первоисточнику. Возраст данных помечен там, где он известен.

## 1. Нужно ли грузинское юрлицо (ИП / LLC), или подойдёт физлицо или иностранная компания?

### Takeaway
TBC E-Commerce подключают только зарегистрированному в Грузии налогоплательщику: ИП (individual entrepreneur) или юрлицу. Физлицо без регистрации как налогоплательщика и иностранная компания без грузинской регистрации, по имеющимся данным, не подходят. На практике путь для иностранца такой: грузинское ИП (или LLC), затем бизнес-счёт в TBC, затем заявка на e-commerce.

### Cited Findings
- В официальном FAQ TBC по e-commerce указано: «You should be registered as a taxpayer, whether as an individual or a legal person». Мерчант обязан быть зарегистрирован в Грузии как налогоплательщик, физлицо-ИП или юрлицо. — [TBC E-Commerce page](https://tbcbank.ge/en/business/card-payments/e-commerce); [TBC E-Commerce (old site)](https://www.tbcbank.ge/web/en/web/guest/e-commerce)
- Договор TBC E-Commerce определяет мерчанта как «an entrepreneur/ individual taxpayer and/or a legal entity/ organizational entity», то есть ИП в него явно включены. — [TBC E-Commerce Key Terms (ctfassets PDF)](https://assets.eu.ctfassets.net/psnuheg7hu1m/2XgPcxANQtwBmlLjvQsGJw/8efc508deca6a65de0b23c0ea4e53a8f/6f6bfe13-fb73-49c5-ac66-13e6aaf19ae7)
- Процесс по документации для разработчиков (TBC Checkout): (1) зарегистрировать компанию как мерчанта и получить merchant credentials; (2) создать developer account и получить API key; (3) интегрировать checkout. — [TBC Developers: Registering Merchant Account](https://developers.tbcbank.ge/docs/checkout-registering-merchant-account); [Checkout overview](https://developers.tbcbank.ge/docs/checkout-overview)
- Платёжный агрегатор Flitt, работающий поверх TBC, требует «registered LLC or individual entrepreneur in Georgia» и активный бизнес-счёт в TBC Bank. — [Quickpay.ge: Flitt module](https://quickpay.ge/en/modules/flitt); [Flitt FAQ](https://flitt.com/faq/) (обслуживает бизнесы, «officially registered in Georgia, Uzbekistan, Armenia, and Moldova»)
- По внутренней политике TBC деятельность ИП долго обслуживалась через личные счета с привязкой ID ИП. Бизнес-счета для ИП появились относительно недавно. Страница FAQ обновлялась в 2022, 2023 и 04.2026. — [FAQ ИП Грузия (Confluence): Открытие счета в TBC](https://manageripgeorgia.atlassian.net/wiki/spaces/FAQ/pages/15695887/TBC+20.11.2022) (прочитан только сниппет)
- Страница TBC для экспатов: для физлиц-нерезидентов «business account opening is currently available only at a TBC Bank branch in person». — [TBC: Open a Business Account as an Expat](https://tbcbank.ge/en/for-expats/open-a-business-account)
- Для разных платёжных методов (интернет-банк, recurring и др.) нужна отдельная активация. Recurring-платежи запрашиваются письменно через бизнес-интернет-банк и требуют подтверждения TBC. — [TBC Developers: Payment Methods](https://developers.tbcbank.ge/docs/payment-methods)

### Inferences
- Иностранная компания (например, эстонская OÜ или UAE FZE) напрямую в TBC E-Commerce, судя по всему, не попадёт: условие «registered as a taxpayer» относится к грузинскому налоговому учёту. Теоретически можно зарегистрировать филиал (branch) иностранной компании в Грузии, но подтверждений, что TBC подключает филиалам эквайринг, не найдено.
- Минимальная рабочая цепочка: регистрация ИП в Публичном реестре (можно через представителя по доверенности), затем личный визит в отделение TBC для открытия бизнес-счёта (для нерезидентов это обязательно), затем заявка на e-commerce. Заявку можно подать напрямую в TBC или через агрегатор Flitt, которому тоже нужен счёт в TBC.

### Gaps
- Полный перечень документов для заявки на e-commerce от ИП-нерезидента не найден. TBC пишет только «documents required per company profile».
- Не удалось подтвердить, требует ли TBC статус резидента Грузии или ВНЖ у владельца ИП для подключения e-commerce. Прямых упоминаний такого требования не найдено.

## 2. Можно ли использовать эквайринг на ИП со статусом малого бизнеса (1%) для дохода от иностранных клиентов? Налоги и ограничения

### Takeaway
Статус малого бизнеса (1% с оборота до 500 000 GEL в год) доступен иностранцам и подходит для онлайн-услуг иностранным клиентам. Ключевое ограничение — вид деятельности: консалтинг (а также юридические, аудиторские, бухгалтерские, медицинские, нотариальные, архитектурные услуги, игорный бизнес, обмен валюты и др.) исключён. Отдельного налогового режима для поступлений через эквайринг не найдено: это часть оборота, как и SWIFT-переводы. Важна квалификация услуги (IT-разработка / курсы против «консультирования»).

### Cited Findings
- Ставка 1% с оборота до 500 000 GEL; при превышении применяется 3% или общий режим. — [advocate-ge.com: Статус малого бизнеса 2026](https://advocate-ge.com/articles/status-malogo-biznesa-v-gruzii-1-procent-2026/); [eservices.ge](https://eservices.ge/account-tbc.html) (там же: микробизнес 0% до 30 000 GEL)
- Режим доступен иностранцам без гражданства и ВНЖ, деятельность можно вести онлайн с иностранными клиентами. — [advocate-ge.com](https://advocate-ge.com/articles/status-malogo-biznesa-v-gruzii-1-procent-2026/) (коммерческий гайд)
- 1% доступен только ИП, не LLC. — [BCA: Открытие бизнеса в Грузии 2026](https://www.bcaun.com/insights/georgia_business)
- Исключённые виды деятельности: консалтинг, юридические, аудиторские, медицинские, нотариальные, архитектурные услуги, игорный бизнес, обмен валюты и др. Перечень привязан к постановлению правительства №415. — [Habr: Как открыть ИП в Грузии](https://habr.com/ru/articles/672748/); [veridia.ge](https://veridia.ge/ru/the-ultimate-guide-to-becoming-an-individual-entrepreneur-in-georgia/); [gegidze.com: полный список запрещённых видов деятельности](https://www.gegidze.com/ru/post/полный-список-запрещённых-видов-деятельности-лишающих-статуса-малого-бизнеса-в-грузии)
- Серая зона с IT: часть источников считает IT-разработку и маркетинговую поддержку допустимыми, другие предупреждают о риске переквалификации IT-услуг в IT-консалтинг. Пример из гайда: предприниматель выбрал код IT-услуг, а фактически консультировал клиентов по IT, и это «не подпадает под статус малого бизнеса». — [Habr](https://habr.com/ru/articles/672748/); [v-gruzii.com: ИП 2026](https://v-gruzii.com/business/ip); источники противоречат друг другу в части рекламы, маркетинга и дизайна.
- С 1 февраля 2025 года услуги в строительном секторе, оказываемые компаниям и предпринимателям, облагаются 20% вместо 1%. К удалённым сервисным бизнесам это не относится, но показывает, что перечень ограничений меняется. — [Mondaq/Eurofast: legislative change construction](https://webiis08.mondaq.com/construction-planning/1577054/legislative-change-for-small-business-entrepreneurs-in-georgias-construction-sector)
- НДС: порог регистрации — 100 000 GEL за любые 12 месяцев подряд, ставка 18%. НДС возникает, когда местом оказания услуги считается Грузия. По нескольким гайдам, при оказании услуг иностранным клиентам НДС «чаще всего» не возникает. Регистрация плательщиком НДС не отменяет 1% подоходного. — [Habr: Налоги для ИП в Грузии](https://habr.com/ru/articles/848902/); [pbservices.ge: гайд по налогам](https://pbservices.ge/blog/tax-guide-companies-georgia/)
- На форуме ИП-шники задают вопрос, возникает ли НДС при оплате иностранными клиентами через грузинские платёжные системы (то есть через эквайринг, когда банк не видит контракт). Однозначного ответа нет, совет — хранить контракты и инвойсы с иностранными заказчиками. — [travelask.ru: обсуждение эквайринга BoG/Payze](https://travelask.ru/questions/4830530_ge_u-kogo-est-ip-v-gruzii-podskazhite-dopustim-ya-sdelayu-inter)

### Inferences
- Для моделей «онлайн-курсы», «IT-разработка», «цифровые продукты» статус 1%, по всей видимости, совместим, если код деятельности и формулировки в договорах и оферте не похожи на «консультирование». Для «коучинга», «менторства», «бизнес-консалтинга» риск отказа в статусе или его последующей потери высок.
- При приёме карт от физлиц со всего мира (B2C) доказать место оказания услуги и «иностранность» клиента сложнее, чем при B2B по контракту и SWIFT. Отсюда налоговая неопределённость по НДС при превышении 100 000 GEL. Нужна консультация грузинского бухгалтера. Эквайринговые поступления банк видит и передаёт как оборот, «спрятать» их нельзя.
- Если оплату вносят грузинские физлица, место оказания услуги — Грузия, и при превышении порога НДС применяется.

### Gaps
- Официальный текст постановления №415 (matsne.gov.ge) и разъяснения rs.ge про онлайн-курсы и коучинг не найдены и не прочитаны.
- Позиция Службы доходов по определению места оказания B2C-услуг, оплаченных картами иностранных банков, не найдена.

## 3. KYC: резидентство, физическое присутствие, санкционные ограничения для граждан РФ, отказы 2024-2026, грузинский адрес и телефон

### Takeaway
Личный счёт нерезиденту TBC может начать открывать онлайн (портал для нерезидентов, video onboarding), но бизнес-счёт ИП-нерезиденту открывают только при личном визите в отделение. Гражданам РФ и РБ в 2022-2023 массово отказывали. К 2025-2026 счета им снова открывают, но с усиленной проверкой источника средств, частыми отказами без объяснений, иногда только в лари или с ограничениями на переводы. Входящие переводы из РФ, РБ, Казахстана, Армении, Кыргызстана, ОАЭ и Азербайджана TBC проверяет с особым вниманием. Требование грузинского телефона или адреса в найденных источниках не подтверждено.

### Cited Findings
- Портал TBC для нерезидентов: заполнение данных и загрузка паспорта онлайн, возможен запрос дополнительных документов, завершение в отделении или через Video Onboarding. — [TBC Non-Resident Registration](https://nonresident.tbcbank.ge/); [TBC Video Bank](https://tbcbank.ge/en/digital-services/video-bank); [TBC for Emigrants](https://tbcbank.ge/en/emigrants)
- Бизнес-счёт для физлиц-нерезидентов открывается только лично в отделении TBC. — [TBC: Open a Business Account as an Expat](https://tbcbank.ge/en/for-expats/open-a-business-account)
- По сторонним гайдам, полное удалённое одобрение для нерезидента не гарантировано и зависит от профиля и гражданства. — [easyglobalbanking.com (2026)](https://www.easyglobalbanking.com/alternative-banking-hubs/open-bank-account-georgia-non-resident-2026/); [wolja.digital: TBC Concept for Non-Residents 2026](https://wolja.digital/services/opening-a-bank-account-abroad-for-non-residents/opening-a-bank-account-in-georgia-for-non-residents/tbc-concept-for-non-residents-in-2026/)
- 2022 (устаревшее): сообщения, что TBC отказывается открывать счета гражданам РФ и РБ. — [Форум Винского (awd.ru), тема про счета в Грузии](https://forum.awd.ru/viewtopic.php?t=409514)
- Позже на том же форуме писали, что TBC «тоже начали открывать мультивалютки гражданам РФ и РБ». Ранее россиянам открывали урезанные счета только в лари и карты, действующие только в Грузии. Пользователь сообщал об онлайн-одобрении заявки в TBC в июле 2026. — [awd.ru, стр. 24 (2026)](https://forum.awd.ru/viewtopic.php?t=409514&start=1160)
- vc.ru (2026): TBC и BoG часто проводят дополнительную проверку, которая может затянуть открытие на неделю, и всё чаще открывают россиянам только счета в лари или ограничивают переводы за границу. — [vc.ru: Открывают ли счет банки Грузии россиянам в 2026](https://vc.ru/money/2257743-kak-rossiyanam-otkryt-schyot-v-gruzii)
- Источники противоречат друг другу по удалённому открытию для россиян. По одному обзору 2026 года, ведущие банки (BoG, TBC, Liberty, Basisbank) «официально прекратили дистанционное обслуживание клиентов из России». Другой источник утверждает, что ни один крупный банк на октябрь 2026 не открывает россиянину личный счёт удалённо. Форумный пост при этом сообщает об онлайн-одобрении в TBC в июле 2026. — [card-open.ru (2026)](https://card-open.ru/blog/gruzinskie-banki-dlya-rossiyan-2026); [awd.ru](https://forum.awd.ru/viewtopic.php?t=409514&start=1160)
- Личный опыт (myreloc): TBC требует рабочий контракт и выписку из другого банка и может отказать без объяснения. Автор оценивает долю отказов россиянам «примерно в половину» (личное наблюдение, не статистика) и советует при отказе идти в Credo или Liberty. — [myreloc.com: подводные камни ИП в Грузии](https://myreloc.com/%D0%BF%D0%BE%D0%B4%D0%B2%D0%BE%D0%B4%D0%BD%D1%8B%D0%B5-%D0%BA%D0%B0%D0%BC%D0%BD%D0%B8/)
- Отказ возможен без объяснения причин даже при полном пакете документов; плата за рассмотрение не возвращается; паспорта часто недостаточно, могут запросить подтверждение дохода. — [awd.is: какие банки Грузии открывают счета россиянам 2026](https://awd.is/otkryt-bankovskuyu-kartu-v-gruzii/); [gegidze.com: TBC KYC step-by-step](https://www.gegidze.com/post/tbc-bank-kyc-process-step-by-step-for-new-account-holders)
- Для контекста: в Bank of Georgia (не TBC) в 2022 году россиянам открывали счета только при подписании декларации, что РФ является оккупантом. — [Эхо Кавказа](https://www.ekhokavkaza.com/a/31736098.html)
- Санкционная политика TBC: соблюдает режимы ООН, UK, US и EU. Операции с санкционными лицами и лицами, «supporting Russia's military-industrial base», строго запрещены. Банк может запрашивать инвойс, контракт или сертификат происхождения по операциям, связанным с РФ. — [TBC: Restrictions on Foreign Currency Transactions](https://tbcbank.ge/en/transfers/prohibition-of-transactions-with-sanctioned-countries); [PDF политики](https://assets.eu.ctfassets.net/psnuheg7hu1m/2chYBHEUmZpQCEJQ7Rj4EF/318206e7ce0a8f88e69390e00db20d9f/eng.pdf)
- 2023: TBC заявил, что может закрывать счета без предварительного уведомления при выявлении операции в нарушение санкций. — [Forum Free Russia (2023-04-21)](https://www.forumfreerussia.org/en/news-en/2023-04-21/large-georgian-bank-tbc-bank-will-close-accounts-of-violators-of-sanctions-against-russia); [justadvisors.ge: New Policy by TBC](https://en.justadvisors.ge/blog/jizn-v-gruzii/novaya-politika-banka-tbc)
- TBC отказался восстанавливать доступ к счетам бывшего генпрокурора Грузии, попавшего под санкции США, даже после указания Нацбанка Грузии. Это показывает, что TBC ставит соблюдение санкций US/EU/UK выше требований местного регулятора. — [frontnews.ge](https://frontnews.ge/en/news/tbc-bank-refuses-to-restore-us-sanctioned-ex-official-s-access-to-accounts-despite-national-bank-s-approval)
- Телефон: страница для эмигрантов описывает регистрацию в приложении по номеру мобильного, но не уточняет, нужен ли грузинский номер. — [TBC for Emigrants](https://tbcbank.ge/en/emigrants)

### Inferences
- Для гражданина РФ или РБ самый тонкий момент — не регистрация ИП, а бизнес-счёт в TBC. Без него нет ни прямого e-commerce TBC, ни Flitt. Если TBC откажет, путь к TBC-эквайрингу закрыт, и остаются BoG, Credo, Liberty и их собственные решения.
- Граждане Украины, Казахстана и ЕС, судя по источникам, проходят KYC проще. Конкретных данных по ним не найдено, кроме того, что входящие переводы из Казахстана тоже под особым контролем.
- Нужно закладывать личную поездку в Тбилиси (бизнес-счёт открывается только в отделении) и пакет документов о происхождении средств: контракты, выписки других банков, подтверждение дохода.

### Gaps
- Нет официальной статистики отказов TBC по гражданству.
- Требование грузинского телефона или адреса не подтверждено и не опровергнуто: в отделении на практике обычно просят местный номер для SMS, но источника на это не найдено.
- Не найдено случаев, когда у ИП-гражданина РФ в TBC заморозили именно эквайринговый мерчант-аккаунт.

## 4. Требования к сайту и запрещённые виды бизнеса

### Takeaway
TBC требует от сайта стандартный набор по правилам карточных схем: контакты, полное описание товаров и услуг, условия покупки, отмены и возврата, торговое имя (DBA) до оплаты, политики конфиденциальности и безопасности, которые клиент принимает до оплаты. Официальный стоп-лист: порнография, табак, оружие, нелицензионный цифровой контент, подделки, форекс, рецептурные лекарства. Для гэмблинга нужна лицензия. Коучинг, эзотерика, крипта, знакомства и инфобизнес в найденных официальных списках прямо не упомянуты.

### Cited Findings
- Запрещённые виды бизнеса по FAQ TBC: «1. Pornography 2. Tobacco 3. Weapons 4. Unlicensed digital content 5. Fake products 6. Forex 7. Prescription medications». — [TBC E-Commerce](https://www.tbcbank.ge/web/en/web/guest/e-commerce); [tbcbank.ge e-commerce](https://tbcbank.ge/en/business/card-payments/e-commerce)
- Документы запрашиваются по профилю: например, подтверждение физического магазина или склада, договоры с поставщиками, лицензия на продажу брендовых товаров; для гэмблинга — лицензия. — [TBC E-Commerce](https://www.tbcbank.ge/web/en/web/guest/e-commerce)
- Договор мерчанта: на сайте должны быть телефон и email мерчанта, «full and clear description of the goods or services», условия и порядок покупки, отмены заказа и возврата. Торговое имя (DBA) должно отображаться до завершения оплаты. Политики конфиденциальности, безопасности транзакций, оплаты и соответствия закону должны быть опубликованы и приняты клиентом до покупки. — [TBC E-Commerce terms (PDF)](https://assets.eu.ctfassets.net/psnuheg7hu1m/6LvBlV3ZxCtHKb1sBvh04s/45b9018afdc1c8824652ee317ad28d56/b6a2acc5-bdc3-48ae-98f5-449e22f6dc51.pdf); [TBC E-Commerce (sub-acquirer) ENG PDF](https://www.tbcbank.ge/web/documents/10184/179959/)
- Сторонний консалтинг (del-ops.ge) также перечисляет обязательные страницы: privacy policy, terms, refund policy и физический адрес. Это не официальный источник TBC. — [del-ops.ge: TBC Bank Account Rejection: 7 Hidden Reasons (2026)](https://www.del-ops.ge/en/blog/tbc-bank-account-rejection-7-hidden-reasons-solutions-2026)
- Есть отдельная программа «E-commerce service provider» (субэквайринг / платёжные провайдеры). — [TBC: E-commerce service provider](https://tbcbank.ge/en/card-payments/e-commerce-service-provider)

### Inferences
- Строка «Unlicensed digital content» важна для онлайн-курсов и цифровых продуктов: нужно показать права на контент (авторство) и чёткое описание продукта.
- Крипту, эзотерику, дейтинг и «инфобизнес» TBC, вероятно, считает high-risk, что выражается в отказе или большем страховом резерве. Это вывод по общей практике эквайеров и по категории «Forex», а не подтверждённый факт.
- Сайт должен быть готов до подачи заявки: собственный домен, SSL (подразумевается правилами PCI и checkout), DBA, совпадающее с ИП, и контакты.

### Gaps
- Официального полного списка high-risk MCC TBC (коучинг, эзотерика, крипта, дейтинг, инфобизнес) не найдено.
- Явное требование SSL или собственного домена в найденных фрагментах не встречено.

## 5. Реальный опыт: сроки, отказы, подводные камни, чарджбэки, заморозки, страховой резерв, комиссии

### Takeaway
Отзывы русскоязычных ИП о прямом эквайринге в TBC скудные и в основном старые (около 2021-2023): сотрудники отделений не понимали запрос, предлагали приём только грузинских карт, открывали счёт, но эквайринг не подключали. Официально для приёма иностранных карт TBC требует страховой резерв (сумма зависит от профиля, оборота и риска), а без резерва можно принимать только грузинские карты. Комиссия за иностранные карты около 2,5%. Payze, популярный ранее обходной путь, по данным 2026 года, прекратил работу.

### Cited Findings
- Страховой резерв не требуется, если принимать карты только грузинских банков. При приёме иностранных карт сумма резерва определяется «according to merchant profile, turnover and risk level» и может быть процентом или фиксированной суммой. Резерв используется только для покрытия убытков банка по оспоренным транзакциям. — [TBC E-Commerce](https://www.tbcbank.ge/web/en/web/guest/e-commerce); [TBC Developers e-commerce FAQ](https://developers.tbcbank.ge/docs/e-commerce-faq)
- Комиссии на разных страницах TBC расходятся: на одной 2,5% для иностранных карт и 1,6% для карт TBC, на другой 2% для карт TBC. — [TBC Online Payments for Business](https://tbcbank.ge/en/business/payment-systems/online-payments); [TBC e-commerce](https://tbcbank.ge/en/business/card-payments/e-commerce)
- Сторонний обзор называет комиссию 1,5-2,5% в зависимости от оборота, без ссылки на тарифы. — [YB Case 2026: TBC Bank](https://ybcase.com/bank-reviews/tbc-bank)
- Сравнение quickpay.ge (2026): у Flitt 2,0-2,2% по внутренним картам и 2,5% по международным. Ставки, в том числе у банков, обсуждаются индивидуально. — [Quickpay.ge: Georgian Payment Gateways Compared 2026](https://quickpay.ge/en/blog/georgian-payment-gateways-comparison)
- Выплаты по иностранным картам зачисляются максимум в течение трёх дней. — [TBC E-Commerce](https://tbcbank.ge/en/business/card-payments/e-commerce)
- При чарджбэке мерчант обязан полностью вернуть оспоренную сумму и хранить документы для банка. — [TBC E-Commerce terms (PDF)](https://assets.eu.ctfassets.net/psnuheg7hu1m/6LvBlV3ZxCtHKb1sBvh04s/45b9018afdc1c8824652ee317ad28d56/b6a2acc5-bdc3-48ae-98f5-449e22f6dc51.pdf)
- Опыт ИП (travelask, около 2021-2023, устаревшее): в TBC и BoG «делают круглые глаза» или предлагают приём платежей только с грузинских карт; банк открыл счёт, но интернет-эквайринг не подключил. Совет — говорить в отделении «терминал для оплаты картами на сайте». — [travelask: ИП в Грузии и интернет-эквайринг](https://travelask.ru/questions/2747368_ge_vsem-privet-te-u-kogo-est-ip-v-gruzii-delali-li-vy-internet); [travelask: «Открыл ИП, очень нужен онлайн эквайринг»](https://travelask.ru/questions/4657101_ge_otkryl-ip-v-gruzii-ochen-nuzhen-onlayn-ekvayring-kart-ne-mog)
- В тех же обсуждениях советовали Payze, Unipay, Paymentwall, при этом отмечали, что первые два, «скорее всего, откажут» владельцам паспортов РФ и РБ. — [travelask](https://travelask.ru/questions/4657101_ge_otkryl-ip-v-gruzii-ochen-nuzhen-onlayn-ekvayring-kart-ne-mog); [travelask: BoG/Payze](https://travelask.ru/questions/4830530_ge_u-kogo-est-ip-v-gruzii-podskazhite-dopustim-ya-sdelayu-inter)
- Блог «Ботинок и карандаш» (старый пост): автор после регистрации ИП и счетов в TBC и BoG подключил интернет-эквайринг через Payze.io в связке со счётом в BoG, когда другие отказали. — [bootandpencil.com: Как я интернет-эквайринг в Грузии подключал](https://bootandpencil.com/lifestyle/%D0%B8%D0%BD%D1%82%D0%B5%D1%80%D0%BD%D0%B5%D1%82-%D1%8D%D0%BA%D0%B2%D0%B0%D0%B9%D1%80%D0%B8%D0%BD%D0%B3-%D0%B2-%D0%B3%D1%80%D1%83%D0%B7%D0%B8%D0%B8/)
- Payze (2026): по обзору paymentpop, Payze прекратил работу в Грузии и не принимает новых клиентов. — [paymentpop: Payze Reviews 2026](https://paymentpop.com/merchant-accounts/payze-reviews/)
- HackerNoon (около 2023): стартап подавал заявки нескольким грузинским провайдерам; от Payze больше месяца не было ответа, через 2 месяца пришёл отказ по риск-политике. — [HackerNoon: Setting Up Online Acquiring as a Startup](https://hackernoon.com/setting-up-online-acquiring-as-a-startup-firsthand-round-1-failed)
- Сервис etoplatezhi.ru рекламирует приём иностранных карт для ИП и ООО в Грузии с комиссией от 8%. Это реклама посредника, а не независимый отзыв. — [etoplatezhi.ru](https://etoplatezhi.ru/international-cards/)

### Inferences
- Главные практические барьеры: (1) получить у TBC разрешение на иностранные карты, а не только грузинские; (2) внести страховой резерв, размер которого для нового ИП с удалённым сервисным бизнесом без истории может быть заметным; (3) сроки — недели или месяцы.
- Flitt (интеграция поверх счёта TBC) выглядит как более «продуктовый» путь подключения TBC-эквайринга для ИП в 2025-2026 при сопоставимой комиссии около 2,5% по иностранным картам. Оценка сделана по маркетинговым материалам, независимые отзывы не найдены.

### Gaps
- Не найдено свежих (2025-2026) подробных отзывов русскоязычных ИП о подключении именно TBC E-Commerce: сроков, размера резерва, отказов по категориям услуг.
- Нет данных о заморозке мерчант-аккаунтов TBC из-за чарджбэков и о пороге chargeback ratio.

## 6. Международные SWIFT-переводы, выплаты и платежи из России

### Takeaway
Карты российских банков (Visa/MC, выпущенные в РФ) отключены от международных схем и в грузинском эквайринге не работают. Принять через TBC оплату российской картой невозможно, а «Мир» TBC не принимает. Входящие SWIFT-переводы на счёт ИП в TBC возможны, но переводы из РФ и ряда стран (РБ, KZ, AM, KG, AE, AZ) под «special focus»: банк может приостановить перевод и запросить контракт или инвойс. Операции с санкционными лицами запрещены, нарушение санкций ведёт к закрытию счёта без уведомления.

### Cited Findings
- Международные платёжные системы отключили российские банки, поэтому грузинский эквайринг их карты «просто не видит». — [vc.ru: Как платить в Грузии россиянам в 2026](https://vc.ru/social/3000863-kak-platit-v-gruzii-rossiyanam-v-2026-godu-kakie-sposoby-dostupny-virtualnye-karty-nalichnye-i-gruzinskii-schet-kakie-karty-rabotayut-v-gruzii); [t-j.ru: счёт в Грузии 2026](https://t-j.ru/georgia-card/)
- TBC может приостановить входящий перевод и через интернет-банк запросить дополнительные документы. Переводы из России, Беларуси, Азербайджана, Армении, Казахстана, Кыргызстана и ОАЭ — под «special focus». — [TBC: Restrictions on Foreign Currency Transactions](https://tbcbank.ge/en/transfers/prohibition-of-transactions-with-sanctioned-countries); [TBC: Transactions — Sanctioned Countries](https://www.tbcbank.ge/web/en/transactions-sanctioned-countries)
- По коммерческим переводам, не связанным с поставкой товаров, в определённые группы стран требуется инвойс и/или контракт «regardless of transaction currency». Беларусь — в Group II. — [TBC sanctions policy PDF](https://assets.eu.ctfassets.net/psnuheg7hu1m/2chYBHEUmZpQCEJQ7Rj4EF/318206e7ce0a8f88e69390e00db20d9f/eng.pdf)
- TBC приостановил операции в России. — [#LeaveRussia: TBC Bank](https://leave-russia.org/tbc-bank)
- Россиянам TBC и BoG всё чаще открывают только счета в лари или ограничивают переводы за границу (2026). — [vc.ru](https://vc.ru/money/2257743-kak-rossiyanam-otkryt-schyot-v-gruzii)
- В 2026 году TBC принимает American Express в магазинах и онлайн. — [The Paypers](https://thepaypers.com/payments/news/tbc-georgia-to-accept-american-express-cards-in-stores-and-online)
- TBC стал первым в Грузии партнёром платформы Visa CyberSource (около 2024), с поддержкой Shopify и аналогов; запущена «new international payment platform for businesses». — [cbw.ge: CyberSource](https://cbw.ge/banking/tbc-bank-emerges-as-georgias-first-partner-of-visas-cybersource-payment-platform); [cbw.ge: new international payment platform](https://cbw.ge/banking/tbc-launches-new-international-payment-platform-for-businesses)

### Inferences
- Для клиентов из РФ: эквайринг TBC бесполезен для карт российских банков. Остаются оплата клиентом картой иностранного банка (KZ, AM, GE и др.), SWIFT-перевод от российского физлица или юрлица (с риском приостановки и проверки) или сторонние посредники с высокой комиссией. Регулярный поток из РФ на счёт ИП гражданина РФ, скорее всего, будет вызывать запросы документов и повышает риск закрытия счёта.
- Для клиентов из ЕС, США и остального мира SWIFT в USD или EUR на ИП-счёт TBC — стандартная операция. Банку нужно показать контракт или инвойс, это хорошо совпадает с B2B-моделью консалтинга и IT. Но консалтинг несовместим со статусом 1% (см. раздел 2).

### Gaps
- Не найдено официальных данных о лимитах и комиссиях SWIFT для ИП-счетов TBC в 2026.
- Не найдено, принимает ли TBC E-Commerce карты UnionPay и выпущенные в Казахстане или Армении карты российских клиентов без дополнительных ограничений (технически должно работать как с любыми иностранными Visa/MC, но с учётом антифрода не подтверждено).
- Не найдено, как TBC контролирует эквайринговые платежи от плательщиков с российскими IP или адресами (геоблокировка, антифрод).
