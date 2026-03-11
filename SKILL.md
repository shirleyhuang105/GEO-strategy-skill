---
name: geo-seo-strategy
description: B2B 内容策略生成器，根据产品信息和目标客户生成完整的 GEO/SEO 内容策略。触发条件：(1) 用户提供产品描述/文件/URL + 目标客户信息，并要求生成内容策略；(2) 用户提到"GEO 策略"、"SEO 策略"、"内容策略"、"内容规划"等关键词；(3) 用户要求进行竞品分析、关键词分析或内容主题规划。输出 Excel 格式的策略文档，包含竞品分析、关键词矩阵、内容主题规划三大板块。
---

# GEO/SEO 内容策略生成器

为 B2B 企业生成数据驱动的内容策略，通过竞品调研、关键词分析和内容规划，帮助企业在搜索引擎和 AI 搜索中获得更好的曝光。

## 工作流程

```
用户输入 → 信息收集 → 竞品调研 → 关键词分析 → 内容规划 → 生成 Excel 策略文档
```

### Step 1: 信息收集

从用户输入中提取：

**必需信息：**
- 产品/服务信息（文字描述、文件或 URL）
- 目标客户描述（行业、规模、角色、痛点）

**可选信息：**
- 已知竞品名称
- 目标市场/地区
- 内容语言偏好

**如果用户提供 URL**：使用 web_fetch 获取产品页面内容。

**如果用户上传文件**：读取文件提取关键产品信息。

**信息不完整时**：询问用户补充，但不要一次问太多问题。

### Step 2: 竞品调研

使用 web_search 进行系统性竞品调研：

**2.1 识别竞品**

```
搜索策略：
- "[产品类型] 解决方案"
- "[产品类型] 供应商 排名"
- "[产品类型] vs"
- "[行业] [产品类型] 厂商"
```

识别 5-8 个主要竞品，包括：
- 用户提供的竞品
- 搜索发现的直接竞品
- 间接竞品/替代方案

**2.2 分析竞品内容策略**

对每个主要竞品使用 web_fetch 分析其官网和博客：

收集信息：
- 核心价值主张
- 目标客户定位
- 内容主题分布
- 关键词使用策略
- 内容形式（博客、白皮书、案例等）

**2.3 竞品矩阵输出**

整理为结构化数据：

| 竞品名称 | 核心定位 | 目标客户 | 主要内容主题 | 内容形式 | 差异化点 |
|---------|---------|---------|-------------|---------|---------|

### Step 3: 关键词分析

使用 web_search 发现真实搜索趋势：

**3.1 核心关键词发现**

```
搜索策略：
- "[产品类型] 是什么"
- "[产品类型] 怎么选"
- "[产品类型] 最佳实践"
- "[痛点问题] 解决方案"
- "[行业] [场景] 工具"
```

**3.2 长尾关键词挖掘**

```
搜索策略：
- "[核心关键词] 教程"
- "[核心关键词] 对比"
- "[核心关键词] 价格"
- "[核心关键词] 案例"
- "如何 [动作] [对象]"
```

**3.3 关键词分类**

将关键词按搜索意图分类：

| 意图类型 | 说明 | 示例 |
|---------|------|------|
| 信息型 | 了解概念、学习知识 | "什么是 XX"、"XX 原理" |
| 导航型 | 寻找特定品牌/产品 | "XX 官网"、"XX 登录" |
| 商业型 | 比较评估、购买准备 | "XX vs YY"、"XX 排名" |
| 交易型 | 准备购买 | "XX 价格"、"XX 试用" |

**3.4 关键词矩阵输出**

| 关键词 | 搜索意图 | 预估搜索量 | 竞争度 | 优先级 | 对应内容类型 |
|-------|---------|-----------|-------|-------|-------------|

优先级判断标准：
- 高：与产品高度相关 + 商业意图明确 + 竞争适中
- 中：相关性中等 或 竞争较高
- 低：相关性低 或 信息型为主

### Step 4: 内容主题规划

基于关键词分析和竞品调研，规划内容主题：

**4.1 内容支柱确定**

确定 3-5 个内容支柱（Pillar），每个支柱对应：
- 一个核心主题领域
- 一组相关关键词
- 多篇子内容

**4.2 内容类型分配**

