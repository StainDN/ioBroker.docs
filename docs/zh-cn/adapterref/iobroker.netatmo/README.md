---
translatedFrom: en
translatedWarning: 如果您想编辑此文档，请删除“translatedFrom”字段，否则此文档将再次自动翻译
editLink: https://github.com/ioBroker/ioBroker.docs/edit/master/docs/zh-cn/adapterref/iobroker.netatmo/README.md
title: ioBroker.netatmo
hash: VmfYceI3tFL2ZaSlWXVhBiFFSN/IIsAiy6z2xNBwESU=
---
![标识](../../../en/adapterref/iobroker.netatmo/admin/netatmo.png)

![安装数量](http://iobroker.live/badges/netatmo-stable.svg)
![NPM 版本](http://img.shields.io/npm/v/iobroker.netatmo.svg)
![下载](https://img.shields.io/npm/dm/iobroker.netatmo.svg)

# IoBroker.netatmo
![测试和发布](https://github.com/PArns/iobroker.netatmo/workflows/Test%20and%20Release/badge.svg)[![翻译状态](https://weblate.iobroker.net/widgets/adapters/-/netatmo/svg-badge.svg)](https://weblate.iobroker.net/engage/adapters/?utm_source=widget)

**此适配器使用 Sentry 库自动向开发人员报告异常和代码错误。**有关更多详细信息以及如何禁用错误报告的信息，请参阅[Sentry 插件文档](https://github.com/ioBroker/plugin-sentry#plugin-sentry)！从 js-controller 3.0 开始使用哨兵报告。

ioBroker 的 Netatmo 适配器

## __2022 年 10 月身份验证更改的重要说明__
根据 Netatmo 的说法，通过将用户名和密码直接输入适配器来进行身份验证的“旧”方式将在 2022 年 10 月被禁用。

2.0 版的适配器解决了这一变化并调整了身份验证。 2022 年 10 月之前的所有升级都应该允许在首次启动时自动无缝升级到 2.0.0 - 否则需要新的身份验证。

## __v2.0.0 的重要说明！__
使用适配器的 v 2.0，对象结构将完全改变！我们决定更好地使用唯一 ID 而不是名称，以确保重复或更改名称不会产生问题。

## 安装和配置
您需要使用 Adapter Admin UI 对您的 NetAtmo 帐户进行身份验证。

首先选择您要为其同步数据的所有相关设备类型。当您更改它们时，您需要稍后再次进行身份验证。

如果您想使用专用的客户端 ID/秘密（见下文），您也可以在身份验证之前输入它们。

使用“使用 Netatmo 进行身份验证”按钮启动身份验证流程。 Netatmo 登录页面将打开一个新的 Windows/选项卡。登录并确认数据访问后，您将被重定向回您的管理页面。

如果成功，只需关闭窗口并重新加载适配器配置。如果出现错误，请检查错误消息并重试

默认情况下，通用 API 密钥用于执行将更新间隔限制为 10 分钟的请求！

要增加间隔或从 Welcome & Presence 获取实时更新，您只需在 NetAtmo 应用程序中输入自己的 ID/秘密。
为此，请转到以下 URL，使用您的 Netatmo 帐户登录并在 https://auth.netatmo.com/access/login?next_url=https%3A%2F%2Fdev.netatmo.com% 上填写请求的表格2Fapps%2Fcreateanapp ！

请确保配置他们尊重 https://dev.netatmo.com/guideline#rate-limits 的限制（请记住，如果您不使用自己的 ID/秘密，所有用户也存在这些限制）

##发送到支持
### SetAway
您还可以使用 sendTo 命令将所有人设置为远离（例如，如果用作警报系统）

```
sendTo('netatmo.0', "setAway", {homeId: '1234567890abcdefg'});
```

或者

```
sendTo('netatmo.0', "setAway");
```

将所有人标记为离开所有摄像机

也可以将一个或多个特定的人标记为离开

```
sendTo('netatmo.0', "setAway", {homeId: '1234567890abcdefg', personsId: ['123123123123123']});
```

参数 homeId 是“对象”选项卡中摄像机名称后面列出的字符串（可选，如果安装了多个摄像机），personId 是“已知”人员文件夹中的 id

＃＃＃ 设为首页
基本上与上述“setAway”描述的功能相同，“setHome”也存在将人员或整个住宅设置为“占用”。

<!-- 下一个版本的占位符（在行首）：

### __工作进行中__ -->

## Changelog
### 2.1.1 (2022-09-30)
* (Apollon77) Make sure device types that require custom credentials are not selectable in UI without entering them
* (Apollon77) Fix a potential crash case

### 2.1.0 (2022-09-23)
* (Apollon77) Fix setAway
* (Apollon77) Adjust setAway/setHome message responses to return all errors/responses when multiple calls where done for multiple homes or persons

### 2.0.5 (2022-09-16)
* (Apollon77) Catch communication errors better

### 2.0.4 (2022-09-15)
* (Apollon77) Fix crash case with Smoke detector events

### 2.0.3 (2022-09-14)
* (Apollon77) Fixes and Optimizations for Doorbell devices

### 2.0.2 (2022-09-12)
IMPORTANT: This Adapter requires Admin 6.2.14+ to be configured!
* BREAKING: Object structure changes completely and now uses unique IDs instead of names!
* (Apollon77) Change the Authentication method as requested by Netatmo till October 2022
* (Apollon77) Doorbell integration
* (Apollon77) Converted to new APIs, values of several objects might be different
* (Apollon77) Fix crash cases reported by Sentry
* (Apollon77) Adjust setAway to the current API
* (Apollon77) Added setHome function (Welcome only) to mark all or specific persons as home (requires your own API key!)
* (Apollon77) setAway and setHome now also return the result of the call as callback tzo the message
* (Apollon77) Allow to edit floodlight and monitoring-state

### 1.7.1 (2022-03-30)
* (Apollon77) Fix Event cleanup

### 1.7.0 (2022-03-24)
* IMPORTANT: js-controller 3.3.19 is needed at least!
* (Apollon77) Activate events again (manually delete objects once if you get type errors)
* (Apollon77) Adjust some roles and written data to prevent warnings in logs

### 1.6.0 (2022-03-13)
* (Apollon77) Important: In person names (Welcome) in state IDs forbidden characters are now replaces by _!!
* (Apollon77) Fix another potential crash case reported by sentry

### 1.5.1 (2022-03-09)
* (Apollon77) Fix jsonconfig for Client secret

### 1.5.0 (2022-03-08)
* (kyuka-dom) Added support for netatmo carbon monoxide sensor.
* (kyuka-dom) Added support for netatmo smoke alarm.
* (foxriver76) prevent crashes if application limit reached
* (Apollon77) Allow to specify own id/secret in all cases
* (Apollon77/foxriver76) ensure that minimum polling interval of 10 minutes is respected if no individual ID/Secret is provided
* (Apollon77) Several pother fixes and optimizations
* (Apollon77) Add Sentry for crash reporting

### 1.4.4 (2021-07-21)
* (Apollon77) Fix typo that lead to a crash

### 1.4.3 (2021-06-27)
* (Apollon77) Fix typo to fix crash

### 1.4.2 (2021-06-27)
* (bluefox) Removed warnings about the type of states

### 1.4.0 (2021-06-24)
* (bluefox) Added the support of admin5 
* (bluefox) Removed warnings about the type of states

### 1.3.3
* (PArns) removed person history

### 1.3.2
* (PArns) Updated libs & merged pending patches
* (PArns) Changed update interval from 5 to 10 minutes (requested by Netatmo)

### 1.3.1
* (PArns) Fixed event cleanup crash

### 1.3.0
* (HMeyer) Added Netatmo Coach

### 1.2.2
* (PArns) Updated meta info

### 1.2.0
* (PArns) Fixed camera picture for events
* (PArns) Added camera vignette for events
* (PArns) Added camera video for events
* (PArns) Added new sub event type (human, vehicle, animal, unknown)
* (PArns) Added LastEventID within the LastEventData section

### 1.1.7
* (PArns) Added missing lib dependencies

### 1.1.6
* (PArns) Removed GIT requirement and included netatmo lib directly

### 1.1.5
* (PArns) Removed 502 error output if API has backend problems

### 1.1.4
* (PArns) Added support for unnamed modules

### 1.1.1
* (PArns) Simplified setAway

### 1.1.0
* (PArns) Added setAway function (Welcome only) to mark all or specific persons as away (requires your own API key!)

### 1.0.1
* (PArns) Fixed scope problems for presence & welcome (requires your own API key!)

### 1.0.0
* (PArns) Added live camera picture & stream for presence & welcome
* (PArns) Fixed known & unknown face image url for presence & welcome

### 0.6.2
* (PArns) Added name of last seen known face

### 0.6.1
* (PArns) Changed realtime server to use new general realtime server
* (PArns) Changed enums to channels to avoid enum creation
* (PArns) Simplified detection for movement-, known- & unknown- face events

### 0.6.0
* (PArns) Rewritten realtime updates to not need a local server any longer! Realtime updates are now turned on by default if a Welcome or Present cam is available

### 0.5.1
* (PArns) Optimized realtime updates to avoid updates if only movement was detected

### 0.5.0
* (PArns) Added realtime events for Netatmo Welcome

### 0.4.1
* (PArns) Removed log warnings for Wind sensor

### 0.4.0
* (PArns) Added absolute humidity
* (PArns) Added dewpoint

### 0.3.1
* (PArns) Reuse of preconfigured OAuth Client data
* (PArns) Added backward compatibility with existing installations

### 0.3.0
* (wep4you) Initial implementation of Netatmo welcome camera

### 0.2.2
* (PArns) Fixed SumRain24MaxDate & SumRain24Max which won't update in some rare cases

### 0.2.1
* (PArns) Corrected DateTime values & object types

### 0.2.0
* (PArns) Added SumRain1Max/SumRain1MaxDate & SumRain24Max/SumRain24MaxDate to get overall rain max since adapter installation

### 0.1.1
* (PArns) Fixed TemperatureAbsoluteMin/TemperatureAbsoluteMax

### 0.1.0
* (PArns) Fixed CO2 calibrating status
* (PArns) Added last update for devices
* (PArns) Added TemperatureAbsoluteMin/TemperatureAbsoluteMax to get overall temperature min/max since adapter installation

### 0.0.4
* (PArns) Fixed typo/missing parameter in GustStrength

### 0.0.3
* (PArns) Added error handling to prevent exceptions for missing parameters

### 0.0.2
* (PArns) Fixed rain sensor

### 0.0.1
* (PArns) Initial release

## License
MIT

Copyright (c) 2016-2022 Patrick Arns <iobroker@patrick-arns.de>