# Personal_Prompt_Template

个人使用的 AI 编程工作流提示词模板，分两段使用：

1. **计划阶段**：从发散性需求收敛到具体、有条理的要求；先按 Trace Bullet 方法验证，再产出 Mermaid 架构图 `pre_architecture.md` 和 UI 设计图，然后停下等待决策。
2. **编码阶段**：约束代码注释、docstring、ADR（架构决策记录）与双向追溯。

下面共四段，复制对应代码块内容直接使用。

---

## 提示词一：计划阶段（中文）

```text
# 计划阶段

## 目标
- 我想做什么？**做的和不做的都很重要**
- **从发散性的需求，收敛到具体的、有条理的要求**

## 功能

## 外观

## 运行环境限制
- 运行系统说明
- Python 语言写就
- 要求使用浮点数时统一使用 FP64

## 架构和代码限制
- 要求外观、配置、主题与核心逻辑分开，但只做必要的分离。
- 模块和文件职责尽量单一。
- 优先使用语言/框架/标准库已有能力。
- 非必要不使用集成。
- 注重 Ubiquitous Language（统一语言）。

## 对你的做事流程要求
先应用 trace bullet 方法，在检查无误后，生成以 mermaid 写成的 class diagram 文件：pre_architecture.md；生成你的 UI 设计图片，之后停止行动，等待我的下一步决策。
```

## 提示词二：编码阶段（中文）

```text
# 编码阶段

## 可读性与可追溯性约束

### 代码注释
1. 每个文件必须有文件头注释：模块名、职责、依赖、被依赖、关联 ADR。
2. 每个公开函数必须有 docstring：前置条件、后置条件、禁止事项、异常。
3. 行内注释只解释"为什么"，不解释"做什么"。
4. 禁止复述代码、禁止死代码、禁止无条件的 TODO。

### 关键决策文档（ADR）
1. 做出算法选择、模块边界、设计模式、权衡取舍时，必须创建 ADR。
2. ADR 格式：状态、背景、决策、理由、代价、关联代码位置。
3. ADR 编号连续，存入 docs/decisions/。
4. 代码中引用 ADR，ADR 中反向引用代码位置。

### 双向追溯
1. 从代码注释能找到 ADR。
2. 从 ADR 能找到代码文件和函数名。

任何关键决策，都能回答"为什么这么做"和"在哪里做的"。
```

## Prompt 1: Planning Phase (English)

```text
# 1. Planning Phase

## Objectives
- What do I want to do? Both what to do and what NOT to do are equally important.
- **Converge from divergent requirements to specific, well-structured requirements.**

## Functionality

## Appearance

## Runtime Environment Constraints
- Operating system specification
- Written in Python
- Use FP64 uniformly when floating-point numbers are required.

## Architecture and Code Constraints
- Separate appearance, configuration, and themes from core logic, applying only necessary separation of concerns.
- Keep module and file responsibilities as single as possible (Single Responsibility Principle).
- Prioritize existing capabilities of the language/framework/standard library.
- Avoid unnecessary integrations.
- Emphasize Ubiquitous Language.

## Workflow Requirements for You
First, apply the Trace Bullet method. After verifying correctness, generate a class diagram file written in Mermaid: pre_architecture.md; generate your UI design image. Then, stop all actions and wait for my next decision.
```

## Prompt 2: Coding Phase (English)

```text
# 2. Coding Phase

## Readability and Traceability Constraints

### Code Comments
- Every file must have a file header comment: module name, responsibilities, dependencies, dependents, and associated ADRs.
- Every public function must have a docstring: preconditions, postconditions, prohibitions, and exceptions.
- Inline comments should only explain "why", not "what".
- Prohibit code paraphrasing, dead code, and unconditional TODOs.

### Architecture Decision Records (ADR)
- An ADR must be created when making algorithm choices, defining module boundaries, applying design patterns, or making trade-offs.
- ADR format: Status, Context, Decision, Rationale, Consequences (Costs), and associated code locations.
- ADR numbering must be sequential and stored in docs/decisions/.
- Reference ADRs in the code, and back-reference code locations in the ADRs.

### Bidirectional Traceability
- From code comments, one can find the corresponding ADR.
- From the ADR, one can find the corresponding code files and function names.
- Any key decision can answer "why it was done" and "where it was done".
```