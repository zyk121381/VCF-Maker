<div align="right">
  <a title="English" href="README_EN.md"><img src="https://img.shields.io/badge/-English-545759?style=for-the-badge" alt="English"></a>
  <a title="简体中文" href="README.md"><img src="https://img.shields.io/badge/-%E7%AE%80%E4%BD%93%E4%B8%AD%E6%96%87-A31F34?style=for-the-badge" alt="简体中文"></a>
</div>

<div align="center">

# 📇 VCF Maker

**轻量级 Excel 通讯录批量转 VCF 工具，内置智能字段映射、简洁界面，开箱即用。**

![Python](https://img.shields.io/badge/Python-3.8+-3776AB?style=flat&logo=python) ![openpyxl](https://img.shields.io/badge/openpyxl-latest-6DA55F?style=flat) ![xlrd](https://img.shields.io/badge/xlrd-latest-4B8BBE?style=flat) ![ttkbootstrap](https://img.shields.io/badge/ttkbootstrap-modern-7952B3?style=flat) ![License](https://img.shields.io/badge/license-Apache%202.0-green)

</div>

![应用预览](assets/preview.png)

---

## ✨ 功能特性

### 📊 多格式 Excel 解析

支持 `.xlsx` 和 `.xls` 两种主流格式，逐行解析高效稳定。

- **`.xlsx` 支持**：基于 `openpyxl` 读取，支持只读模式快速加载大数据表。
- **`.xls` 兼容**：基于 `xlrd` 解析旧版格式，向下兼容 Excel 97–2003。
- **浮点数自动修复**：智能识别并去除电话号码等字段末尾多余的 `.0`，避免号码错乱。

### 🧠 智能字段映射

- **自动识别表头**：读取 Excel 首行作为字段名，中英文关键词自动匹配（如「姓名」→ `name`、「手机」→ `phone`、「邮箱」→ `email`）。
- **手动灵活调整**：提供下拉框逐字段手动指定映射关系，满足各类表头命名习惯。
- **必填校验**：姓名与手机列为必选项，防止生成不完整的通讯录。

### 📇 标准 VCF 3.0 输出

- **vCard 3.0 格式**：生成符合国际标准的 `BEGIN:VCARD` / `END:VCARD` 结构，兼容 iOS、Android、Outlook 等主流通讯录。
- **多字段支持**：姓名、手机、公司、部门、职位、工作电话、邮箱、地址、网址、备注共 10 个字段。
- **空值智能跳过**：空白单元格自动忽略，不生成冗余空标签。

### 🎨 简洁直观的界面

- **清晰分区布局**：文件导入、字段映射、一键转换三大区域划分明确，操作路径一目了然。
- **响应式布局**：窗口可自由拉伸，字段映射区域自适应扩展。
- **一键式操作**：「浏览文件 → 智能映射 → 一键生成」三步完成转换。

---

## 🏗️ 技术栈

| 组件 | 说明 |
| --- | --- |
| **Python 3.8+** | 核心语言 |
| **ttkbootstrap** | 现代化 Tkinter UI 引擎，提供 Bootstrap 风格主题 |
| **openpyxl** | `.xlsx` 文件读写 |
| **xlrd** | `.xls` 文件读取 |
| **Tkinter** | Python 内置 GUI 框架 |

---

## 📂 项目结构

```
VCF Maker/
├── VCF Maker.py               # 主程序（GUI 界面 + 核心转换逻辑）
├── assets/
│   └── favicon.ico              # 应用图标
├── README.md                    # 项目文档（中文）
└── README_EN.md                 # 项目文档（英文）
```

---

## 🚀 快速开始

1. 从 [Releases](https://github.com/zyk121381/VCF-Maker/releases) 页面下载最新的 `VCF Maker.exe`
2. 双击运行，无需安装任何依赖

---

## 📖 使用指南

### 1. 导入 Excel 文件

运行 `VCF Maker.exe`，点击「📂 浏览文件」选择 `.xlsx` 或 `.xls` 文件，程序自动加载并识别所有工作表。

### 2. 选择工作表

在下拉框中切换目标工作表，表头字段自动刷新。

### 3. 字段映射

程序会根据关键词自动匹配字段，也可手动通过下拉框调整每个 VCF 字段对应的 Excel 列。

> **必填字段**：带 `*` 标记的「姓名」和「手机」列不可为空。

### 4. 一键生成

点击「⚡ 一键生成 VCF 通讯录」，选择保存路径，即可获得标准 `.vcf` 文件。

---

## 📋 Excel 表格规范建议

| 推荐列名 | 映射字段 | 说明 |
| --- | --- | --- |
| 姓名 / 名 / Name | 👤 姓名 | **必填** |
| 手机 / 移动 / Mobile | 📱 手机 | **必填** |
| 公司 / 企业 / Org | 🏢 公司 | 可选 |
| 部门 / Dept | 🤖 部门 | 可选 |
| 职位 / 职务 / Title | 💼 职位 | 可选 |
| 座机 / 工作电话 / 分机 | ☎️ 电话 | 可选 |
| 邮箱 / Mail | 📧 邮箱 | 可选 |
| 地址 / 住址 / Address | 📍 地址 | 可选 |
| 网址 / 网站 / URL | 🌐 网址 | 可选 |
| 备注 / Note | 📝 备注 | 可选 |

---

## 🎨 设计理念

1. **极致轻量**：单文件 exe，无需安装 Python 环境或任何依赖，即开即用。
2. **零学习成本**：导入即用，智能映射减少手动操作，一键生成 VCF。
3. **专注核心**：围绕「Excel → VCF」这一核心任务，去除冗余功能，操作流程最简。

---

<div align="center">
<b>让每一次通讯录转换，都精准、高效、优雅。📇</b>
</div>
