# Concept Learning Hub · 概念学习资料生成

> 一个会自己"生产教材"的仓库。
> 把 `concept-learning-material-generator` Skill 装进项目，给它一个概念名，就能产出一份**单文件、可离线、可打印**的 HTML 学习资料。

## 它解决什么问题

学一个新概念时，痛点不是"找不到资料"，而是：

1. 资料散乱（公众号 / 文档 / 论文各说各话）
2. 抽象难落地（文字定义懂了，对不上真实系统）
3. 缺图、缺反例（看完就忘）
4. 读完不知道掌握没（没有自检）

本仓库用**一个 Skill + 一组输出规范**把"学一个概念"这件事封装成流水线。

---

## 仓库结构

```
concept-learning-hub/
├── .workbuddy/
│   └── skills/
│       └── concept-learning-material-generator/
│           └── SKILL.md              ← 唯一的 Skill，定义"如何生成概念学习资料"
├── learning-materials/
│   ├── agent.html                    ← Agent 概念学习资料
│   ├── llm-context.html              ← 大模型的上下文 学习资料
│   ├── skill.html                    ← Skill 概念学习资料
│   ├── transformer.html              ← Transformer 学习资料（由本仓库 Skill 生成）
│   └── concept-relationship.html     ← 三概念关系全景图
├── README.md
└── .gitignore
```

> `.workbuddy/skills/` 内的 Skill 是**项目级 Skill**，随仓库分发，团队共享。其它 `.workbuddy/` 子目录（如 `cache/`、`memory/`、`state/`）在 `.gitignore` 里被忽略，不入库。

---

## 怎么用

### 1. 把项目级 Skill 加载到 WorkBuddy
打开本仓库根目录，WorkBuddy 会自动发现 `.workbuddy/skills/concept-learning-material-generator/`，无需手动配置。

### 2. 触发 Skill 生成新概念资料

直接对 WorkBuddy 说：

```
帮我用概念学习资料生成 Skill 学一下 "Transformer"
```

或者按 Skill 接受的格式：

```
<概念名> [/ 难度: 入门|进阶|深入] [/ 长度: 短|标准|长]
```

例如：

```
大模型的幻觉 / 进阶 / 标准
```

### 3. 打开生成的学习资料

```
learning-materials/<slug>.html
```

每个 HTML 都是：
- ✅ 单文件，**离线可开**
- ✅ 内联 CSS / JS / SVG，**无外链**
- ✅ 自适应深色 / 浅色模式
- ✅ 打印友好（Ctrl + P）
- ✅ 移动端友好

---

## 输出规范（Skill 的硬性要求）

每个学习资料必须包含 8 个章节，顺序固定：

1. **Hero 区**：概念名 + 一句话定义 + 难度 / 时长标签
2. **一句话三连**：What / Why / How 三栏卡片
3. **核心机制**：含至少一张 inline SVG 图
4. **三个递进示例**：从最小 → 复杂
5. **常见误区 / 反直觉点**：至少 3 条
6. **自检题**：3 ~ 5 题 4 选 1，含答案揭示
7. **与相邻概念的边界**：对比小表
8. **延伸阅读**：链接到其它资料

完整规范见 [`SKILL.md`](./.workbuddy/skills/concept-learning-material-generator/SKILL.md)。

---

## 已生成的学习资料

| 资料 | 概念 | 主色 |
| --- | --- | --- |
| [`agent.html`](./learning-materials/agent.html) | Agent / 智能体 | `#6366f1` 靛紫 |
| [`llm-context.html`](./learning-materials/llm-context.html) | 大模型的上下文 | `#0ea5e9` 天空蓝 |
| [`skill.html`](./learning-materials/skill.html) | Skill / 技能 | `#10b981` 翠绿 |
| [`transformer.html`](./learning-materials/transformer.html) | Transformer / 自注意力架构 | `#f59e0b` 琥珀 |
| [`concept-relationship.html`](./learning-materials/concept-relationship.html) | 三概念关系全景图 | 三色渐变 |

每份资料预计阅读 8 ~ 10 分钟。

---

## 设计理念

- **单一职责**：仓库只做一件事 —— 把概念变成可学的资料。
- **可复用资产**：Skill 是仓库的核心，所有 HTML 都遵循同一规范，方便横向对比与扩展。
- **离线优先**：所有资料单文件可开，无需联网 / 启动服务。
- **暗色友好**：跟系统主题切换，打印也清晰。
- **可演进**：新增概念只需要 `learning-materials/<slug>.html`，不改其它文件。

---

## 路线图（可能的扩展方向）

- [ ] 自动出题 + 自动判分
- [ ] 移动端 TOC 抽屉
- [ ] 资料间的双向链接图谱
- [ ] 集成 PDF / DOCX 导出（按需触发）
- [ ] 国际化（i18n）

---

## 许可证

MIT。你可以做任何事，包括复制这套规范到自己的仓库。