# delivery-focus · 交付优先

让 AI 少做重复检查、过度准备和反复评审，把时间用在完成用户已经确定的任务上。

A lightweight Codex skill that helps agents finish agreed work by reducing redundant checks, unnecessary preparation, and repeated reviews—while retaining necessary validation and permission boundaries.

[中文说明](#中文说明) · [English](#english) · [MIT License](LICENSE)

## 中文说明

### 它解决什么问题

AI 有时会一直忙，却没有推进交付：已经通过的检查反复重跑，已经决定的事情重新评审，原本简单的任务不断长出采集系统、台账和新流程。

这个 skill 为这些情况提供行动约束：

- 沿用仍然有效的目标、决定和检查结果。
- 新增工作必须能影响当前交付、结论或具体风险处置。
- 做足必要检查；通过后继续交付，避免无依据地追加检查。
- 支线没有带来新信息时及时结束，回到尚未完成的任务。
- 不为执行这个 skill 再建立一套监督流程。

它适合实现、研究、调试和交付中出现上述问题时使用。用户明确要求的审计、整理和验证仍须完整完成。

### 安装

这是一个纯文本 skill，无需安装 Python、Node.js 或其他依赖。

1. 下载本仓库：在 GitHub 点击 **Code → Download ZIP**，然后解压。
2. 将解压后的仓库文件夹命名为 `delivery-focus`，放到 Codex 的个人技能目录 `~/.agents/skills/`。Windows 通常是 `%USERPROFILE%\.agents\skills\`。如果目录不存在，可先创建。
3. 确认最终路径为 `~/.agents/skills/delivery-focus/SKILL.md`，避免多嵌套一层仓库文件夹。若 Codex 未显示该 skill，重启后再查看。

也可以只为一个项目安装：放在该项目的 `.agents/skills/delivery-focus/` 中。个人安装和项目安装二选一即可。

技能目录与发现方式参见 [Codex 官方技能文档](https://learn.chatgpt.com/docs/build-skills)。

### 使用

在 Codex 中明确调用：

```text
使用 $delivery-focus 完成当前任务。沿用已经确定的方案和仍然有效的检查结果，
优先完成尚缺的交付，保留必要验证。
```

也可以在具体请求中使用：

```text
使用 $delivery-focus 把已经选定的方案实现出来，不需要重新做方案选型。
```

技能保留 Codex 的默认自动匹配方式；是否自动使用由当前请求和运行环境决定。

### 行为示例

以下是期望行为示例，不是已完成的效果测试。

| 情况 | 期望的处理方式 |
| --- | --- |
| 某项检查已经通过，相关输入、实现和环境都没变化 | 复用结果，继续完成交付。 |
| 修复一个局部问题 | 验证受影响的行为；影响范围不明确时扩大检查。 |
| 用户要求分析历史记录 | 先分析已有历史记录；不要擅自改为长期实时监控。 |
| 一条研究支线持续没有新信息 | 结束重复尝试，转向已授权的其他工作；没有可执行工作时说明具体阻碍。 |

### 能力边界

这是给模型的行为指导，不是强制执行的检查器。它不能保证消除所有无用功，也不能保证研究成功、收益或完成期限。目前未完成系统性的行为对照测试，不宣称已经证明节省了多少时间或 token。

本仓库不包含执行脚本、联网采集器或账号配置。使用该 skill 不增加工具权限；发布、删除、交易等操作仍按原有授权边界处理。

### 参与改进

欢迎提交 Issue 或 Pull Request。最有用的反馈包括：脱敏后的任务、AI 实际做了什么、哪些动作没有价值，以及你期望它怎么处理。请勿提交密钥、个人信息或未获授权的项目资料。

优先修正真实复发的问题，保持规则简短；不要用更多检查流程来解决检查过多的问题。

## English

### Purpose

An agent can stay busy without moving a task forward: rerunning valid checks, reopening settled choices, or building supporting infrastructure before establishing its value. This skill guides the agent to:

- Reuse decisions and validation results while they remain applicable.
- Add work only when it can change the current deliverable, conclusion, or handling of a concrete risk.
- Complete necessary validation, then move on to delivery.
- End repetitive branches that produce no new information.
- Avoid creating extra process just to enforce these principles.

Explicitly requested audits and reviews retain their full scope. The skill does not replace necessary correctness checks or expand permissions.

### Install and use

Download this repository using **Code → Download ZIP**, extract it, and rename the extracted folder to `delivery-focus`. Place it at `~/.agents/skills/delivery-focus/` for personal use, or at `.agents/skills/delivery-focus/` inside a project. Choose one location. Ensure `SKILL.md` is directly inside that folder; restart Codex if the skill does not appear.

No runtime dependencies are required. See the [official Codex skills documentation](https://learn.chatgpt.com/docs/build-skills) for discovery details.

Invoke it explicitly:

```text
Use $delivery-focus to finish the current task. Reuse settled decisions and
applicable validation results, complete the missing deliverable, and retain
necessary checks.
```

Default automatic matching remains enabled. The skill instructions and UI metadata are written in Chinese; your request can specify the language of the response. Compatibility with other agents has not been verified.

### Status and contributions

This is instruction-based guidance, not an enforcement mechanism. No systematic behavioral comparison has been completed; no measured time or token savings are claimed. There are no execution scripts, network collectors, or account configurations in this repository.

Issues and pull requests are welcome. Share a sanitized task, the observed behavior, the unnecessary work, and the expected behavior. Prefer focused corrections grounded in real failures over adding more process.

## Repository files

```text
delivery-focus/
├── SKILL.md             # Skill instructions
├── agents/
│   └── openai.yaml      # Codex UI metadata
├── README.md            # Installation, usage, and examples
└── LICENSE              # MIT License
```

## License

[MIT](LICENSE). You may use, modify, and redistribute this skill under the license terms.
