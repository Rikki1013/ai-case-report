---
name: ai-case-report
description: "Generate structured Chinese AI practice case reports from rough user input. Use when the user wants to submit, polish, review, package, or draft an AI practice case; when they mention AI practice examples, Prompt/Skill cases, AI coding productivity, Agent workflows, AI business process improvement, AI tools/apps, or activity submission forms; or when the user needs guided questions to turn a real AI use case into a concise reusable report."
---

# AI Practice Case Report

Use this skill to help a user turn a real AI practice into a clear, truthful, high-density Chinese case report. Do not write advertising copy or generic tool introductions. Help the reader quickly understand what problem existed, what the user did with AI, what changed, what came out of it, and how others can reuse the method.

## Core Rules

- Prioritize truth. Do not invent tools, data, steps, results, materials, author information, or quotes.
- Do not invent metrics. If the user gives no numbers, describe concrete qualitative changes.
- Ask follow-up questions when information is insufficient. Ask at most 3 rounds, with at most 5 questions per round.
- Keep questions concrete and easy to answer. Do not ask the user to write a full essay.
- Use restrained language. Avoid exaggerated terms such as "颠覆", "革命性", "史无前例", "行业首创", "完美解决", unless the user provides strong support.
- Preserve real details: tool names, models, Prompt, Skill config, workflow nodes, file names, materials, outputs, failures, and constraints.
- Mark missing information as "暂未提供", "待补充", or "用户未说明".
- If the user includes obvious non-public company, customer, price, account, contract, or internal data, generalize it in the report. Do not create a standalone "脱敏说明" section.
- Do not output internal scoring, audit notes, editorial suggestions, or operation advice unless the user explicitly asks for internal evaluation.
- Include a "改造前后对比" table in every final report.
- Make effects perceptible. Replace vague claims like "效率提升" with concrete changes such as "从人工整理 Excel 变成实时仪表盘" or "从不可编辑图片变成可编辑 PPTX".
- Default to 1200-1800 Chinese characters unless the user requests a detailed version.
- Do not explain what common tools are. Only describe how the user used them in this case.
- Lead with the conclusion, then explain the process.
- Avoid repeating the same key information in multiple sections.

## Case Types

Classify each case with one main type and optional auxiliary types:

- AI Skill / Prompt 沉淀
- AI 编程与开发提效
- Agent / 自动化工作流搭建
- AI 改造业务 / 工作流程
- AI 小工具 / 小应用开发

If the practice is mostly low-code automation, data transfer, or process redesign rather than large-model AI, state that honestly as "自动化工作流实践" or "AI 辅助流程改造" instead of forcing it into an AI category.

## Intake Template

When the user first says they want to submit or create a case, ask them to fill this template:

```text
你好，我可以帮你把一个真实 AI 实践整理成结构化案例报告。
你不需要会写文章，只需要按下面模板简单填写即可。
如果信息不完整，我会继续追问。

请复制并填写：

【我解决的问题】
请说明你原来遇到了什么问题，为什么想用 AI 解决。

【使用场景】
例如：开发、运营、产品、销售、客服、内容生产、设计、学习、研究、个人效率、公司汇报等。

【使用工具】
例如：GPT、Claude、Gemini、Kimi、豆包、通义、智谱、Cursor、Codex、Claude Code、Copilot、Dify、FastGPT、扣子、Coze、飞书、Notion、多维表格、n8n、image2 等。

【具体流程】
我先……
然后……
最后……

【最终效果】
例如：节省了多少时间、减少了什么重复劳动、提升了什么质量、生成了什么产物。
如果没有具体数字，也可以写定性效果。

【可复用经验】
这个方法适合谁复用？别人照着做时最关键的步骤是什么？

【相关材料】
例如：Prompt、Skill 配置、工作流截图、项目地址、演示视频、GitHub 链接、前后对比图等。没有可以写“暂无”。

【作者信息】
你的姓名 / 昵称 / 岗位是什么？如果不想公开，可以写“匿名”或“暂不公开”。
```

## Completeness Check

After receiving the user's case details, silently classify the input:

Minimum viable case:

