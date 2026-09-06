# Design Token 体系与基础组件库

可直接落地的基础 Token 系统。实际项目中将色值/字体替换为品牌值，结构保持不变。所有界面元素必须引用 Token，禁止硬编码流浪数值。

## 1. Design Token System（亮色 + 暗色双主题）

```css
:root {
  /* ===== 色彩 Token ===== */
  /* 主色阶（100=浅底, 500=基准, 900=深） */
  --color-primary-100: #f0f9ff;
  --color-primary-500: #3b82f6;
  --color-primary-600: #2563eb;
  --color-primary-900: #1e3a8a;

  /* 中性色阶（文本与背景） */
  --color-secondary-100: #f3f4f6;
  --color-secondary-200: #e5e7eb;
  --color-secondary-300: #d1d5db;
  --color-secondary-500: #6b7280;
  --color-secondary-900: #111827;

  /* 语义色 */
  --color-success: #10b981;
  --color-warning: #f59e0b;
  --color-error:   #ef4444;
  --color-info:    #3b82f6;

  /* ===== 字体 Token ===== */
  --font-family-primary:   'Inter', system-ui, sans-serif;
  --font-family-secondary: 'JetBrains Mono', monospace;

  --font-size-xs:   0.75rem;    /* 12px */
  --font-size-sm:   0.875rem;   /* 14px */
  --font-size-base: 1rem;       /* 16px */
  --font-size-lg:   1.125rem;   /* 18px */
  --font-size-xl:   1.25rem;    /* 20px */
  --font-size-2xl:  1.5rem;     /* 24px */
  --font-size-3xl:  1.875rem;   /* 30px */
  --font-size-4xl:  2.25rem;    /* 36px */

  /* ===== 间距 Token（4px 基准） ===== */
  --space-1:  0.25rem;   /* 4px  */
  --space-2:  0.5rem;    /* 8px  */
  --space-3:  0.75rem;   /* 12px */
  --space-4:  1rem;      /* 16px */
  --space-6:  1.5rem;    /* 24px */
  --space-8:  2rem;      /* 32px */
  --space-12: 3rem;      /* 48px */
  --space-16: 4rem;      /* 64px */

  /* ===== 阴影 Token（层级 = 深度） ===== */
  --shadow-sm: 0 1px 2px 0 rgb(0 0 0 / 0.05);
  --shadow-md: 0 4px 6px -1px rgb(0 0 0 / 0.1);
  --shadow-lg: 0 10px 15px -3px rgb(0 0 0 / 0.1);

  /* ===== 动效 Token ===== */
  --transition-fast:   150ms ease;
  --transition-normal: 300ms ease;
  --transition-slow:   500ms ease;
}

/* 暗色主题：只覆盖变量，组件零改动 */
[data-theme="dark"] {
  --color-primary-100: #1e3a8a;
  --color-primary-500: #60a5fa;
  --color-primary-900: #dbeafe;

  --color-secondary-100: #111827;
  --color-secondary-500: #9ca3af;
  --color-secondary-900: #f9fafb;
}
```

## 2. 基础组件样式（含关键状态）

```css
/* 按钮基类：focus-visible 与 disabled 状态必须实现 */
.btn {
  display: inline-flex;
  align-items: center;
  justify-content: center;
  font-family: var(--font-family-primary);
  font-weight: 500;
  text-decoration: none;
  border: none;
  cursor: pointer;
  transition: all var(--transition-fast);
  user-select: none;

  &:focus-visible {
    outline: 2px solid var(--color-primary-500);
    outline-offset: 2px;
  }

  &:disabled {
    opacity: 0.6;
    cursor: not-allowed;
    pointer-events: none;
  }
}

.btn--primary {
  background-color: var(--color-primary-500);
  color: white;

  &:hover:not(:disabled) {
    background-color: var(--color-primary-600);
    transform: translateY(-1px);
    box-shadow: var(--shadow-md);
  }
}

/* 表单输入：focus 用边框色 + 光晕双信号 */
.form-input {
  padding: var(--space-3);
  border: 1px solid var(--color-secondary-300);
  border-radius: 0.375rem;
  font-size: var(--font-size-base);
  background-color: white;
  transition: all var(--transition-fast);

  &:focus {
    outline: none;
    border-color: var(--color-primary-500);
    box-shadow: 0 0 0 3px rgb(59 130 246 / 0.1);
  }
}

/* 卡片：hover 提升 = 阴影加深 + 位移 */
.card {
  background-color: white;
  border-radius: 0.5rem;
  border: 1px solid var(--color-secondary-200);
  box-shadow: var(--shadow-sm);
  overflow: hidden;
  transition: all var(--transition-normal);

  &:hover {
    box-shadow: var(--shadow-md);
    transform: translateY(-2px);
  }
}
```

## 3. 响应式框架（移动优先）

断点策略：Mobile 320-639px（基准）→ Tablet 640-1023px → Desktop 1024-1279px → Large Desktop 1280px+。

```css
/* Mobile First：默认即移动端 */
.container {
  width: 100%;
  margin-left: auto;
  margin-right: auto;
  padding-left: var(--space-4);
  padding-right: var(--space-4);
}

@media (min-width: 640px) {
  .container { max-width: 640px; }
  .sm\:grid-cols-2 { grid-template-columns: repeat(2, 1fr); }
}

@media (min-width: 768px) {
  .container { max-width: 768px; }
  .md\:grid-cols-3 { grid-template-columns: repeat(3, 1fr); }
}

@media (min-width: 1024px) {
  .container {
    max-width: 1024px;
    padding-left: var(--space-6);
    padding-right: var(--space-6);
  }
  .lg\:grid-cols-4 { grid-template-columns: repeat(4, 1fr); }
}

@media (min-width: 1280px) {
  .container {
    max-width: 1280px;
    padding-left: var(--space-8);
    padding-right: var(--space-8);
  }
}
```

## 4. Token 使用规则

1. **一切数值来自 Token**：颜色、字号、间距、阴影、动效时长禁止硬编码。
2. **语义化命名**：Token 按用途命名（`--color-error`），不按外观命名（`--color-red`），换肤时才不用改组件。
3. **暗色主题只覆盖变量**：组件代码不感知主题，主题切换 = 换一组变量值。
4. **间距只用阶内值**：需要新间距时先问"能否用现有阶"，确需新增则按 4px 倍数扩展。
