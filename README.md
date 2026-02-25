# Bid_Document_Generation - 智能标书助手

🎯 **一个命令，智能对话，完成所有标书工作**

通过自然语言对话完成标书的全流程生成和管理的智能工具。

## ✨ 核心特性

### 🤖 智能对话引擎
- **自然语言理解**: 理解用户的标书需求和指令
- **智能任务规划**: 自动分解复杂任务，制定执行计划
- **上下文记忆**: 记住项目状态和历史对话
- **智能建议**: 主动提供专业建议和下一步操作
- **多轮对话**: 支持复杂任务的分步完成
- **自适应调整**: 根据进展动态调整任务计划

### 🛠️ 内置 MCP 工具集

#### 📁 文件操作工具
- 读取/写入文件内容
- 创建目录结构
- 管理三级标题文件
- 获取完整章节结构

#### 📄 招标文件处理工具
- 提取PDF文本内容
- 解析招标要求
- 提取关键信息
- 分析评分标准
- 识别招标类型

#### 📝 内容生成工具
- 生成标书大纲
- 并行生成章节内容
- 优化三级标题内容
- 生成技术方案
- 创建项目时间表
- 生成预算分解

#### 📊 文档处理工具
- 一键导出Word文档
- 合并所有章节内容
- 应用专业模板
- 格式化表格和图表
- 导出PDF文档

### 🎯 智能任务规划特色

- **自动任务分解**: 将"制作标书"自动分解为4个阶段、20+个子任务
- **精准时间预估**: 基于历史数据预估每个任务耗时
- **智能决策能力**: 自动评估大纲质量，决定是否需要调整
- **实时进度跟踪**: 清晰显示当前执行阶段和进度

## 🚀 快速开始

### 安装

```bash
# 克隆项目
git clone https://github.com/Qingfengfumian/Bid_Document_Generation.git
cd tender-cli

# 安装依赖
pip install -e .
```

### 配置方式

#### 方式一：环境变量配置（推荐）

1. 复制环境变量模板：
```bash
cp .env.example .env
```

2. 编辑 `.env` 文件：
```bash
# OpenAI API 配置
OPENAI_API_KEY=your_openai_api_key_here
OPENAI_BASE_URL=https://api.openai.com/v1
OPENAI_MODEL=gpt-4

# 或者使用自定义端点（如本地模型服务）
OPENAI_BASE_URL=http://localhost:8000/v1
OPENAI_MODEL=your_model_name

# AI 服务提供商
AI_PROVIDER=openai

# 项目工作目录
TENDER_WORKSPACE=~/tender_projects

# 调试模式
TENDER_DEBUG=false
```

#### 方式二：交互式配置

```bash
# 启动配置向导
tender

# 按提示配置 API 密钥和工作目录
```

### 基本使用

```bash
# 启动智能助手
tender

# 开始对话
> 我有一个智慧城市项目的招标文件，帮我分析一下并制作标书
```

## 🔧 配置说明

### 支持的配置方式

1. **环境变量** (优先级最高)
2. **`.env` 文件** (在项目根目录、用户主目录或配置目录)
3. **配置文件** (`~/.tender/config.yaml`)
4. **交互式配置**

### 环境变量列表

| 环境变量 | 配置项 | 说明 | 示例 |
|---------|--------|------|------|
| `OPENAI_API_KEY` | `ai.api_key` | OpenAI API 密钥 | `sk-xxx...` |
| `OPENAI_BASE_URL` | `ai.base_url` | API 基础URL | `https://api.openai.com/v1` |
| `OPENAI_MODEL` | `ai.model` | 使用的模型 | `gpt-4` |
| `AI_PROVIDER` | `ai.provider` | AI服务提供商 | `openai` |
| `TENDER_WORKSPACE` | `project.default_workspace` | 工作目录 | `~/tender_projects` |
| `TENDER_DEBUG` | `debug` | 调试模式 | `true/false` |

### 自定义模型端点

支持使用自定义模型端点（如本地部署的模型服务）：

```bash
# .env 文件配置
OPENAI_BASE_URL=http://localhost:8000/v1
OPENAI_MODEL=your_custom_model
# API_KEY 可选，取决于你的服务是否需要
OPENAI_API_KEY=optional_if_needed
```