- Has a real usage scenario.
- Uses an AI tool, model, platform, Prompt, Skill, Agent, workflow, or AI method.
- Solves a specific problem.
- Includes a basic workflow.
- Includes a result, output, or feedback.

Grades:

- **A: 信息不足** - The user only says they used AI, or lacks concrete tool, workflow, result, or output. Do not generate a full report; ask follow-up questions.
- **B: 基本成案** - The user gives scenario, tool, workflow, and result/output, but lacks effect details, reusable method, failures, materials, or author info. Ask one follow-up round. If the user does not want to add more, generate from available information and mark gaps.
- **C: 信息完整** - The user gives clear pain point, concrete tools, workflow, final effects/outputs, reusable method, materials or author info. Generate the report. If web search is available, do a similar-case check first.

## Follow-Up Format

When asking follow-up questions, use this format:

```text
我已经了解了你的大致实践。为了把案例写得更完整，还需要补充几个信息：

1. ...
2. ...
3. ...

你可以简单回答，不需要写成长文。
```

Prioritize asking about:

- How the task was done before AI.
- The main pain point or approximate time cost.
- What changed after using AI.
- Which parts AI handled and which parts required human confirmation.
- The final output.
- Time saved, rework reduced, quality improved, or other concrete effects.
- Failed attempts, limitations, or pitfalls.
- Who can reuse the method.
- Public Prompt, screenshots, configuration, links, or before/after comparison.
- Author name, nickname, or role.

## Similar-Case Check

If web search is available, run one similar-case search before the final report. Generate keywords from tool names, task, scenario, output, Chinese terms, and English terms.

Do not claim originality, prove plagiarism, or make legal conclusions. Use cautious language only.

Output:

```markdown
## 相似案例检查

检查方式：
搜索关键词：
初步结论：
可能相似点：
建议强化的原创细节：
```

If search is unavailable or fails, say so plainly and suggest keywords the user can search themselves.

## Final Report Structure

When information is sufficient, generate the user-facing report in Chinese. Do not include internal ratings, editorial suggestions, audit notes, or a standalone privacy/desensitization section.

```markdown
# AI 实践案例报告

## 1. 案例标题

## 2. 一句话简介

## 3. 案例类型
主类型：
辅助类型：

## 4. 背景与痛点

## 5. 解决方案概览

## 6. 改造前后对比
| 环节 | 改造前 | 改造后 |
|---|---|---|
| ... | ... | ... |

## 7. 具体流程

## 8. 关键设计：Prompt / Skill / 工作流 / 方法

## 9. 最终效果

## 10. 可复用经验与注意事项

## 11. 相关材料

## 12. 作者信息

以上是根据你提供的信息整理出的案例报告。
提交前请确认：
- 内容是否真实准确；
- 是否可以补充截图、Prompt、工作流配置、项目链接或前后对比图；
- 是否允许用于活动投稿、展示和传播。

确认无误后，请复制以上报告内容提交到活动表单。
```

Section requirements:

- **Title**: State what was done, optionally include key tool names, avoid clickbait or inflated results.
- **One-sentence summary**: In 1-2 sentences, say the scenario, tools, problem, output, and result.
- **Background**: Describe the original problem directly; avoid generic industry background.
- **Solution overview**: Use 3-5 sentences; mention tools, key actions, final output, and the role of AI.
- **Comparison table**: Include at least 4 concrete rows. Do not use only "效率低/效率高".
- **Workflow**: Use numbered steps. Clarify what AI did and what the human checked.
- **Key design**: For Prompt/Skill cases, include role, input format, output format, standards, and constraints. For Agent/workflow cases, include nodes, input/output, triggers, and human review. For apps/tools, include core function, input/output, implementation idea, and editability/reusability. If unavailable, write "用户暂未提供完整 Prompt / 配置，可在后续补充。"
- **Final effect**: Use user-provided metrics if available; otherwise write concrete qualitative changes.
- **Reusable experience**: Include who can reuse it, key steps, known pitfalls, and "建议注意" for inferred risks.
- **Materials**: List Prompt, screenshots, links, project address, demos, config files. If none, write "暂无公开材料。"
- **Author**: Use the provided name/nickname/role. If missing, write "作者信息待补充。"
