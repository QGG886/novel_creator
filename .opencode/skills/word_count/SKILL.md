# 字数统计Skill

## 功能
通过读取实际的章节文件，统计准确的字数，包括中文字符、英文单词、标点符号等。确保字数统计的准确性，而不是基于估算。

## 使用场景
- 章节创作完成后统计字数
- 进度追踪时统计总字数
- 质量检查时验证字数范围
- 导出时生成字数报告

## 输入格式
```json
{
  "统计对象": "单个章节/多个章节/全书",
  "文件路径": {
    "单个章节": "output/chapters/第1卷_第1章_六人奇遇.md",
    "多个章节": [
      "output/chapters/第1卷_第1章_六人奇遇.md",
      "output/chapters/第1卷_第2章_初见炊烟.md"
    ],
    "全书": "output/chapters/"
  },
  "统计选项": {
    "统计中文": true,
    "统计英文": true,
    "统计标点": true,
    "统计空格": false,
    "统计空行": false
  }
}
```

## 输出格式
```json
{
  "状态": "成功",
  "统计结果": {
    "总字符数": 3500,
    "中文字符数": 3200,
    "英文字符数": 250,
    "标点符号数": 50,
    "空格数": 0,
    "空行数": 15,
    "有效字符数": 3500,
    "有效字数": 3450
  },
  "详细统计": [
    {
      "文件路径": "output/chapters/第1卷_第1章_六人奇遇.md",
      "文件名": "第1卷_第1章_六人奇遇.md",
      "总字符数": 3500,
      "中文字符数": 3200,
      "英文字符数": 250,
      "标点符号数": 50,
      "空格数": 0,
      "空行数": 15,
      "有效字符数": 3500,
      "有效字数": 3450
    }
  ],
  "字数范围检查": {
    "目标范围": "2000-5000",
    "实际字数": 3500,
    "是否符合": "符合"
  },
  "统计时间": "2026-01-29 17:00:00"
}
```

## 统计规则

### 字符分类
1. **中文字符**：
   - 范围：`\u4e00-\u9fff`（基本汉字）
   - 包括：简体中文、繁体中文
   - 统计方式：逐个字符计数

2. **英文字符**：
   - 范围：`a-zA-Z`
   - 包括：大写字母、小写字母
   - 统计方式：逐个字符计数

3. **标点符号**：
   - 中文标点：`，。！？；：""''（）【】《》`
   - 英文标点：`,.!?;:"'()[]{}`
   - 统计方式：逐个字符计数

4. **空格**：
   - 包括：普通空格、制表符、换行符
   - 统计方式：逐个字符计数

5. **空行**：
   - 定义：只包含空格、制表符的行
   - 统计方式：逐行检查

### 字数定义
1. **总字符数**：所有字符的总和（包括标点、空格）
2. **中文字符数**：中文字符的总和
3. **英文字符数**：英文字符的总和
4. **标点符号数**：标点符号的总和
5. **空格数**：空格的总和
6. **空行数**：空行的总和
7. **有效字符数**：总字符数 - 空格数（可选，根据统计选项）
8. **有效字数**：中文字符数 + 英文字符数 + 标点符号数（不含空格）

## 使用流程

### 第一步：读取文件
- 读取指定的章节文件
- 如果是多个章节，逐个读取
- 如果是全书，读取output/chapters/目录下所有章节文件

### 第二步：解析文件内容
- 读取文件的完整文本内容
- 识别并过滤掉Markdown标记（如标题、分隔线等）
- 保留正文内容用于统计

### 第三步：分类统计
- 统计中文字符数
- 统计英文字符数
- 统计标点符号数
- 统计空格数
- 统计空行数

### 第四步：计算结果
- 计算总字符数
- 计算有效字符数（根据统计选项）
- 计算有效字数
- 如果有目标范围，检查是否符合

### 第五步：生成报告
- 生成详细统计结果
- 生成字数范围检查结果
- 添加统计时间戳

## 统计脚本实现

