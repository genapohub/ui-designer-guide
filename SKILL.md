---
name: ui-designer-guide
description: UI 设计师方案与执行一体化指南——上游「UX 方案方法论」（5 类场景识别/产出清单/交付标准）与下游「像素君视觉执行引擎」（Design System First/美学手艺/像素级界面/设计转代码）按任务链路编排在单一技能内。当需要 UI 设计全链路产出时触发：从需求/PRD 出设计方案文档，再到可看的美观界面稿与高保真实现，一次走完"方案不美、出稿难看"的断链。覆盖：App/Web/小程序界面设计、按 PRD 出 UI 稿、设计系统/Token/组件库、像素级还原、暗色主题换肤、无障碍 WCAG AA、设计走查 QA、设计转代码。触发词：UI设计、UX设计、界面设计、设计系统、组件库、设计规范、设计稿、原型、高保真、设计走查、像素级还原、design token、换肤、暗色模式、设计转代码、页面怎么做、按PRD出稿。
version: 1.0.0
tags:
  - ui-design
  - ux-design
  - design-system
  - design-tokens
  - interaction-design
  - frontend-implementation
  - UI设计
  - 视觉设计
  - 组件库
  - 设计转代码
trigger_keywords:
  - UI设计
  - 交互设计
  - 界面设计
  - 设计稿
  - 设计系统
  - 设计规范
  - 像素级还原
  - 原型
  - 高保真
  - 视觉规范
  - 换肤
  - 设计走查
  - 设计转代码
  - 页面设计
---

# UI 设计师方案与执行一体化指南（ui-designer-guide）

单一技能、双引擎、一条任务链路：**上游方案引擎**（源自 UX 方案方法论——5 类场景识别、按场景产出清单、通用交付标准）与**下游视觉执行引擎**（源自像素君 Pixel UI Designer——Design System First、美学手艺库、像素级界面、设计转代码）。需求无论从"一句话/PRD/迭代需求"哪里进来，都能走到**可看的、美观的界面或实现**，补齐"方案规范但出稿不美"的断链。

两套方法论按任务链路编排，不物理混排——每一环节由对应引擎主导，按需读取对应 reference。

## 任务链路总览

```
入口（PRD / 一句话需求 / 迭代需求 / 设计系统任务）
  │
  ▼
① 入口路由 ──────────► L1 页面级 / L2 需求级 / L3 系统级
  │
  ▼
② 链路阶段 A · 方案设计（主力：UX 方案方法论）
   需求理解 → 场景识别(5类) → 确认场景 → 按场景出方案文档
  │
  ▼
③ 链路阶段 B · 视觉执行（主力：像素君执行引擎）
   设计上下文 → Design System First → 美学决策 → 像素级界面/设计转代码
  │
  ▼
④ 美学闸门（AI Slop Test + DO/DON'T + 去AI味自检）
  │
  ▼
⑤ 质量闸门（9状态 / WCAG AA / 还原度≥95%）→ 交付
```

## ① 入口路由（先判断任务落点，决定 A/B 引擎配比）

| 落点 | 入口特征 | 走法 |
|------|---------|------|
| **L1 页面级** | "设计登录页""这个页面怎么做"——明确到页面/组件 | 轻上游（A 只做需求理解，跳过场景清单）→ **B 为主力**，直接产出可看界面 |
| **L2 需求级** | PRD / 新产品 / 中大型迭代 / 优化 / 概念探索 | **A 为主力**出方案 → B 视觉执行 → 交付 |
| **L3 系统级** | Design Token / 组件库 / 主题换肤 / 规范文档 | 直接进 B 的设计系统分支（B1-B2），无页面任务 | 

**判定口诀**：用户要"文档/方案评审件"→ A 出文档即可；用户要"能看的稿/能跑的界面"→ 必经 B；两者都要 → 全链路。

## ② 链路阶段 A ｜ 方案设计（主力：UX 方案方法论）

所有方法细节在 `references/UX设计方法论.md`，按环节读取对应章节，禁止凭印象执行。

