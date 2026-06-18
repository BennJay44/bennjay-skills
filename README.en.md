[中文](./README.md) · **English**

# Bennjay Skills

A small collection of AI Skills I use in my Codex / Claude Code workflow: exam cramming, Claude-based plan review, and programming retrospectives.

[![License](https://img.shields.io/badge/License-MIT-3B82F6?style=for-the-badge)](./LICENSE)
[![Skills](https://img.shields.io/badge/Skills-3-10B981?style=for-the-badge)](#skills)
[![AgentSkills](https://img.shields.io/badge/AgentSkills-Standard-8B5CF6?style=for-the-badge)](https://agentskills.io)
![Codex](https://img.shields.io/badge/Codex-Skill-10B981?style=flat-square&logo=openai&logoColor=white)
![Claude Code](https://img.shields.io/badge/Claude_Code-Skill-D97706?style=flat-square&logo=anthropic&logoColor=white)

Each skill is a structured instruction set an agent can load directly. The repo follows the common Agent Skills layout: one folder per skill, with `SKILL.md` as the entry point.

---

## Index

| Name | One-liner | Best for |
|---|---|---|
| [exam-cram-cn](#exam-cram-cn) | Turns slides, homework, past papers, and teacher notes into a beginner-friendly Chinese exam guide | Finals, midterms, quizzes, question banks, code fill-ins, calculations |
| [claude-grill](#claude-grill) | Uses Claude Code as a read-only reviewer for Codex plans | Plan approval, implementation review, multi-round critique |
| [vibe-retrospective-tutor](#vibe-retrospective-tutor) | Turns an agent-assisted programming session into a Chinese learning retrospective | Understanding what changed, why it changed, and how to practice |

---

## Install

In any agent that supports Skills, ask it to install a skill folder:

```text
Install this skill: https://github.com/BennJay44/bennjay-skills/tree/main/<skill-name>
```

Replace `<skill-name>` with:

```text
exam-cram-cn
claude-grill
vibe-retrospective-tutor
```

Manual local install:

```bash
cp -R exam-cram-cn ~/.codex/skills/
cp -R claude-grill ~/.codex/skills/
cp -R vibe-retrospective-tutor ~/.codex/skills/
```

---

## Skills

### exam-cram-cn

A Chinese exam-cramming skill. It treats the learner as nearly zero-background by default and aims to produce a usable `期末通关教程.md`, not generic notes.

Core behavior:

- Explain concepts before questions.
- Target high exam performance, roughly 95-point difficulty.
- Put every extracted question into both the index and the tutorial body.
- Attach original questions to their relevant knowledge point.
- Explain multiple-choice options one by one; explain each code blank and each calculation step.
- Never invent missing stems, images, answers, or platform explanations.

Trigger examples:

```text
帮我整理期末通关教程
我零基础，明天考试，从头带我过
把当前文件夹里的题库整理成复习资料
```

-> [SKILL.md](./exam-cram-cn/SKILL.md)

### claude-grill

Uses Claude Code as a read-only external reviewer for a Codex plan. Claude returns one of:

```text
VERDICT: APPROVED
VERDICT: REVISE
VERDICT: BLOCKED
```

Codex remains the owner of the work and applies any changes.

Trigger examples:

```text
让 claudecode 审批一下这个方案
和 claudegrill 商讨后再做
多轮审查方案，直到能执行
```

-> [SKILL.md](./claude-grill/SKILL.md)

### vibe-retrospective-tutor

Turns a completed agent-assisted programming task into a Chinese learning retrospective. It explains what changed, why it changed, alternatives considered, pitfalls, validation, and practice ideas.

It only triggers when the user explicitly asks for a retrospective or tutorial.

Trigger examples:

```text
复盘你是如何完成的
给我写复盘教程
帮我理解刚才的实现
```

-> [SKILL.md](./vibe-retrospective-tutor/SKILL.md)

---

## About

This repository is organized for personal use first. Skills that prove useful across repeated work can be added here over time.

MIT licensed. See [LICENSE](./LICENSE).
