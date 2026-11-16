# 第三方组件声明

本项目（DC04U 控制台）在构建产物中内联了下列第三方组件。它们各自受其原始许可约束，
本项目的许可不改变这些组件的许可，也不对这些组件提供任何额外授权或担保。

分发本项目的任何形态时，请连同本文件与 `LICENSES/` 目录一起分发。

---

## 1. Apache ECharts 5.6.0

| 项 | 内容 |
| --- | --- |
| 组件 | Apache ECharts（图表引擎） |
| 版本 | 5.6.0 |
| 许可 | Apache License, Version 2.0 |
| 版权 | Copyright 2017-2024 The Apache Software Foundation |
| 修改 | 未修改。构建时按需裁剪（只打包用到的部分），未改源码，未改许可声明 |
| 位置 | 内联于 `index.html` 开头的第一个 `<script>` 段 |

## 2. ZRender

| 项 | 内容 |
| --- | --- |
| 组件 | ZRender（ECharts 依赖的 2D 绘图底层，随 ECharts 一起内联） |
| 许可 | Apache License, Version 2.0 |
| 版权 | Copyright (c) 2013, Baidu Inc. |
| 修改 | 未修改 |

## 3. tslib

| 项 | 内容 |
| --- | --- |
| 组件 | tslib（ECharts 的构建期辅助模块，随 ECharts 一起内联） |
| 许可 | 0BSD |
| 版权 | Copyright (c) Microsoft Corporation |
| 修改 | 未修改 |
| 说明 | 0BSD 要求保留许可声明，其完整声明文本已随代码内联在原位置，无需额外全文 |

---

## 许可全文

- Apache License 2.0 全文：[`LICENSES/Apache-2.0.txt`](LICENSES/Apache-2.0.txt)
- `index.html` 文件末尾附有同一份 Apache-2.0 全文，
  因此单独下载这一个文件的人也拿得到完整许可文本。

## 说明

- Apache-2.0 第 4 条要求：分发时须提供许可副本、保留版权与许可声明、标注是否修改。
  以上三项在本项目中均已满足。
- 本项目未使用 Apache、Apache ECharts、ECharts、ZRender 的名称或标识进行推广，
  也不声称获得 Apache 软件基金会或百度的背书。
- 本项目的授权范围限于仓库内的自有代码，不包含任何第三方素材（图表引擎、字体、位图等）。
  设备报文格式依据设备实际通信行为整理，属于接口事实，不随本项目授权。