- **A1 需求理解**：解析产品类型（App/Web/小程序）、平台、功能范围、现有设计基础、目标用户；关键信息缺失时提问补全（一次 ≤ 2-3 问）。
- **A2 场景识别**：读取「一、场景识别」决策表/决策树 → 判断属于 5 类场景（0→1 新产品 / 中大型迭代 / 小优化微调 / 设计系统大升级 / 概念探索）。L1 页面级任务跳过本步。
- **A3 与用户确认场景**：输出场景判断 + 依据 + 建议产出清单 + 预估周期。**不可跳过确认**。
- **A4 按场景产出方案**：读取「二~六」对应场景章节 +「七、通用设计交付标准」（命名/标注/9 状态/无障碍/设备适配）+「十一、超越AI味」（反模板化/品牌气质/张力/情感节奏/真实内容/行业精度）。产出保存为 Markdown。
- **A5 边界判定**：仅需"方案文档"→ 直接走 ④美学闸门 + ⑤质量闸门交付；需要"可看的稿/界面/实现"→ **必须进 ③ 阶段 B**，把方案的结构性产出（页面清单/交互流程/状态/规格）作为 B 的输入。

> A 引擎产出形态是「文字描述 + 规格参数」的方案与规范——这是它的定位，不是缺陷。**凡要视觉成品，往下走 B**，不要停在 A 交付文字稿了事。

## ③ 链路阶段 B ｜ 视觉执行（主力：像素君执行引擎）

把方案/PRD/页面任务变成**真正好看的成品**。执行标准源自像素君：三大使命（设计系统/像素级界面/赋能落地）、三条铁律（Design System First / 无障碍内建 / 性能意识）。

- **B0 设计上下文三问（必做）**：目标用户是谁？使用场景要完成什么？品牌调性应是什么感觉？**禁止通过代码/文档推断设计上下文**——缺失先问，不猜。
- **B1 Design System First**：先立地基再画页面。读取 `references/design-tokens.md`（亮/暗双主题 Token 体系 + 基础组件 + 响应式框架），把 A 输出的语义需求落成 Token 与组件（含 9 种状态变体）。
- **B2 美学决策**：应用本文档「④ 美学闸门」的 DO/DON'T 与 AI Slop Test；需深度技法时按场景读取 `references/design-quality/`（30 份手艺参考：排版/色彩/空间/动效/交互/响应式/文案/认知负载/启发式/画像 + 增强冲击/降噪/上色/精简/打磨/加固/优化等场景动作）。
- **B3 界面产出 / 设计转代码**：
  - 产出形态为**可看界面或可运行实现**时：读 `references/frontend-implementation.md`（6 阶段工作流 + 设计旋钮 + 反 AI 技巧与禁用模式），用本地素材（81 字体在 `assets/canvas-fonts/`）高保真实现，**严禁占位符 URL 与外链素材**；
  - 产出形态为**交付文档/规范**时：用 `references/deliverable-template.md`（设计系统交付文档模板）。
- **B4 状态完备**：所有交互元素覆盖 9 状态：default / hover / focus / active / disabled + loading / error / empty / success。

## ④ 美学闸门（两引擎共用，出稿前必过）

### AI Slop Test

> 把成品给某人看并说"这是 AI 做的"，对方立刻相信吗？如果是，就是失败。
> 好设计让人问"这是怎么做出来的？"，不是"哪个 AI 做的？"

### DO / DON'T 速查

| 维度 | ✅ DO | ❌ DON'T |
|------|-------|----------|
| 字体 | 独特展示字体 + 精致正文字体；模块化比例；clamp() 流体尺寸 | Inter/Roboto/Arial 默认三件套；等宽字体冒充"技术感" |
| 色彩 | oklch/color-mix；中性色微微偏向品牌色 | 纯黑 #000/纯白 #fff；青+深色的 AI 标配；紫蓝渐变+霓虹点缀 |
| 空间 | 变化的间距创造节奏；4px 基准；clamp() 流式间距 | 万物皆卡片、卡片套卡片；一切居中 |
| 动效 | 状态变化驱动；100/300/500ms 分级；指数缓动 | 动画化布局属性；滥用回弹缓动 |
| 交互 | 渐进式披露；有教育意义的空状态；可见焦点环 | 重复信息；所有按钮都是主按钮；无替代 outline:none |
| 响应式 | 容器查询 @container；移动优先；pointer/coarse 区分输入 | 移动端隐藏关键功能；桌面优先 |
| 文案 | 按钮"动词+对象"；报错=发生了什么+为什么+怎么办 | "OK/Submit" 懒标签；复述用户已见信息 |
| 细节 | 有意图的装饰强化品牌 | 毛玻璃滥用；无意义圆角+通用阴影 |

### 去AI味自检（接 UX 方法论 §11）

读 `references/UX设计方法论.md`「十一、超越AI味」末尾的"交付物去AI味自检"，逐条对照：反模板化十条是否违例、品牌一票否决是否通过、情感节奏是否映射、极端内容是否已测试。

