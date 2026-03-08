# Auto Run Task Cursor

基于 Cursor 子代理架构的自动化任务执行框架。

## 项目简介

本项目是一个自动化任务执行系统，采用 **主对话决策 + 子代理执行** 的架构模式。主对话负责任务选择和协调，子代理负责具体实现和验证。

## 核心特性

- **任务驱动开发**: 通过 `task.json` 定义任务清单，系统自动按优先级执行
- **子代理架构**: 分离决策与执行，主对话负责协调，子代理负责实现
- **自动验证**: 每个任务完成后自动验证，确保代码质量
- **进度追踪**: 自动记录任务进度和执行日志

## 项目结构

```
/
├── CLAUDE.md              # 主对话决策指南
├── task.json              # 任务定义文件
├── .cursor/
│   ├── agents/
│   │   ├── task-executor.md   # 任务执行子代理
│   │   └── verifier.md        # 验证子代理
│   └── skills/
│       └── ai-ui-design-workflow/
│           └── SKILL.md       # AI UI 设计工作流技能
└── .gitignore
```

## 工作流程

```
┌─────────────┐    ┌──────────────┐    ┌──────────┐
│  读取任务    │ -> │  执行任务     │ -> │  验证    │
│  task.json  │    │  task-executor│    │  verifier│
└─────────────┘    └──────────────┘    └──────────┘
                                              │
                                              v
                                       ┌──────────┐
                                       │ Git 提交 │
                                       └──────────┘
```

## 使用方法

### 1. 定义任务

在 `task.json` 中定义任务：

```json
{
  "project": "项目名称",
  "description": "项目描述",
  "tasks": [
    {
      "id": 1,
      "title": "任务标题",
      "description": "任务描述",
      "steps": ["步骤1", "步骤2"],
      "passes": false
    }
  ]
}
```

### 2. 子代理执行

主对话自动选择任务并委派给子代理：

- **task-executor**: 负责具体实现
- **verifier**: 负责验证和测试

### 3. 自动提交

验证通过后自动提交代码。

## 当前项目

当前 `task.json` 定义的任务是开发一个**小清新风格个人简历展示网站**，包含：

- 市场调研与竞品分析
- PRD 产品需求文档
- 设计规范（颜色、字体、布局、动画）
- UI 组件库
- 页面模块（Hero、Projects、Skills、Timeline、Reading、Blog、Contact）
- SEO 和性能优化

## 技术栈

- **框架**: Next.js (App Router)
- **样式**: Tailwind CSS
- **动画**: Framer Motion
- **语言**: TypeScript
- **图标**: Lucide React

## 开发命令

```bash
# 安装依赖
npm install

# 启动开发服务器
npm run dev

# 生产构建
npm run build

# 代码检查
npm run lint
```

## 许可证

MIT License