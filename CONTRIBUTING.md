# Contributing / 参与贡献

Thank you for improving Project State Governor. Contributions should make project-state decisions clearer, safer, or cheaper to retrieve—not merely add more process or documentation.

感谢你改进 Project State Governor。贡献应当让项目状态决策更清晰、更安全或更容易检索，而不是单纯增加流程和文档数量。

## Contribution principles / 贡献原则

- Preserve the authority boundary: the skill must not invent product intent or accept material risk for the owner.
- Treat code, tests, reviews, and prior AI output as evidence, not automatic truth.
- Keep `SKILL.md` focused; put conditional detail in `references/`.
- Do not add host-specific requirements to the portable core unless they are optional and clearly labeled.
- Never include credentials, personal data, private repository content, or proprietary examples.
- Preserve compatibility with the existing status vocabulary unless a verified requirement supports a change.

- 保持权责边界：Skill 不得编造产品意图，也不得替所有者接受重大风险；
- 将代码、测试、审查和旧 AI 输出视为证据，而不是自动成立的事实；
- 保持 `SKILL.md` 聚焦，将条件性细节放入 `references/`；
- 除非明确标注为可选，否则不要把某个宿主的专有要求写入可移植核心；
- 不得提交凭据、个人数据、私有仓库内容或专有示例；
- 除非有可核验证据支持，不要破坏现有状态词汇的兼容性。

## Pull request checklist / PR 检查清单

1. Explain the concrete failure mode or use case the change addresses.
2. Cite the requirement, invariant, observed behavior, or reproducible example supporting it.
3. Keep the change scoped to that problem.
4. Run the skill validator described below.
5. Verify all relative links and referenced files.
6. Update both README files when user-visible behavior or compatibility changes.

1. 说明本次修改解决的具体失败模式或使用场景；
2. 提供支持该修改的需求、约束、已观察行为或可复现实例；
3. 将修改范围限制在该问题内；
4. 运行下方技能校验；
5. 验证全部相对链接和引用文件；
6. 如果用户可见行为或兼容性变化，同时更新中英文 README。

## Validation / 校验

If Codex's `skill-creator` utilities are installed, run:

```text
python <skill-creator>/scripts/quick_validate.py <path-to-project-state-governor>
```

Also inspect the final Git diff and confirm the package contains no secrets or machine-specific absolute paths.

如果本机已安装 Codex 的 `skill-creator` 工具，请运行上面的校验命令；同时检查最终 Git 差异，确认包中没有秘密或与某台机器绑定的绝对路径。
