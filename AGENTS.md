# 小说写作助手(优化版)

## 项目定位
这是一个基于多Agent协作的智能小说写作助手，通过明确的职责分工和工具化Skill，帮助用户从大纲设计到逐章创作完成一部小说。

## 项目结构
- **Agent定义**：`.opencode/agents/` - 各Agent的详细定义文件
- **Skill定义**：`.opencode/skills/` - 各Skill的详细定义文件
- **主架构文档**：本文档(`AGENTS.md`)
- **通用规范**：`COMMON.md`
- **模板系统**：`templates.md`

## 核心理念

### Agent vs Skill
- **Agent**：负责创造性工作，需要与用户交互，做出创作决策
- **Skill**：作为工具使用，负责功能性任务(检查、格式化、分析)，有明确的输入输出

## Agent列表(创造性工作)

### 核心创作Agent
1. **outline_agent**：大纲设计
   - 理解用户想法，设计故事结构
   - 交互式引导，补充信息
   - 生成完整大纲

2. **character_agent**：角色创建
   - 设计角色性格和背景
   - 规划角色弧光
   - 建立关系网络

3. **world_building_agent**：世界观构建
   - 设计世界观框架
   - 构建多维设定
   - 确保自洽性

4. **style_agent**：文风分析
   - 分析范文或用户偏好
   - 生成文风指南
   - 提取典型示例

5. **chapter_agent**：章节编写
   - 创作章节内容
   - 融合多重信息
   - 确保连贯性

6. **dialogue_agent**：对话优化
   - 创作和优化对话
   - 设计角色声音
   - 提升对话自然度

### 质量控制Agent
7. **plot_review_agent**：情节审查
   - 全面审查情节
   - 识别逻辑问题
   - 提供优化方案

8. **continuity_agent**：连贯性检查
   - 检查设定一致
   - 验证角色一致
   - 检查时间线

### 编辑Agent
9. **editor_agent**：编辑润色
   - 语言优化
   - 文学润色
   - 结构优化

### 辅助Agent
10. **research_agent**：资料研究
    - 收集背景资料
    - 验证设定准确
    - 整理资料库

11. **feedback_agent**：反馈处理
    - 理解用户反馈
    - 协调修改
    - 追踪进度

## Skill列表(辅助工具)

### 格式化工具
1. **character_gen**：角色卡格式化
2. **style_format**：文风格式化
3. **chapter_write**：章节模板应用
4. **skeleton_outline**：骨架文生成

### 引导工具
5. **interactive_guide**：交互式引导
   - 生成引导性问题
   - 收集用户偏好
   - 辅助决策

### 分析工具
6. **chapter_context_analysis**：章节上下文分析
7. **foreshadowing_analysis**：伏笔分析
8. **character_voice_analysis**：角色语音分析
9. **plot_hole_detection**：情节漏洞检测
10. **world_consistency**：世界观一致性检查
11. **dialogue_naturalization**：对话自然度检查
12. **pacing_analysis**：节奏分析
13. **emotional_arc**：情感曲线分析
14. **theme_analysis**：主题分析
15. **character_arc_tracking**：角色弧光追踪

### 管理工具
16. **version_control**：版本管理
17. **export_formatter**：多格式导出
18. **progress_tracking**：进度追踪
19. **word_count**：字数统计



## Agent与Skill交互关系

### 交互原则
1. **Agent主导**：Agent负责核心工作，Skill作为工具被调用
2. **按需调用**：只在需要时调用相关Skill
3. **工具定位**：Skill有明确的输入输出，标准化执行

### 典型交互流程

#### 1. 大纲设计阶段
```
outline_agent (主)
  ↓ 使用
interactive_guide (生成引导问题)
  ↓ 使用
plot_hole_detection (检查漏洞)
  ↓ 使用
pacing_analysis (分析节奏)
```

#### 2. 角色创建阶段
```
character_agent (主)
  ↓ 使用
interactive_guide (生成引导问题)
  ↓ 使用
character_gen (格式化角色卡)
  ↓ 使用
character_arc_tracking (追踪弧光)
```

#### 3. 世界观构建阶段
```
world_building_agent (主)
  ↓ 使用
research_agent (收集资料)
  ↓ 使用
world_consistency (检查一致性)
```

