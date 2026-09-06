# UI Designer Guide — UI 设计方案与执行一体化指南

[![License](https://img.shields.io/badge/license-MIT-blue.svg)](LICENSE)
[![Version](https://img.shields.io/badge/version-1.0.0-green.svg)](SKILL.md)

一个面向 AI 编程助手的 **UI 设计师全链路 Skill**，由两套方法论按任务链路整合而成（非物理混排）：上游 **UX 方案方法论**（5 类场景识别/产出清单/交付标准）+ 下游**像素君视觉执行引擎**（Design System First/美学手艺库/像素级界面/设计转代码）。需求无论从"一句话 / PRD / 迭代需求 / 设计系统任务"哪里进来，都能走到**可看的、美观的界面或实现**——补齐"方案规范但出稿不美"的断链。

## 特性

- **单技能双引擎任务链路**：入口路由（L1 页面级 / L2 需求级 / L3 系统级）→ 方案设计（UX 方法论主力）→ 视觉执行（像素君主力）→ 美学闸门 → 质量闸门
- **按任务落点裁剪**：要文档给文档、要能看的稿/能跑的界面给界面——不再停在文字描述稿
- **反泛 AI 审美**：AI Slop Test + 八大维度 DO/DON'T 速查 + UX 去AI味自检（反模板化十条）双闸门
- **可执行视觉手艺库**：30 份深度参考（排版/色彩/空间/动效/交互/响应式/文案/认知负载 + 20+ 场景动作）
- **设计转代码**：6 阶段工作流 + 设计旋钮 + 反 AI 技巧，产出高保真真实界面（含 81 个自托管开源字体）
- **无障碍内建**：WCAG AA 是默认底线，9 种交互状态全覆盖

## 任务链路

```
入口(PRD/一句话/迭代/系统任务) → ①入口路由
  → ②方案设计(UX方法论：场景识别→产出清单→方案文档)
  → ③视觉执行(像素君：上下文三问→Design System First→美学决策→像素级界面/转码)
  → ④美学闸门(AI Slop Test + DO/DON'T + 去AI味自检)
  → ⑤质量闸门(9状态/WCAG AA/还原度≥95%) → 交付
```

## 适用场景

| 场景 | 示例 | 主力引擎 |
|------|------|---------|
| 按 PRD 出 UI | 把需求文档变成可看的登录页/首页 UI | 像素君执行引擎（B） |
| 新产品方案 | 0→1 App 完整设计方案（交互+视觉规范） | UX 方法论（A）→ 像素君（B） |
| 中大型迭代 | CRM 新增看板模块的方案与页面 | 全链路 |
| 小优化 | 单页间距/文案/颜色微调 | UX 方法论 A 简版 |
| 设计系统 | Token/组件库/暗色主题/规范文档 | 像素君设计系统分支 |
| 概念探索 | 新方向 Mood Board、风格预研 | UX 方法论场景五 |
| 设计走查/转码 | 现有界面走查、设计稿高保真还原 | 像素君（B） |

## 触发热词

UI设计、UX设计、交互设计、界面设计、设计系统、设计规范、设计稿、原型、线框图、高保真、设计走查、像素级还原、design token、换肤、暗色模式、设计转代码、页面怎么做、按PRD出稿

---

## 安装

本 Skill 遵循 **Open Agent Skills 标准**（SKILL.md 格式），兼容以下工具：

### WorkBuddy / CodeBuddy

**方式一：克隆到 skills 目录**
```bash
git clone https://github.com/genapohub/ui-designer-guide.git ~/.workbuddy/skills/ui-designer-guide
```

**方式二：ZIP导入**
```bash
git clone https://github.com/genapohub/ui-designer-guide.git
zip -r ui-designer-guide.zip ui-designer-guide/
```
然后在 WorkBuddy 桌面端 → **技能市场** → **添加技能/上传技能** → **点击"跳过检测，直接安装"**。

### Trae

**ZIP 导入**
```bash
git clone https://github.com/genapohub/ui-designer-guide.git
```
然后在 Trae → **设置** → **Rules & Skills** → **创建** → 上传 `ui-designer-guide.zip`。

### Codex / ZCode

```bash
# 克隆到 skills 目录
git clone https://github.com/genapohub/ui-designer-guide.git ~/.codex/skills/ui-designer-guide

# ZCode
git clone https://github.com/genapohub/ui-designer-guide.git ~/.zcode/skills/ui-designer-guide
```

重启 Codex / ZCode 客户端后自动发现。也可以在对话中输入 `${ui-designer-guide}` 手动调用。

### Cursor
```bash
# 克隆到 skills 目录
git clone https://github.com/genapohub/ui-designer-guide.git ~/.cursor/skills-cursor/ui-designer-guide
```

重启 Cursor客户端 后自动发现。也可以在对话中输入 `${ui-designer-guide}` 手动调用。

## 使用

安装后无需额外配置，对话中自然描述需求即可触发：

```
按这份 PRD 把登录和首页的 UI 做出来，要能直接看效果的
帮我们的新项目出一套完整设计方案（交互流程 + 设计系统）
这个功能迭代涉及 3 个页面，出方案并做高保真稿
把这张设计稿高保真转成 HTML/CSS
帮现有界面做设计走查，功能对但不好看的地方改美
```

## 许可

[MIT](LICENSE) © zhangmengbo
