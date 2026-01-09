# 氨合成产率计算器 (Ammonia Yield Calculator)

[![License: MIT](https://img.shields.io/badge/License-MIT-blue.svg)](https://opensource.org/licenses/MIT)
![Language](https://img.shields.io/badge/language-HTML%2FJS-orange)

这是一个基于 Web 的轻量级计算工具，专门用于**电催化氮还原 (NRR)** 实验中氨产率的计算。

该工具基于 **GB 17378.4-2007 (靛酚蓝分光光度法)** 原理，集成了标准曲线拟合与摩尔产率批量计算功能，旨在替代繁琐的 Excel 处理流程，帮助科研人员快速获取实验数据。

## ✨ 主要功能 (Features)

* **📈 标准曲线自动拟合**：
    * 支持输入多组标液浓度与吸光度。
    * 自动采用最小二乘法进行线性回归。
    * 实时计算斜率 ($k$)、截距 ($b$) 及相关系数 ($R^2$)。
    * 拟合参数自动同步至计算模块。
* **⚡ 实时产率计算**：
    * 无需点击“计算”按钮，输入数据即刻显示结果。
    * 支持批量添加/删除采样点。
    * 自动处理 $N \to NH_3$ 的分子量转换。
* **🧪 科研友好型设计**：
    * 输出单位为标准的 $\mu mol \cdot g^{-1} \cdot h^{-1}$。
    * 界面清爽，移除冗余的输入框微调按钮。
    * 表格化布局，清晰展示采样时间、吸光度与最终产率。
* **🔒 数据隐私**：
    * 纯前端实现 (Vanilla JS)，无后端服务器。
    * 所有数据仅在本地浏览器运行，不上传任何云端，确保实验数据安全。

## 🛠️ 计算原理 (Methodology)

[cite_start]本工具计算逻辑严格遵循 **GB 17378.4-2007 海洋监测规范 第4部分：海水分析** [cite: 1]。

### 1. 浓度计算
根据朗伯-比尔定律 (Lambert-Beer Law) 及标准曲线：
$$C_{N} = \frac{(A_w - A_b) - \text{Intercept}}{\text{Slope}}$$
其中：
* $C_{N}$：溶液中氨氮浓度 ($\mu g/mL$)
* $A_w$：样品吸光度
* $A_b$：空白吸光度

### 2. 物质的量转换
将氨氮 ($N$) 质量转换为氨气 ($NH_3$) 摩尔数：
$$n_{NH_3} = \frac{C_{N} \times V}{14.007}$$
其中：
* $V$：捕获液体积 ($mL$)
* $14.007$：氮的原子量 ($g/mol$)

### 3. 产率计算
$$\text{Yield Rate} = \frac{n_{NH_3}}{m_{cat} \times t}$$
其中：
* $m_{cat}$：催化剂用量 ($g$)
* $t$：采样反应时间 ($h$)
* 最终单位：$\mu mol \cdot g^{-1} \cdot h^{-1}$

## 🚀 快速开始 (Quick Start)

### 方法 1：直接运行
1.  下载本项目中的 `index.html` 文件（或您保存的 html 文件名）。
2.  双击文件，使用 Chrome、Edge 或 Firefox 浏览器打开即可使用。
3.  **注意**：请保持联网状态，因为公式渲染依赖 MathJax CDN。

### 方法 2：部署到 GitHub Pages
1.  Fork 本仓库。
2.  进入仓库 `Settings` -> `Pages`。
3.  在 `Branch` 处选择 `main` (或 `master`) 并保存。
4.  几分钟后，您将获得一个在线链接，可在任何设备上访问。

## 🖥️ 使用截图 (Screenshots)

*(此处建议您上传一张工具运行时的截图，并将链接替换下方的占位符)*

![App Screenshot](./screenshot.png)

## 📂 文件结构
```text
.
├── index.html      # 包含所有逻辑、样式和结构的单文件
└── README.md       # 项目说明文档
