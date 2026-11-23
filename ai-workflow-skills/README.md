# ai-workflow-skills

[查看全部技能集](../README.md)

把自己的工作方法和质量判断，变成一套可以放心委派、独立验收、持续改进的 AI 工作系统。先选一项你经常做、有资料可以核对、做错了也容易纠正的工作。**先说清怎么做、怎样算做好，再交给 AI 执行，换一个会话验收。** 不用安装全部技能，也不用先评估 AI 应用层级。

## 先做完一轮：写一份项目周报

准备本周的项目记录、一份你满意的旧周报，以及你喜欢它的理由。有退回过的稿子或修改意见，也可以带上。第一次用这些技能，先看[安装与使用](#安装与使用)。手边没有材料，就用下面的虚构示例练习。

<details>
<summary>展开示例材料</summary>

- **本周项目记录**：周二，导出功能通过测试。周四，供应商接口仍未联通，下周的联调可能推迟。下一步是排查接口问题，负责人还未确定。
- **满意的旧周报**：进展：权限页面已完成验收。风险：试用合同还没签，试用可能推迟。下一步：由产品经理跟进合同签署。
- **平时的做法和反馈**：我只写进展、风险和下一步。进展要能核对，风险要写清影响。上次退回稿件，是因为它把没定下来的人写成了负责人。遇到这种情况应该写「负责人待确认」。

想练习验收不通过的情况，可以把演练稿里的「负责人待确认」改成「由小周负责」，再按第 3、4 步检查并找出问题。项目记录没有指定小周，这一项不应通过验收。

</details>

1. **定标准：把你说的「写得好」变成能检查的要求。** 让 `$taste-to-rubric` 根据旧周报和反馈列出验收标准，由你确认哪些必须做到，哪些只是偏好。比如「每条进展都能在项目记录里找到依据」，比「周报要靠谱」更容易核对。已有验收标准就直接用。

   > `$taste-to-rubric` 根据旧周报和我的反馈，列出这类周报的验收标准。每条都写清要查什么、怎样算通过。需要我确认的地方单独列出。

2. **委派：把材料、做法和标准一起交给 AI。** 把本周记录、旧周报、你平时的做法和确认过的验收标准交给 `$taste-guided-writing`。说明缺资料时怎么办，以及哪些事不能替你做。

   > `$taste-guided-writing` 根据本周记录和已确认的标准写一份周报。先列进展，再写风险和下一步；没有证据的地方标为待确认。参考旧周报的写法，不照搬以前的事实。只交草稿，不发送。

3. **独立验收：换一个没参与制作的会话。** 把本周原始记录、验收标准和周报草稿带到新会话，用 `$independent-acceptance` 逐项检查。让验收依据原始材料，而不是制作会话的自评。是否发送周报，由你决定。

   > `$independent-acceptance` 用原始记录和验收标准核对这份周报。逐项说明是否通过、依据是什么；没证据就标明证据不足。只给验收结论，不改稿、不发送。

4. **改进：找出返工的原因，下次用同一套标准再试。** 没通过时，把原始任务说明和材料、初稿及验收意见交给 `$failure-diagnosis`，先判断是材料不够、要求没说清，还是执行时没有遵守要求。确认改动后，用原案例重试，再用一个没用来制定改动方案的同类任务检查效果。通过了就先保留做法，不必为了改进而改动。

   > `$failure-diagnosis` 根据原始任务说明、材料、初稿和验收意见找出返工原因。建议只改一个地方，并说明怎么判断改动有没有用。先给建议，不直接修改技能。

把**确认过的任务说明和验收标准**留在你自己的工作目录，下次换上新材料就能再用。每轮记录是否一次通过验收、返工几次，或人工核对花了多久。先选一项来比较；省下时间不能以降低验收标准为代价。技能不会替你在会话之间传材料，也不用把自己的工作资料提交到这个公开仓库。

## 安装与使用

**先在本技能集目录里试用，不必另行安装技能。** 第一次使用，请先按[仓库首页的说明](../README.md#在-codex-中使用)克隆仓库。用 Codex 桌面版打开 `ai-workflow-skills` 目录；如果用 CLI，在克隆得到的仓库根目录运行：

```sh
cd ai-workflow-skills
codex
```

在消息输入框输入 `$`，选中第一步的 `taste-to-rubric`，再输入上面的要求。看不到技能时，先确认打开的是 `ai-workflow-skills`，而不是仓库根目录，再重新打开会话。

**要在自己的项目里用**，把需要的技能目录连同 `SKILL.md` 和其他文件一起复制到该项目的 `.agents/skills/`。如果希望在多个项目里都能调用，可从 `ai-workflow-skills` 目录运行下面的命令，把单项技能复制到个人技能目录。示例安装 `taste-to-rubric`，**不会覆盖已有的同名目录或链接**。需要其他技能时，替换第一行的技能名。

```sh
skill=taste-to-rubric
source_dir=".agents/skills/$skill"
target_dir="$HOME/.agents/skills"
if [ ! -f "$source_dir/SKILL.md" ]; then
  printf '未找到技能，请从 ai-workflow-skills 目录运行：%s\n' "$source_dir" >&2
elif [ -e "$target_dir/$skill" ] || [ -L "$target_dir/$skill" ]; then
  printf '已有同名技能，未覆盖：%s\n' "$target_dir/$skill" >&2
else
  mkdir -p "$target_dir" && cp -R "$source_dir" "$target_dir/$skill"
fi
```

其他支持 Agent Skills 的客户端可按各自的方式导入技能目录。技能只说明怎么做，不会自行读取历史会话、安排定时任务、修改规则或扩大工具权限。

## 技能目录

| 用途 | 技能 | 什么时候用 |
| --- | --- | --- |
| 定标准 | [`taste-to-rubric`](.agents/skills/taste-to-rubric/SKILL.md) | 从满意和不满意的例子里，整理出以后还能用的验收标准。 |
| 制作 | [`taste-guided-writing`](.agents/skills/taste-guided-writing/SKILL.md) | 参考满意的范文和反馈，写文章、邮件或简报。 |
| 制作 | [`deck-production`](.agents/skills/deck-production/SKILL.md) | 根据给谁看、为什么讲，使用手头的资料和模板制作或更新 PPT。 |
| 制作 | [`nps-dashboard`](.agents/skills/nps-dashboard/SKILL.md) | 根据 0–10 分的推荐意愿评分制作 NPS 仪表板，并核对计算结果。 |
| 验收 | [`independent-acceptance`](.agents/skills/independent-acceptance/SKILL.md) | 有了成品，用原始材料和验收标准判断能否交付。 |
| 改进 | [`failure-diagnosis`](.agents/skills/failure-diagnosis/SKILL.md) | 任务失败或反复返工，需要找原因，明确该改哪一步。 |
| 改进 | [`benchmark-case-curation`](.agents/skills/benchmark-case-curation/SKILL.md) | 把获准使用的真实任务整理成可以反复测试的案例。 |
| 改进 | [`model-benchmark`](.agents/skills/model-benchmark/SKILL.md) | 用同一组案例和验收标准比较模型，或检验技能改动。 |
| 协作 | [`ai-work-coaching`](.agents/skills/ai-work-coaching/SKILL.md) | 用真实案例找出人工干预最多的环节，试一种新做法并比较结果。 |
| 协作 | [`ai-adoption-diagnosis`](.agents/skills/ai-adoption-diagnosis/SKILL.md) | 有了实际运行记录，想判断某类任务或 Agent 团队处在哪个 AI 应用层级。 |

## 做过几轮之后

- **每次做同类任务都得盯着 AI**：用 `$ai-work-coaching` 找出最耗时或最容易出错的一步，只改一项做法，再比较新旧结果。
- **想知道换模型或改技能有没有用**：用 `$benchmark-case-curation` 整理案例，另留一些没用来制定改动方案的案例；再用 `$model-benchmark` 按同一套标准比较结果。
- **想弄清现在谁在分配任务、处理异常和验收**：用 `$ai-adoption-diagnosis` 根据运行记录判断。定级可以帮助你看清协作方式，但不必为了升一级而增加权限或自动化。

## 参考

- [The Eight Levels of AI Adoption](https://every.to/guides/the-eight-levels-of-ai-adoption) 与 [How to Get Better at AI by Asking AI](https://every.to/p/codex-graded-my-ai-habits-then-it-became-my-coach)：根据任务判断 AI 的使用方式，结合真实项目改进协作。
- [How to Create Your Own Personal AI Benchmark](https://every.to/also-true-for-humans/how-to-create-your-own-personal-ai-benchmark) 与 [Giving your AI a Job Interview](https://www.oneusefulthing.org/p/giving-your-ai-a-job-interview)：用真实任务建立不公开的基准测试，把个人偏好变成可以反复使用的检查项。
- [Agent Skills Specification](https://agentskills.io/specification) 与 [OpenAI Docs: Build skills](https://learn.chatgpt.com/docs/build-skills)：技能文件的格式和客户端查找本地技能的路径。