### 配置文件位置
- 默认配置文件: `~/.tender/config.yaml`
- 工作目录: `~/tender_projects/`
- 日志文件: `~/.tender/logs/tender.log`
- 环境变量文件: `./.env`, `~/.env`, `~/.tender/.env`

### 配置项说明

```yaml
ai:
  provider: openai          # AI服务提供商
  model: gpt-4             # 使用的模型
  api_key: "your-api-key"  # API密钥
  base_url: ""             # 自定义API地址（可选）
  temperature: 0.7         # 生成温度
  max_tokens: 4000         # 最大token数

project:
  default_workspace: "~/tender_projects"  # 默认工作目录
  auto_backup: true        # 自动备份
  backup_interval: 3600    # 备份间隔（秒）

document:
  default_template: standard  # 默认模板
  font_family: "宋体"        # 字体
  font_size: 12             # 字号
  line_spacing: 1.5         # 行距

mcp:
  server_port: 8080        # MCP服务端口
  timeout: 30              # 超时时间
  max_workers: 24          # 最大工作线程数
```

## 💡 使用示例

### 项目管理
```bash
> 创建新项目：智慧城市建设
> 列出所有项目
> 切换到项目XXX
> 备份当前项目
```

### 文件处理
```bash
> 分析这个招标文件: /path/to/tender.pdf
> 上传招标文件让我分析
> 提取PDF内容
```

### 内容生成
```bash
> 生成标书大纲
> 写第3章技术方案
> 优化公司介绍部分
> 生成项目时间表
```

### 文档导出
```bash
> 导出Word文档
> 一键生成标书
> 转换为PDF
```

### 查看内容
```bash
> 查看第2章
> 显示项目结构
> 打开技术方案章节
```

## 📁 项目结构

```
tender-cli/
├── src/tender_cli/           # 主要源码
│   ├── core/                # 核心模块
│   │   ├── tender_ai.py     # AI助手主类
│   │   ├── config.py        # 配置管理
│   │   ├── conversation.py  # 对话管理
│   │   └── project_manager.py # 项目管理
│   ├── mcp_tools/           # MCP工具集
│   │   ├── mcp_server.py    # MCP服务器
│   │   ├── file_tools.py    # 文件操作工具
│   │   ├── tender_tools.py  # 招标文件处理
│   │   ├── content_tools.py # 内容生成工具
│   │   └── document_tools.py # 文档处理工具
│   ├── prompts/             # 提示词库
│   │   └── prompt_library.py
│   ├── utils/               # 工具模块
│   │   ├── logger.py        # 日志工具
│   │   └── ai_client.py     # AI客户端
│   └── main.py              # 主入口
├── tests/                   # 测试文件
├── examples/                # 示例文件
├── docs/                    # 文档
├── assets/                  # 资源文件
│   ├── templates/           # 文档模板
│   └── logos/               # Logo文件
├── .env.example             # 环境变量模板
├── pyproject.toml           # 项目配置
├── README.md                # 项目说明
└── design.MD                # 设计文档
```

## 🎯 智能对话示例

### 完整标书制作流程

