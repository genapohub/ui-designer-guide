# 设计系统架构师专家蒸馏 · Design.md Architect（规范范）

> **来源**：WorkBuddy 专家中心「规范范·设计系统架构师」专家包蒸馏（2026-09-06）
> **源包**：`~/.workbuddy/plugins/marketplaces/experts/plugins/design-md-architect/agents/design-md-architect.md`（241 行）
> **蒸馏方式**：并入 ui-designer-guide 的 expert-distill。
> **去重说明**：Design Token 四层架构、组件状态、像素级执行已由像素君引擎（design-tokens.md + design-quality/）覆盖；本文档**只保留增量**——DESIGN.md 9 章标准结构（AI 可消费的设计契约文档）、58 品牌参考速查、风格混搭配方、设计规范质量自检。

---

## 一、DESIGN.md 9 章标准结构（AI 可消费的设计契约）

> 用途：把"视觉意图"转成**结构化 Markdown 设计规范**，Cursor/Claude Code 等 AI 代理可直接消费——一份文档同时服务设计师和 AI 编程工具。

```
1. Visual Theme & Atmosphere   视觉主题与氛围（设计哲学/基调/3-5 关键词/光影质感倾向）
2. Color Palette & Roles       调色板与角色（主色/品牌&深色/强调/中性/表面/语义/阴影——每色 HEX+CSS 变量+场景）
3. Typography Rules            排版规则（字体族/Type Scale 全层级表：Size/Weight/LineHeight/LetterSpacing）
4. Component Stylings          组件样式（Button 4 变体/Card/Input/Nav/Badge/Modal 精确 CSS 参数）
5. Layout Principles           布局原则（间距基数/网格/Container/Section 间距/留白哲学）
6. Depth & Elevation           深度与层级（shadow-xs→2xl 完整值/Surface 层级/Z-index/毛玻璃参数）
7. Do's and Don'ts             设计规范与禁忌（各 5-8 条，覆盖色彩/排版/间距/组件/动画）
8. Responsive Behavior         响应式行为（断点/触摸目标/折叠策略/字体缩放）
9. Agent Prompt Guide          AI 提示指南（快速参考 + 5+ 组件 Prompt 示例 + 8-10 条迭代建议）
```

**输出规范**：文件名大写 `DESIGN.md`；色值双格式（HEX + CSS 变量）；px 为主 rem 为辅；Type Scale 用表格；目标 280-350 行高信息密度；**精确性第一**（禁"大约/差不多"）；各章节数值一致。

**质量自检 6 项**：章节完整？色值全精确？Type Scale 四要素齐？组件有可用 CSS？Shadow 有完整 box-shadow？Agent Prompt Guide 有可用示例？

---

## 二、58 品牌参考速查（按 8 行业分类）

| 行业 | 品牌 |
|------|------|
| **AI & 大模型**（11） | claude / cohere / minimax / mistral.ai / ollama / opencode.ai / replicate / runwayml / together.ai / x.ai / elevenlabs |
| **开发者工具 & IDE**（16） | cursor / expo / figma / framer / hashicorp / linear.app / lovable / mintlify / raycast / sentry / supabase / vercel / warp / webflow / composio / voltagent |
| **生产力 & SaaS**（10） | airtable / intercom / miro / cal / posthog / resend / sanity / semrush / zapier / superhuman |
| **科技巨头**（3） | apple / ibm / nvidia |
| **汽车**（5） | bmw / ferrari / lamborghini / renault / tesla |
| **金融科技 & 加密**（5） | coinbase / kraken / revolut / wise / stripe |
| **消费互联网**（4） | airbnb / pinterest / spotify / uber |
| **其他**（4） | clay / clickhouse / mongodb / spacex |

**用法**：选 1-3 个最匹配品牌做参考基础；支持**跨品牌混搭**（"Stripe 的色彩 + Apple 的排版 + Tesla 的组件"——分别提取对应章节）。参考品牌但不抄袭——生成的是用户项目自己的设计系统。

---

## 三、品牌匹配工作流（定风格）

1. 明确项目类型（SaaS 仪表板/电商/官网…）+ 风格倾向（指定品牌 / 描述感觉 / 混搭）+ 特殊要求（品牌色/字体/已有资产）
2. 从 58 品牌选 1-3 个匹配基准
3. 按 9 章生成（色值精确到 HEX/rgba；组件给可直接用的 CSS 参数）
4. 质量审核（6 项自检）
5. 交付 `DESIGN.md` 到项目根目录 + 说明参考品牌与核心决策理由

---

## 四、设计交付模式（要页面/组件，不要文档时）

有 DESIGN.md → 读作约束直出；没有 → 先快速生成精简版 DESIGN.md 再输出。交付物 = **自包含 HTML/CSS（内联样式，浏览器直接打开）**，严格遵循文档中色彩/排版/间距/阴影系统，响应式适配三端，语义化可维护，Tailwind class 与设计规范对应。

---

## 五、与 ui-designer-guide 原生体系及蒸馏的配合

| 场景 | 用哪个 |
|------|--------|
| UX 方法论 / 像素君视觉执行 / 设计转代码 | 原生引擎（主） |
| 动手前定标杆（寄存器/速配/评审顺序） | mvp-designer-蒸馏（颜好看） |
| **项目级 DESIGN.md 设计契约文档（9 章标准）/ 58 品牌速查 / 风格混搭 / AI 可读交付** | **本文档（增量，唯一来源）** |

> **使用原则**：项目需要"设计规范文档 + AI 可直接消费的设计契约"或"快速参照知名品牌风格"时用本文档；需要品牌/产品级风格方向时先查第二节 58 品牌速查定位参考，再按 9 章结构产出 DESIGN.md。

---

_蒸馏记录：v1.0（2026-09-06）· 专家「规范范」→ ui-designer-guide/expert-distill/_
