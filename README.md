# DC04U 控制台

iBasso DC04U 便携解码耳放的网页控制台。**单文件、纯前端**，通过 WebHID 直接与设备通信，
没有后端、不联网、不上传任何数据。

用支持 WebHID 的浏览器打开本仓库的 `index.html` 即可使用。

> 非官方工具。与 iBasso 无隶属关系，也未获其背书。设备固件与商标归原厂所有。

## 快速开始

1. 下载 `index.html`（或 clone 本仓库），用 **Chrome / Edge 89+** 打开；
2. 用数据线把 DC04U 接到电脑（纯充电线不行，必须走 USB 数据通道）；
3. 页面右上角会请求 WebHID 权限，授权后自动读取设备状态。

本地双击打开即可，不需要起服务器；若浏览器拦截本地文件访问设备，把 `index.html` 放到
任意 https 页面下同样可用。

### 指定界面语言

地址后加查询参数即可，例如 `index.html?lang=en`：

| 取值 | 界面语言 |
|---|---|
| `?lang=zh` | 中文（无参数时的默认） |
| `?lang=en` | English |
| `?lang=ja` | 日本語 |

它只在**本机还没有记住语言**时生效（首次访问、换了台电脑、清过缓存）——方便把某个
语言的链接直接发给别人。之后以你在设备页「显示语言」里的选择为准，这个选择会记在本机，
可用「清除控制台缓存」清掉。

优先级是：**地址栏参数 > 本机记住的语言 > 中文**。带着参数打开就以参数为准，并把它
写成这台电脑的新记忆；不带参数才读记忆。界面语言一变，地址栏里的 `lang` 也会同步改写
（不新增浏览历史），所以随时复制地址发给别人，对方打开都会是同一种语言。

## 功能

**设备选项** —— 音量、数字滤波、EQ 档位、增益、DRE、同轴、麦克风、DAC 供电、耳放电压、
屏幕旋转 / 熄屏 / 语言 / 主题色 / 主题模式、声道平衡、亮度。

写入走「读-改-写 + 读回比对」：先读该组真实值，只替换目标字段，写完读回核对，
不一致按原值回补，并把收发帧写进日志。固件不在授权名单内时，写入会在发报文之前被拦下。

**均衡器** —— 10 段参数（类型 / 频率 / 增益 / Q）、7 种内置音效 + 3 个自定义槽、
频响曲线与落点对照、官方格式 JSON 导入导出、Parametric EQ 文本导入（Equalizer APO / REW 格式）。

**音量静态补偿** —— 按设备音量档位做等响度对齐，只对自定义预设生效，不落盘。

**已知限制：UAC 协议只读。** 网页写入 `uacVersion` 能改设备里存的值，但触发不了固件
「设置已更新，请重新连接 USB」那条提示，会造成屏显与 USB 身份不一致、又不会催你拔插的
半生效状态，因此不提供网页切换 —— 请用设备按键切换。

## 关于源码

本仓库发布的 `index.html` **未压缩、未混淆**，代码可读、可直接编辑，改完存盘即生效。
它是本项目的完整对应源码（AGPL 语义下的 Corresponding Source），不含构建步骤。

如果你只想要一个能用的控制台，拿这一个文件就够了。

## 许可

本项目以 **GNU Affero General Public License v3.0 or later** 授权。

```
Copyright (C) 2026 SNTube

This program is free software: you can redistribute it and/or modify
it under the terms of the GNU Affero General Public License as published
by the Free Software Foundation, either version 3 of the License, or
(at your option) any later version.

This program is distributed in the hope that it will be useful,
but WITHOUT ANY WARRANTY; without even the implied warranty of
MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
GNU Affero General Public License for more details.

You should have received a copy of the GNU Affero General Public License
along with this program.  If not, see <https://www.gnu.org/licenses/>.
```

许可全文见 [`LICENSE`](LICENSE)。

三条要点：

- **分发修改版必须开源**。你改了再发布、或放到网上给别人用，须以同一许可提供完整源码；
- **通过网络提供服务也要提供源码**（AGPL 第 13 条）。把修改版架成在线服务，须向使用者
  提供获取对应源码的途径；
- **商业使用需要单独授权**。闭源商用、OEM 集成、或不愿遵守 AGPL 的商用场景，
  请通过 GitHub Issues 联系：https://github.com/SNTube/DC04U-WEB-CONSOLE/issues。
  请在标题里写「商业授权」并简述用途（产品名 / 是否闭源 / 分发规模）。

以上授权仅覆盖本仓库自有代码。名称与图标不随代码授权，基于本项目的衍生作品请更换名称与图标。

## 第三方组件

| 组件 | 许可 | 版权 |
| --- | --- | --- |
| Apache ECharts 5.6.0 | Apache-2.0 | Copyright 2017-2024 The Apache Software Foundation |
| ZRender | Apache-2.0 | Copyright (c) 2013, Baidu Inc. |
| tslib | 0BSD | Copyright (c) Microsoft Corporation |

均未修改。许可全文与逐项说明见 [`THIRD-PARTY-NOTICES.md`](THIRD-PARTY-NOTICES.md)
与 [`LICENSES/Apache-2.0.txt`](LICENSES/Apache-2.0.txt)；`index.html` 末尾也附有 Apache-2.0 全文，
因此单独下载这一个文件的人也拿得到完整许可文本。

## 免责

本项目按现状提供，不对任何设备损坏、数据丢失或听力损伤负责。写入设备参数前请确认
固件版本受支持；不支持的固件会在写入前被门禁拦下。
