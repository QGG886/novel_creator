# 小说写作助手

基于多Agent协作的智能小说写作系统，帮助你从大纲到逐章创作完成高质量小说。

## 快速开始

1. 阅读 **AGENTS.md** 了解系统架构和工作流程

## 核心功能

### 创作功能
- ✅ 交互式大纲设计 - 支持多卷结构，逐步完善
- ✅ 智能角色创建 - 生成详细角色卡和成长弧光
- ✅ 世界观构建 - 完整的多维设定系统
- ✅ 文风分析 - 分析范文或确定文风偏好
- ✅ 逐章创作 - 按大纲和文风自动写作
- ✅ 对话优化 - 提升对话自然度和角色声音

### 质量控制
- ✅ 情节审查 - 全面检查逻辑和漏洞
- ✅ 连贯性检查 - 确保设定、角色、时间一致
- ✅ 编辑润色 - 专业的语言和结构优化
- ✅ 节奏分析 - 分析叙事节奏
- ✅ 情感分析 - 分析情感曲线
- ✅ 主题分析 - 识别和评估主题

### 项目管理
- ✅ 版本管理 - 完整的版本控制系统
- ✅ 进度追踪 - 实时记录章节和字数进度
- ✅ 字数统计 - 基于实际文件的准确字数统计
- ✅ 多格式导出 - 支持 Markdown、PDF、EPUB、DOCX 等
- ✅ 反馈处理 - 灵活处理修改请求

## 文件结构

```
小说写作助手/
├── README.md                   # 项目说明
├── AGENTS.md                  # 系统架构和工作流程
├── .opencode/                 # OpenCode标准目录
│   ├── agents/                # Agent定义（8个）
│   │   ├── outline_agent.md
│   │   ├── character_agent.md
│   │   ├── world_building_agent.md
│   │   ├── style_agent.md
│   │   ├── golden_three_chapters_agent.md
│   │   ├── continuation_agent.md
│   │   ├── quality_agent.md
│   │   └── feedback_agent.md
│   └── skills/                # Skill工具定义（10个）
│       ├── character_gen/SKILL.md
│       ├── style_format/SKILL.md
│       ├── chapter_write/SKILL.md
│       ├── chapter_outline/SKILL.md
│       ├── interactive_guide/SKILL.md
│       ├── chapter_prep/SKILL.md
│       ├── auto_check/SKILL.md
│       ├── plot_hole_detection/SKILL.md
│       ├── world_consistency/SKILL.md
│       └── version_control/SKILL.md
├── outline/                    # 大纲文件（使用时创建）
├── characters/                 # 角色文件（使用时创建）
├── world_building/             # 世界观文件（使用时创建）
├── output/                     # 输出文件（使用时创建）
│   ├── chapters/
│   └── reports/
├── research/                   # 研究资料（使用时创建）
├── versions/                   # 版本管理（使用时创建）
├── exports/                    # 导出文件（使用时创建）
└── reference/                  # 参考范文（使用时创建）
```

## 使用流程

### 基本流程

1. **项目初始化** - 配置项目基本信息
2. **需求分析** - 提供初始想法或大纲
3. **大纲设计** - 创建完整故事大纲
4. **角色创建** - 生成详细角色设定
5. **世界观构建**（可选）- 构建详细世界观
6. **文风确定** - 确定写作风格
7. **逐章创作** - 按顺序创作各章节
8. **编辑润色** - 优化语言和结构
9. **导出交付** - 导出多种格式

### 核心理念

**Agent vs Skill**

- **Agent**：负责创造性工作，需要与用户交互，做出创作决策
- **Skill**：作为工具使用，负责功能性任务（检查、格式化、分析），有明确的输入输出

### Agent说明

| Agent | 功能 | 何时使用 |
|-------|------|----------|
| outline_agent | 大纲设计 | 需要创建或完善故事大纲 |
| character_agent | 角色创建 | 需要创建角色卡 |
| world_building_agent | 世界观构建 | 需要构建设定背景 |
| style_agent | 文风分析 | 需要确定写作风格 |
| golden_three_chapters_agent | 黄金三章创作 | 创作前三章内容 |
| continuation_agent | 续写创作 | 创作第4章及以后内容 |
| quality_agent | 质量控制 | 检查情节漏洞和世界观矛盾 |
| feedback_agent | 反馈处理 | 需要处理修改请求 |

### Skill说明

| Skill | 功能 | 类型 |
|-------|------|------|
| character_gen | 角色卡格式化 | 格式化工具 |
| style_format | 文风格式化 | 格式化工具 |
| chapter_write | 章节模板应用 | 格式化工具 |
| interactive_guide | 交互式引导 | 引导工具 |
| plot_hole_detection | 情节漏洞检测 | 检查工具 |
| world_consistency | 世界观一致性 | 检查工具 |
| dialogue_naturalization | 对话自然度检查 | 检查工具 |
| pacing_analysis | 节奏分析 | 分析工具 |
| emotional_arc | 情感曲线分析 | 分析工具 |
| theme_analysis | 主题分析 | 分析工具 |
| character_arc_tracking | 角色弧光追踪 | 分析工具 |
| version_control | 版本管理 | 管理工具 |
| export_formatter | 多格式导出 | 管理工具 |
| progress_tracking | 进度追踪 | 管理工具 |
| word_count | 字数统计 | 管理工具 |

## 常见问题

**Q: 我只有模糊的想法怎么办？**
A: 没问题，提供你想到的任何内容，Agent会通过引导问题帮你完善。

**Q: 需要参考范文吗？**
A: 不需要，Agent可以询问你的文风偏好来生成文风指南。

**Q: 可以创建复杂的世界观吗？**
A: 可以，世界观构建Agent支持多个维度的详细设定。

**Q: 创作过程中可以修改吗？**
A: 可以，在任何阶段都可以提出修改，Agent会相应调整并保持一致性。

**Q: 每章字数是多少？**
A: 建议每章2000-5000字，可根据需要调整。

**Q: 支持多卷小说吗？**
A: 完全支持，大纲系统专门为多卷小说设计。

**Q: 如何保证质量？**
A: 系统有多层质量控制，包括情节审查、连贯性检查、漏洞检测等。

**Q: 可以导出哪些格式？**
A: 支持Markdown、文本、HTML、PDF、EPUB、DOCX等多种格式。

## 最佳实践

1. **规划先行** - 充分利用大纲系统，提前规划好故事结构
2. **角色先行** - 创建详细的角色卡，为后续创作打好基础
3. **世界观可选** - 根据故事需要决定是否构建详细世界观
4. **定期检查** - 利用质量控制系统定期检查和改进
5. **版本管理** - 重要节点及时创建版本
6. **进度追踪** - 保持进度追踪，了解创作状态
7. **质量第一** - 充分利用各种质量控制工具

## 技术说明

这是一个基于提示词的系统，不是代码项目。所有Agent和Skill都通过自然语言指令工作。

- **8个核心Agent** - 负责创造性任务
- **10个Skill工具** - 负责功能性任务
- **通用规范** - 统一的输入输出和质量标准

## 开始创作

现在你可以开始创作你的小说了！这个强大的系统将帮助你完成高质量的作品。

如需更详细的技术说明，请阅读 **AGENTS.md** 文件。
