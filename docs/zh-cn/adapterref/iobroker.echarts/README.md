---
translatedFrom: en
translatedWarning: 如果您想编辑此文档，请删除“translatedFrom”字段，否则此文档将再次自动翻译
editLink: https://github.com/ioBroker/ioBroker.docs/edit/master/docs/zh-cn/adapterref/iobroker.echarts/README.md
title: ioBroker.echarts
hash: k+wb/Y8bMxvy/eqo6X/6kaLqYCBO1FxqP3qh5TipVCk=
---
![标识](../../../en/adapterref/iobroker.echarts/admin/echarts.png)

![安装数量](http://iobroker.live/badges/echarts-stable.svg)
![NPM 版本](http://img.shields.io/npm/v/iobroker.echarts.svg)
![下载](https://img.shields.io/npm/dm/iobroker.echarts.svg)

# IoBroker.echarts
![测试和发布](https://github.com/ioBroker/ioBroker.echarts/workflows/Test%20and%20Release/badge.svg)[![翻译状态](https://weblate.iobroker.net/widgets/adapters/-/echarts/svg-badge.svg)](https://weblate.iobroker.net/engage/adapters/?utm_source=widget)

**此适配器使用 Sentry 库自动向开发人员报告异常和代码错误。**有关更多详细信息以及如何禁用错误报告的信息，请参阅[Sentry 插件文档](https://github.com/ioBroker/plugin-sentry#plugin-sentry)！

## 用于 ioBroker 的 echarts 适配器
在 ioBroker 中构建有用的图表：

![截屏](../../../en/adapterref/iobroker.echarts/img/screenshot1.png)

＃＃ 用法
重启后在后台添加选项卡：![行政](../../../en/adapterref/iobroker.echarts/img/admin.png)

创建的预设也可以在网络适配器中访问。网址：`http://IP:8082/echarts/index.html?preset=echarts.0.PRESETID`。

对于 vis，有一个特殊的小部件，可以轻松选择预设。

### 工具提示
小写 `i` 表示该值是从 2 个相邻值中插入的，并且在此时间戳中不存在。

![工具提示](../../../en/adapterref/iobroker.echarts/img/tooltip.png)

### 服务器端渲染
您可以在服务器上呈现预设并将其作为 base64 URL 获取或将其保存在 ioBroker DB 的磁盘上：

```
sendTo('echarts.0', {
    preset:   'echarts.0.myPreset', // the only mandatory attribute

    renderer: 'svg',                // svg | png | jpg | pdf, default: svg

    width: 1024,                    // default 1024
    height: 300,                    // default 300
    background: '#000000',          // Background color
    theme: 'light',                 // Theme type: 'light', 'dark'

    title: 'ioBroker Chart',        // Title of PDF document
    quality: 0.8,                   // quality of JPG
    compressionLevel: 3,            // Compression level of PNG
    filters: 8,                     // Filters of PNG (Bit combination https://github.com/Automattic/node-canvas/blob/master/types/index.d.ts#L10)

    fileOnDisk: '',                 // Path on disk to save the file.
    fileName: '',                   // Path in ioBroker DB to save the files on 'echarts.0'. E.g. if your set "chart.svg", so you can access your picture via http(s)://ip:8082/echarts.0/chart.png
}, result => {
    if (result.error) {
        console.error(result.error);
    } else {
        console.log(result.data);
    }
});
```

**注意：您不能在启用缩放的触摸设备上启用/禁用图例中的线条**

## 开发者手册
**对于非开发人员，此链接无效！**

您可以使用以下方法在本地调试视图图表：

- cd iobroker.echarts/src-chart
- npm 运行开始
- 浏览器：http://localhost:8081/adapter/echarts/tab.html?dev=true

＃＃ 去做
- 可见小部件（按钮）
- 材料小部件
- 在文件夹或附近显示枚举图标

<!-- 下一个版本的占位符（在行首）：

### **正在进行中** -->

## Changelog
### **WORK IN PROGRESS**
* (bluefox) Added background to export image

### 1.0.5 (2022-02-16)
* (bluefox) Added "i" in tooltips by interpolated values

### 1.0.4 (2022-01-31)
* (bluefox) License changed to Apache-2.0 (because of apache/echarts)
* (bluefox) Updated some packages
* (bluefox) Added fast properties editor

### 1.0.3 (2021-07-21)
* (bluefox) Fixed server-side rendering

### 1.0.2 (2021-07-20)
* (bluefox) Fixed the communication with admin4

### 1.0.1 (2021-07-14)
* (bluefox) Fixed the "no background" option

### 1.0.0 (2021-07-02)
* (bluefox) Fixed many bugs

### 0.4.14 (2021-04-29)
* (bluefox) Fixed reorder of presets

### 0.4.13 (2021-03-27)
* (bluefox) Tried to sort the time series before displaying it

### 0.4.12 (2021-03-27)
* (bluefox) Added the support of parameters in URL

### 0.4.11 (2021-02-06)
* (bluefox) Fixed the dashed lines

### 0.4.10 (2020-12-22)
* (bluefox) Allow the hiding of lines at start and show them via legend later
* (bluefox) Use canvas renderer on touch devices to allow zoom and pan

### 0.4.9 (2020-12-21)
* (bluefox) Updated echarts to 5.0
* (bluefox) Implemented copy&paste of lines and markings
* (bluefox) Available vertical legend
* (bluefox) Allowed the hiding the interpolated values in tooltip

### 0.4.7 (2020-12-13)
* (bluefox) Updated the select ID dialog

### 0.4.6 (2020-12-12)
* (bluefox) Allowed the same names in different folders

### 0.4.5 (2020-12-11)
* (bluefox) Some sentry errors were corrected.
* (bluefox) Added the possibility to show actual values in legend.

### 0.4.4 (2020-12-07)
* (bluefox) Some sentry errors were corrected.

### 0.4.2 (2020-11-29)
* (bluefox) Corrected the error with overflow of axis.

### 0.4.1 (2020-11-29)
* (bluefox) Disconnection errors are caught now.

### 0.4.0 (2020-11-28)
* (bluefox) Added new option: no background

### 0.3.9 (2020-11-28)
* (bluefox) Corrected error with the chart.

### 0.3.8 (2020-11-27)
* (bluefox) Implemented the conversion of the flot presets into echarts.

### 0.3.7 (2020-11-17)
* (bluefox) Hide nulls in hover details

### 0.3.6 (2020-11-13)
* (bluefox) The copy of charts is implemented

### 0.3.5 (2020-11-10)
* (bluefox) Corrected SENTRY errors

### 0.3.4 (2020-11-08)
* (bluefox) Corrected server-side rendering of PNG

### 0.3.1 (2020-10-31)
* (bluefox) Added the color of export button 
* (bluefox) The interpolated values are shown now
* (bluefox) Server-side rendering is implemented

### 0.2.1 (2020-10-25)
* (bluefox) GUI fixes

### 0.2.0 (2020-10-22)
* (bluefox) Implemented the grouping by the category.

### 0.1.2 (2020-10-21)
* (bluefox) Added support of multiple charts

### 0.1.1 (2020-10-21)
* (bluefox) initial release

## License
ioBroker.echarts is available under the Apache License V2.

Copyright (c) 2019-2022 bluefox <dogafox@gmail.com>

Apache ECharts
Copyright (c) 2017-2022 The Apache Software Foundation

This product includes software developed at
The Apache Software Foundation (https://www.apache.org/).