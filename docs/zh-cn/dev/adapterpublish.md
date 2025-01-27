---
title: 发布
lastChanged: 21.01.2020
editLink: https://github.com/ioBroker/ioBroker.docs/edit/master/docs/zh-cn/dev/adapterpublish.md
translatedFrom: de
translatedWarning: 如果您想编辑此文档，请删除“translatedFrom”字段，否则此文档将再次自动翻译
hash: I0FIhrW7GjK+oU9/a+Snt1/LZjxE7xtbGDLoF8Lr2VE=
---
# 发布适配器
在您考虑发布适配器之前，应在 [论坛测试帖](https://forum.iobroker.net/category/91/tester) 中将其提供给测试。
如果测试成功并且适配器运行稳定，则应该暂时包含在最新的仓库中。

如果适配器在特定版本号上稳定运行，欢迎您将其转移到稳定存储库。这需要开发人员结合用户反馈进行自己的评估。

***在此处查看其他当前要求：*** https://github.com/ioBroker/ioBroker.repositories/blob/master/README.md

## 最新存储库的要求
0. 使用 [https://adapter-check.iobroker.in/](https://adapter-check.iobroker.in/) 测试适配器 repo。

1. 适配器的 Github 仓库在 ioBroker 中应该有一个大写的 B，而在 package.json 中它必须是小写，因为 ``npm`` 不允许大写字母。

2. io-package.json 中的标题不应包含“ioBroker”或“Adapter”。

3、io-package.json中的``title``属性（常用）是适配器的英文简称。而 ``titleLang`` 包含 ``title`` 属性的翻译。 （Lang 扩展代表语言）

4. 适配器应包含 README.md 文件形式的指令。这应该至少有英文版本。也欢迎其他语言。这个[示例]（https://github.com/foxriver76/ioBroker.denon）可以作为一个建议。

5. 适配器需要许可证。在 io-package.json 和 Github 存储库中的一个单独的 [file](https://github.com/foxriver76/ioBroker.denon/blob/master/LICENSE) 中。

   示例 io-package.json：

```json
{
  "common": {
      "license": "MIT"
  }
}
```

6. `www` 目录和`widget` 目录如果不使用应删除。

7. 在 io-package.json 中，应该在 common 下创建一个 `type` 属性。为此，应从此 [列表]（#adapter 类别）中指定最佳匹配类别。

8. 在 io-package.json 中，`connectionType` 和 `dataSource` 属性应该在 common 下创建。为此，应从此 [列表]（#adapter 连接类型）中指定最合适的连接类别。

9. 适配器创建的状态在 common 下应该有其“角色”的有效规范。

应避免使用角色`state`。

10. 适配器应该同时使用模板中指定的测试。为此，可以将 Github 帐户链接到 Appveyor（Windows 测试）和 Travis CI（Linux 和 Mac OS 测试），并且可以注册相应的存储库进行测试。

这两个持续集成工具已被证明适用于 ioBroker 项目，并且可免费用于公共 Github 存储库。

开发人员可以扩展测试范围。

11. 在 io-package.json 中，必须在 common 下为 `authors` 属性创建至少一个条目。

package.json中的属性`author`也必须填写。
或者，也可以使用 package.json 中的 `contributors` 属性为 npm 存储多个作者。

12. 适配器必须以 npm 包的形式提供。可以在 [这里](https://github.com/ioBroker/ioBroker.repositories#how-to-publish-on-npm) 找到更多信息。

13、需要在npm上添加ioBroker组织。这对于允许长期维护包是必要的，即使开发人员由于时间或其他原因不再能够维护包。

更多信息可以在[这里](https://github.com/ioBroker/ioBroker.repositories#add-owner-to-packet)中找到。

## 稳定的存储库要求
1.适配器已成功添加到最新存储库
2. 已经给出用户反馈的适配器有一个[论坛测试线程](https://forum.iobroker.net/viewforum.php?f=36)。
3. 应实现发现功能。这是 [Discovery Adapter](https://github.com/ioBroker/ioBroker.discovery) 中的一个功能，

自动检测用户是否可以使用适配器的实例。
为此，必须将拉取请求提交到 [发现适配器](https://github.com/ioBroker/ioBroker.discovery) 存储库。

## 将适配器添加到官方仓库
1. 应访问 [官方 Github 存储库](https://github.com/ioBroker/ioBroker.repositories) 并使用以下内容发出拉取请求，具体取决于存储库。

2. 请在现有适配器之间按字母顺序正确排列适配器。

3.当包含在稳定库中时，必须声明版本号。这必须在适配器进一步开发时更新。

4. 适配器应该在 io-package.json 中设置一个列表属性 `docs` 指示在哪里可以找到相应语言的指令。

语言被指定为键，markdown 文件的路径被指定为值。
英文手册是强制性的（在紧急情况下，可以参考标准 README）。德语说明也是可取的，因为大多数用户会说德语，但这是可选的。
详细的说明可以为开发者节省大量的论坛时间。
可以在[这里](https://github.com/foxriver76/ioBroker.denon/blob/master/docs/de/README.md)中找到一个示例。

   例子：

```json
{
  "common": {
     "docs": {
         "de": "docs/de/README.md"
     }
  }
}
```

＃＃＃ 最新的
`sources-dist.json`文件必须编辑：

例子：

```json
  "admin": {
    "meta": "https://raw.githubusercontent.com/ioBroker/ioBroker.admin/master/io-package.json",
    "icon": "https://raw.githubusercontent.com/ioBroker/ioBroker.admin/master/admin/admin.png",
    "published": "2017-04-10T17:10:21.690Z",
    "type": "general"
  }
```

`published` 日期表示首次发布的日期，不应更改。

＃＃＃ 稳定的
`sources-dist-stable.json`文件必须编辑：

例子：

```json
  "admin": {
    "meta": "https://raw.githubusercontent.com/ioBroker/ioBroker.admin/master/io-package.json",
    "icon": "https://raw.githubusercontent.com/ioBroker/ioBroker.admin/master/admin/admin.png",
    "version": "2.0.7",
    "published": "2017-04-10T17:10:21.690Z",
    "type": "general"
  }
```

`published` 日期表示首次发布的日期，不应更改。

## 适配器版本管理
在 io-package.json 和 package.json 中都指定了适配器的当前版本号。
这两个细节必须匹配。版本号由两个点分隔为三个部分。

```json
"version": "1.7.6"
```

第一部分（从左到右）代表`Major Part`，第二部分是`minor`部分，最后一部分是`micro`部分。
版本号应根据以下列表递增：

- **micro**：仅修复了错误
- **次要**：已添加功能，但版本与以前的版本兼容
- **major**：重大更改，这意味着不再提供与旧版本的向后兼容性

`news` 属性也应该在 io-package.json 中维护。
这允许用户从管理界面安装列出的任何版本（假设它已发布到 npm）。
版本号和更改应存储在这里。
可以为每种支持的语言记录更改，其中至少应以英语指定这些更改。

例子：

```json
"news": {
    "1.7.6": {
        "en": "Configuration dialog was corrected",
        "de": "Konfigurationsdialog wurde korrigiert",
        "ru": "Диалог конфигурации был исправлен",
        "pt": "A caixa de diálogo de configuração foi corrigida",
        "nl": "Configuratiedialoog is gecorrigeerd",
        "fr": "La boîte de dialogue de configuration a été corrigée",
        "it": "La finestra di configurazione è stata corretta",
        "es": "Se corrigió el diálogo de configuración",
        "pl": "Okno dialogowe konfiguracji zostało poprawione"
    },
    "1.7.5": {
        "en": "The roles were tuned",
        "de": "Die Rollen waren abgestimmt",
        "ru": "Роли были настроены",
        "pt": "Os papéis foram afinados",
        "nl": "De rollen zijn afgestemd",
        "fr": "Les rôles ont été réglés",
        "it": "I ruoli erano sintonizzati",
        "es": "Los roles fueron sintonizados",
        "pl": "Role zostały dostrojone"
    }
}
```

## 适配器类别
- `警报` - 安全系统
- `climate-control` - 空调、空气过滤器、加热器等
- `communication` - 为其他适配器提供数据，例如B. 通过 REST
- `日期和时间` - 例如B. 日历
- `能源` - 电流监测、太阳能系统、逆变器等等。
- `计量` - 其他测量系统（例如水、气、油）
- `花园` - 例如B. 割草机、洒水系统
- `general` - 通用适配器，如 Admin、Web、Discovery
- `geoposition` - 物体或人的地理位置
- `hardware` - 不同的多功能硬件，如 Arduino、ESP、蓝牙、...
- `健康` - 血压，心率，体重，...
- `家庭` - 厨房用具、吸尘器等。
- `基础设施` - 网络、NAS、打印机、电话
- `iot-systems` - 其他智能家居系统（硬件和软件）
- `照明` - 照明
- `logic` - 规则、脚本、解析器等。
- `messaging` - 用于发送和接收消息的适配器，例如例如，通过电子邮件、电报、...
- `misc-data` - 数据的导出和导入、货币转换器等。
- `多媒体` - 电视、AVR、盒子、语音助手等。
- `network` - ping，网络发现，UPnP，...
- `protocols` - 通信协议，例如B.MQTT
- `storage` - 记录，数据管理，例如B. 关系数据库，...
- `utility` - 支持适配器，例如B. 备份
- `车辆` - 汽车
- `visualization` - 可视化适配器，如 vis 等。
- `visualization-icons` - 可视化图标
- `visualization-widgets` - iobroker.vis 小部件
- `weather` - 天气信息、空气质量、环境信息

##适配器连接类型
在`io-package.json`的`common`部分中将`connectionType`定义为：

- `local` - 提供与设备或集线器的直接通信。
- `cloud` - 此设备通过云集成，需要有效的互联网连接

将`common`中的`dataSource`定义为：

- `poll` - 轮询状态意味着稍后可能会注意到更新。
- `push` - 一旦有新状态可用，ioBroker 就会收到通知。
- `假设` - 无法确定设备的状态。 ioBroker 根据上一个 ioBroker 命令获取状态。