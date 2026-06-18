**中文** · [English](./README.en.md)

# Bennjay Skills

我自己在 Codex / Claude Code 工作流里沉淀出来的 AI Skills，先放三个最常用的：考试通关、Claude 方案审查、编程复盘导师。

[![License](https://img.shields.io/badge/License-MIT-3B82F6?style=for-the-badge)](./LICENSE)
[![Skills](https://img.shields.io/badge/Skills-3-10B981?style=for-the-badge)](#skills)
[![AgentSkills](https://img.shields.io/badge/AgentSkills-Standard-8B5CF6?style=for-the-badge)](https://agentskills.io)
![Codex](https://img.shields.io/badge/Codex-Skill-10B981?style=flat-square&logo=openai&logoColor=white)
![Claude Code](https://img.shields.io/badge/Claude_Code-Skill-D97706?style=flat-square&logo=anthropic&logoColor=white)

这些 skill 都是为了解决真实工作里反复出现的问题：考前冲刺资料太散、方案需要第二个模型审一遍、任务做完之后想真正学会而不是只看总结。

每个 skill 都是 Agent 可以直接加载的结构化指令集，遵循 Agent Skills 的基本目录约定：每个 skill 一个文件夹，核心入口是 `SKILL.md`。

---

## 目录

| 名字 | 一句话 | 适合场景 |
|---|---|---|
| [exam-cram-cn（考试通关）](#exam-cram-cn考试通关) | 把课件、作业题、真题和老师重点整理成零基础也能看的期末通关教程 | 期末、midterm、quiz、题库冲刺、代码填空、计算题 |
| [claude-grill（Claude 审方案）](#claude-grillclaude-审方案) | 让 Claude Code 只读审查 Codex 的方案，给出 APPROVED / REVISE / BLOCKED | 重要改动前的方案审批、多轮审查、实现前把关 |
| [vibe-retrospective-tutor（编程复盘导师）](#vibe-retrospective-tutor编程复盘导师) | 把一次智能体辅助编程过程整理成能学习的中文复盘教程 | 想理解刚才怎么实现、为什么这么改、下次怎么练 |

---

## 安装方式

在支持 Skill 的 Agent 里，可以直接让它安装某个目录：

```text
帮我安装这个 skill：https://github.com/BennJay44/bennjay-skills/tree/main/<skill-name>
```

把 `<skill-name>` 换成：

```text
exam-cram-cn
claude-grill
vibe-retrospective-tutor
```

本地手动安装也可以：

```bash
cp -R exam-cram-cn ~/.codex/skills/
cp -R claude-grill ~/.codex/skills/
cp -R vibe-retrospective-tutor ~/.codex/skills/
```

---

## Skills

### exam-cram-cn（考试通关）

给中文考试复习用的 skill。它默认把学生当成几乎没有背景知识的新手，目标不是写漂亮笔记，而是产出能直接拿去学、拿去考的《期末通关教程》。

它会先快速扫描当前文件夹，再只问一次有没有老师重点、复习范围、题库、作业题或真题。之后默认把资料整理到 `期末通关教程.md` 里。

核心规则：

- 概念先讲清楚，再讲题。
- 默认目标是考试 95 分难度。
- 所有原题必须进入题目索引和教程正文。
- 原题放在对应知识点后面，不集中堆到最后。
- 选择题逐项解释，代码题逐空解释，计算题写公式、变量、代入和结果。
- 图片、公式、答案来源看不到就标注限制，不编造。

怎么触发：

```text
帮我整理期末通关教程
这些作业题可能考原题，帮我逐题讲
我零基础，明天考试，从头带我过
把当前文件夹里的题库整理成复习资料
```

-> [SKILL.md](./exam-cram-cn/SKILL.md)

### claude-grill（Claude 审方案）

让 Claude Code 作为只读外部评审，审查 Codex 当前方案或实现计划。它不让 Claude 直接改文件，只让 Claude 给出明确 verdict：

```text
VERDICT: APPROVED
VERDICT: REVISE
VERDICT: BLOCKED
```

适合那些“先别急着做，让另一个模型挑刺”的场景。Codex 仍然负责最终判断和修改。

怎么触发：

```text
让 claudecode 审批一下这个方案
和 claudegrill 商讨后再做
让 Claude Code grill 一轮
多轮审查方案，直到能执行
```

-> [SKILL.md](./claude-grill/SKILL.md)

### vibe-retrospective-tutor（编程复盘导师）

这个 skill 用来把一次已经完成的智能体辅助编程过程，整理成中文学习复盘。它不是普通总结，也不是 changelog，而是解释“为什么这么改、还可以怎么做、踩了什么坑、怎么验证、用户下次怎么练”。

触发条件比较严格：只有用户明确要求复盘或教程时才使用，不会在每次任务结束后自动冒出来。

怎么触发：

```text
复盘你是如何完成的
给我写复盘教程
讲讲这次怎么做的
帮我理解刚才的实现
```

-> [SKILL.md](./vibe-retrospective-tutor/SKILL.md)

---

## 关于

这个仓库先按个人使用习惯整理，后续会继续把稳定、反复用得上的 skill 放进来。

自由使用、修改、再分发。见 [MIT License](./LICENSE)。
