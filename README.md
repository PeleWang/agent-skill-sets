# Agent Skill Sets

把个人工作方法变成可以委派、验收和持续改进的流程。衡量效果看同类任务的首次验收通过率、返工轮次和人工核对时间，不看 Skill 的数量或追求统一的 AI 采纳等级。

每项 Skill 是 `.agents/skills/` 下一个独立的目录，含 `SKILL.md` 和实际需要的资源。可以单独使用，不需要安装整套。仓库原有的 `asd-web-explainer` 已原样迁入这个目录，名称和用法不变。

## 技能目录

| 用途 | Skill | 什么时候用 |
| --- | --- | --- |
| 输出 | [`asd-web-explainer`](.agents/skills/asd-web-explainer/SKILL.md) | 学习或理解材料，需要 ASD-STE100 英文底稿及中文交互解释。 |
| 输出 | [`nps-dashboard`](.agents/skills/nps-dashboard/SKILL.md) | 用 0–10 推荐意愿数据制作可复核的 NPS 仪表板。 |
| 输出 | [`deck-production`](.agents/skills/deck-production/SKILL.md) | 根据听众、场景、证据和模板制作或更新 PPT。 |
| 输出 | [`taste-guided-writing`](.agents/skills/taste-guided-writing/SKILL.md) | 有认可的风格样例，需要写作或改稿，而不是提炼规则。 |
| 验收 | [`taste-to-rubric`](.agents/skills/taste-to-rubric/SKILL.md) | 想把正反例和反馈变成之后都能复用的验收标准。 |
| 验收 | [`independent-acceptance`](.agents/skills/independent-acceptance/SKILL.md) | 有成品，要按原始材料和验收规则判定能不能交付。 |
| 改进 | [`failure-diagnosis`](.agents/skills/failure-diagnosis/SKILL.md) | 有一次失败或反复返工，要找原因并拟定最小修改。 |
| 改进 | [`benchmark-case-curation`](.agents/skills/benchmark-case-curation/SKILL.md) | 要把获准使用的真实任务变成可复跑的评测案例。 |
| 改进 | [`model-benchmark`](.agents/skills/model-benchmark/SKILL.md) | 有固定案例和验收标准，要比较模型或验证 Skill 改动。 |
| 协作 | [`ai-adoption-diagnosis`](.agents/skills/ai-adoption-diagnosis/SKILL.md) | 想按运行证据判断某类任务或 Agent 团队的实际采纳层级。 |
| 协作 | [`ai-work-coaching`](.agents/skills/ai-work-coaching/SKILL.md) | 想减少重复干预，需要设计或复盘下一项可验证的委派实验。 |

## 从一个任务开始

- **评估协作方式**：`$ai-adoption-diagnosis`：根据我提供的两次运行记录，分别判定层级。区分谁派工、谁验收、谁处理异常，不从角色名称推断。要改进哪一步，再用 `$ai-work-coaching` 设计一项实验。
- **把失败变成可验证的改进**：用 `$failure-diagnosis` 查一次失败并预览最小修改，用 `$benchmark-case-curation` 保留原案例和未用于拟定修改的案例，再用 `$model-benchmark` 在同一模型设置下比较新旧指令。同一会话的出错记录不默认保存或外传。
- **让质量标准可复用**：用 `$taste-to-rubric` 从正反例提炼检查项；需要判断一份产物能否交付时，用 `$independent-acceptance` 按原始证据验收。脚本负责可计算检查，授权和高影响判断仍由人负责。

## 使用与迁移

在仓库根目录或其子目录中使用 Codex，项目技能从 `.agents/skills/` 发现。用 `$ai-adoption-diagnosis` 之类的名称显式调用；如果列表没刷新，重开会话或重启 Codex。其他支持 Agent Skills 的客户端可以按各自的方式导入单个目录。

如果要在其他项目中使用某项 Skill，可在仓库根目录运行下面的命令。示例只安装层级诊断，**不会覆盖现有同名目录或链接**：

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

原来的仓库根 `SKILL.md` 现在位于 [`.agents/skills/asd-web-explainer/SKILL.md`](.agents/skills/asd-web-explainer/SKILL.md)，界面配置也随目录迁移。如果原先直接引用根文件或将仓库根当作安装源，请改为技能子目录。已安装的独立副本可以继续使用；如果客户端出现两个同名入口，检查路径并保留你想用的版本。

Skill 说明怎么做，不自动读取会话、安装工具、安排定时任务、启动子 Agent、修改规则或改变工具权限。是否执行由当前任务授权决定。

## 参考

- [The Eight Levels of AI Adoption](https://every.to/guides/the-eight-levels-of-ai-adoption) 与 [How to Get Better at AI by Asking AI](https://every.to/p/codex-graded-my-ai-habits-then-it-became-my-coach)：按任务判断采纳方式，用真实项目改进协作。
- [How to Create Your Own Personal AI Benchmark](https://every.to/also-true-for-humans/how-to-create-your-own-personal-ai-benchmark) 与 [Giving your AI a Job Interview](https://www.oneusefulthing.org/p/giving-your-ai-a-job-interview)：从真实任务制作私有基准，把偏好转成可重复的检查。
- [Agent Skills Specification](https://agentskills.io/specification) 与 [OpenAI Docs: Build skills](https://learn.chatgpt.com/docs/build-skills)：技能文件格式与本地发现路径。