```bash
$ tender

🎯 Tender AI - 标书智能体助手 v1.0.0

👋 你好！我是你的标书智能助手，可以帮你完成标书的全流程工作。

> 我有一个智慧城市项目的招标文件，帮我分析一下并制作标书

🤖 **智能任务规划启动**

📋 **任务概览**
目标：分析智慧城市招标文件并制作完整标书
范围：从文件分析到最终Word文档输出
预估工作量：中等复杂度项目

🎯 **自动执行计划**
1️⃣ **文件分析阶段** (预估3-5分钟)
   • 提取PDF招标文件内容
   • 解析关键信息和要求  
   • 分析评分标准和权重
   • 识别技术难点和机会

2️⃣ **项目准备阶段** (预估1-2分钟)
   • 创建项目目录结构
   • 生成标书大纲框架
   • 设置章节模板

3️⃣ **内容生成阶段** (预估8-12分钟)
   • 并行生成各三级标题内容
   • 重点优化技术方案章节
   • 定制化公司介绍内容

4️⃣ **质量优化阶段** (预估3-5分钟)  
   • 整体内容审查
   • 格式统一和美化
   • 导出专业Word文档

⏰ **总预估时间**: 15-24分钟
💡 **优化建议**: 准备好公司资质材料以便快速定制

🚀 **开始执行计划？** 请提供招标文件路径，我将按计划自动完成所有步骤。

> ./documents/智慧城市招标文件.pdf

🔍 **[1/4] 文件分析阶段** - 正在执行...
✅ 分析完成！

📋 **项目概况**
• 项目名称：某市智慧城市综合管理平台建设
• 招标单位：某市政府信息化办公室  
• 预算范围：800-1200万元
• 项目周期：18个月
• 投标截止：2024年3月15日

🎯 **关键要求**
• 需要建设统一的城市数据平台
• 要求支持10万+并发用户
• 必须通过等保三级认证
• 需要7*24小时运维服务

📊 **评分标准**
• 技术方案 (40分)
• 公司资质 (20分) 
• 项目经验 (20分)
• 报价合理性 (20分)

💡 **自动进入下一阶段** - 无需手动确认，按计划继续执行

🚀 **[2/4] 项目准备阶段** - 正在执行...
✅ 项目"智慧城市综合管理平台"创建完成！

⚡ **[3/4] 内容生成阶段** - 启动多线程并行生成各三级标题内容...

🔄 **并行生成进度** (24个线程同时工作)

**第1章：公司介绍及资质证明**
✅ 1.1-公司基本情况.md - 完成 (1.2s)
✅ 1.2-资质证书.md - 完成 (0.8s)
✅ 1.3-技术团队介绍.md - 完成 (1.5s)

**第2章：项目需求理解与分析**  
✅ 2.1-招标需求分析.md - 完成 (1.8s)
✅ 2.2-技术难点识别.md - 完成 (1.4s)
✅ 2.3-解决方案概述.md - 完成 (2.1s)

...

📄 **自动导出Word文档** - 按计划执行最后步骤...

🎉 **任务计划完美执行完成！**

📄 **Word文档导出完成！**

📁 **文件信息**
• 保存位置：./projects/智慧城市综合管理平台/output/标书_v1.0.docx
• 文件大小：2.3MB
• 总页数：45页
• 包含图表：12个

🎉 **标书制作完成！**
```

## 🔍 精细化文件管理

### 目录结构
```
项目名称/
├── sections/                    # 章节内容目录
│   ├── 01-公司介绍及资质证明/
│   │   ├── 1.1-公司基本情况.md
│   │   ├── 1.2-资质证书.md
│   │   └── 1.3-技术团队介绍.md
│   ├── 02-项目需求理解与分析/
│   │   ├── 2.1-招标需求分析.md
│   │   ├── 2.2-技术难点识别.md
│   │   └── 2.3-解决方案概述.md
│   └── ...
├── assets/                      # 资源文件
├── output/                      # 输出文件
│   └── 标书_v1.0.docx
├── backup/                      # 备份文件
├── temp/                        # 临时文件
├── project.json                 # 项目配置
└── README.md                    # 项目说明
```

### 精细化管理优势
- **独立编辑**: 每个三级标题内容可单独编辑，粒度更细
- **模块化复用**: 小节内容可在不同项目间复用
- **版本控制**: Git友好，每个小节变更独立跟踪
- **并行处理**: 多个三级标题可同时生成和修改
- **智能组装**: 自动按章节结构组装完整文档

## 🛠️ 开发指南

### 环境要求
- Python 3.8+
- OpenAI API Key 或其他支持的AI服务

### 开发安装
```bash
# 克隆项目
git clone https://github.com/Qingfengfumian/Bid_Document_Generation.git
cd tender-cli

# 创建虚拟环境
python -m venv venv
source venv/bin/activate  # Linux/Mac
# 或
venv\Scripts\activate     # Windows

# 安装开发依赖
pip install -e ".[dev]"

# 运行测试
pytest

# 代码格式化
black src/
isort src/

# 类型检查
mypy src/
```

### 扩展开发

#### 添加新的MCP工具
```python
# 在 mcp_tools/ 目录下创建新工具类
class NewTool:
    def new_function(self, param: str) -> str:
        """新功能描述"""
        # 实现逻辑
        return result

# 在 mcp_server.py 中注册
def new_function(self, param: str) -> str:
    return self.new_tool.new_function(param)
```

#### 添加新的提示词
```python
# 在 prompt_library.py 中添加
def _get_new_prompt(self) -> str:
    return """
    新的提示词模板...
    """
```

## 📝 许可证

MIT License - 详见 [LICENSE](LICENSE) 文件

## 🤝 贡献

欢迎提交 Issue 和 Pull Request！
