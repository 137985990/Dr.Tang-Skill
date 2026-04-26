# Dr.Tang Advisor Review Skill — 使用手册

这是我自己用来在发给唐老师之前预审内容的私有 skill。

核心功能：对照唐老师真实的审稿偏好（从录音和聊天记录中提炼），帮我在发之前找出会被批的地方。

---

## 30 秒上手

| 情况 | 怎么做 |
|---|---|
| 有新录音 / 聊天记录 | 粘进来，说"帮我提炼唐老师的偏好" → 场景 A |
| 有草稿，想全面审 | 粘草稿，说"按唐老师标准审一下" → 场景 B |
| 快发了，只想确认没问题 | 粘草稿，说"帮我做最终检查" → 场景 C |

---

## 如何安装这个 Skill

下面按 **Claude Code** 的常见使用方式来写。

### 方式 1：安装到全局（推荐）

适合：你希望这个 skill 在所有项目里都能用。

```bash
npx skills add 137985990/Dr.Tang-Skill -g -y
```

安装后，这个 skill 通常会出现在你的全局 skills 目录里（例如 `~/.claude/skills/`）。

### 方式 2：安装到当前项目

适合：你只想在当前项目里使用它。

在项目根目录执行：

```bash
npx skills add 137985990/Dr.Tang-Skill -y
```

这样通常会把 skill 安装到当前项目的 `.claude/skills/` 目录。

### 方式 3：手动安装（最稳妥的兜底方式）

如果 CLI 安装后 Claude 识别不到，可以手动把这个仓库里的 `SKILL.md` 放到 Claude Code 会扫描的目录里。

**全局安装目录示例：**

- macOS / Linux: `~/.claude/skills/dr-tang-advisor-review/SKILL.md`
- Windows: `%USERPROFILE%\.claude\skills\dr-tang-advisor-review\SKILL.md`

**项目内安装目录示例：**

- `[你的项目目录]/.claude/skills/dr-tang-advisor-review/SKILL.md`

如果你手动安装，建议把本仓库里的这些文件一起保留，方便 skill 参考：

- `SKILL.md`
- `templates/`
- `examples/`
- `references/`

### 安装后怎么确认成功

你可以用下面几种方式确认：

1. 运行：

```bash
npx skills list -g
```

如果是项目内安装，也可以先试：

```bash
npx skills list
```

2. 在 Claude Code 里直接问：

```text
What skills are available?
```

看是否能看到 `dr-tang-advisor-review`。

3. 直接显式触发：

```text
/dr-tang-advisor-review
```

如果 slash command 能触发，说明 skill 已经被 Claude Code 识别到了。

### 如果装完后 Claude 还是不用这个 skill

按这个顺序检查：

1. 先确认 skill 是否真的装到了 Claude Code 会扫描的目录里
2. 如果刚创建了新的 `.claude/skills/` 目录，重启 Claude Code 一次
3. 试着直接用：

```text
/dr-tang-advisor-review
```

4. 再用更贴近触发词的自然语言，比如：

- `按唐老师的标准审一下这段话`
- `帮我做发给导师前的最终检查`
- `根据这些聊天记录提炼导师偏好`

---

## 最快的用法（不到 2 分钟）

把你要发的内容直接粘贴进来，说：

> "帮我按唐老师的标准检查一下这段话能不能发"

skill 会用已内置的唐老师偏好库直接审，给你：

- **能不能发**（🔴/🟡/🟢）
- **必须改的问题**（带具体改法）
- **建议改的问题**

---

## 三种使用场景

### 场景 A：我有新的聊天记录 / 录音，想更新导师偏好画像

```
提供材料，说：根据这些新聊天记录，帮我更新唐老师的偏好画像
```

会输出：新提炼的偏好 + 置信度标注

保存结果到 `references/advisor-patterns-distilled.md` 供后续复用。

---

### 场景 B：我有草稿，想做完整预审

```
提供草稿（+ 可选：最近的聊天记录），说：按唐老师标准审一下这段话
```

会输出：
1. 审稿结论（能不能发）
2. 必须改的问题（每条带依据）
3. 建议改的问题
4. 重写建议

---

### 场景 C：稿子基本改完了，只想做最后检查

```
提供草稿，说：帮我做一次发给唐老师前的最终检查
```

只输出 blocking issues。没有就说没有，不展开。

---

## 如果我时间很少

直接用场景 C。把内容粘进来，说"最终检查"，拿到结论后只改必须改的那几条。

---

## 如何更新导师偏好画像

每次有新录音或聊天记录时：

1. 把新材料粘进来，触发场景 A
2. 对比 `references/advisor-patterns-distilled.md` 里的现有规律
3. 如果有新规律，手动更新那个文件（或让 skill 帮你写增量更新）

模板在：`templates/advisor-profile-update-template.md`

---

## 哪种内容最适合用这个 skill

最有价值的使用场景：

| 内容类型 | 典型问题 | 效果 |
|---|---|---|
| Paper introduction | 段落没有中心思想、urgency 缺失 | ★★★ |
| Related work | 用了别人的术语没解释、和自己工作关系不明 | ★★★ |
| Reviewer response | 漏回某条评论、谢谢语用多了 | ★★★ |
| 进展汇报邮件 | 逻辑跳跃、问题没说清 | ★★ |
| 方法描述段落 | claim 范围过大、因果链不清 | ★★ |

---

## 仓库结构

```
Dr.Tang-Skill/
├── SKILL.md                               ← skill 主体（包含唐老师已知偏好 P1–S2）
├── README.md                              ← 这个文件
├── references/
│   ├── advisor-patterns-distilled.md      ← 高频偏好结构化存档（可持续更新）
│   ├── revision-heuristics.md             ← 改稿快速判断 checklist
│   └── design-notes.md                   ← 设计决策说明
├── templates/
│   ├── advisor-priority-profile-template.md  ← 场景 A 输出格式
│   ├── draft-review-template.md              ← 场景 B 输出格式
│   ├── final-send-check-template.md          ← 场景 C 输出格式
│   └── advisor-profile-update-template.md    ← 有新录音时增量更新画像用
├── examples/
│   ├── demo-conversation.md               ← 完整流程示例（场景 A→B→C）
│   ├── sample-final-send-check.md         ← 场景 C 独立示例
│   ├── example-reviewer-response.md       ← Reviewer response 场景
│   ├── example-before-after.md            ← 改稿前后对比
│   ├── example-edge-cases.md              ← 边缘情况：差一点 / 证据不足
│   ├── sample-transcript-input.md         ← 录音转写输入格式参考
│   ├── sample-chat-history-input.md       ← 聊天记录输入格式参考
│   ├── sample-draft-input.md              ← 草稿输入格式参考
│   └── sample-review-output.md            ← 早期版本完整输出参考
└── record/                                ← 本地原始录音文本（私有，不提交）
```

---

## 内置偏好库说明

`SKILL.md` 末尾的"已知唐老师偏好"基于 40+ 次会议录音和聊天记录，按主题分为：

- 逻辑与结构（P1–P6）
- 精确性与 claim 范围（L1–L5）
- 措辞与语气（T1–T3）
- Reviewer Response 专属（R1–R4）
- 发稿前自我审查（S1–S2）

这部分不依赖 `record/` 目录，删掉原始录音后仍然有效。
