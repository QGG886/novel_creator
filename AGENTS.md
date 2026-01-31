# 小说写作助手系统

基于多Agent协作的智能小说创作系统，帮助你从大纲到逐章创作完成高质量小说。

---

## 快速开始

1. 选择你需要的功能模块
2. 根据提示提供相关信息
3. 系统自动生成内容并保存

---

## 核心功能

### 创作功能

| Agent | 功能 | 说明 |
|-------|------|------|
| **outline** | 大纲设计 | 创建完整故事大纲，支持多卷结构 |
| **character** | 角色创建 | 生成详细角色卡和成长弧光 |
| **world_building** | 世界观构建 | 构建完整的多维设定系统 |
| **style** | 文风分析 | 分析范文或确定文风偏好 |
| **golden_three_chapters** | 黄金三章创作 | 一口气生成前三章，确保高度连贯 |
| **continuation** | 续写创作 | 创作第4章及以后，防止跑题 |

### 质量控制

| Agent | 功能 | 说明 |
|-------|------|------|
| **quality_inspector** | 质量检查 | 协调检查工具，识别并分类问题 |
| **quality_fixer** | 质量修复 | 自动修复问题，验证修复效果 |
| **feedback** | 反馈处理 | 处理修改请求，协调各Agent |

### Skill工具

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

## 文件结构

```
小说写作助手/
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
├── output/                     # 输出文件
│   ├── chapters/              # 章节文件
│   ├── style_guide.json       # 文风指南
│   └── reports/               # 详细报告
├── outline/                    # 大纲文件
├── characters/                 # 角色文件
├── world_building/             # 世界观文件
└── versions/                   # 版本管理
```

---

## 创作流程

### 阶段1：准备阶段

```
大纲设计
├─ outline Agent：创建完整大纲
└─ interactive_guide Skill：引导补充信息

角色创建
├─ character Agent：创建角色卡
└─ character_gen Skill：格式化输出

世界观构建
├─ world_building Agent：构建设定
└─ world_consistency Skill：检查一致性

文风确定
├─ style Agent：分析范文或收集偏好
└─ style_format Skill：格式化指南
```

### 阶段2：黄金三章创作

```
golden_three_chapters Agent
├─ 一口气生成前三章
├─ 确保高度连贯性
└─ 快速建立吸引人的开篇

质量检查与修复
├─ quality_inspector Agent：多维质量检查
│   ├─ dialogue_check Skill（对话）
│   ├─ rhythm_check Skill（节奏）
│   ├─ emotion_check Skill（情感）
│   ├─ theme_check Skill（主题）
│   ├─ logic_check Skill（逻辑）
│   ├─ setting_check Skill（设定）
│   ├─ plot_check Skill（情节）
│   ├─ character_consistency_check Skill（角色）
│   ├─ timeline_check Skill（时间线）
│   └─ world_consistency Skill（世界观）
└─ quality_fixer Agent：自动修复问题
    ├─ 批量执行修改方案（auto_fix Skill）
    └─ 验证修复效果
```

### 阶段3：续写创作（第4章及以后）

```
continuation Agent
├─ 阶段零：chapter_prep Skill（获取上下文）
│   ├─ 上下文分析
│   ├─ 伏笔安排
│   └─ 角色语音指导
│
├─ 阶段一：chapter_outline Skill（生成骨架）
│   ├─ 骨架文（开场、发展、高潮、结尾）
│   └─ 强制约束清单（防跑题）
│
├─ 阶段二：章节创作
│   ├─ 严格遵循骨架文结构
│   ├─ 严格遵守约束清单
│   └─ 实时自检每500字
│
└─ 阶段三：质量检查与修复
    ├─ quality_inspector Agent（检查）
    │   ├─ dialogue_check Skill
    │   ├─ rhythm_check Skill
    │   ├─ emotion_check Skill
    │   ├─ theme_check Skill
    │   ├─ logic_check Skill
    │   ├─ setting_check Skill
    │   ├─ plot_check Skill
    │   ├─ character_consistency_check Skill
    │   ├─ timeline_check Skill
    │   └─ world_consistency Skill
    └─ quality_fixer Agent（修复）
        ├─ 批量执行修改方案（auto_fix Skill）
        └─ 验证修复效果
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

### 质量保证

- **多维检查**：对话、节奏、情感、主题、情节漏洞、世界观一致性
- **自动修复**：60-80%的问题可自动修复
- **闭环验证**：修复后自动验证，确保无新问题
- **简洁报告**：清晰的问题分级和修复建议

---

## 使用建议

1. **按顺序使用**：先完成准备阶段，再进行章节创作
2. **保持连贯**：每个阶段都基于前一个阶段的成果
3. **及时检查**：利用质量检查工具及时发现问题
4. **灵活调整**：根据反馈随时修改和完善

---
