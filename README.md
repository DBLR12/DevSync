[README.md](https://github.com/user-attachments/files/23480565/README.md)
# DevSync - 环境迁移助手

> 一键扫描、导出、恢复你的完整开发环境

DevSync 是一个强大的开发环境迁移工具，帮助程序员在换机器时快速恢复开发环境。

## ✨ 核心功能

### 🔍 智能扫描
- **90+ 种开发工具**：自动检测编程语言、框架、工具、数据库等
- **多版本检测**：智能识别 NVM、JDK 等工具管理的所有版本
- **当前版本标记**：自动标记正在使用的版本（★）

### 💾 可视化报告
- **HTML 报告**：美观的可视化报告，支持实时搜索
- **JSON 配置**：完整的环境配置文件，可用于自动化恢复
- **详细信息**：包含版本号、路径、下载链接、安装指南

### 🚀 自动化恢复
- **一键安装**：自动安装 pip 包、npm 包、VSCode 插件
- **安装指南**：为无法自动安装的工具生成详细指南
- **三层策略**：全自动、半自动、手动安装分类处理

---

## 📦 支持的工具（90+）

### 🔧 版本管理工具
- **NVM** - Node.js 版本管理（支持目录扫描）
- **JDK 多版本** - 智能检测所有 JDK 安装
- pyenv, rbenv, rustup, SDKMAN

### 💻 编程语言（20+）
**主流语言**：Python, Node.js, Java, Go, Rust, Ruby, PHP, C/C++, .NET/C#

**JVM 语言**：Kotlin, Scala

**移动开发**：Dart, Flutter

**其他**：Perl, Lua

### 📦 包管理器
**Node.js**：npm, yarn, pnpm

**Python**：pip, pip3

**系统级**：chocolatey, scoop, winget

### 🎨 前端工具（15+）
**框架 CLI**：Vue CLI, Angular CLI, Create React App, Next.js, Vite

**编译器**：TypeScript, Babel

**打包工具**：Webpack, Rollup, Parcel

**任务运行器**：Gulp, Grunt

**代码质量**：ESLint, Prettier

### 🧪 测试框架
Jest, Mocha, Pytest

### 🗄️ 数据库工具（15+）
**关系型**：MySQL, PostgreSQL, SQL Server (sqlcmd), Oracle (sqlplus), SQLite, MariaDB

**NoSQL**：MongoDB, Redis, CouchDB, Cassandra, Neo4j, InfluxDB

**搜索引擎**：Elasticsearch

### ☁️ 云服务 CLI
AWS CLI, Azure CLI, Google Cloud SDK

### 🐳 容器与编排
Docker, Docker Compose, Kubernetes (kubectl)

### 🏗️ 构建工具
Maven, Gradle, Make, CMake, Terraform, Ansible

### 🌐 服务器
Nginx, Apache

### 🔐 版本控制
Git, SVN, Mercurial

### 🛠️ 系统工具
curl, wget, ssh, rsync, 7-Zip

---

## 🚀 快速开始

### 安装依赖

```bash
pip install -r requirements.txt
```

### 1. 扫描当前环境

```bash
python scan.py
```

**生成文件**：
- `environment_config_YYYYMMDD_HHMMSS.json` - 配置文件
- `scan_report_YYYYMMDD_HHMMSS.html` - 可视化报告（自动在浏览器打开）

**报告特点**：
- 🔍 实时搜索功能
- 📊 分类展示（自动安装 vs 手动安装）
- ⭐ 当前使用版本标记
- 📝 详细的安装指南和下载链接

### 2. 在新机器上恢复

```bash
python restore.py environment_config_YYYYMMDD_HHMMSS.json
```

**自动执行**：
1. 自动安装 pip 包
2. 自动安装 npm 包
3. 自动安装 VSCode 插件
4. 生成手动安装清单（HTML）

---

## 🎯 特色功能

### 多版本智能检测

#### NVM 支持
- **问题**：nvm-windows 无法在 Python subprocess 中直接调用
- **解决**：通过读取 `NVM_HOME` 目录结构，扫描所有已安装版本
- **结果**：成功检测所有 Node.js 版本并标记当前版本

#### JDK 多版本
- **智能搜索**：自动搜索所有驱动器的常见安装位置
- **支持类型**：Oracle JDK、OpenJDK、Zulu、Corretto 等
- **当前版本**：通过 `JAVA_HOME` 识别当前使用的 JDK

### 版本解析处理
- 支持多种版本输出格式（stdout/stderr）
- 特殊处理 Java、Maven 等工具的版本信息
- 正则表达式智能匹配

---

## 📁 项目结构

```
programerER/
├── scanners/                    # 扫描器模块
│   ├── base_scanner.py          # 扫描器基类
│   ├── version_manager_scanner.py  # 版本管理工具（nvm, pyenv 等）
│   ├── jdk_scanner.py           # JDK 多版本扫描器
│   ├── language_scanner.py      # 编程语言和工具扫描器
│   ├── package_scanner.py       # 包管理器扫描器
│   └── vscode_scanner.py        # VSCode 插件扫描器
├── installers/                  # 安装器模块
│   ├── auto_installer.py        # 自动安装器
│   └── guide_generator.py       # HTML 报告生成器
├── utils/                       # 工具函数
│   ├── config_manager.py        # 配置管理
│   └── logger.py                # 日志工具
├── scan.py                      # 扫描入口
├── restore.py                   # 恢复入口
├── requirements.txt             # Python 依赖
└── README.md                    # 项目文档
```

---

## 🔧 技术实现

### 核心技术
- **后端**：Python 3.8+
- **前端**：HTML + Tailwind CSS
- **数据格式**：JSON

### 特殊处理
- **NVM 检测**：目录扫描绕过命令行限制
- **JDK 多版本**：智能搜索所有驱动器
- **版本解析**：支持 stdout/stderr 多种格式
- **错误处理**：优雅处理权限错误和超时

---

## 📊 使用示例

### 扫描输出示例

```
======================================================================
扫描 版本管理工具
======================================================================
INFO -   ✓ 检测到 nvm (从目录)
INFO -     从目录检测到 3 个版本
INFO -     检测到 3 个 Node.js 版本

======================================================================
扫描 JDK 多版本
======================================================================
INFO -   检测到 4 个 JDK 安装
INFO -     ✓ JDK 1.8.0_431 ★ (当前)
INFO -     ✓ JDK 17.0.14
INFO -     ✓ JDK 21
INFO -     ✓ JDK 23.0.2

======================================================================
扫描 编程语言
======================================================================
INFO -   ✓ 检测到 python: 3.11.5
INFO -   ✓ 检测到 node: v24.1.0
INFO -   ✓ 检测到 npm: 10.9.2
INFO -   ✓ 检测到 yarn: 1.22.19
INFO -   ✓ 检测到 git: 2.43.0
...
```

---

## 🎨 报告预览

生成的 HTML 报告包含：
- **统计卡片**：总计、可自动安装、需手动安装
- **搜索框**：实时过滤工具
- **自动安装表格**：可自动安装的工具列表
- **手动安装表格**：需要手动安装的工具，含下载链接和指南

---

### 添加新工具支持
1. 在 `scanners/language_scanner.py` 的 `LANGUAGES` 字典中添加配置
2. 如需特殊处理，添加对应的解析方法
3. 测试并提交 PR

---

## 📝 License

MIT License

---

## 🙏 致谢

感谢所有开源工具和社区的支持！
