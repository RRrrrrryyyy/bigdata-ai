# bigdata-ai

AI 核心概念学习资料仓库：围绕 **Agent（智能体）**、**大模型的上下文（Context）**、**Skill（智能体技能）** 三个概念，沉淀结构化学习资料与概念关系解析，并存放驱动资料生成的通用 Skill 定义。

## 仓库用途

1. **概念学习**：为任意新概念生成结构化的八段式学习资料（学习目标 / 核心问题 / 个人解释 / 核心机制 / 应用场景 / 边界辨析 / 自测问题 / 来源链接）；
2. **概念关联**：说明 Agent、上下文、Skill 三者之间的协作关系（见 `learning-materials/concept-relationship.md`，Mermaid 流程图 + 文字）；
3. **技能沉淀**：存放「概念学习资料生成 Skill」的定义文件（SKILL.md）与分发包，使其可复用、可迭代。

## 目录结构

```
bigdata-ai/
├── learning-materials/              # 概念学习资料
│   ├── agent.html                   # Agent（智能体）
│   ├── llm-context.html             # 大模型的上下文
│   ├── skill.html                   # Skill（智能体技能）
│   └── concept-relationship.md      # 三者关系解析（Mermaid 流程图 + 文字）
├── README.md
├── .gitignore
├── concept-learning-material.zip    # Skill 分发包（含最新 SKILL.md）
└── .workbuddy/
    └── skills/
        └── concept-learning-skill/
            └── SKILL.md             # 项目级 Skill 定义文件
```

## Skill 存放路径

| 位置 | 路径 | 说明 |
|------|------|------|
| 项目级（本仓库） | `.workbuddy/skills/concept-learning-skill/SKILL.md` | 随仓库分发，团队内共享 |
| 用户级（本机） | `C:\Users\l\.workbuddy\skills\concept-learning-material\SKILL.md` | 全局可用，所有项目生效 |
| 分发包 | `concept-learning-material.zip` | 可导入其他环境使用，已与项目级同步 |

> 注意：项目级目录名 `concept-learning-skill` 与 Skill 内部 `name` 字段（`concept-learning-material`）不一致，规范化处理待定。

## 调用方法

### 方式一：自然语言触发（推荐）

在 WorkBuddy 对话中直接说出包含概念学习意图的话，技能会自动加载并执行：

```
帮我学习「XX概念」
什么是 XX？给我一份学习资料
解释一下 XX / XX 入门
```

### 方式二：显式指定

```
调用 concept-learning-skill，主题是「XX概念」，输出 HTML 格式，保存到 learning-materials/
```

### 可选参数

| 参数 | 缺省值 | 说明 |
|------|--------|------|
| 概念名称 | **必填**（唯一必填项） | 任意领域、任意语言的新概念 |
| 用户背景 | 无领域专业背景的聪明初学者 | 影响比喻选择和解释深度 |
| 深度 | 入门到中级 | 可选：入门 / 进阶 / 专家 |
| 语言 | 与提问语言一致 | — |
| 输出格式 | 对话内 Markdown | 可选 HTML / .md 文件，配合保存目录参数 |

### Skill 执行流程

技能加载后严格按四步执行：

1. **拆解概念**：识别领域、别名与易混淆概念，同名多义时先消歧义；
2. **强制检索**：联网检索权威来源（≥3 条独立来源，含 ≥1 条一手来源，此步不可跳过）；
3. **综合生成**：按八段式结构输出学习资料；
4. **自检**：逐项核对 9 项清单（完整性、五要素齐备、目标↔测评呼应、通用性、有据可依、通俗性、辨析有效、链接可达、篇幅合规），未通过项修正后才交付。

### 学习资料的八段式结构

每份资料固定包含：**学习目标 → 核心问题 → 个人解释（含比喻）→ 核心机制 → 应用场景（含反例）→ 边界辨析（对比表格）→ 自测问题（附折叠参考答案）→ 来源链接**。"学习目标"承诺的能力与"自测问题"一一呼应，形成"目标引导 → 正文学习 → 自测检验"的完整自学闭环。

## ⚠️ 人工核查说明

**本仓库中的所有学习资料均经过我（仓库所有者）的人工核查。**

- 三份概念学习资料（`learning-materials/*.html`）与概念关系解析（`learning-materials/concept-relationship.md`）中的事实性内容，均已由我**逐条人工核对**，与 Skill 流程中检索到的权威来源（Anthropic 官方文档、IBM Think 等）比对确认；
- 来源链接部分经逐一验证，确保真实可达、贡献说明与内容相符；
- 自测题的题干与参考答案均经人工校对，确认答案能在正文中找到依据、且与学习目标呼应；
- 尽管 Skill 的生成流程已内置"强制检索 + 9 项自检"，**人工核查仍作为发布前的最后一道关口**。引用本仓库内容前，建议读者访问来源链接做二次确认。

## 后续维护

- 新增概念学习资料：直接对话触发 Skill，产出保存至 `learning-materials/`；
- 迭代 Skill 本身：修改 `.workbuddy/skills/concept-learning-skill/SKILL.md`，重新打包 `concept-learning-material.zip`，并同步用户级副本；
- 相关阅读：每个概念的详细来源清单见对应 HTML 文件的"来源链接"章节；三个概念的关系见 `learning-materials/concept-relationship.md`。
