# 🚀 AI 驱动的 GitHub 技术猎头工具

一个自动化的 AI 驱动工具，每天搜索、分析并推送 GitHub 上最新的硬核 AI 技术项目。

## 功能特性

- 🔍 **智能搜索**: 每日自动搜索 RAG、AI Agent、LangChain 相关的热门项目
- 🤖 **AI 分析**: 使用 GPT-4o-mini 分析项目 README，精选最硬核的 5 个项目
- 📱 **即时推送**: 通过 PushDeer 将精选项目推送到手机
- ⭐ **一键收藏**: 支持一键 Star 项目并分类到 GitHub Stars List
- ⏰ **自动化**: 每日 9:00 (UTC+8) 自动运行

## 项目结构

```
.
├── main.py                 # 核心逻辑：搜索、AI分析、推送
├── api/
│   └── star.py            # Vercel Serverless Function：收藏功能
├── requirements.txt       # Python 依赖
├── .env.example           # 环境变量模板
├── vercel.json            # Vercel 部署配置
└── .github/
    └── workflows/
        └── daily_hunt.yml # GitHub Actions 自动化配置
```

## 快速开始

### 1. 准备环境变量

复制 `.env.example` 为 `.env` 并填入以下信息：

```bash
cp .env.example .env
```

需要准备的信息：

| 变量名 | 说明 | 获取方式 |
|--------|------|----------|
| GITHUB_TOKEN | GitHub Personal Access Token | [GitHub Settings → Developer settings](https://github.com/settings/tokens) (需要 repo 和 user 权限) |
| OPENAI_API_KEY | OpenAI API Key | [OpenAI Platform](https://platform.openai.com/api-keys) |
| PUSHDEER_KEY | PushDeer 推送 Key | [PushDeer](https://www.pushdeer.com/) |
| MY_VERCEL_URL | Vercel 部署域名 | 部署后获取 |

### 2. 安装依赖

```bash
pip install -r requirements.txt
```

### 3. 本地测试

```bash
python main.py
```

## 部署指南

### 1. 部署到 Vercel (收藏后端)

1. Fork 此项目
2. 登录 [Vercel](https://vercel.com) 并导入项目
3. 在 Vercel 项目设置中添加环境变量 `GITHUB_TOKEN`
4. 部署完成后获取你的 Vercel URL

### 2. 配置 GitHub Secrets

在你的 GitHub 仓库 Settings → Secrets and variables → Actions 中添加以下 Secrets：

- `GITHUB_TOKEN`
- `OPENAI_API_KEY`
- `PUSHDEER_KEY`
- `MY_VERCEL_URL` (你的 Vercel 域名，如 `your-project.vercel.app`)

### 3. 启用 GitHub Actions

GitHub Actions 会自动在每天 9:00 (UTC+8, 对应 UTC 1:00) 运行。你也可以手动触发测试。

## 使用说明

### 收到推送后

1. 查看 Markdown 格式的项目列表
2. 点击 GitHub 链接访问项目
3. 点击「知乎」或「小红书」搜索教程
4. 点击「一键收藏」Star 项目并分类

### 手动触发

在 GitHub 仓库的 Actions 标签页中，选择 "Daily AI Tech Hunt" 工作流，点击 "Run workflow" 手动运行。

## 技术栈

- **PyGithub**: GitHub API 交互
- **OpenAI API**: 项目智能分析
- **PushDeer**: 消息推送
- **Vercel Serverless Functions**: 收藏后端
- **GitHub Actions**: 自动化调度
