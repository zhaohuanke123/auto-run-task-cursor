---
name: ai-ui-design-workflow
description: A 4-step prompt engineering workflow for building high-quality UI with any AI model. Use when designing app interfaces, creating design systems, building React/Tailwind UI components, or when the user wants to avoid "UI as afterthought" problems.
---

# AI-Driven UI Design Workflow

A structured approach to design-first development with any AI assistant: think deeply about design before writing business logic.

## Core Principle

**Problem**: Developers often build complex features first, then treat UI as an afterthought, resulting in poor interfaces.

**Solution**: Use structured prompt engineering to design first, then build. This 4-step system ensures UI/UX is a first-class citizen.

---

## The 4-Step Workflow

### Step 1: Generate PRD (Product Requirements Document)

Define product features, user stories, requirements, and validation plans before any design work.

**Prompt Role**: Act as a Product Manager

**Output includes:**
- Executive summary (what, why, who, solution)
- Key features (max 3) with user stories and acceptance criteria
- Requirements: functional, non-functional (performance, security, accessibility), UX
- Validation plan with assumptions and next steps

### Step 2: Extract Feature List & UX Considerations

Filter the PRD to retain only UI/UX-relevant information.

**Output includes:**
- Feature list with categories
- User stories per feature
- UX/UI considerations: core experience, states (empty, loading, error, active), animations, information architecture
- Edge cases and power user scenarios

**UX Principles to apply:**
- Simplicity
- Breathing room with whitespace
- Strategic negative space
- Clear visual hierarchy

### Step 3: Create Design Specification (Token-based Design System)

Build a project-specific design system with tokens.

**Prompt Role**: Act as a SaaS Product Designer

**Output includes:**
- Color system with hex codes
- Typography: font family, weights, text styles
- Components: buttons, cards, inputs, icons
- Spacing system
- Animation guidelines
- Dark mode variants

**Tip**: Use design inspiration from platforms like Mobbin, Dribbble, or reference apps to guide the visual direction.

### Step 4: Build Screens (High-fidelity UI Components)

Generate production-ready components screen by screen.

**Key requirements:**
- Use Tailwind CSS for styling
- Handle all states: empty, loading, error, active
- One feature module at a time to avoid context overload
- Include animations and interactions

---

## Prompt Template Structure

Each step follows this pattern:

```markdown
## Goal
[What the AI should accomplish]

## Input/Context
[PRD from previous step / Design specs / App overview]

## Guidelines
[UX principles / Design constraints / Technical requirements]

## Output Format
[Expected structure and format]
```

---

## Context Management Rules

1. **Iterative context passing**: Each step receives relevant output from previous steps
2. **Avoid context overload**: Process one feature module at a time in Step 4
3. **Progressive disclosure**: Start with PRD → narrow to features → design tokens → components
4. **Chain the context**: Pass the output of each step as input to the next

---

## Quick Reference

| Step | Input | Output |
|------|-------|--------|
| 1. PRD | App concept | Requirements document |
| 2. Features | PRD | Filtered feature list with UX considerations |
| 3. Design System | Features + Inspiration | Token-based style guide |
| 4. Components | Design System + Features | Production-ready React/Tailwind components |

---

## Task.json Generation Workflow

When user requests to generate a task file for AI web development, follow this structured workflow to create a complete `task.json` that guides AI agents through the entire design-to-build process.

### Trigger Phrases

User may say:
- "生成一份 AI 网页制作 task"
- "帮我创建一个项目的 task.json"
- "生成 task 文件，项目是 XXX"
- "按照这个 workflow 生成任务清单"

### Task.json Structure

The generated `task.json` must follow this schema:

```json
{
  "project": "Project Name",
  "description": "Project description",
  "tasks": [
    {
      "id": 1,
      "title": "Task title",
      "description": "Task description",
      "steps": ["Step 1", "Step 2", "..."],
      "passes": false
    }
  ]
}
```

### Task Generation Phases

Generate tasks in exactly this order, mapping to the 4-Step Workflow:

#### Phase 1: Research & PRD (Step 1 of Workflow)

| Task ID | Task Title | Steps | Output Document |
|---------|------------|-------|-----------------|
| 1 | 市场调研与竞品分析 | 调研设计趋势、竞品分析、用户关注点、整理调研报告 | `docs/research.md` |
| 2 | 用户需求分析 | 定义用户画像、分析用户场景、验证需求优先级 | `docs/user-analysis.md` |
| 3 | PRD 产品需求文档 | Executive Summary、Features、Requirements、Validation Plan | `docs/prd.md` |