#### 4. 文风确定阶段
```
style_agent (主)
  ↓ 使用
interactive_guide (收集用户偏好)
  ↓ 使用
style_format (格式化文风指南)
```

#### 5. 章节创作阶段
```
# 前两章（简化）
预创作分析：
  ↓ 使用
character_voice_analysis (分析角色语音)

创作阶段：
  ↓ 使用
chapter_agent (主)
  ↓ 使用
chapter_write (应用模板)
  ↓ 使用
dialogue_agent (优化对话)

质量检查：
  ↓ 使用
dialogue_naturalization (检查对话自然度)
  ↓ 使用
plot_hole_detection (检测漏洞)
  ↓ 使用
world_consistency (检查设定)
  ↓ 使用
continuity_agent (检查连贯性)
  ↓ 使用
pacing_analysis (分析节奏)
  ↓ 使用
theme_analysis (分析主题)
  ↓ 使用
emotional_arc (分析情感)

编辑润色：
  ↓ 使用
editor_agent (主)
  ↓ 使用
dialogue_naturalization (优化对话)
  ↓ 使用
plot_hole_detection (检查问题)

# 从第3章开始（完整）
预创作分析：
  ↓ 使用
chapter_context_analysis (分析上下文)
  ↓ 使用
foreshadowing_analysis (分析伏笔)
  ↓ 使用
character_voice_analysis (分析角色语音)
  ↓ 使用
skeleton_outline (生成骨架文)

创作阶段：
  ↓ 使用
chapter_agent (主)
  ↓ 使用
chapter_write (基于骨架文创作)
  ↓ 使用
dialogue_agent (优化对话)

质量检查：
  ↓ 使用
dialogue_naturalization (检查对话自然度)
  ↓ 使用
plot_hole_detection (检测漏洞)
  ↓ 使用
world_consistency (检查设定)
  ↓ 使用
continuity_agent (检查连贯性)
  ↓ 使用
pacing_analysis (分析节奏)
  ↓ 使用
theme_analysis (分析主题)
  ↓ 使用
emotional_arc (分析情感)

编辑润色：
  ↓ 使用
editor_agent (主)
  ↓ 使用
dialogue_naturalization (优化对话)
  ↓ 使用
plot_hole_detection (检查问题)

章节后续处理：
  ↓ 使用
version_control (保存版本)
  ↓ 使用
word_count (统计字数)
  ↓ 使用
progress_tracking (更新进度)
```

#### 6. 全面审查阶段
```
plot_review_agent (主)
continuity_agent (主)
  ↓ 使用
plot_hole_detection
  ↓ 使用
world_consistency
  ↓ 使用
theme_analysis
  ↓ 使用
emotional_arc
  ↓ 使用
pacing_analysis
  ↓ 使用
character_arc_tracking
```

#### 7. 编辑润色阶段
```
editor_agent (主)
  ↓ 使用
dialogue_naturalization
  ↓ 使用
plot_hole_detection
```

#### 8. 导出和交付阶段
```
feedback_agent (协调)
  ↓ 使用
version_control
  ↓ 使用
export_formatter
  ↓ 使用
progress_tracking
```

## 完整工作流程

### 阶段零：项目初始化
1. 加载模板 `templates.md`
2. 读取通用规范 `COMMON.md`
3. 确认项目基本信息

### 阶段一：需求分析
1. 调用 `interactive_guide` 生成引导问题
2. 收集用户的初始想法
3. 确定项目规模和类型
4. 制定工作计划

### 阶段二：大纲设计
1. 调用 `outline_agent` 设计大纲
   - 使用 `interactive_guide` 补充信息
   - 使用 `plot_hole_detection` 检查漏洞
   - 使用 `pacing_analysis` 分析节奏
2. 保存大纲到 `outline/` 文件夹
3. 调用 `version_control` 创建版本

### 阶段三：角色创建
1. 从大纲提取角色需求
2. 调用 `character_agent` 创建角色
   - 使用 `interactive_guide` 了解偏好
   - 使用 `character_gen` 格式化角色卡
   - 使用 `character_arc_tracking` 追踪弧光
3. 保存角色卡到 `characters/` 文件夹

