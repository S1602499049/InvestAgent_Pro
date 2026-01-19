# InvestAgent_Pro
# StratEdge AI - Enterprise Investment Decision System 
# (企业级智能投资决策系统)

![Version](https://img.shields.io/badge/version-3.0.0-blue.svg)
![Python](https://img.shields.io/badge/python-3.10+-yellow.svg)
![Build](https://img.shields.io/badge/build-passing-brightgreen.svg)
![License](https://img.shields.io/badge/license-Commercial-orange.svg)

> **StratEdge AI** 是一款基于 DeepSeek-V3 大模型的桌面端智能投资分析软件。它能够自动执行全网政策与市场数据检索，进行多维度经济模型推演，并生成排版精美的 PDF/Word 投资研判报告。

---

## ✨ 核心功能 (Key Features)

*   **🧠 顶级云端大脑**: 集成 DeepSeek-V3 (671B 参数) 模型，提供专家级的金融逻辑分析。
*   **🔍 实时情报检索**: 内置 DuckDuckGo 商业搜索接口，实时抓取最新的产业政策、产值数据与风险案例。
*   **📊 结构化研判**: 自动生成 SWOT 分析、PEST 宏观环境分析及风险量化矩阵（Risk Matrix）。
*   **🖥️ 现代化 GUI**: 基于 `CustomTkinter` 打造的深色模式界面，流畅、美观、无卡顿（异步多线程）。
*   **📄 专业报告导出**: 支持一键导出排版精美的 PDF 和 Word (.docx) 报告，包含标准化的表格与格式。
*   **🛡️ 商业级架构**: 采用 MVC 设计模式，配置与代码分离，支持日志追踪与异常自动恢复。

---

## 🛠️ 技术栈 (Tech Stack)

*   **Frontend (界面)**: CustomTkinter (Python GUI)
*   **Backend (逻辑)**: OpenAI SDK (接入 SiliconFlow API)
*   **Search (搜索)**: DuckDuckGo Search (DDGS)
*   **Export (文档)**: ReportLab, xhtml2pdf, python-docx
*   **Packaging (封装)**: PyInstaller, Inno Setup

---

## 📂 项目结构 (Project Structure)

```text
InvestAgent_Pro/
├── assets/              # 资源文件 (Logo图标等)
│   ├── logo.ico
│   └── logo.png
├── config/              # 配置文件
│   └── settings.json    # API Key 及系统配置
├── core/                # 核心业务逻辑
│   ├── api_client.py    # 大模型接口封装
│   ├── search_engine.py # 搜索引擎封装
│   └── workflow.py      # 业务流程控制器
├── ui/                  # 界面层
│   └── main_window.py   # 主窗口 GUI 代码
├── utils/               # 工具库
│   ├── exporter.py      # PDF/Word 导出引擎
│   └── logger.py        # 日志系统
├── main.py              # 程序启动入口
└── requirements.txt     # 依赖清单

🚀 快速开始 (Quick Start)
1. 环境准备
确保已安装 Python 3.10 或以上版本。
# 克隆项目 (示例)
git clone https://github.com/YourUsername/StratEdge-AI.git
cd StratEdge-AI

# 安装依赖
pip install -r requirements.txt

2. 配置 API Key
打开 config/settings.json 文件，填入你的 SiliconFlow (或 DeepSeek) API Key：
{
    "api": {
        "api_key": "sk-your-api-key-here",
        "base_url": "https://api.siliconflow.cn/v1",
        "model": "deepseek-ai/DeepSeek-V3"
    }
}

3. 运行软件
python main.py

📦 打包指南 (Build Instructions)
本项目包含复杂的第三方库（如 torch 排除、reportlab 隐式调用），请务必使用以下标准命令进行打包。

Step 1: 生成 EXE 可执行文件
在项目根目录下打开终端 (CMD)，运行以下命令：
python -m PyInstaller --noconsole --onefile ^
    --name="InvestAgent_Pro" ^
    --icon="assets/logo.ico" ^
    --add-data "assets;assets" ^
    --add-data "config;config" ^
    --hidden-import=customtkinter ^
    --hidden-import=htmldocx ^
    --hidden-import=markdown2 ^
    --hidden-import=xhtml2pdf ^
    --hidden-import=reportlab.graphics.barcode.common ^
    --hidden-import=reportlab.graphics.barcode.code128 ^
    --hidden-import=reportlab.graphics.barcode.usps ^
    --hidden-import=reportlab.graphics.barcode.qr ^
    --exclude-module=torch ^
    main.py

(注：生成的 EXE 文件位于 dist/ 目录下)

Step 2: 制作安装包 (Setup Installer)
下载并安装 Inno Setup。

打开项目根目录下的 install_script.iss (需自行创建，参考开发文档)。

点击 Build -> Compile。

最终的安装包将生成在 Output/ 文件夹中。

📄 依赖列表 (Requirements)
customtkinter
openai
duckduckgo-search
packaging
markdown2
xhtml2pdf
python-docx
htmldocx
pillow
requests

⚠️ 免责声明 (Disclaimer)
本软件生成的投资分析报告基于互联网公开数据和大模型逻辑推演，仅供参考，不构成实质性投资建议。开发者不对基于本软件做出的投资决策承担任何责任。

Copyright © 2026 Enterprise Solutions Co. All Rights Reserved.