#### Phase 2: Features & UX (Step 2 of Workflow)

| Task ID | Task Title | Steps | Output Document |
|---------|------------|-------|-----------------|
| 4 | Feature List 功能清单 | 从 PRD 提取功能、按模块分类、标注优先级、识别依赖 | `docs/feature-list.md` |
| 5 | UX Considerations UX考量 | 核心体验、状态处理、动画规范、信息架构、边界情况 | `docs/ux-considerations.md` |

#### Phase 3: Design System (Step 3 of Workflow)

| Task ID | Task Title | Steps | Output Document |
|---------|------------|-------|-----------------|
| 6 | 颜色系统 | Primary/Accent/Neutral/Semantic 颜色定义 | `docs/design-system/colors.md` |
| 7 | 字体系统 | 字体选择、Type Scale、行高、字重规范 | `docs/design-system/typography.md` |
| 8 | 间距和布局 | Spacing System、Border Radius、Shadow、Grid | `docs/design-system/layout.md` |
| 9 | 动画系统 | 时长 Token、缓动函数、动画变体定义 | `docs/design-system/animations.md` |
| 10 | 组件库清单 | 基础组件、布局组件、业务组件列表及 Props 定义 | `docs/design-system/components.md` |

#### Phase 4: Build Implementation (Step 4 of Workflow)

Build tasks follow this pattern for each feature module:

```
For each Feature Module (e.g., Projects, Skills, Timeline):
├── Data Structure Task
│   └── Define TypeScript types, content schema, data access functions
└── UI Implementation Task
    └── Build components, handle states, add animations
```

**Standard Build Tasks:**

| Task Range | Category | Tasks |
|------------|----------|-------|
| 11-13 | Infrastructure | 项目配置、基础组件、布局组件 |
| 14 | Hero | 首屏个人介绍 |
| 15-17 | Projects | 数据结构 + UI + Modal |
| 18-19 | Skills | 数据结构 + UI |
| 20-21 | Timeline | 数据结构 + UI |
| 22-23 | Reading | 数据结构 + UI |
| 24-27 | Blog | 数据结构 + 列表UI + 详情页 + 列表页 |
| 28 | Contact | 联系方式模块 |
| 29-33 | Enhancement | 动画系统、响应式、暗色模式、SEO、性能优化 |
| 34 | Content | 内容填充 |
| 35 | Final | 最终测试和优化 |

### Task Step Guidelines

Each task's `steps` array should follow these rules:

1. **Concrete and actionable**: Each step is a specific action (e.g., "创建 components/ui/Button.tsx")
2. **Verifiable**: Each step produces a tangible output (file, document, feature)
3. **Ordered**: Steps follow logical dependency order
4. **Self-contained**: Each step includes enough context to execute independently

### Step Writing Template

For **Data Structure Tasks**:
```
- 创建 types/[module].ts 定义 [Type] 类型
- 定义字段: id, title, description, ...
- 创建 content/[module]/ 目录存放数据
- 定义 Markdown frontmatter 格式 (if applicable)
- 创建 lib/[module].ts 读取数据
- 实现排序/筛选逻辑
```

For **UI Implementation Tasks**:
```
- 创建 components/sections/[Module].tsx 区域组件
- 创建 components/[module]/[Module]Card.tsx 卡片组件
- 实现 [具体功能] 显示
- 实现 [交互效果]
- 添加滚动触发动画
- 实现响应式适配
```

### Generation Process

When generating task.json, follow this process:

```
1. 接收用户需求 (项目类型、风格偏好、目标用户)
2. 进行 Web 调研 (设计趋势、最佳实践)
3. 按 Phase 顺序生成任务:
   - Phase 1: 3 tasks (Research → User Analysis → PRD)
   - Phase 2: 2 tasks (Feature List → UX Considerations)
   - Phase 3: 5 tasks (Color → Typography → Layout → Animation → Components)
   - Phase 4: N tasks (根据 Feature 数量动态生成)
4. 确保每个 task 的 steps 具体可执行
5. 输出完整的 task.json 文件
```

### Example Usage

**User Input:**
```
生成一份 AI 网页制作 task，项目是个人简历网站，小清新风格，面向求职
```

**Agent Should:**
1. 先调研个人简历网站的设计趋势
2. 生成包含 35+ 任务的完整 task.json
3. 任务覆盖从调研、设计到实现的全流程
4. 每个任务有清晰的 steps 和输出文档

---

## Key Mindset

> Users don't buy features; they buy **results**. UX/UI is the critical path to delivering those results.

Never treat UI as an afterthought. Design first, code second.