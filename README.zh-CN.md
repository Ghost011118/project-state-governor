# Project State Governor（项目状态治理器）

[English](README.md)

**别再让项目真相丢失在一次次 Agent 会话之间。**

Project State Governor 是一个面向长期项目的 Agent Skill，用于在多轮会话、多分支、开发周期、审查和研究迭代之间维护精简、可核验、可持续更新的项目事实源。它帮助 Agent 区分当前状态与历史记录，核实完成声明，保留有价值的负面证据，并阻止项目文档演变成大量过期的状态文件。

## 为什么需要它

长期使用 AI Agent 做项目时，常见的问题并不是代码立刻报错，而是代码、测试、计划、审查结论和对话摘要逐渐互相矛盾。新的 Agent 需要重复重建上下文，甚至会基于已经失效的前提继续工作。

Project State Governor 提供一套持久化治理模型：

- Git 保存底层历史；
- `AGENTS.md` 规定 Agent 如何工作；
- 精简的规范状态系统记录“现在什么是真的”；
- 对话只是工作上下文，不是权威项目记忆；
- 证据优先于信心。

## 它能做什么

- 根据需求、契约、Git、代码、测试和文档重建当前项目状态；
- 对使命、工作流、里程碑、任务、研究假设、决策、约束、阻塞和经验进行分类；
- 区分“本次会话完成”与任务、里程碑、工作流、使命完成；
- 协调互相矛盾的文档，不把旧 AI 输出直接当成事实；
- 保存代价高昂的负面证据，避免重复走已经证伪的路线；
- 合并过期或重复状态，同时让 Git 继续承担历史档案职责；
- 与工程治理、研究治理类 Skill 清晰协作；
- 拒绝编造产品意图、代替所有者接受发布风险或持久化秘密。

## 什么时候使用

适合以下场景：

- 在新会话中恢复一个持续时间较长的项目；
- 回答“究竟哪些已完成、进行中、受阻，下一步是什么”；
- 清理碎片化的计划、TODO、交接和审查摘要；
- 协调不同分支的局部进度与项目规范状态；
- 在写入“已完成”之前验证完成声明；
- 保存被否定的研究方向或值得长期保留的教训；
- 判断一次对话是否真的产生了应当持久化的新项目事实。

它不能替代产品所有者、编码 Agent、研究执行者或发布审批人。

## 安装

### Codex

macOS/Linux：

```bash
mkdir -p ~/.codex/skills
git clone https://github.com/Ghost011118/project-state-governor.git \
  ~/.codex/skills/project-state-governor
```

Windows PowerShell：

```powershell
New-Item -ItemType Directory -Force "$env:USERPROFILE\.codex\skills" | Out-Null
git clone https://github.com/Ghost011118/project-state-governor.git `
  "$env:USERPROFILE\.codex\skills\project-state-governor"
```

安装后新建一个 Codex 任务，使技能列表重新加载。

### Claude Code 与其他兼容 Agent Skills 的宿主

可移植的核心是 `SKILL.md` 和 `references/`。请把仓库复制或克隆到对应宿主文档指定的技能目录。Claude Code 个人 Skill 常用路径为：

```bash
mkdir -p ~/.claude/skills
git clone https://github.com/Ghost011118/project-state-governor.git \
  ~/.claude/skills/project-state-governor
```

不同宿主的发现路径和元数据支持可能不同。`agents/openai.yaml` 是 Codex 使用的界面元数据，其他宿主可忽略。

## 快速开始

重建或修复项目状态时，可以显式调用：

```text
使用 $project-state-governor 检查这个仓库，识别当前权威状态，
并提出最小的规范状态更新。
```

也可以自然描述任务：

```text
协调最近三个分支产生的项目状态。核实哪些工作真正完成，保留重要的
失败路线，并指出下一项有证据支持的任务。
```

Skill 会先回忆和验证证据，再应用语义状态差异：

```text
RECALL -> PROPOSE -> VERIFY -> APPLY -> CONSOLIDATE
```

## 规范状态结构

小型和中型项目：

```text
AGENTS.md
PROJECT_STATE.md
```

大型项目：

```text
AGENTS.md
.project/
  MANIFEST.md
  STATE.md
  DECISIONS.md
  CONSTRAINTS.md
  NEGATIVE_EVIDENCE.md
  areas/
```

这些文件共同组成一个规范状态系统。目标不是文档越多越好，而是让新 Agent 能以最低成本获得足够、可信、最新的项目知识。

## 核心安全边界

Project State Governor 不会自主执行以下行为：

- 重新定义项目使命或成功标准；
- 在多个合法但尚未定义的业务结果之间替所有者做决定；
- 接受尚未解决的发布、安全、法律、运营或研究风险；
- 自动把代码、测试、审查或旧 AI 输出当成最高权威；
- 在价值不明确时删除可能包含独特信息的历史；
- 保存凭据、令牌、个人数据或其他秘密。

## 仓库内容

```text
SKILL.md                         Skill 主指令
agents/openai.yaml              Codex 界面元数据
assets/icon.svg                 Skill 图标
references/project-state-schema.md
references/persistence-lifecycle.md
references/reconstruction-workflow.md
references/manifest-routing.md
```

## 兼容性与验证

- 包结构遵循以 `SKILL.md` 为入口的 Codex Skill 结构；
- 核心指令不依赖运行时代码或外部服务；
- Skill 主指令使用英文，以提高跨宿主可移植性；完整用户文档同时提供英文和中文；
- 不同宿主的发现机制和界面元数据可能不同。如发现兼容问题，请提交包含复现证据的 Issue。

## 参与贡献

欢迎提交有证据支持的改进。发起 Pull Request 前请阅读 [CONTRIBUTING.md](CONTRIBUTING.md)，安全问题请按 [SECURITY.md](SECURITY.md) 说明报告。

## 目录投稿资料

Skills/Agents 目录维护者可以直接使用 [docs/DIRECTORY-LISTING.md](docs/DIRECTORY-LISTING.md) 中的中英文简介、标签和兼容性说明。

## 许可证

本项目采用 [Apache License 2.0](LICENSE) 开源许可证。