### 方法一：Python脚本
```python
import re
import os

def count_chinese(text):
    """统计中文字符"""
    return len(re.findall(r'[\u4e00-\u9fff]', text))

def count_english(text):
    """统计英文字符"""
    return len(re.findall(r'[a-zA-Z]', text))

def count_punctuation(text):
    """统计标点符号"""
    chinese_punctuation = '，。！？；：""''（）【】《》'
    english_punctuation = ',.!?;:"\'()[]{}'
    punctuation = chinese_punctuation + english_punctuation
    return sum(1 for char in text if char in punctuation)

def count_spaces(text):
    """统计空格"""
    return len(re.findall(r'\s', text))

def count_empty_lines(text):
    """统计空行"""
    lines = text.split('\n')
    return sum(1 for line in lines if not line.strip())

def count_words(file_path, options):
    """统计字数"""
    with open(file_path, 'r', encoding='utf-8') as f:
        text = f.read()

    # 过滤Markdown标记
    text = re.sub(r'^#{1,6}\s.*$', '', text, flags=re.MULTILINE)  # 标题
    text = re.sub(r'^---*$', '', text, flags=re.MULTILINE)  # 分隔线
    text = re.sub(r'\*\*.*?\*\*', '', text)  # 加粗
    text = re.sub(r'\*.*?\*', '', text)  # 斜体
    text = re.sub(r'`[^`]*`', '', text)  # 代码

    total_chars = len(text)

    chinese_chars = count_chinese(text) if options['统计中文'] else 0
    english_chars = count_english(text) if options['统计英文'] else 0
    punctuation_chars = count_punctuation(text) if options['统计标点'] else 0
    spaces = count_spaces(text) if options['统计空格'] else 0
    empty_lines = count_empty_lines(text) if options['统计空行'] else 0

    valid_chars = total_chars - spaces if options['统计空格'] else total_chars
    valid_words = chinese_chars + english_chars + punctuation_chars

    return {
        '总字符数': total_chars,
        '中文字符数': chinese_chars,
        '英文字符数': english_chars,
        '标点符号数': punctuation_chars,
        '空格数': spaces,
        '空行数': empty_lines,
        '有效字符数': valid_chars,
        '有效字数': valid_words
    }
```

### 方法二：Node.js脚本
```javascript
const fs = require('fs');
const path = require('path');

function countChinese(text) {
    const matches = text.match(/[\u4e00-\u9fff]/g);
    return matches ? matches.length : 0;
}

function countEnglish(text) {
    const matches = text.match(/[a-zA-Z]/g);
    return matches ? matches.length : 0;
}

function countPunctuation(text) {
    const chinesePunctuation = '，。！？；：""''（）【】《》';
    const englishPunctuation = ',.!?;:"\'()[]{}';
    const punctuation = chinesePunctuation + englishPunctuation;
    let count = 0;
    for (const char of text) {
        if (punctuation.includes(char)) {
            count++;
        }
    }
    return count;
}

function countSpaces(text) {
    const matches = text.match(/\s/g);
    return matches ? matches.length : 0;
}

function countEmptyLines(text) {
    const lines = text.split('\n');
    return lines.filter(line => !line.trim()).length;
}

function countWords(filePath, options) {
    const text = fs.readFileSync(filePath, 'utf-8');

    // 过滤Markdown标记
    let filteredText = text
        .replace(/^#{1,6}\s.*$/gm, '')  // 标题
        .replace(/^---*$/gm, '')  // 分隔线
        .replace(/\*\*.*?\*\*/g, '')  // 加粗
        .replace(/\*.*?\*/g, '')  // 斜体
        .replace(/`[^`]*`/g, '');  // 代码

    const totalChars = filteredText.length;

    const chineseChars = options['统计中文'] ? countChinese(filteredText) : 0;
    const englishChars = options['统计英文'] ? countEnglish(filteredText) : 0;
    const punctuationChars = options['统计标点'] ? countPunctuation(filteredText) : 0;
    const spaces = options['统计空格'] ? countSpaces(filteredText) : 0;
    const emptyLines = options['统计空行'] ? countEmptyLines(filteredText) : 0;

    const validChars = options['统计空格'] ? totalChars - spaces : totalChars;
    const validWords = chineseChars + englishChars + punctuationChars;

    return {
        总字符数: totalChars,
        中文字符数: chineseChars,
        英文字符数: englishChars,
        标点符号数: punctuationChars,
        空格数: spaces,
        空行数: emptyLines,
        有效字符数: validChars,
        有效字数: validWords
    };
}
```

## 检查清单

### 文件读取
- [ ] 文件路径正确
- [ ] 文件编码正确（UTF-8）
- [ ] 文件存在且可读

### 内容解析
- [ ] 正确过滤Markdown标记
- [ ] 正确识别正文内容
- [ ] 不遗漏重要内容

### 统计准确性
- [ ] 中文字符统计准确
- [ ] 英文字符统计准确
- [ ] 标点符号统计准确
- [ ] 空格统计准确
- [ ] 空行统计准确

### 结果计算
- [ ] 总字符数计算正确
- [ ] 有效字符数计算正确
- [ ] 有效字数计算正确
- [ ] 字数范围检查正确

## 常见错误

### 文件读取错误
- **文件不存在**：文件路径错误或文件未创建
- **编码错误**：文件不是UTF-8编码
- **权限错误**：没有读取文件的权限

### 内容解析错误
- **过滤不完整**：Markdown标记过滤不完整
- **内容遗漏**：误将正文当作标记过滤
- **格式识别错误**：无法识别某些格式

### 统计错误
- **统计范围错误**：统计了不应该统计的内容
- **统计规则错误**：统计规则定义不清晰
- **计算错误**：有效字数计算错误

## 注意事项
1. 必须读取实际文件，不能基于估算
2. 使用UTF-8编码读取文件
3. 正确过滤Markdown标记
4. 统计规则要清晰明确
5. 多次统计要保证一致性
6. 统计结果要可验证
7. 注意不同系统的换行符差异
8. 考虑特殊字符的处理

## 与其他Skill的配合

- **progress_tracking**：调用word_count获取准确字数，更新进度
- **chapter_agent**：章节完成后调用word_count统计字数
- **export_formatter**：导出时生成字数报告
- **quality_check**：质量检查时验证字数范围

## 示例输出

```json
{
  "状态": "成功",
  "统计结果": {
    "总字符数": 3500,
    "中文字符数": 3200,
    "英文字符数": 250,
    "标点符号数": 50,
    "空格数": 0,
    "空行数": 15,
    "有效字符数": 3500,
    "有效字数": 3450
  },
  "详细统计": [
    {
      "文件路径": "output/chapters/第1卷_第1章_六人奇遇.md",
      "文件名": "第1卷_第1章_六人奇遇.md",
      "总字符数": 3500,
      "中文字符数": 3200,
      "英文字符数": 250,
      "标点符号数": 50,
      "空格数": 0,
      "空行数": 15,
      "有效字符数": 3500,
      "有效字数": 3450
    }
  ],
  "字数范围检查": {
    "目标范围": "2000-5000",
    "实际字数": 3450,
    "是否符合": "符合"
  },
  "统计时间": "2026-01-29 17:00:00"
}
```

## 更新日志

| 版本 | 日期 | 更新内容 |
|------|------|----------|
| 1.0 | 2026-01-29 | 初始版本，建立字数统计功能 |
