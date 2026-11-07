# Deep Research Survey Skill

一个中文、可单独安装的深度调研工作流：先设可证伪假设，再精读原件，检验可比案例、反例和数据，最后形成有来源与边界的判断。证据卡可交给报告写作和 PPT 制作，沿用同一 ID。

## 安装

把本仓库克隆或下载到你的 Agent 可读取的 Skill 目录，并确保入口文件为 `SKILL.md`。不同客户端的目录和启用方式不同，以其官方 Skill 加载说明为准。本包没有运行脚本、密钥或专用客户端依赖。

```text
https://github.com/Nikki99999999/deep-research-survey-skill
```

支持从 URL 读取 Skill 的 Agent，也可直接给它这句安装指令：

```text
请读取 https://raw.githubusercontent.com/Nikki99999999/deep-research-survey-skill/main/SKILL.md ，并将其作为 deep-research-survey Skill 安装到当前环境支持的 Skill 目录；同时保留同仓库 references/ 下的两个文件。安装后列出实际路径和可读取性检查结果。不要替我创建任何凭据。
```

如果你的 Agent 不能自行安装，下载仓库后手动放入 Skill 目录即可。使用时可以说：“用 deep-research-survey 调研这个问题，保留证据卡和未解决的反证。”

## 运行所需能力

需要能检索资料、打开来源正文、记录可复查定位和写出报告。并行协作者、文档生成器及 PPT 工具是可选的；没有它们也能顺序执行。联网方式、资料访问和交付格式服从你当前环境的权限与要求。报告质量仍需要原件核查和实际独立审查。

## 文件

- [SKILL.md](SKILL.md)：完整工作流与交付要求。
- [references/evidence-handoff.md](references/evidence-handoff.md)：证据卡字段与写作、PPT 交接。
- [references/review-checklist.md](references/review-checklist.md)：交付检查。
- [ORIGINS.md](ORIGINS.md)：方法来源、重述方式与许可边界。
- [CHANGELOG.md](CHANGELOG.md)：本包版本记录。

## 来源与许可

本包参考 [grapeot/context-infrastructure](https://github.com/grapeot/context-infrastructure) 公开工作流所展示的研究顺序，由 Nikki99999999 维护，并以独立文字重述。未核实任何个人作者身份；本包没有收录上游原文。[MIT 许可证](LICENSE)仅覆盖本仓库原创文件，不声明上游文件的许可。详细说明见 [ORIGINS.md](ORIGINS.md)。
