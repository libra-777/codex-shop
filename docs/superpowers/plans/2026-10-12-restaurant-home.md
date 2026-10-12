# 禾间小馆首页 Implementation Plan

> **For agentic workers:** REQUIRED SUB-SKILL: Use superpowers:subagent-driven-development or superpowers:executing-plans to implement this plan task-by-task. Steps use checkbox (`- [x]`) syntax for tracking.

**Goal:** 实现帮助顾客了解餐馆、查看招牌菜的中文响应式首页。

**Architecture:** 使用静态 HTML 展示完整内容，CSS 负责响应式视觉，JavaScript 增强菜品筛选和移动导航。无构建、无后台依赖；在当前工作目录交付可预览源码。

**Tech Stack:** HTML5、CSS、原生 JavaScript。

**Spec:** [设计文档](../specs/2026-10-12-restaurant-home-design.md)

## Global Constraints

- 品牌“禾间小馆”、菜品及到店信息均为可替换的示例内容。
- 使用温暖的现代中餐馆风格：米白背景、深棕文字、朱红强调色。
- 使用无构建步骤的 HTML、CSS 和 JavaScript。
- 不包含在线点餐、支付、订座后台或用户账户。
- 页面在 JavaScript 不可用时仍能阅读全部核心内容。
- 本次交付为当前工作目录内的完整前端首页。

## Review Focus

- 320px 手机屏幕：导航、菜品和联系信息不横向溢出。
- 仅键盘访问：菜单和筛选可操作，焦点清晰可见。
- 图片加载失败：保留稳定的区域尺寸及替代文本。
- 禁用 JavaScript：核心内容和六道菜仍可见。
- 减少动态效果偏好：禁用非必要动画和滚动过渡。

---

### Task 1: 内容与视觉首页

**Files:** Create `index.html`, `styles.css`, `README.md`.

**Interfaces:** 产出 `#home`、`#menu`、`#story`、`#visit` 锚点；菜品元素使用 `data-category="signature"` 或 `data-category="seasonal"`。筛选按钮使用 `data-filter="all|signature|seasonal"`。移动导航采用 `#site-nav` 和 `#menu-toggle`。

- [x] 创建语义化 HTML：导航、首屏、六道菜、故事、到店信息、页脚。菜品名称分别为红烧肉、葱油鸡、松鼠桂鱼、蒜香排骨、时令蔬菜、桂花糯米藕；前四道为招牌热菜，后两道为时令小菜。
- [x] 创建 CSS：米白与深棕配色、朱红按钮、大幅美食图，桌面舒展布局和移动单列布局。图片使用固定比例和占位背景。
- [x] 添加键盘焦点、减少动态效果规则；JavaScript 启用前展示全部导航与菜品。
- [x] 在 README 中说明启动静态预览方法和示例内容替换位置。
- [x] 检查全部锚点有效；已浏览器验证 320px、1440px 无横向溢出。无脚本和图片失败场景通过源码检查，未在浏览器实际模拟。

### Task 2: 浏览交互

**Files:** Create `script.js`.

**Interfaces:** 消费 Task 1 的锚点及 data 属性；`setFilter(category: string): void` 更新可见菜品与 `aria-pressed`；`setMenuOpen(open: boolean): void` 更新导航展开状态与 `aria-expanded`。

- [x] 实现筛选：全部显示六道、招牌热菜显示四道、时令小菜显示两道；更新按钮选中状态。
- [x] 实现手机菜单：按钮切换、点击锚点关闭、Escape 关闭并恢复按钮焦点；桌面导航保持可见。
- [x] 使用浏览器验证 all → signature → seasonal → all 的数量为 6 → 4 → 2 → 6；验证点击与键盘操作结果一致。
- [x] 验证移动菜单开关和 Escape 行为，以及导航目标位置。

### Task 3: 完成验证与交付

**Files:** 更新 `README.md` 和本计划的复选框。

**Interfaces:** 交付 `index.html` 为首页入口，无安装或构建要求。

- [x] 执行 `node --check script.js`，要求退出状态为 0；如果 Node 不可用，使用浏览器检查脚本异常。
- [x] 检查桌面和手机的图片、文本、间距以及页面完整性；读取浏览器控制台并修复实际错误。
- [x] 完成一次独立代码审查，修复影响本次需求的问题后仅重复相关验证。
- [x] 更新计划进度并提供源码入口和预览方式；如浏览器验证不可用，明确报告验证限制。

## 仓库状态

当前目录无 Git 仓库，不创建工作树或执行提交。所有交付文件保留在当前工作目录。