## ⑤ 质量闸门（两引擎统一验收，交付前逐项核对）

- 场景判断正确且已与用户确认（L2/L3 任务）
- 产出清单完整：方案交付物齐全（L2）或界面/实现可用（L1/B）
- 9 状态覆盖完备（error/empty/loading 不遗漏）
- 视觉规范清晰：颜色/字体/间距/阴影/圆角有确定值，全部来自 Token，无流浪数值（一致性 ≥ 95%）
- 无障碍达标：WCAG AA（正文对比度 ≥ 4.5:1、大文本 ≥ 3:1、触控区 44px、焦点管理、读屏支持）
- 响应式 320px-1280px+ 无破版
- 去AI味达标（④美学闸门全过）
- 设计转代码类产出：还原度 ≥ 95%，素材已优化，无占位符/外链素材
- 交付返工率目标 < 10%

读 `references/quality-checklist.md` 走完整走查流程；发现遗漏即补充，最后输出交付清单。

## 交付衔接

- 交付开发时附「设计 token ↔ CSS 变量映射表」与 AI 转码试跑说明（`references/UX设计方法论.md` §8.1/§8.2），执行 AI 转码还原度检查（§10）。
- 本技能可直接产出界面代码（B3 设计转代码分支），或产出精确到 px/rem 的标注供开发实现，按任务落点选择。
- 若处于角色技能体系被调度场景，遵循体系的执行记录约定。

## 参考资料

**方案层**（链路 A 引擎 · 源自 UX 方案方法论）

- `references/UX设计方法论.md` — 场景识别/5 类产出清单/通用交付标准/下游交付衔接/AI 工具/质量清单/超越AI味 全量方法

**执行层**（链路 B 引擎 · 源自像素君）

- `references/design-tokens.md` — Design Token 体系（亮/暗双主题 CSS）+ 基础组件 + 响应式框架
- `references/frontend-implementation.md` — 设计转代码规范（6 阶段 + 设计旋钮 + 反 AI 技巧）
- `references/deliverable-template.md` — 设计系统交付文档模板（可填空）
- `references/quality-checklist.md` — 无障碍与设计 QA 走查清单
- `references/design-quality/` — 30 份手艺参考：typography / color-and-contrast / spatial-design / motion-design / interaction-design / responsive-design / ux-writing / cognitive-load / heuristics-scoring / personas / bolder / quieter / colorize / overdrive / arrange / typeset / adapt / animate / delight / onboard / audit / critique / polish / harden / optimize / extract / normalize / distill / clarify / teach-impeccable

**专家蒸馏增量（2026-09-06 并入）**

- `references/expert-distill/mvp-designer-蒸馏.md` — MVP 团队「颜好看」：寄存器二分（Brand/Product 定标杆）、10 级评审优先级（无障碍→图表，带反模式）、8 类产品风格速配、三轴设计刻度（DESIGN_VARIANCE/MOTION_INTENSITY/VISUAL_DENSITY）、反 AI 模板 7 大罪具体 CSS 表现、反射拒绝字体列表（Inter 禁作展示字体）——与像素君引擎互补：像素君管"做美做对"，本文档管"动手前定标杆 + 评审按优先级"
- `references/expert-distill/design-md-蒸馏.md` — 设计系统架构师「规范范」：DESIGN.md 9 章标准结构（AI 可消费的设计契约）、58 品牌参考速查（8 行业）、跨品牌风格混搭、设计交付直出模式

**资产层**

- `assets/canvas-fonts/` — 81 个开源自托管字体（含 OFL 授权），本地引用避免外链
- `assets/art-templates/` — 视觉艺术生成模板（generator_template.js + viewer.html）

## 目录结构

```
ui-designer-guide/
├── SKILL.md                      # 任务链路：入口路由 → A方案(UX方法论) → B视觉执行(像素君) → 美学闸门 → 质量闸门
├── references/
│   ├── UX设计方法论.md           # 方案层：5场景/产出清单/交付标准/超越AI味（A 引擎）
│   ├── design-tokens.md          # 执行层：Token 体系 + 组件 + 响应式框架
│   ├── frontend-implementation.md # 执行层：设计转代码规范
│   ├── deliverable-template.md   # 执行层：交付文档模板
│   ├── quality-checklist.md      # 执行层：QA 走查清单
│   └── design-quality/           # 执行层：30 份手艺参考（领域理论 + 场景动作）
├── assets/
│   ├── canvas-fonts/             # 81 个自托管开源字体
│   └── art-templates/            # 视觉艺术生成模板
├── README.md
└── LICENSE
```
