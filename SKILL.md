---
name: dr-tang-advisor-review
description: |
  Use when the user wants to review a draft, message, paper section, email, or progress update
  before sending it to their advisor or mentor.
  Use when the user wants to extract advisor preferences from meeting transcripts or chat history.
  Use when the user wants to know if something is ready to send to their advisor.
  Use when the user wants to rewrite a draft to match their advisor's standards.

  Trigger phrases (English): "review this draft against my advisor's priorities", "extract my
  advisor's preferences from these transcripts", "is this ready to send to my advisor?",
  "do a final pre-send check on this", "what would my advisor push back on",
  "pre-send check", "advisor review", "ready to send to advisor"

  触发场景（中文）：根据聊天记录提炼导师偏好、按导师标准审稿、判断内容是否可以发给导师、
  发给老师前做最终检查、按唐老师的标准看这段话、这段话能发给导师吗、帮我做发给导师前的检查、
  从录音记录里总结导师的偏好、导师审稿、导师预审、发给老师之前检查一下
---

# Dr.Tang Advisor Review Skill

这个 skill 只做一件事：在你把东西发给导师之前，帮你找出她大概率会批的地方。

---

## 模式自动选择

根据你提供的材料自动判断，不需要手动指定：

| 你提供的 | 执行模式 |
|---|---|
| 只有聊天记录 / 录音转写 | **模式 A：提炼导师偏好** |
| 聊天记录 + 草稿 | **模式 A → 模式 B（自动串联）** |
| 只有草稿 | **模式 B（直接用已知唐老师偏好审稿）** |
| 草稿 + 说"帮我快速检查" | **模式 C：临门一脚检查** |

**没有提供聊天记录时：直接使用本文件末尾的"已知唐老师偏好"作为审稿依据，无需说明。**

---

## 模式 A：提炼导师偏好

**触发条件：** 用户提供了聊天记录、录音转写或会议笔记。

**执行步骤：**

1. 通读所有材料
2. 只提炼在多次对话中重复出现的模式——单次评论不算规律
3. 区分稳定偏好（跨多个场景出现）和情境偏好（特定文章类型 / 特定时间压力）
4. 按下面结构输出

**输出格式：**

```
## 导师偏好画像

### 高频必达标准（出现 3 次以上）
- [规律] — [支撑证据简述]

### 常见被批触发点
- [什么情况下导师会要求修改]

### 措辞和语气偏好
- [导师对语言表达的稳定要求]

### 结构和逻辑偏好
- [段落结构、论证方式的稳定要求]

### 置信度
- 高置信度（3 次以上）：[列举]
- 中置信度（2 次）：[列举]
- 低置信度（1 次或语境模糊）：[列举]

### 不确定说明
- [证据薄弱 / 矛盾 / 情境化的地方]
```

---

## 模式 B：草稿预审

**触发条件：** 用户有草稿需要审。

**执行步骤：**

1. 如果用户提供了聊天记录，先执行模式 A，再用提炼出的偏好来审
2. 如果用户没有提供聊天记录，直接使用本文件末尾"已知唐老师偏好"审稿
3. 逐段检查草稿，对照以下**核心审稿检查清单**
4. 按下面格式输出——**先给结论，再给细节**

**核心审稿检查清单（每段都要过）：**

- [ ] 这段有没有一句核心论点？（还是只有事实罗列）
- [ ] 段与段之间有没有被跳跃？读者能不能跟上逻辑链条？
- [ ] 有没有无 citation 支撑的强 claim？（"所有…都…""没有人做过…"）
- [ ] 有没有把不同的问题混为一谈？（比如 availability ≠ degradation）
- [ ] 批评他人 / 自身局限时，措辞是否过强？（"has a deficit" → "has room for improvement"）
- [ ] Introduction 第一段结尾有没有 urgency？（不是描述困难，是说明这个 gap 为什么现在必须解决）
- [ ] Related work 里每篇引用是否用了自己的语言解释清楚了？（不是复制对方术语）
- [ ] Related work 里每篇引用有没有说清楚与自己工作的关系？
- [ ] 如果是 reviewer response：每条都回应了吗？感谢语是否只在末尾出现一次？

**输出格式（结论优先）：**

```
## 审稿结论

🔴 现在不能发 / 🟡 改完这几项再发 / 🟢 可以发

[一句话理由]

---

## 必须改（不改就别发）

- [ ] [具体问题 + 位置 + 为什么唐老师会批 + 改法建议]

---

## 建议改（改了更好，不改还能发）

- [ ] [具体问题 + 改法建议]

---

## 可以不改

- [低优先级问题，仅供参考]

---

## 重写建议

（只为必须改的项目提供）

**[问题位置]**
- 原文：[原句]
- 建议：[改写后的句子]
- 依据：[引用了哪条唐老师偏好]

---

## 审稿依据

[说明这次审稿用的是什么依据：用户提供的聊天记录 / 已知唐老师偏好 / 两者结合]
```

