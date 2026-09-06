# 前端实现规范（设计转代码）

当设计需要落地为真实前端代码（落地页、营销站、产品页、Dashboard）时遵循本规范。目标：生产级、视觉惊艳、无占位符、无泛 AI 审美。

## 工作流（6 个阶段）

1. **设计架构**：判断页面类型 → 设定设计旋钮 → 规划布局分区与素材需求
2. **动效架构**：按工具选择矩阵为每个分区选动效方案，遵循性能护栏
3. **素材生成**：所有图片/视频/音频用环境内置的媒体生成工具产出并保存到本地——**严禁占位符 URL**（unsplash/picsum/placehold 等）和外链素材
4. **文案撰写**：用 AIDA/PAS/FAB 框架写真实文案，**严禁 Lorem ipsum**
5. **构建 UI**：按设计与动效规则逐区构建，所有 `<img>/<video>/background-image` 必须引用本地素材
6. **质量门**：过本文末尾的检查清单后才交付

## 设计旋钮（Design Dials）

| 旋钮 | 默认 | 范围 |
|------|------|------|
| DESIGN_VARIANCE | 8 | 1=对称，10=不对称 |
| MOTION_INTENSITY | 6 | 1=静态，10=电影感 |
| VISUAL_DENSITY | 4 | 1=通透，10=紧凑 |

按用户要求动态调整。

## 设计规则

| 规则 | 指令 |
|------|------|
| 字体 | 标题 `tracking-tighter`；正文 `leading-relaxed max-w-[65ch]`；**禁用 Inter**——用 Geist/Outfit/Satoshi；Dashboard 禁用衬线体 |
| 色彩 | 最多 1 个强调色，饱和度 < 80%；**禁用 AI 紫蓝**；全套只用一个色板 |
| 布局 | VARIANCE > 4 时**禁用居中 Hero**——强制分屏或不对称布局；视口用 `min-h-[100dvh]` 而非 `h-screen` |
| 卡片 | DENSITY > 7 时禁用通用卡片——用 `border-t`、`divide-y` 或纯间距分区 |
| 状态 | **必须实现**：Loading（骨架屏）、Empty、Error、触觉反馈（`scale-[0.98]`） |
| 表单 | Label 在输入框上方，错误提示在下方，输入块间距 `gap-2` |
| 图标 | **禁用 emoji 充当图标**——用 Phosphor / Radix 等图标库 |

## 反泛 AI 技巧（Anti-Slop）

- **液态玻璃**：`backdrop-blur` + `border-white/10` + `shadow-[inset_0_1px_0_rgba(255,255,255,0.1)]`
- **磁吸按钮**：用 `useMotionValue`/`useTransform`——连续动画禁用 `useState`
- **永续微动效**：INTENSITY > 5 时加无限微动画（Pulse/Float/Shimmer）
- **布局过渡**：用 Framer 的 `layout` 和 `layoutId`
- **错落入场**：`staggerChildren` 或 CSS `animation-delay: calc(var(--index) * 100ms)`

## 禁用模式

| 类别 | 禁止 |
|------|------|
| 视觉 | 霓虹发光、纯黑 #000、过饱和强调色、标题渐变文字、自定义光标 |
| 字体 | Inter、超大 H1、Dashboard 用衬线 |
| 布局 | 三列等宽卡片排、悬浮元素配尴尬的间隙 |
| 组件 | 无定制的默认 shadcn/ui |

## 创意武器库

| 类别 | 模式 |
|------|------|
| 导航 | Dock 放大、磁吸按钮、Gooey 菜单、动态岛、径向菜单、Mega 菜单 |
| 布局 | Bento 网格、瀑布流、分屏滚动、幕布揭示 |
| 卡片 | 视差倾斜、聚光灯边框、玻璃拟态、全息烫印、滑动卡堆、形变弹窗 |
| 滚动 | 粘性堆叠、水平劫持、缩放视差、进度路径 |
| 文字 | 跑马灯、文字遮罩揭示、乱码解码、圆形路径文字 |
| 微交互 | 粒子爆炸、骨架微光、方向性悬浮、涟漪点击、SVG 描边、网格渐变 |

## Bento 范式

- 背景 `#f9fafb`，卡片纯白 + `border-slate-200/50`
- 圆角 `rounded-[2.5rem]`，弥散阴影
- 字体 Geist/Satoshi，标题 `tracking-tight`
- 弹簧物理（`stiffness: 100, damping: 20`），无限循环动画隔离在 `React.memo` 叶组件

## 动效引擎

### 工具选择矩阵

| 需求 | 工具 |
|------|------|
| UI 进场/退场/布局 | Framer Motion（`AnimatePresence`、`layoutId`、弹簧） |
| 滚动叙事（钉住、scrub） | GSAP + ScrollTrigger |
| 循环图标 | Lottie（懒加载） |
| 3D/WebGL | Three.js / R3F（隔离 `<Canvas>`） |
| 悬浮/焦点态 | 纯 CSS（零 JS 成本） |
| 原生滚动驱动 | CSS `animation-timeline: scroll()` |

**冲突规则（强制）**：同一组件不混用 GSAP + Framer Motion；R3F 必须在隔离 Canvas 内；Lottie/GSAP/Three.js 一律懒加载。

### 强度阶梯

