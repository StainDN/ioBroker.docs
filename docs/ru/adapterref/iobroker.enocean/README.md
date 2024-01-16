---
translatedFrom: en
translatedWarning: Если вы хотите отредактировать этот документ, удалите поле «translationFrom», в противном случае этот документ будет снова автоматически переведен
editLink: https://github.com/ioBroker/ioBroker.docs/edit/master/docs/ru/adapterref/iobroker.enocean/README.md
title: ioBroker.enocean
hash: QNO0R0DvCAiSzcWKddNvcZ3euDr4iYeTUY5RiEwTInw=
---
![Логотип](../../../en/adapterref/iobroker.enocean/admin/enocean.png)

![версия NPM](http://img.shields.io/npm/v/iobroker.enocean.svg)
![Загрузки](https://img.shields.io/npm/dm/iobroker.enocean.svg)
![Количество установок (последние)](http://iobroker.live/badges/enocean-installed.svg)
![Количество установок (стабильно)](http://iobroker.live/badges/enocean-stable.svg)
![Статус зависимости](https://img.shields.io/david/jey-cee/iobroker.enocean.svg)
![НПМ](https://nodei.co/npm/iobroker.enocean.png?downloads=true)
![Трэвис-CI](http://img.shields.io/travis/jey-cee/ioBroker.enocean/master.svg)

# IoBroker.enocean
## Адаптер EnOcean для ioBroker
Подключает устройства EnOcean через USB/последовательные устройства с чипами TCM300.

## Присоединяйтесь к серверу Discord, чтобы обсудить все об интеграции ioBroker-enocean!
<a href="https://discord.gg/4EBGwBE"><img src="https://discordapp.com/api/guilds/743167951875604501/widget.png?style=banner2" width="25%"></a>

## [Спонсоры](./SPONSORS.md)
Если вам нравится моя работа, пожалуйста, сделайте личное пожертвование (это личная ссылка для пожертвований для Jey Cee, не имеющая отношения к проекту ioBroker!) [![Пожертвовать](https://raw.githubusercontent.com/iobroker-community-adapters/ioBroker.wled/master/admin/button.png)](https://www.paypal.com/cgi-bin/webscr?cmd=_s-xclick&hosted_button_id=95YZN2LR59Q64&source=url)

## Совместимые USB-накопители и модули
USB300

USB-накопитель DOSMUNG с портом SMA — [Купить](https://amzn.to/33EapbN)

FAM-USB (прошивка ESP3)

Модуль EnOcean Pi

Eltako FGW14: Вы должны включить режим ESP2 в конфигурации адаптера, чтобы использовать FGW14.
**Важные примечания**: Этот шлюз не поддерживает все функции и устройства этого адаптера. Известные функции, которые не работают: RSSI, информация о шлюзе не может быть прочитана, и только устройства шины RS485 могут управляться без FTD14 (еще не тестировалось). Если нет технических причин для использования этого шлюза, настоятельно рекомендуется использовать другой.

Шлюз ALL SMART EnOcean LAN — [КУПИТЬ](https://www.all-smart.net/produkt/all-smart-enocean-lan-gateway/)

## Устройства управления
В общем, есть объект cmd, где вы можете выбрать команду, которую хотите выполнить. Прежде чем вы сможете выполнить команду, вы должны установить все необходимые атрибуты, вы можете найти эту информацию в определении профиля.

Специальный:

* A5-20-xx: Устройства с этим профилем принимают команды только в течение 1 секунды после отправки сообщения. Присылают периодически (минут 10?), читайте инструкцию.

## Учить в
- Процесс задокументирован (краткими) пошаговыми инструкциями в конфигурации адаптера. Там вы можете выбрать

  ваше устройство и инструкции будут отображаться. Следуйте за ними.

- Устройства без возможности обучения на другом устройстве (например, Eltako Series 12, также известном как Opus Green Net):

Ими можно управлять с помощью виртуального переключателя (F6-02-02): Откройте конфигурацию и нажмите «Добавить новое устройство».
Теперь выберите X_Virtual в качестве производителя и Switch в качестве устройства, используйте идентификатор ffffffff0. Подсчитайте последний знак, 1-9 и a-f, для каждого нового виртуального коммутатора.
Нажмите добавить устройство и закрыть конфигурацию. Затем запустите обучение на своем устройстве согласно инструкции, отправьте команду с виртуального коммутатора.
Теперь вы должны иметь возможность управлять устройством.

## Teach-out (удалить привязку адаптера к устройству)
- Eltako Tipp-Funk: отправьте 3 команды обучения в течение 2 секунд с ioBroker на устройство
- Устройства с UTE: запустите Teach-in для адаптера и следуйте инструкциям устройства.
- RPS: Просто удалите объекты
- нет: просто удалить объекты

## Исправление проблем
- Устройство не реагирует на команду: Откройте объект устройства во вкладке «Объект», перейдите в «родной» и посмотрите, не зарегистрировано ли более одного EEP.

Если да, то первым должен быть тот, который будет управлять устройством.

## Файл определения профиля
#### Структура данных
***case:*** Может быть один элемент или массив, содержащий набор полей данных. В случае массива элемент привязан к условию.

***send:*** true означает, что этот набор данных является командой, которая будет отправлена на устройство.

***auto_answer:*** true означает, что эта команда будет выполнена после получения телеграммы от устройства.

***условие:*** Условие, которое должно быть истинным для обработки этого набора полей данных. В большинстве случаев условием является конкретное значение из пакета данных.

***поле данных:*** Информация о том, где в пакете данных находятся данные и как обрабатывать значение. Также есть определение объекта для ioBroker.

***поле данных -> secondArgument:*** Используется для получения вторичной информации/значения из пакета данных. Вариант использования: Единицы могут различаться по количеству, поэтому устройство отправляет единицу измерения как отдельную информацию.
Чтобы изменить единицу измерения внутри ioBroker в зависимости от отправленной информации, это необходимо знать при обработке значения.

***поле данных -> условие:*** Это может быть формула для преобразования значения. Это основано на логике JSON. Подробную информацию см. на http://jsonlogic.com/operations.html.

Пример:

```
//True or false
"==": [{"var": "value"}, 0]

//This will take the delivered value and check if it is equal to 0, if it is the state in iobroker will set to true.
```

***поле данных -> значение:*** Представляет возвращаемое значение, за исключением того, что условие является выходным значением. Значение не должно быть определено.

Пример:

```
//Temperature conversion from received data
 "+": [{
         "*": [
              { "-": [{"var": "value"}, 0] },
              0.2
            ]}, 0]

//This is a more complex looking formula.
//It is based on this one: Device Value = Multiplier * ( rawValue - Range min) + Scale min
//The Multiplier, in this case 0.2, is calculated in this way: (Scale max - Scale min) / (Range max - Range min)
```

***поле данных -> value_out:*** Представляет собой значение, которое будет отправлено на устройство. Это должно быть определено только в том случае, если требуется преобразование.

Пример:

```
//Temperature conversion from ioBroker
 "/": [{
         "+": [
              { "-": [{"var": "value"}, 0] },
              0
            ]}, 0.2]

//This is a more complex looking formula.
//It is based on this one: Device Value = ( ( rawValue - Range min) + Scale min ) / Multiplier
//The Multiplier, in this case 0.2, is calculated in this way: (Scale max - Scale min) / (Range max - Range min)
```

***datafield -> decimals:*** Определяет, сколько цифр после запятой будет отображаться.

***datafield -> unit:*** Используйте это, если Unit является переменной, в противном случае определите его в iobroker.

Пример:

```
//Choose between Watt(W) and Kilowatt(kW) depending on the unit information from the device
 "unit":{
            "if": [
              {"==":[{"var": "value2"}, 3]}, "W",
              {"==":[{"var": "value2"}, 4]}, "kW"
            ]
          }

//value2 comes from secondArgument.
```

## Определение устройства
Полная реализация устройства состоит как минимум из двух частей: записи в 'lib/definitions/devices.json' и файла EEP, который определяет объекты и способ обработки телеграммы данных.
Существуют устройства, которые используют более одного типа телеграмм данных для связи, это означает, что они имеют больше файлов EEP.
В особых случаях, таких как Eltako, в файле «packet_handler.js» определена часть, специфичная для производителя.

```
"Model name or type" : {
      "EEP": [                    //The EEP(s) that will be used for this device. First one has to be the one that controlls the device.
        "TF-13-07",
        "TF-13-06"
      ],
      "autocreate": false,         //false if the device needs additional steps for teachin
      "teachin_method": "none",    //filter for automated teachin telegrams
      "id_offset": true,           //not all devices checks if the telegram whether it is for them
      "broadcast": false,          //true if the receiver id has to be ffffffff. This is used for virtual devices like a switch.
      "help": {                    //a step by step instruction how to add the device.
        "en": {
          "1": "Enter device ID.",
          "2": "Click on 'Add Device'."
        },
        "de": {
          "1": "Geräte ID eintragen.",
          "2": "Auf 'Gerät Hinzufügen' klicken."
        }
      }
    }
```

## Для разработки
Для проверки обработки телеграммы создайте канал с именем development и в этом канале объект с именем телеграммы, тип string.

## Changelog
### 0.8.3 (2022-09-28)
* fix TTT and TT handling in TF-14-04 (Eltako FSB14 and similar)
* remove RT from TF-14-04 (Eltako FSB14 and similar)

### 0.8.2 (2022-09-25)
* Fix: Wrong or missing Base ID for gateway

### 0.8.0 (2022-09-16)
* added EIMSIG EM-USE-00 & EM-FSGE-00
* added Kieback & Peter RBW322-FTL
* added MICROPELT MVA002
* added EEP A5-14-07
* added Traveled Time & Time to travel objects to TF-14-04 (FSB14)
* added EnOcean Pi & FAM-USB (ESP3 Firmware) as choice in admin
* added translation for object names
* change teachin method for Kieback and Peter MD15-FTL-HE
* check on startup if all objects for existing devices are exists, if not create them
* fix D2-10-01 sending configuration message

### 0.7.1 (2022-07-24)
* increase timeout for response time from gateway
* change base id for dummy gateway info (effects Eltako FGW14)
* change EEP for TF-TAx5J
* update FSR61-230V (>10/14) help text
* update PSC 234 help text
* update TF61L-230V help text
* update help for Eltako FSR14-2/4x
* fix Teachin for Eltako FAFT60

### 0.7.0 (2022-05-30)
* added ELTAKO FGW14-USB as possible Gateway (Please read the notes in readme for FGW14-USB)
* added PEHA 452 FU-EBIM JR o.T.
* added EUROTRONIC Stella E
* added SIEGENIA senso secure
* added new Eltako MSC Teachin Telegram for FSR71-2x
* added state for window to F6-10-00
* updated settings page 
* fix HORA SmartDrive MX teachin
* fix A5-20-01 CMD default value string to number

### 0.6.4 (2022-02-22)
* fix split Eltako FSVA-230V & FSR61VA into to sepperate devices for control and measurement

### 0.6.3 (2022-02-07)
* added SODA S8
* added Thermokon SAB+
* added Eltako FHB, FWRB, TF-RWB, FSR61VA, FFT65B, FFT55B, FFTF65B, FTFB & FTFSB
* added Battery state to D2-06-01
* added default values to all objects
* updated Eltako FSVA-230V
* fix FJ62/12-36V DC teachin

### 0.6.2 (2022-01-08)
* fix teachin

### 0.6.1 (2022-01-08)
* added Dimplex DL 50 WE2
* added EnOcean STM 350
* added Eltako & MACO eTronic
* added Afriso CO2-Sensor
* change TF-13-03 set time to 100ms for sending cases
* change TF-13-07 add On with last value
* fix teachin which makes it hard to add new devices
* (uklatt) fix Humidity datapoint & change decimals from 2 to 1

### 0.6.0 (2021-11-22)
* (j1s2e3 / Jey-Cee) added Eltako FL62NPN-230V, FD62NPN-230V, FSSA-230V, FTAF55D/230V, FRGBW71L, FMS65ESB, FAH, FKS-SV, TF-TTB(PioTek Tracker), FLGTF55
* (j1s2e3) added virtual Window/Door contact
* use /dev/serial/by-id/xxx as path for USB device #104
* use index for sender ID. Remeber already learnd device IDs.
* seperated objects from datafields
* detect when socket connection is broken #72
* fix Teachin for Eltako devices

### 0.5.4 (2021-09-10)
* added Kessel Staufix Control
* added Thermokon SR-MDS Solar
* added Omnio WS-CH-102
* added PENTAIR Transmitter FTJP
* split datapoint PAE for D2-06-10 & 11 to EPA und PAE

### 0.5.3 (2021-08-08)
* fix context for sendData when called from packet handler
* fix teachin method
* fix ser2net reconnect

### 0.5.1 (2021-07-25)
* fix crash if no mailboxes present in controller

### 0.5.0 (2021-07-25)
* added serial over network (ser2net) capabilities
* added release script

### 0.4.0
* added Permundo PSC 234 & PSC 152 
* added Nodon Soft Button (TSB-2-2-01)
* added Eltako FFT60SB 
* added REHAU Smart Guard & Smart Guard Inline / Ontop 
* added Hoppe eHandle ConnectHome
* added SCHÜCO SenseTrack wireless
* added Smart ACK teachin procedure
* fix teach-in Nodon SDO-2-1-05
* TF-13-07 set Dimming Level to 100% with on command

### 0.3.8
* added Thermokon SR04 & SR07
* added Micropelt MVA003
* added Eltako FWG14MS & FSR61-230V KW 02/21 and newer

### 0.3.7
* added WINKHAUS FM.V.SW
* added Eltako TF-TA55DL, DSZ14
* added PHEA D 451 FU-BM, D 4511 FU-BM, D450 FU FK 
* added telegram repeater count object
* fix numbers with decimals are strings
* fix warning "Read-only state "enocean.0.gateway.lastID" has been written without ack-flag with value "xxxxxxxx""
* fix A5-20-01 remove conversion for valve position in summer mode & summer mode valve position
* fix TF-14-06

### 0.3.6
* added Eltako FMS14 (<32/19)
* added Eltako FTS14EM
* revised profiles
* fix FUD14 ON command

### 0.3.5
* added Eltako FMZ61-230V, FSR70S-230V 
* added Trio2Sys OUTDOOR -30/+50°C TEMPERATURE SENSOR 
* added Nodon Motion Sensor PIR-2-1-01 
* added Virtual Room operating panel EEP: A5-10-06 
* added Oventrop R-Tronic RT B
* change help description for eltako rs485 devices
* update FFR61-230V
* make id always lower case
* fix Eltako F4HK14

### 0.3.4
* added PHEA 451 FU-EBI PF o.T. 
* added Hora SmartDrive MX
* added Eltako FAFT60, FWZ-65A, FSVA-230V
* extended teachin description for Eltako FSB14
* fix A5-02-05 calculation
* fix A5-04-02

### 0.3.3
* add techin procedure for FSR61 to Packet_handler.js
* add ack for cmd & optionals
* added A5-14-09 
* use queue for sending message 
* changed Telefunken SES FS-EO to D2-01-08
* fix A5-04-01 calculation
* fix TF-13-10 calculation

### 0.3.2
* added possibility to request a device directly 
* added Base ID & Sender ID to configuration 
* added Eltako F4SR14-LED
* added Afriso FTM T, FTM TF & Viessmann Temperature sensor 7554507, Temperature- and humidity sensor 7554951
* added Eltako FFG7B (A5-14-09) & FFG7B (F6-10-00)
* added Micropelt MVA005
* added Eltako FKF65 & Nodon Card Switch (CCS-2-1-01)
* added Eltako FSS12-12V-DC
* added OPUS GN-BH63AP-pw
* added Thermokon SR04
* revised D2-01-0E, this effects Micro Smart Plug (MSP-2-1-11) & Plug actuator (SES FS-EO)
* fix A5-20-06
* fix TF-13-01 Windspeed, Rain, Dawn Sensor
* fix Eltako Teachin ID offset
* fix TF-13-13: removed useless fixed parameter
* small fixes
* Eltako automatic device teachin wait before send teachin telegram
* use serialport esp3 parser in getGatewayInfos
* close listener properly
* change Hoppe SecuSignal teachin procedure

### 0.3.1
* added Eltako FABH65S, FBH65, FBH65S, FHF, FTR65DSB, FTR55DSB, FTR65HB, FTR55HB, FTR65SB, FTR55SB, FTRF65HB, FTRF65SB
* added Hoppe SecuSignal Window Handle 
* added Telefunken SES FS-EO
* updated: FTA65J teachin
* changed: FWS61 teachin
* fix TF-13-12 & TF-13-10 
* fixed TF-13-03
* use sender ID instead offset

### 0.3.0
* added Eltako devices: TF61D, TF100D, FTA65D, FTA55D, TF100L, TF100SSR, FTA65L, FTA55L, TF-1FT, TF-2FT, TF-2FT55, TF-2ZT, 
  TF-2ZT55, F4PT, F4PT55, TF-4FT, TF-4FT55, TF-8FM, FUD71, FSUD-230V, FSG71/1-10V, FDG71L, FKLD61, FLD61, FL62-230V, 
  FL62NP-230V, FR62-230V, FR62NP-230V FSR61NP-230V, TF-TA55D, TF-TA65D, TF-TA55J, TF-TA65J, TF-TA55L, TF-TA65L, FTK, 
  FTKB-RW, FFKB, FTKB-gr, FAH65S, FIH65S   
* re-add virtual switch with broadcast
* added possibility to use json logic for conditions
* added send converted value
* added value out to a5-20-01
* added double response for UTE 
* added send eltako teachin response twice
* added filter telegrams in addEltakoDevices
* update FSUD-230V teachin help
* update device list in config during teachin
* fix id offset for Eltako devices
* fix teachin for eltako devices when no offset in gateway is defined
* fix teachin for Eltako FTKB-hg
* fix manaual teachin devices
* fix correct formula in EEPs
* fix name of Eltako TF100L
* fix id offset for manual teachin

### 0.2.1
* fix for UTE teachin
* double response for UTE
* fix id offset for Eltako devices
* added Eltako devices: TF61D, TF100D, FTA65D, FTA55D, TF100L, TF100SSR, FTA65L, FTA55L, TF-1FT, TF-2FT, TF-2FT55, TF-2ZT, TF-2ZT55, F4PT, F4PT55, TF-4FT, TF-4FT55, TF-8FM, FUD71, FSUD-230V, FSG71/1-10V, FDG71L, FKLD61, FLD61
* update fsud-230v teachin help

### 0.2.0
* fix calculation for temperature in A5-02-13
* added Eltako FMMS44SB
* correct formula in readme
* add commands for D2-05-00
* json-logic-js security update
* change UI for add new devices
* teachin procedure revised

### 0.1.8
* added devices Eltako FUD61NPN-230V, FRW, TF61L-230V, FTKB
* fix teachin: was not set to false

### 0.1.7
* added profiles for Eltako F4HK14, FSB14, FUD14
* fix tf-14-01

### 0.1.5
* added virtual switch
* rewrite A5-20-01
* fix profile A5-02-13

### 0.1.4
* added base id offset
* added new devices

### 0.1.3
* fix profile F6-10-00

### 0.1.2
* fix 4BS Teach-in
* added profile A510-20
* added profile TF14-02 relais contact
* fix profile D5-00-01
* fix profile A5-04-01
* fix profile TF-13-02

### 0.1.1
* fix Teach-in/out
* fix send data
* fix profile D2-05-00

### 0.1.0
* (Jey Cee) initial release

## License
MIT License

Copyright (c) 2022 Jey Cee <jey-cee@live.com>

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is**
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
SOFTWARE.