# Security Policy / 安全策略

Project State Governor is an instruction-only skill and does not execute network calls or modify production systems by itself. Its main security risks are unsafe governance instructions, accidental secret persistence, and misleading authority or completion claims.

Project State Governor 是纯指令型 Skill，本身不会执行网络请求或修改生产系统。主要安全风险来自不安全的治理指令、意外保存秘密，以及对权限或完成状态的误导性声明。

## Reporting a vulnerability / 报告漏洞

Please do not include credentials, private repository content, personal data, or an unredacted exploit in a public issue. Use GitHub's private vulnerability reporting feature when it is available for this repository. If private reporting is unavailable, open a minimal public issue asking the maintainer for a private contact channel without disclosing sensitive details.

请勿在公开 Issue 中包含凭据、私有仓库内容、个人数据或未脱敏的利用细节。如果仓库启用了 GitHub 私有漏洞报告，请优先使用；如果没有，请只创建一个不包含敏感信息的最小公开 Issue，请维护者提供私下沟通渠道。

Useful reports include:

- the affected file and section;
- the unsafe behavior or authority bypass;
- a minimal, redacted reproduction;
- expected safe behavior;
- whether the issue affects the portable core or only one host integration.

有效报告应包含：受影响文件和章节、不安全行为或越权路径、最小且脱敏的复现、期望的安全行为，以及问题影响可移植核心还是仅影响某个宿主集成。
