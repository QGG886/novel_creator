# 小说写作助手

基于多Agent协作的智能小说写作系统，帮助你从大纲到逐章创作完成高质量小说。

---

## 快速开始

1. 阅读 **AGENTS.md** 了解系统架构和工作流程
2. 选择你需要的功能模块开始创作

---

## 核心功能

### 创作功能

- ✅ **大纲设计** - 支持多卷结构，逐步完善
- ✅ **角色创建** - 生成详细角色卡和成长弧光
- ✅ **世界观构建** - 完整的多维设定系统
- ✅ **文风分析** - 分析范文或确定文风偏好
- ✅ **黄金三章** - 一口气生成前三章，确保高度连贯
- ✅ **续写创作** - 创作第4章及以后，防止跑题

### 质量控制

- ✅ **多维检查** - 对话、节奏、情感、主题、情节漏洞、世界观一致性
- ✅ **自动修复** - 60-80%的问题可自动修复
- ✅ **闭环验证** - 修复后自动验证，确保无新问题
- ✅ **简洁报告** - 清晰的问题分级和修复建议

### 项目管理

- ✅ **版本管理** - 完整的版本控制系统
- ✅ **反馈处理** - 灵活处理修改请求

---

## 文件结构

```
小说写作助手/
├── README.md                   # 项目说明（本文件）
├── AGENTS.md                  # 系统架构和工作流程
├── .opencode/
│   ├── agents/                # Agent定义（8个）
│   │   ├── outline_agent.md
│   │   ├── character_agent.md
│   │   ├── world_building_agent.md
│   │   ├── style_agent.md
│   │   ├── golden_three_chapters_agent.md
│   │   ├── continuation_agent.md
│   │   ├── quality_inspector_agent.md
│   │   ├── quality_fixer_agent.md
│   │   └── feedback_agent.md
│   └── skills/                # Skill工具定义（16个）
│       ├── interactive_guide/SKILL.md
│       ├── character_gen/SKILL.md
│       ├── style_format/SKILL.md
│       ├── chapter_prep/SKILL.md
│       ├── chapter_outline/SKILL.md
│       ├── dialogue_check/SKILL.md
│       ├── rhythm_check/SKILL.md
│       ├── emotion_check/SKILL.md
│       ├── theme_check/SKILL.md
│       ├── logic_check/SKILL.md
│       ├── setting_check/SKILL.md
│       ├── plot_check/SKILL.md
│       ├── character_consistency_check/SKILL.md
│       ├── timeline_check/SKILL.md
│       ├── world_consistency/SKILL.md
│       ├── auto_fix/SKILL.md
│       └── version_control/SKILL.md
├── output/                     # 输出文件（使用时创建）
│   ├── chapters/              # 章节文件
│   ├── style_guide.json       # 文风指南
│   └── reports/               # 详细报告
├── outline/                    # 大纲文件（使用时创建）
├── characters/                 # 角色文件（使用时创建）
├── world_building/             # 世界观文件（使用时创建）
└── versions/                   # 版本管理（使用时创建）
```

---

## 使用流程

### 完整创作流程

```
1. 大纲设计
   └─ outline Agent

2. 角色创建
   └─ character Agent

3. 世界观构建（可选）
   └─ world_building Agent

4. 文风确定
   └─ style Agent

5. 黄金三章创作
   └─ golden_three_chapters Agent
       └─ 自动质量检查与修复

6. 续写创作（第4章及以后）
   └─ continuation Agent
       ├─ chapter_prep Skill（准备）
       ├─ chapter_outline Skill（骨架+约束）
       ├─ 实时自检（每500字）
       └─ 自动质量检查与修复

7. 质量检查与修复
   ├─ quality_inspector Agent（检查）
   └─ quality_fixer Agent（修复）

8. 反馈修改
   └─ feedback Agent
```

---

## 核心理念

### Agent vs Skill

