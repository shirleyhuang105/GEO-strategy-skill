# GEO/SEO Content Strategy Generator — Claude Skill

A Claude custom skill that generates data-driven B2B content strategies through competitor research, keyword analysis, and content planning. Outputs a structured Excel strategy document ready for execution.

## What It Does

Given a product/service description and target customer profile, this skill:

1. **Competitor Research** — Identifies 5-8 competitors, analyzes their content strategies, finds differentiation gaps
2. **Keyword Analysis** — Discovers core and long-tail keywords, classifies by search intent, prioritizes by business value
3. **Content Planning** — Defines content pillars, maps topics to buyer journey stages, sets priorities and scheduling
4. **Excel Output** — Delivers a 4-sheet strategy workbook ready for team execution

### Output

A professional `.xlsx` file with 4 sheets:

| Sheet | Contents |
|-------|----------|
| **策略概览** (Strategy Overview) | Product summary, target customer profile, value proposition, strategy goals |
| **竞品分析** (Competitor Analysis) | Competitor matrix, content strategy comparison, differentiation opportunities |
| **关键词矩阵** (Keyword Matrix) | Full keyword list by intent, priority ranking, content type mapping |
| **内容主题规划** (Content Plan) | Content pillars, detailed topic list, buyer journey mapping, publishing schedule |

## File Structure

```
geo-seo-strategy-skill/
├── SKILL.md                              # Main skill instructions (workflow)
├── references/
│   ├── competitor-analysis.md            # Competitor research framework
│   ├── keyword-analysis.md               # B2B keyword strategy guide
│   └── content-planning.md               # Content pillar & buyer journey mapping
├── README.md
└── LICENSE
```

## How to Use

### In Claude.ai (with Skills feature)

1. Upload this folder as a custom skill in Claude
2. Provide your product info + target customer, then ask for a content strategy
3. Examples:
   - "Here's our product page [URL]. Our target customers are mid-size e-commerce companies. Generate a content strategy."
   - "GEO 策略：我们是做企业短信服务的，目标客户是电商和物流行业"
   - "帮我做一个内容规划，产品资料在附件里"

### Trigger Keywords

The skill activates on: `GEO 策略`, `SEO 策略`, `内容策略`, `内容规划`, `content strategy`, `keyword analysis`, `竞品分析`, `关键词分析`, or when you provide product materials and ask for a content plan.

### Required Input

- **Product/service info** (text description, file upload, or URL)
- **Target customer description** (industry, company size, roles, pain points)

### Optional Input

- Known competitor names
- Target market/region
- Content language preference

## Key Frameworks

### Search Intent Classification

| Intent | Description | Example Keywords | Content Match |
|--------|-------------|-----------------|---------------|
| Informational | Learning, research | "什么是 XX", "XX 入门" | Guides, explainers |
| Navigational | Finding specific pages | "XX 官网", "XX 文档" | Product pages, docs |
| Commercial | Evaluating options | "XX vs YY", "XX 排名" | Comparisons, reviews |
| Transactional | Ready to act | "XX 价格", "XX 试用" | Pricing, demo pages |

### Keyword Priority Scoring

Score = Relevance × 0.4 + Business Value × 0.35 + Competition × 0.25

- **High priority** (≥ 3.5): Execute immediately
- **Medium** (2.5–3.4): Plan for next quarter
- **Low** (< 2.5): Backlog

### Buyer Journey Content Mix

- Awareness stage: 40%
- Consideration stage: 35%
- Decision stage: 25%

## Content Planning Principles

- 15-25 topics per strategy (quality over quantity)
- Cover all buyer journey stages
- Balance informational and commercial content
- Plan internal linking between content pillars
- Suggested publishing cadence: 1-2 high-quality pieces per week

## Customization

Edit the reference files to adapt:

- **`references/competitor-analysis.md`** — Adjust competitor analysis dimensions and templates
- **`references/keyword-analysis.md`** — Modify priority scoring weights, add industry-specific keyword patterns
- **`references/content-planning.md`** — Change content type ratios, buyer journey definitions, pillar strategies

## Requirements

- Claude Pro / Team / Enterprise subscription (for custom skills)
- `openpyxl` (automatically available in Claude's environment)

## Related Skills

- **[GEO Expert](https://github.com/shirleyhuang105/GEO-skill)** — After generating your content strategy, use GEO Expert to write individual articles optimized for AI search citations

## License

MIT License — see [LICENSE](./LICENSE) for details.

## About

Created for B2B product marketing workflows. Works across industries — cloud computing, SaaS, CPaaS, and any B2B technology product that needs a systematic content strategy.
