# The Eight Levels of AI Adoption：取证速查

框架来自 Mike Taylor 和 Laura Entis 的 [The Eight Levels of AI Adoption](https://every.to/guides/the-eight-levels-of-ai-adoption)。下面是按可见行为编写的判定提示，不是对作者全文的复刻。[How to Get Better at AI by Asking AI](https://every.to/p/codex-graded-my-ai-habits-then-it-became-my-coach) 展示了如何用实际项目复盘采纳方式。

| 级别 | 主要证据 | 容易误判的情况 |
|---|---|---|
| 1 · Chatbot | 人提供问题和材料，AI 回复，人把答复用到外部工作 | 响应很长或用了推理模型，不因此升级 |
| 2 · Copilot | AI 在工作材料或工具中与人协同，人逐步主导修改 | 能编辑文件不等于能接手一项任务 |
| 3 · Agent | AI 接手多步骤任务；常规中间步骤需要人批准后才继续 | 一次给了详细指令不等于能独立完成 |
| 4 · Autopilot | 人发起单项任务，AI 在边界内做完，人在末端验收 | 完成一次不等于已有可复用流程 |
| 5 · Workflows | 同类任务复用明确的输入、步骤和质量关卡 | 保存一份 Skill 只能证明设计，不能证明实际采用 |
| 6 · Assistant | 时间或事件触发后，Agent 不等每次人工下达指令就开展工作 | 一次人发起的长任务自动续轮，不单独证明此级 |
| 7 · Multi-agent | 人直接管理多个独立长程 Agent，分发任务、跟踪或整合成果 | 轮询多模型的输出，不足以证明多个执行 Agent |
| 8 · Orchestrator | 主 Agent 在授权内调度执行者、跟踪进度并整理交付；人保留目标和关键批准 | 主席只总结人已收好的答案，或群里只有岗位名称，不足以证明此级 |

## 边界示例（合成）

- 人给三个 Agent 各自的任务，并自己跟踪和汇总：Level 7。群里即便有名为“总监”的 Bot，也不改变该样本。
- 人只交给主席一个议题；主席实际发给独立议员、安排互评并交付结论：该议题可判 Level 8。未见异常处理，不能宣称它已具备自动补跑或长期可靠性。若四个角色只是一次模型调用中的模拟，则不按多 Agent 编排计。
- 人批准项目目标和合并；总监 Agent 自己启动执行 Agent、核对结果、安排下一轮：该执行段可判 Level 8。没有看到无人发起的背景任务，不能据此断言该团队另有 Level 6 的主动触发能力。
- 配置页有定时任务，但没有启用状态或记录：记为设计具备 Level 6 特征、实际未证实，不拿更低等级填补未知。

其他 AI 采纳框架分别解释，不做数字对齐。若用户给了不同定义，先说明采用哪一套。