- **Agent**：负责创造性工作，需要与用户交互，做出创作决策
- **Skill**：作为工具使用，负责功能性任务（检查、格式化、分析），有明确的输入输出

### 防跑题机制

续写创作采用三层保障：
1. **骨架文约束**：明确章节结构
2. **强制约束清单**：禁止写的内容、必须达成的事件、限制条件
3. **实时自检**：每500字检查一次

---

## Agent说明

| Agent | 功能 | 何时使用 |
|-------|------|----------|
| **outline** | 大纲设计 | 需要创建或完善故事大纲 |
| **character** | 角色创建 | 需要创建角色卡 |
| **world_building** | 世界观构建 | 需要构建设定背景 |
| **style** | 文风分析 | 需要确定写作风格 |
| **golden_three_chapters** | 黄金三章创作 | 创作前三章内容 |
| **continuation** | 续写创作 | 创作第4章及以后内容 |
| **quality_inspector** | 质量检查 | 多维质量检查，识别并分类问题 |
| **quality_fixer** | 质量修复 | 自动修复问题，验证修复效果 |
| **feedback** | 反馈处理 | 需要处理修改请求 |

---

## Skill说明

| Skill | 功能 | 类型 |
|-------|------|------|
| **interactive_guide** | 交互式引导 | 引导工具 |
| **character_gen** | 角色卡格式化 | 格式化工具 |
| **style_format** | 文风格式化 | 格式化工具 |
| **chapter_prep** | 章节准备 | 创作工具 |
| **chapter_outline** | 章节骨架 | 创作工具 |
| **dialogue_check** | 对话自然度检查 | 检查工具 |
| **rhythm_check** | 节奏分析检查 | 检查工具 |
| **emotion_check** | 情感分析检查 | 检查工具 |
| **theme_check** | 主题分析检查 | 检查工具 |
| **logic_check** | 逻辑漏洞检查 | 检查工具 |
| **setting_check** | 设定漏洞检查 | 检查工具 |
| **plot_check** | 情节漏洞检查 | 检查工具 |
| **character_consistency_check** | 角色一致性检查 | 检查工具 |
| **timeline_check** | 时间线检查 | 检查工具 |
| **world_consistency** | 世界观一致性检查 | 检查工具 |
| **auto_fix** | 自动修复（批量执行修改方案） | 修复工具 |
| **version_control** | 版本管理 | 管理工具 |

---

## 最佳实践

1. **规划先行** - 充分利用大纲系统，提前规划好故事结构
2. **角色先行** - 创建详细的角色卡，为后续创作打好基础
3. **世界观可选** - 根据故事需要决定是否构建详细世界观
4. **定期检查** - 利用质量控制系统定期检查和改进
5. **版本管理** - 重要节点及时创建版本

---

## 常见问题

**Q: 我只有模糊的想法怎么办？**
A: 没问题，提供你想到的任何内容，系统会通过引导问题帮你完善。

**Q: 需要参考范文吗？**
A: 不需要，系统可以询问你的文风偏好来生成文风指南。

**Q: 可以创建复杂的世界观吗？**
A: 可以，世界观构建Agent支持多个维度的详细设定。

**Q: 创作过程中可以修改吗？**
A: 可以，在任何阶段都可以提出修改，系统会相应调整并保持一致性。

**Q: 每章字数是多少？**
A: 建议每章2000-5000字，可根据需要调整。

**Q: 支持多卷小说吗？**
A: 完全支持，大纲系统专门为多卷小说设计。

**Q: 如何保证质量？**
A: 系统有多层质量控制，包括：
- **10个维度检查**（对话、节奏、情感、主题、逻辑、设定、情节、角色、时间线、世界观）
- **自动修复**（60-80%的问题可自动修复，每个检查提供具体修改方案）
- **闭环验证**（修复后自动验证，确保无新问题）
- **防跑题机制**（骨架约束、强制约束清单、实时自检）
