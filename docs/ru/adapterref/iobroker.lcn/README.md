---
translatedFrom: en
translatedWarning: Если вы хотите отредактировать этот документ, удалите поле «translationFrom», в противном случае этот документ будет снова автоматически переведен
editLink: https://github.com/ioBroker/ioBroker.docs/edit/master/docs/ru/adapterref/iobroker.lcn/README.md
title: ioBroker.lcn
hash: uBMIxrsosNK2id39fZal584VZWlG8tHiVJdBTw5/xDM=
---
![Логотип](../../../en/adapterref/iobroker.lcn/admin/lcn.png)

![версия NPM](http://img.shields.io/npm/v/iobroker.lcn.svg)
![Загрузки](https://img.shields.io/npm/dm/iobroker.lcn.svg)
![НПМ](https://nodei.co/npm/iobroker.lcn.png?downloads=true)

# IoBroker.lcn
Этот адаптер позволяет подключить Локальную сеть управления [LCN](https://www.lcn.eu/) к ioBroker.

## Поддерживаемые шлюзы
- ЛКН-ПКЕ

![пке](../../../en/adapterref/iobroker.lcn/img/lcn-pke.png)

- ЛЦН-ПКУ с ЛЦН-ПЧК

![пке](../../../en/adapterref/iobroker.lcn/img/lcn-pku.png)

**Не забывайте, что ioBroker.lcn заблокирует одну лицензию на подключение LCN.**

Конфигурация и модули будут автоматически обнаружены при сканировании, которое должно быть запущено вручную из диалогового окна конфигурации и может быть повторено в любое время снова.

## Типы
Поддерживаются следующие группы чтения и записи:

- Аналоговые значения (выход/вход)
- Реле (выход)
- Датчики (вход)
- светодиоды (выход/вход)
- Переменные (вход)

## Переменные
Чтобы применить допустимые функции преобразования к переменным, переменные должны иметь допустимые роли. Поддерживаются следующие роли:

- **value.temperature** - температура в градусах Цельсия
- **value.brightness** - Люкс (I-вход) в люксах
- **value.speed.wind** - скорость ветра в м/с
- **value.voltage** - напряжение в вольтах
- **value.current** - ток в амперах
- **value.sun.azimuth** - азимут солнца
- **value.sun.elevation** - высота солнца

## Отображать
Для каждого устройства вы можете активировать, есть ли у него дисплей или нет.

## Регулятор (Реглер)
Для каждого устройства вы можете активировать независимо от того, есть у него регуляторы или нет.

## Настройки
- Интервал повторного подключения (сек) - как часто адаптеры пытаются подключиться. По умолчанию каждые 30 секунд.
- Время ожидания подключения (мс) - как долго адаптер ожидает ответа на подключение, включая аутентификацию. По умолчанию 6 секунд.
- Scan response timeout(ms) - сколько времени адаптер ожидает ответов при сканировании модулей.
- Response timeout(ms) - таймаут для управляющих команд
- Интервал пинга (сек) - как часто адаптер отправляет пинг-запросы
- Тайм-аут ответа на пинг (мс) - тайм-аут для пинг-запросов
- Реле IN/OUT одинаковые - если реле "out" и "in" одно и то же или эти реле разные.

```
// =====================  Same relays =============================
//                                    +-------+
// ----------------- OUT -----------> |       |
//                                    | Relay |
// <----------------- IN ------------ |       |
//                                    +-------+
//
//
// ======================  Different relays =======================
//                                    +-------+
//                                    |       |
// ----------------- OUT -----------> | Relay |
//                                    |       |
//                                    +-------+
//
//                                    +--------+
//                                    | Sensor |
// <----------------- IN ------------ |   or   |
//                                    | Relay  |
//                                    +--------+
```

## Как использовать
После первого запуска устройства должны быть просканированы. Это можно сделать в диалоговом окне конфигурации с помощью кнопки сканирования.

![сканирование](../../../en/adapterref/iobroker.lcn/img/scanButton.png)

## Сделать
- Диалоговое окно конфигурации для определения типа переменных.

<!-- Заполнитель для следующей версии (в начале строки):

### **В РАБОТЕ** -->

## Changelog
### 1.1.1 (2022-10-19)
* (bluefox) Corrected license check

### 1.1.0 (2022-10-18)
* (bluefox) Corrected issue with password

### 1.0.4 (2021-05-21)
* (bluefox) Ack will be ignored for the display commands

### 1.0.3 (2021-05-21)
* (bluefox) Changed the calculation of the temperature variables

### 1.0.2 (2020-10-11)
* (bluefox) Implemented the regulators and the display support.

### 0.6.3 (2019-12-18)
* (bluefox) General relays mode implemented

### 0.6.2 (2019-12-07)
* (bluefox) Detected delayed responses
* (bluefox) Dynamical creation of states is implemented

### 0.5.5 (2019-12-05)
* (bluefox) Relay inputs were corrected

### 0.5.4 (2019-12-04)
* (bluefox) Connection indication was corrected

### 0.5.1 (2019-11-29)
* (bluefox) Finger scanner supported
* (bluefox) Added possibility to set the analog mode
* (bluefox) Relay outputs are supported now

### 0.4.4 (2019-11-26)
* (bluefox) Fixed error by parsing of acknowledgement

### 0.4.2 (2019-06-12)
* (bluefox) Support of old measure values was added

### 0.3.2 (2018-11-19)
* (bluefox) add variables support

### 0.2.1
* (bluefox) initial release

## License
CC-BY-NC-4.0

Copyright (c) 2018-2022 bluefox <dogafox@gmail.com>

Up to 10 devices can be connected for free. If you need more devices, you must buy a commercial license.