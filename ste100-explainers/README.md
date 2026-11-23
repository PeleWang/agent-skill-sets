# ste100-explainers

[查看全部技能集](../README.md)

用 ASD-STE100 的写作原则解释论文、代码、概念或流程。两项技能都先准备英文讲解，再译成中文，保留原有的英文标题、术语和专有名称。区别在于你想怎么读：

| 我想要 | 用哪个技能 | 默认交付 |
| --- | --- | --- |
| 在聊天里直接读讲解 | [`ste100-text-explainer`](.agents/skills/ste100-text-explainer/SKILL.md) | 中文文字，不另建文件。 |
| 通过操作看参数、步骤或结果怎么变 | [`asd-web-explainer`](.agents/skills/asd-web-explainer/SKILL.md) | 一个可以离线打开的中文交互网页。 |

## 开始使用

第一次使用，请先按[仓库首页的说明](../README.md#在-codex-中使用)克隆仓库。用 Codex 桌面版打开 `ste100-explainers` 目录；如果用 CLI，在克隆得到的仓库根目录运行：

```sh
cd ste100-explainers
codex
```

提供要讲解的材料，再在消息输入框输入 `$` 选择文字版或网页版。例如：

> `$ste100-text-explainer` 解释这段代码为什么要先排序，再逐项比较。给一个小例子，直接在聊天里回答。

> `$asd-web-explainer` 用一个离线中文网页解释这篇论文的核心机制。让我能调整一个关键参数，观察结果怎么变；把教学模拟和论文的实验结果分开。
