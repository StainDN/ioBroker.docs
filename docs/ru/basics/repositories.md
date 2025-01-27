---
title: Что такое репозиторий?
lastChanged: 13.10.2022
translatedFrom: de
translatedWarning: Если вы хотите отредактировать этот документ, удалите поле «translationFrom», в противном случае этот документ будет снова автоматически переведен
editLink: https://github.com/ioBroker/ioBroker.docs/edit/master/docs/ru/basics/repositories.md
hash: yDArL/+U8eSwR8c0eD/00/VFVFgjGapEZFWn/L7np9U=
---
Репозиторий — это центральный репозиторий программ.

Адаптеры, которые можно просматривать и устанавливать/обновлять через административный интерфейс ioBroker, управляются через центральный репозиторий (репозиторий).
По умолчанию ioBroker настраивается после установки таким образом, что осуществляется доступ к «стабильному» репозиторию и предлагаются для установки хранящиеся там адаптеры.

В ioBroker доступны два репозитория:

- **стабильный**: в этом репозитории адаптеры доступны в уже протестированной версии, поэтому их можно использовать в продуктивной системе.
- **бета**: в этом репозитории доступны версии адаптера, которые в настоящее время находятся на стадии тестирования (!) и могут содержать несколько ошибок. Раньше бета-репозиторий назывался последним, так как назначение названия было не совсем понятно, его переименовали с последнего в бета.

?> По сути, стабильный репозиторий ***ВСЕГДА*** должен использоваться для продуктивной установки ioBroker. Репозиторий бета-версии содержит версии, которые все еще содержат ошибки и могут повлиять на всю систему.

## Выбор репозитория
Откройте основные настройки в системных настройках с помощью рожкового ключа:

![](../../de/basics/media/Repository_IconBasicSettings.png)

Желаемый репозиторий можно выбрать на вкладке Repositories:

![](../../de/basics/media/Repository_BasicsSettingsDefaultPath.png)

Пути по умолчанию для стабильного и бета-репозиториев:

- стабильная версия - ссылка на репозиторий http://download.iobroker.net/sources-dist.json
- бета - Ссылка на репозиторий http://download.iobroker.net/sources-dist-latest.json

Если был выбран бета-репозиторий, в обзоре адаптера появится соответствующее предупреждение:

![](../../de/basics/media/Repository_AdapterRepInfo.png)

## Что делать, если мне когда-нибудь понадобится адаптер из бета-репозитория?
Раньше это означало переключение репозитория со стабильного на бета-версию в ioBroker, установку одного адаптера, а затем обратное переключение. Последние обычно отходили на второй план.

Начиная с Админа 5 это гораздо удобнее БЕЗ смены репозитория!

- Активировать экспертный режим
- В меню «Адаптер» перейдите к кнопке «Установить с собственного URL» (GitHub) и перейдите на первую вкладку «Из NPM».
- В поле "Выбор адаптера" теперь можно ввести/выбрать нужный адаптер, который необходимо установить

Таким образом, можно установить последнюю бета-версию, не переключая репозиторий.

![](../../de/basics/media/Repository_AdapterInstallNpm.png)

## Как адаптер попадает в бета-версию или стабильный репозиторий?
Задолго до того, как адаптер будет готов к установке в ioBroker через интерфейс администратора, разработчик подает заявку на включение в репозиторий. Когда это происходит, опытные разработчики просматривают исходный код нового адаптера и сообщают запрашивающему разработчику, какие элементы необходимо обработать, прежде чем новый адаптер можно будет включить в репозиторий.

Новый адаптер сначала доступен в бета-репозитории, а затем может быть тщательно протестирован (бета-тестерами). Когда фаза тестирования будет завершена и обнаруженные ошибки будут исправлены, версия адаптера будет доступна в стабильном репозитории.

После изменения функции адаптера он обычно снова становится доступным только в бета-репозитории для тестирования, пока версия не будет выпущена для стабильного репозитория после завершения фазы тестирования.