---

## 模式 C：临门一脚检查

**触发条件：** 用户说稿子基本改完了，只想知道现在能不能发。

**执行步骤：**

1. 只看最高风险的问题
2. 给明确的 go / no-go
3. 如果有 blocking issue，给最小改动建议

**输出格式：**

```
## 能不能发

🔴 不能发 / 🟡 改完下面这几项就能发 / 🟢 可以发

---

## Blocking Issues（有的话）

- [只列会让导师当场提出修改要求的问题]

## 最小改动建议

- [最少改动让这段话过关]
```

---

## 审稿时的基本规则

1. **只报真风险，不刷存在感。** 不要为了显示有在工作就列出很多小问题。只有真正会被批的才进"必须改"。

2. **区分唐老师稳定偏好和泛泛的写作建议。** 如果一个问题是一般写作惯例而不是唐老师的已知偏好，放在"建议改"里，不要放"必须改"。

3. **单次评论不是规律。** 在用户提供的聊天记录中，只有重复出现的模式才算导师偏好。

4. **没有 citation 来源的偏好要标注。** 如果对一个问题的判断是"猜测导师会在意"而非"已知她在意"，要说清楚。

5. **结论先，分析后。** 用户需要先知道能不能发，再看为什么。

---

## 已知唐老师偏好（Known Patterns）

基于 40+ 次会议录音，每条均出现在多次不同场合。没有提供聊天记录时，直接用这部分审稿。完整解析见 `references/advisor-patterns-distilled.md`。

---

### 【逻辑与结构】

**P1 — 每段一个核心论点。** 能用一句话说清楚这段的中心主张，不能只是事实罗列。
> "你没把一句忠心思想递给我"

**P2 — 段间逻辑不能断。** 从上段末句到下段首句，读者不需要自己猜中间步骤。
> "这个跳跃太怪了"

**P3 — 事实 ≠ 问题。** 说明某件事发生了，还不够——必须解释为什么这是需要解决的问题。
> "Something happening, that's not a problem, that's a fact."

**P4 — Introduction 第一段以 urgency 收尾。** 末句不是描述困难，而是说明这个 gap 为什么现在必须解决。
> "你第一段的结尾就应该说 practical deployment 才是我们 urgent need"

**P5 — Related work 不说问题，只说别人做了什么。** 问题在 introduction 里说，related work 里只说前人工作及其与自己的关系。
> "问题已经在 introduction 就说了，你没必要去阐述问题"

**P6 — Related work 每篇用自己的话解释。** 不能复制对方的术语，要用没读过那篇文章的人也能看懂的语言。
> "用你的理解以后的语言去描述，给任何没有背景的人来看"

---

### 【精确性与 claim 范围】

**L1 — 泛化 claim 必须有 citation 或缩小范围。** "所有传感器…""没有人…"——任何反例就能打掉，必须加引用或改成 "many" / "most existing"。
> "全世界所有的三色都被你打了一枪"

**L2 — 领域现状的强陈述不能靠自己说。** 必须有文献支撑。
> "这句话多么 strong，你不能自己说出来"

**L3 — 不同性质的问题不能混在一段里。** 典型：availability（信号中断）≠ degradation（信号存在但质量差），原因和解法都不同。

**L4 — 易错术语清单：**
- "missing modality" → 指模态完全缺失，不用于质量差
- "transform" vs "augment" → 本质不同，不可混用
- "impractical" → 太强，改 "challenging in real-world deployment"
- "unavailability" → 要说清是哪种原因（信号断 / 太贵 / 传感器坏）

**L5 — 因果链逐步写，不让读者脑补。** "采集贵" ≠ "质量差"——每步因果都要明确。

---

### 【措辞与语气】

**T1 — 批评他人：diplomatic 且精准。** 说 "room for improvement"，不说 "has a deficit"；但 diplomatic 不等于范围含糊。
> "你真不行"和"还有 improvement space"说的是同一件事，语气截然不同

**T2 — 自身局限：用 limitation，不用 failure。** 表述为情境性约束（"在某条件下受限"），不说"我们的方法有问题"。

**T3 — 重心比对错更重要。** 句子可以都不错，但重心放错，照样被批。
> "没有 delivered 错，你的重心 delivered 错"

---

### 【Reviewer Response 专属】

**R1 — 每条都必须正面回应，包括你不同意的。**

**R2 — 感谢语只在每个 reviewer 末尾出现一次。** 不要在每条 response 前面都说谢谢。

**R3 — 不同意就直说，给出理由。** 含糊回避比直接说"我们不同意，因为…"更差。

**R4 — 只改被要求的内容。** 主动添加其他改动可能引入新问题。

---

### 【发稿前】

**S1 — 发之前通读一遍，检查前后一致性。** 读两遍可能不够。

**S2 — 同类错误不能重复出现。** 被指出过的问题，下次发稿前要主动扫全文。

---
