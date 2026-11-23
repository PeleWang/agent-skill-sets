# Agent Skill Sets

这个仓库维护多套可以单独使用的 AI 技能。先选你要做的事，不用安装整个仓库的技能。

| 我想做什么 | 打开哪个技能集 | 从哪里开始 |
| --- | --- | --- |
| 把自己的工作方法和质量判断变成一套可以放心委派、独立验收、持续改进的 AI 工作系统 | [`ai-workflow-skills`](ai-workflow-skills/README.md) | 跟着项目周报的例子做一轮：定标准、委派、独立验收、改进。 |
| 把论文、代码或其他难懂的内容讲清楚 | [`ste100-explainers`](ste100-explainers/README.md) | 选一种交付方式：在聊天里读文字，或打开可以操作的离线网页。 |

## 在 Codex 中使用

已安装 Git 和 Codex 的话，先在终端克隆仓库：

```sh
git clone https://github.com/PeleWang/agent-skill-sets.git
cd agent-skill-sets
```

然后用 Codex 桌面版打开你选的子目录：`ai-workflow-skills` 或 `ste100-explainers`。如果用 CLI，先进入该子目录，再运行 `codex`。每套技能都放在自己目录下的 `.agents/skills/` 里；只打开仓库根目录，不会加载这两套技能。在消息输入框输入 `$`，选择要用的技能。

如果只想在自己的项目里用某一项，从对应技能集的 `.agents/skills/` 下把那项技能的完整目录复制到你的项目的 `.agents/skills/`。其他支持 Agent Skills 的客户端，可按各自的方式导入该目录。