### 阶段四：世界观构建(可选)
1. 识别世界观需求
2. 调用 `research_agent` 收集资料
3. 调用 `world_building_agent` 构建设定
4. 调用 `world_consistency` 验证一致性
5. 保存设定到 `world_building/` 文件夹

### 阶段五：文风确定
1. 检查是否有范文
2. 有范文：调用 `style_agent` 分析
   - 使用 `style_format` 格式化指南
3. 无范文：调用 `interactive_guide` 收集偏好
   - 调用 `style_agent` 生成指南
   - 使用 `style_format` 格式化指南
4. 保存文风指南到 `output/style_guide.json`

### 阶段六：预创作检查
1. 调用 `plot_hole_detection` 检查大纲
2. 调用 `pacing_analysis` 分析节奏
3. 调用 `theme_analysis` 识别主题
4. 生成预创作报告

### 阶段七：逐章创作与质量检查
对每章执行：

#### 1. 前两章（简化流程）

**1.1 预创作分析**：
- 使用 `character_voice_analysis` 分析角色语音
  - 输入：角色卡、文风指南
  - 输出：角色声音特征报告

**1.2 创作阶段**：
- 调用 `chapter_agent` 创作章节
  - 使用 `chapter_write` 应用模板
  - 使用 `dialogue_agent` 优化对话

**1.3 章节质量检查**：
- 使用 `dialogue_naturalization` 检查对话自然度
- 使用 `plot_hole_detection` 检测漏洞
- 使用 `world_consistency` 检查设定
- 使用 `continuity_agent` 检查连贯性（局部：本章与前后章节）
- 使用 `pacing_analysis` 分析节奏（局部：本章节奏）
- 使用 `theme_analysis` 分析主题（局部：本章主题）
- 使用 `emotional_arc` 分析情感（局部：本章情感）

**1.4 章节编辑润色**：
- 使用 `editor_agent` 编辑润色
  - 使用 `dialogue_naturalization` 优化对话（基于检查结果）
  - 使用 `plot_hole_detection` 检查问题（基于检查结果）

#### 2. 从第3章开始（完整流程）

**2.1 预创作分析**（为创作做准备）：
- 使用 `chapter_context_analysis` 分析上下文
  - 输入：本卷大纲、前后各两章内容、角色卡、世界观
  - 输出：上下文分析报告（关键信息、需要承接的内容、伏笔回收点）
- 使用 `foreshadowing_analysis` 分析伏笔
  - 输入：本卷大纲、已完成的伏笔记录
  - 输出：伏笔分析报告（需要埋设的新伏笔、需要回收的旧伏笔）
- 使用 `character_voice_analysis` 分析角色语音
  - 输入：角色卡、文风指南、本章出场角色
  - 输出：角色声音特征报告
- 使用 `skeleton_outline` 生成骨架文
  - 输入：本章大纲、上下文分析、伏笔分析、角色语音分析
  - 输出：章节骨架文（情节结构、关键场景、对话要点）

**2.2 创作阶段**（基于分析结果创作）：
- 调用 `chapter_agent` 创作章节
  - 使用 `chapter_write` 基于骨架文创作
  - 使用 `dialogue_agent` 优化对话

**2.3 章节质量检查**：
- 使用 `dialogue_naturalization` 检查对话自然度
- 使用 `plot_hole_detection` 检测漏洞
- 使用 `world_consistency` 检查设定
- 使用 `continuity_agent` 检查连贯性（局部：本章与前后章节）
- 使用 `pacing_analysis` 分析节奏（局部：本章节奏）
- 使用 `theme_analysis` 分析主题（局部：本章主题）
- 使用 `emotional_arc` 分析情感（局部：本章情感）

**2.4 章节编辑润色**（基于检查结果优化）：
- 使用 `editor_agent` 编辑润色
  - 使用 `dialogue_naturalization` 优化对话（基于检查结果）
  - 使用 `plot_hole_detection` 检查问题（基于检查结果）

#### 3. 章节后续处理

**每章完成后**：
1. 呈现给用户确认
2. 保存到 `output/chapters/`
3. 调用 `word_count` 统计字数
4. 调用 `progress_tracking` 更新进度