| 级别 | 手法 |
|------|------|
| 1-2 微妙 | 纯 CSS 过渡，150-300ms |
| 3-4 顺滑 | CSS keyframes + Framer animate，错落 ≤3 项 |
| 5-6 流动 | `whileInView`、磁吸悬浮、视差倾斜 |
| 7-8 电影感 | GSAP ScrollTrigger、钉住分区、水平劫持 |
| 9-10 沉浸 | 全滚动序列、Three.js 粒子、WebGL shader |

### 性能护栏

- **只动 GPU 属性**：`transform`、`opacity`、`filter`、`clip-path`
- **禁动**：`width/height/top/left/margin/padding/font-size`——需要时用 `scale()` 或 `clip-path` 替代
- 永续动画隔离在 `React.memo` 叶组件；`will-change` 仅在动画期间
- 移动端：尊重 `prefers-reduced-motion`；`pointer: coarse` 禁用视差/3D；粒子上限桌面 800/平板 300/手机 100；< 768px 禁用 GSAP pin
- 每个含 GSAP/observer 的 `useEffect` 必须 `return () => ctx.revert()`

### 弹簧与缓动

| 手感 | Framer 配置 |
|------|------------|
| 干脆 | `stiffness: 300, damping: 30` |
| 顺滑 | `stiffness: 150, damping: 20` |
| 弹跳 | `stiffness: 100, damping: 10` |
| 厚重 | `stiffness: 60, damping: 20` |

| CSS 缓动 | 值 |
|----------|-----|
| 平滑减速 | `cubic-bezier(0.16, 1, 0.3, 1)` |
| 平滑加速 | `cubic-bezier(0.7, 0, 0.84, 0)` |
| 弹性 | `cubic-bezier(0.34, 1.56, 0.64, 1)` |

## 素材生成规范

用环境内置的图像/视频生成工具（而非外链）：

1. **解析需求**：类型、数量、风格、规格、用途
2. **写提示词**：具体（构图、光线、风格）；图像提示词中**不要包含文字**
3. **确认后生成**：提示词先给用户确认再执行
4. **本地保存**：`assets/{images,videos,audio}/`，命名 `{type}-{descriptor}-{timestamp}.{ext}`
5. **后处理**：图片转 WebP、视频压缩、音频归一化

预设规格：`hero`=16:9 电影感、`thumb`=1:1 居中主体、`icon`=1:1 扁平净底、`banner`=21:9、`bg-video`=6 秒静态镜头、`bgm`=30 秒无人声可循环。

## 文案框架

**AIDA**（落地页/邮件）：抓注意（大胆标题）→ 引兴趣（"对，说的就是我"）→ 激欲望（展示转变）→ 促行动（明确 CTA）

**PAS**（痛点驱动产品）：问题 → 放大紧迫感 → 产品即解法

**FAB**（差异化）：功能 → 优势 → 客户收益

标题公式：承诺式（"30 天翻倍打开率"）/ 提问式 / 数字式 / 反语式 / 好奇式 / 转变式——要具体，结果先行。

CTA 公式：**[动作动词] + [得到什么] + [紧迫/低门槛]**。禁用"提交/点击这里/了解更多"。位置：首屏、价值点后、长页多处。

异议处理（放 FAQ/证言/CTA 旁）：太贵→算 ROI；不适合我→同类客户证言；没时间→"10 分钟搭好"；怕失败→"30 天退款"。

## 视觉艺术模式（海报 / 生成艺术）

哲学先行的工作流，两种输出：

| 模式 | 输出 | 场景 |
|------|------|------|
| 静态 | PDF/PNG | 海报、印刷、设计素材 |
| 交互 | HTML（p5.js） | 生成艺术、可探索变体 |

流程：
1. **创立哲学**：命名流派（1-2 词），写 4-6 段哲学阐述（静态：空间/形态/色彩/尺度/节奏/层次；交互：计算/涌现/噪声/参数变化）
2. **概念种子**：找一个小众微妙的参照——爵士乐手引用另一首歌，不是字面抄袭
3. **创作**：静态模式用 `assets/canvas-fonts/` 的字体做克制排版，重复 pattern、完美几何、互不重叠；交互模式先读 `assets/art-templates/viewer.html`，保留 FIXED 区（头部/侧栏/种子控件），替换 VARIABLE 区（算法/参数），用 `randomSeed(seed); noiseSeed(seed);` 保证可复现
4. **打磨**：做减法不做加法，磨到锐利

## 质量门（交付前必过）

**设计**：
- [ ] 高反差设计在移动端正确塌缩（`w-full`、`px-4`）
- [ ] 用 `min-h-[100dvh]` 而非 `h-screen`
- [ ] Empty/Loading/Error 状态齐备
- [ ] 间距够用的地方没有多余卡片

**动效**：
- [ ] 工具选择符合矩阵；同组件未混用 GSAP + Framer
- [ ] 所有 `useEffect` 有 cleanup return
- [ ] 尊重 `prefers-reduced-motion`；只动 GPU 属性；重库懒加载

**通用**：
- [ ] 依赖已核对 `package.json`
- [ ] **零占位符 URL**——grep 输出查 `unsplash|picsum|placeholder|placehold|dummyimage`，有任何命中立即替换为生成素材
- [ ] 所有媒体素材是项目 assets 目录下的本地文件
- [ ] 素材提示词已经用户确认