| 内容类型 | 目的 | 搜索意图匹配 | 示例 |
|---------|------|-------------|------|
| 概念解读 | 建立认知 | 信息型 | "什么是 XX"、"XX 入门指南" |
| 实践指南 | 提供价值 | 信息型 | "XX 最佳实践"、"如何实现 XX" |
| 对比评测 | 辅助决策 | 商业型 | "XX vs YY"、"XX 选型指南" |
| 案例分析 | 建立信任 | 商业型 | "XX 客户案例"、"XX 成功故事" |
| 趋势洞察 | 展示专业 | 信息型 | "XX 趋势"、"XX 未来发展" |

**4.3 内容规划输出**

| 内容标题 | 内容支柱 | 目标关键词 | 内容类型 | 买家旅程阶段 | 优先级 | 预估字数 |
|---------|---------|-----------|---------|-------------|-------|---------|

买家旅程阶段：
- 认知阶段 (Awareness)：发现问题
- 考虑阶段 (Consideration)：评估方案
- 决策阶段 (Decision)：选择供应商

### Step 5: 生成 Excel 策略文档

读取 xlsx skill 获取最佳实践：

```bash
view /mnt/skills/public/xlsx/SKILL.md
```

**5.1 文档结构**

创建包含以下 Sheet 的 Excel 文件：

**Sheet 1: 策略概览**
- 产品/服务简介
- 目标客户画像
- 核心价值主张
- 内容策略目标

**Sheet 2: 竞品分析**
- 竞品基本信息
- 竞品内容策略对比
- 差异化机会点

**Sheet 3: 关键词矩阵**
- 完整关键词列表
- 按意图分类
- 按优先级排序
- 关键词与内容映射

**Sheet 4: 内容主题规划**
- 内容支柱说明
- 详细内容列表
- 优先级和排期建议

**5.2 代码实现**

```python
from openpyxl import Workbook
from openpyxl.styles import Font, PatternFill, Alignment, Border, Side
from openpyxl.utils import get_column_letter

wb = Workbook()

# 定义样式
header_font = Font(bold=True, color='FFFFFF')
header_fill = PatternFill('solid', fgColor='4472C4')
subheader_fill = PatternFill('solid', fgColor='D6DCE5')
thin_border = Border(
    left=Side(style='thin'),
    right=Side(style='thin'),
    top=Side(style='thin'),
    bottom=Side(style='thin')
)

def style_header_row(sheet, row_num, col_count):
    for col in range(1, col_count + 1):
        cell = sheet.cell(row=row_num, column=col)
        cell.font = header_font
        cell.fill = header_fill
        cell.alignment = Alignment(horizontal='center', vertical='center')
        cell.border = thin_border

def auto_column_width(sheet):
    for column_cells in sheet.columns:
        max_length = 0
        column = column_cells[0].column_letter
        for cell in column_cells:
            if cell.value:
                max_length = max(max_length, len(str(cell.value)))
        sheet.column_dimensions[column].width = min(max_length + 2, 50)

# Sheet 1: 策略概览
ws1 = wb.active
ws1.title = '策略概览'
# ... 添加内容

# Sheet 2: 竞品分析
ws2 = wb.create_sheet('竞品分析')
# ... 添加内容

# Sheet 3: 关键词矩阵
ws3 = wb.create_sheet('关键词矩阵')
# ... 添加内容

# Sheet 4: 内容主题规划
ws4 = wb.create_sheet('内容主题规划')
# ... 添加内容

# 保存
wb.save('/mnt/user-data/outputs/content_strategy.xlsx')
```

**5.3 格式要求**

- 使用专业字体（Arial 或微软雅黑）
- 表头使用深色背景 + 白色文字
- 数据行使用交替底色增强可读性
- 自动调整列宽
- 冻结首行便于浏览
- 添加筛选器便于数据操作

## 输出交付

保存文件到 `/mnt/user-data/outputs/`，文件名格式：

```
[产品名称]_内容策略_[日期].xlsx
```

向用户呈现文件时，简要说明：
- 策略文档包含的内容
- 发现的关键洞察
- 建议的优先执行事项

## 注意事项

**搜索调研原则：**
- 每次搜索使用简洁的关键词（1-6 个词）
- 根据复杂度调整搜索次数（基础调研 3-5 次，深度调研 8-12 次）
- 优先使用原始来源（官网、官方博客）而非聚合站点

**内容规划原则：**
- 内容数量控制在 15-25 篇为宜
- 覆盖买家旅程全阶段
- 平衡信息型和商业型内容
- 考虑内容之间的内链关系

**B2B 特性考虑：**
- 关注决策链中的多个角色
- 内容要体现专业性和权威性
- 案例和数据是重要的信任信号
- 考虑长销售周期的内容培育需求
