# 龙悟 AI 虚拟学校 · 设计思路 | Longwu AI Virtual School — Design Concepts

> **这不是一个可直接运行的项目，而是一份开源的设计思路文档（Design Doc）。**
> 它描述"如何用智能体（Agent）构建一所 AI 虚拟学校"的核心架构理念，供开发者在**应用方向**上自行实现。
>
> **This is NOT a runnable project. It is an open design document** describing the core architecture of an agent-native AI virtual school, for developers to build upon in the **application direction**.

---

## 一、这是什么 | What This Is

「AI 虚拟学校」是一种**智能体优先（Agent-Native）**的教育产品形态：

- 不是 App，不是网站，不是题库软件
- 而是一个**会教书、懂孩子、记得住**的智能体团队
- 孩子与它在**对话**中上课，浏览器只负责"把抽象的东西画出来看"

An "AI Virtual School" is an **agent-native** education product: not an app, not a website, not a question bank — a team of AI agents that **teach, understand the child, and remember**, where class happens in **conversation**, and the browser only serves as a visual aid.

---

## 二、六个核心设计理念 | Six Core Design Concepts

### 1. 对话即课堂 | Conversation IS the Classroom

一切互动发生在对话里：出题、回答、判断对错、讲解、安抚、激励。
**判断与反馈永远来自模型的思考，绝不由页面里写死的脚本代劳。**

All interaction happens in conversation. Judgment and feedback always come from the model's reasoning — never from hardcoded page scripts.

### 2. 展示层与互动层分离 | Display Layer ≠ Interaction Layer

这是与传统"教育 App"最本质的差别：

| | 传统教育应用 | 智能体虚拟学校 |
|---|---|---|
| 交互主体 | 页面上的按钮/输入框 | **对话** |
| 页面职责 | 承载交互+判断+展示 | **只展示**（教具台） |
| 判断逻辑 | 前端代码写死 | **模型思考** |
| 课程形态 | 固定模板/固定流程 | **每堂课现场生成** |

The browser is a pure "teaching-aid stage" — display only, no answer buttons, no input boxes. The child watches; the agent asks, judges, and explains.

### 3. 记忆画像 | Persistent Student Profile

孩子的姓名、年级、掌握度、错题、情绪、偏好，持久化保存在本地画像文件中：

- 每次对话先读画像 → 不当陌生人
- 每次互动后更新画像 → 越教越懂这个孩子
- 数据留在自家电脑 → **隐私不出门**

A local, persistent student profile gives the school cross-session memory: it knows the child's grade, weaknesses, mistakes and moods, and improves with every lesson. Privacy stays on the family's own computer.

### 4. 一校多师 | One School, Many Teachers

单一角色撑不起"学校"。设计采用：

- **角色分工**：校长（规划/目标/画像）+ 各学科老师（专业教学）+ 教学法规范（全员遵守）
- **前台只有一个主讲**：孩子眼里永远只有一位老师在说话
- **后台静默协同**：其他角色观察数据（情绪信号、连续对错），必要时向主讲"递纸条"给建议，孩子看不到

Multiple specialized roles (principal, subject teachers) behind a single speaking teacher — collaboration the child never sees, quality the child always feels.

### 5. 教学法内化 | Pedagogy Baked In

三个不可违反的铁律，写在智能体的行为规范里：

1. **不直接给答案，先引导**（苏格拉底式："你觉得第一步该怎么做？"）
2. **说人话，术语自动降级**（孩子听不懂就立刻换大白话）
3. **小步走**（一次讲一点，每步等孩子确认）

Three iron rules: Socratic guidance before answers; instant jargon-downgrade to plain language; small steps with confirmation at each one.

### 6. 可视化三分类 | Three Classes of Visualization

| 类型 | 用什么 | 示例 |
|---|---|---|
| 数学精确图形/公式 | 专业数学库渲染 | 天平、数轴、几何、分数 |
| 创意画面 | AI 生图 | 古诗意境图、单词配图 |
| 语言讲解/比喻 | 纯文字 | 大白话解释 |

**绝不用手绘假图充数**——精确的归数学库，想象的归生图，比喻的归语言。

Precise visuals from professional math libraries; creative visuals from image generation; metaphors in plain words. Never fake hand-drawn stand-ins.

---

## 三、给开发者的方向建议 | Directions for Developers

如果你想基于这套思路做产品，两条路都通：

1. **应用方向（App Direction）**：把上述理念封装成独立应用——你负责 UI、交互、判题逻辑，AI 作为引擎。适合做面向大众的产品。
2. **智能体方向（Agent Direction）**：把理念做成"技能包"——交给任意编程智能体执行。适合极客/自托管场景。

无论哪条路，最有价值的三个问题请优先想清楚：
- **记忆**怎么设计？（画像结构决定了"越教越懂"的上限）
- **展示与互动的边界**画在哪？（边界画错，AI 就被架空）
- **教学法**怎么内化？（产品体验的天花板在这里，不在 UI）

If you build on these ideas, prioritize: how memory is designed, where the display/interaction boundary lies, and how pedagogy is internalized. These three decide the ceiling of the product.

---

## 四、演示 | Demo

**[🌐 打开产品落地页 | Open the Product Landing Page](index.html)** — 三个学段的完整产品形态与在线演示（中英双语）

静态演示页（仅展示"展示层"效果，无交互逻辑）：

- [互动演示 | Interactive Demo](demo/interactive-demo.html) — 一节课的展示层形态
- [学习报告示例 | Report Demo](demo/report-demo.html) — 画像数据生成的学习报告形态

Static demo pages (display layer only, no interactive logic).

---

## 五、关于 | About

设计思路以 MIT 协议开源，欢迎基于此思路构建你自己的产品。

The design concepts are open-sourced under the MIT License. Feel free to build your own product on top of them.

**龙悟 · AI 学习工作台** | 龙悟在抖音/小红书/视频号：`龙悟AI创业` / `龙悟IP智能体`

---

*本仓库仅包含设计思路与静态演示，不包含可运行的实现。*
*This repository contains design concepts and static demos only — no runnable implementation.*
