# Agent Skill Sets

把自己做事的方法整理成可交给 AI 执行、可验收、可持续改进的流程。衡量效果看同类任务有多少能一次通过验收、要返工几次、人工核对要花多久，不看技能有多少，也不追求统一的 AI 应用层级。

每项技能在 `.agents/skills/` 下各有一个目录，其中包含 `SKILL.md` 和所需的资源。可以单独使用，不必安装整套。

## 技能目录

| 用途 | Skill | 什么时候用 |
| --- | --- | --- |
| 制作 | [`asd-web-explainer`](.agents/skills/asd-web-explainer/SKILL.md) | 学习或理解材料时，需要 ASD-STE100 英文底稿和中文交互式讲解。 |
| 制作 | [`nps-dashboard`](.agents/skills/nps-dashboard/SKILL.md) | 用 0–10 分的推荐意愿评分制作便于核对的 NPS 仪表板。 |
| 制作 | [`deck-production`](.agents/skills/deck-production/SKILL.md) | 根据听众、用途、依据和模板制作或更新 PPT。 |
| 制作 | [`taste-guided-writing`](.agents/skills/taste-guided-writing/SKILL.md) | 手头有满意的范文，需要写作或改稿，而不是归纳写作规则。 |
| 验收 | [`taste-to-rubric`](.agents/skills/taste-to-rubric/SKILL.md) | 想从正反面例子和反馈中归纳出以后还能用的验收标准。 |
| 验收 | [`independent-acceptance`](.agents/skills/independent-acceptance/SKILL.md) | 已经有成品，需要依据原始材料和验收标准判断能不能交付。 |
| 改进 | [`failure-diagnosis`](.agents/skills/failure-diagnosis/SKILL.md) | 任务失败或反复返工，需要找出原因并提出尽可能小的改动。 |
| 改进 | [`benchmark-case-curation`](.agents/skills/benchmark-case-curation/SKILL.md) | 要把获准使用的真实任务整理成可以反复测试的案例。 |
| 改进 | [`model-benchmark`](.agents/skills/model-benchmark/SKILL.md) | 已有固定案例和验收标准，需要比较模型或检验技能改动。 |
| 协作 | [`ai-adoption-diagnosis`](.agents/skills/ai-adoption-diagnosis/SKILL.md) | 想根据实际运行情况判断某类任务或 Agent 团队处在哪个 AI 应用层级。 |
| 协作 | [`ai-work-coaching`](.agents/skills/ai-work-coaching/SKILL.md) | 想减少反复干预，需要设计或回顾一项能检验效果的任务委派试验。 |

## 从一个任务开始

- **评估协作方式**：`$ai-adoption-diagnosis`：请根据我提供的两次运行记录，分别判断处在哪个层级。看谁分配任务、谁验收、谁处理异常，不要光凭角色名称判断。确定要改进哪一步后，再用 `$ai-work-coaching` 设计一项试验。
- **从失败中找到改进办法并验证效果**：用 `$failure-diagnosis` 查明一次失败的原因并查看最小改动建议，用 `$benchmark-case-curation` 保留原案例和未参与制定改动方案的案例，再用 `$model-benchmark` 在相同的模型设置下比较新旧指令。默认不保存或外传该次会话的出错记录。
- **让质量标准以后还能用**：用 `$taste-to-rubric` 从正反面例子中归纳要检查的事项；需要判断一份成果能否交付时，用 `$independent-acceptance` 依据原始证据验收。能用计算核对的事项交给脚本，授权和影响重大的判断仍由人负责。

## 安装与使用

在仓库根目录或其子目录中使用 Codex 时，Codex 会从 `.agents/skills/` 查找项目技能。用 `$ai-adoption-diagnosis` 之类的名称直接调用；如果列表没有更新，重新打开会话或重启 Codex。其他支持 Agent Skills 的客户端可以按各自的方法导入单个技能目录。

如果要在其他项目中使用某项技能，可以在仓库根目录运行下面的命令。这个示例只安装 AI 应用层级诊断技能，**不会覆盖已有的同名目录或链接**：

```sh
skill=ai-adoption-diagnosis
source_dir=".agents/skills/$skill"
target_dir="$HOME/.agents/skills"
if [ ! -f "$source_dir/SKILL.md" ]; then
  printf '未找到技能，请从仓库根目录运行：%s\n' "$source_dir" >&2
elif [ -e "$target_dir/$skill" ] || [ -L "$target_dir/$skill" ]; then
  printf '已有同名技能，未覆盖：%s\n' "$target_dir/$skill" >&2
else
  mkdir -p "$target_dir" && cp -R "$source_dir" "$target_dir/$skill"
fi
```

技能说明怎么做，不会自动读取会话、安装工具、安排定时任务、启动子 Agent、修改规则或更改工具权限。是否执行取决于用户在当前任务中授予的权限。

## 参考

- [The Eight Levels of AI Adoption](https://every.to/guides/the-eight-levels-of-ai-adoption) 与 [How to Get Better at AI by Asking AI](https://every.to/p/codex-graded-my-ai-habits-then-it-became-my-coach)：根据任务判断 AI 的使用方式，结合真实项目改进协作。
- [How to Create Your Own Personal AI Benchmark](https://every.to/also-true-for-humans/how-to-create-your-own-personal-ai-benchmark) 与 [Giving your AI a Job Interview](https://www.oneusefulthing.org/p/giving-your-ai-a-job-interview)：用真实任务建立不公开的基准测试，把个人偏好变成可以反复使用的检查项。
- [Agent Skills Specification](https://agentskills.io/specification) 与 [OpenAI Docs: Build skills](https://learn.chatgpt.com/docs/build-skills)：技能文件的格式和客户端查找本地技能的路径。