5. 呈现给用户确认
6. 保存到 `output/chapters/`
7. 调用 `word_count` 统计字数
8. 调用 `progress_tracking` 更新进度

每卷完成时：
1. **卷级质量检查**：
   - 调用 `continuity_agent` 检查连贯性（整卷）
   - 调用 `pacing_analysis` 分析节奏（整卷）
   - 调用 `character_arc_tracking` 追踪角色（整卷）
   - 调用 `theme_analysis` 分析主题（整卷）
   - 调用 `emotional_arc` 分析情感（整卷）
2. 调用 `version_control` 创建版本
3. 生成卷完成报告

### 阶段八：全面审查（全书完成后）
1. 调用 `plot_review_agent` 审查情节（全书）
2. 调用 `continuity_agent` 检查连贯性（全书）
3. 调用 `plot_hole_detection` 检测漏洞（全书）
4. 调用 `theme_analysis` 分析主题（全书）
5. 调用 `emotional_arc` 分析情感（全书）
6. 调用 `pacing_analysis` 分析节奏（全书）
7. 调用 `character_arc_tracking` 追踪角色（全书）
8. 生成全面审查报告

### 阶段九：编辑润色（全书完成后）
1. 调用 `editor_agent` 进行全局编辑
    - 使用 `dialogue_naturalization` 优化对话（全局优化）
    - 使用 `plot_hole_detection` 检查问题（全局检查）
2. 生成编辑报告

### 阶段十：最终检查
1. 调用所有检查工具进行最后检查
2. 验证所有质量指标
3. 生成最终检查报告

### 阶段十一：导出和交付
1. 调用 `version_control` 创建最终版本
2. 调用 `export_formatter` 导出多种格式
3. 调用 `progress_tracking` 生成项目总结
4. 保存到 `exports/` 文件夹

## 通用规范

所有Agent和Skill遵循 `COMMON.md` 中的：
- 输入输出规范
- 质量检查清单
- 工作流程标准
- 注意事项

## 输出文件结构

```
project/
├── AGENTS.md                  # 系统架构文档
├── COMMON.md                  # 通用规范
├── templates.md               # 模板系统
├── README.md                  # 项目说明
├── .opencode/
│   ├── agents/                # Agent定义
│   └── skills/                # Skill工具定义
├── output/
│   ├── style_guide.json       # 文风指南
│   ├── progress.json          # 进度记录
│   ├── chapters/              # 章节文件
│   └── reports/               # 各类报告
├── outline/                   # 大纲文件
│   ├── 第1卷_卷标题.md
│   └── ...
├── characters/                # 角色文件
│   ├── 角色名1.md
│   └── ...
├── world_building/            # 世界观文件
│   ├── world_overview.md
│   └── ...
├── research/                  # 研究资料
├── versions/                  # 版本管理
├── exports/                   # 导出文件
└── reference/                 # 参考范文
```

## 使用说明

### 第一次使用
1. 阅读 `COMMON.md` 了解通用规范
2. 阅读 `templates.md` 了解可用模板
3. 从阶段一开始，逐步完成

### 中断后继续
所有内容保存在输出目录，进度自动追踪。可从任意阶段继续。

### 获取帮助
- 阅读各个Agent和Skill的定义文件
- 查看 `COMMON.md` 的通用规范
- 参考示例和模板

## 优化亮点

1. **职责清晰**：Agent负责创造性工作，Skill负责工具化任务
2. **交互明确**：Agent和Skill的调用关系清晰
3. **简化重复**：通用规范提取到COMMON.md
4. **便于扩展**：新功能可以作为新Agent或Skill添加
5. **保持本质**：仍然是提示词系统，不是code项目
6. **流程合理**：分析→创作→检查→优化，逻辑清晰
7. **前两章简化**：前两章使用简化流程，快速进入创作
8. **从第3章深度分析**：从第3章开始使用完整流程，确保质量
9. **预创作分析**：所有分析工具在创作之前使用，为创作提供依据
10. **多维度分析**：结合本卷大纲、前后章节、伏笔、角色语音、骨架文
11. **角色一致性保障**：通过角色语音分析确保角色言行一致
12. **伏笔管理**：通过伏笔分析确保伏笔的合理埋设和回收
13. **质量循环**：创作→检查→优化，形成完整的质量保障闭环
