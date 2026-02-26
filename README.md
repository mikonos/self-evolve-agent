# self-evolve — Agent 自主进化引擎

让 AI agent 像生物进化一样持续变强：**感知差距 → 搜索方案 → 设计实验 → 跑实验 → 选赢家 → 固化 → 下一轮**。每个进化周期有明确的评估截止时间，到期自动触发评估。

## When to Use

- 定期自主进化、能力升级、工作流优化、skill/工具迭代
- self-think 诊断出能力短板时，自动建议启动一轮进化
- 显式调用：「进化一下 X 能力」/「self-evolve 记忆检索」/「找个更好的 Y 方案」

## 核心机制

- **四步滴答巡航**：扫描运行中实验 → 记录观察数据 → 到期评估与固化 → 启动新轮次
- **状态机**：`memory/evolve/state.json` 管理 `active_experiments`，支持多实验并发观察（正交、可逆、可测）
- **红线**：禁止伪进化（仅改排版/报告）、遇阻必须挂起 BLOCKED、不可越过底线

## Install

**ClawHub（OpenClaw）**

```bash
npx clawhub@latest install self-evolve --workdir . --force
```

**Cursor / 本地**

将本仓库中的 `SKILL.md` 放到你的 skills 目录（如 `.cursor/skills/self-evolve/`），并在规则中注册 `self-evolve` 及触发方式（如 Cron）。

## 文档

- `SKILL.md` — 主入口：进化周期、四步巡航、红线、输出规范、质量自检
