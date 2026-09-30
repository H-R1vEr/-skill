# 提示词工程教练（Codex Skill）

把任务需求问清楚，在 Codex 内部优化任务说明，然后直接完成任务。默认不把一段提示词交给用户，要求用户复制后再发一次。

## 能力

- 通过 Grill 访谈，一次问一个问题，找到用户尚未说出的成功标准、边界、例外和取舍。
- 面向科研技术、写作翻译、编程数据、日常工作与学习调整任务要求。
- 按确认的条件形成内部任务说明并直接执行；只有用户要求提示词文本时才展示。
- 从明确且稳定的反馈中学习个人偏好；个人偏好私有保存，共享版本改动需维护者审核。

## 安装

### 当前项目

保留 `.agents/skills/prompt-engineering-coach/` 在项目仓库根目录。项目根目录的 `AGENTS.md` 说明何时调用它。Codex 的技能说明支持项目级 `.agents/skills` 和全局用户级 Skill；详见 [Codex customization](https://developers.openai.com/codex/concepts/customization#skills)。

### 所有项目与对话

将技能文件夹复制到你的 Codex 个人 Skill 目录（通常为 `$CODEX_HOME/skills`；若未设置 `CODEX_HOME`，检查你当前 Codex 安装使用的默认目录）。把本仓库 `AGENTS.md` 中“提示词工程请求”一节合并到个人全局 `AGENTS.md`，不要覆盖你已有的个人规则。全局指引的目录说明见 [Codex customization](https://developers.openai.com/codex/concepts/customization#agents-guidance)。

如果技能列表尚未刷新，可开一个新对话或使用 `$prompt-engineering-coach` 显式调用。隐式触发由 Codex 决定；清楚的 Skill 描述和全局 AGENTS 指引能提高稳定性，但无法保证每个版本、每个对话都自动触发。

或克隆本仓库后直接复制技能文件夹：

```powershell
git clone https://github.com/H-R1vEr/-skill "$env:TEMP\pec"
Copy-Item "$env:TEMP\pec\.agents\skills\prompt-engineering-coach" "$env:USERPROFILE\.codex\skills\" -Recurse
```

## 自我进化

共享的 `SKILL.md` 不因某个人的一次反馈而自动改写。每位使用者的长期偏好单独保存在其 Codex 用户目录中的 `prompt-engineering-coach/preferences.md`，不把个人偏好或任务资料混进仓库。反复出现且对其他人也有帮助的改进，先作为提案交给维护者，审核后再进入共享版本。

不保存敏感信息、凭证、完整对话或私人任务内容。一次性纠正不自动变成长久偏好；无法判断是否长期适用时，先询问使用者。

## 文件

- `.agents/skills/prompt-engineering-coach/SKILL.md`：提示词教练工作流
- `.agents/skills/prompt-engineering-coach/agents/openai.yaml`：Codex 界面名称、简介与调用策略
- `.agents/skills/prompt-engineering-coach/references/domains.md`：各领域追问清单，按需读取
- `AGENTS.md`：在该仓库内自动调用技能的项目指引
- `LICENSE`：MIT

## 发布状态

公开仓库，MIT 许可。仓库地址：https://github.com/H-R1vEr/-skill
