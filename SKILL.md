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
- [ ] 有没有把下一段才展开的对比或否定抢先写进这一段？（比如读者还不知道第二个 challenge，就先写 `not about ...`）
- [ ] Related work 的每个 subsection 有没有清楚交代：它为什么在这里、和前后小节的关系是什么、和本文方法的关系是什么？
- [ ] Related work 是不是按“类别/机制/表示层次”综合出来的，而不是按论文一篇一篇流水账地写？
- [ ] 如果把多篇文章归为一类，是否既讲清了它们的共同 procedure，也讲清了代表方法之间真正不同的地方？
- [ ] 有没有无 citation 支撑的强 claim？（"所有…都…""没有人做过…"）
- [ ] 有没有把不同的问题混为一谈？（比如 availability ≠ degradation）
- [ ] 核心术语是不是沿用了领域已有的标准定义？如果 `source` / `target` / `missing` 这类词是相对性的，是否已经说清比较基准？
- [ ] 对最接近的 prior work，是否明确写出了它为什么不能直接用于本文任务？如果只是 application 不同，是否已经说明这还不够？
- [ ] 例子或术语会不会把读者注意力带偏？如果这个例子需要背景知识，是否已经解释了它为什么 relevant？
- [ ] 批评他人 / 自身局限时，措辞是否过强？（"has a deficit" → "has room for improvement"）
- [ ] 有没有用了不必要的生僻词或半定义术语？（比如 `closed set` 这种如果不是必要术语，就换成更普通的英文）
- [ ] 缩写、protocol label 或内部术语是不是在第一次出现时就讲清楚了？如果 `CSDI`、`window-level protocol`、`complete-channel setting` 不是读者公认会懂的词，就先写全称或改成白话。
- [ ] Methodology 读起来是不是像 project report：`I did this, then I did that`？如果是，是否先把 why / reasoning 讲清楚，再讲 how？
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

**P7 — 不要把下一段的对比抢先写进这一段。** 当前段先把当前问题讲清楚；像 `not about ...` 这种句子，如果读者还没被引到下一层问题，通常应该后移到下一段开头。
> "not about 那句话放在这里不妥了... 放在下一段的起点反而更好"

**P8 — Related work 的小节安排要有 guideline。** A、B、C 不是并列堆料；每个 subsection 都要让读者看得出它为什么在这里、和前后小节怎么接、和本文方法有什么关系。
> "你从A到B到C总有一个guideline... 到C你总没有找出为什么"

**P10 — Related work 优先按类别综合，不按论文流水账展开。** 先说这一类工作在做什么、解决到哪一层（raw signal / feature / transfer setting），再用一两篇代表论文举例；如果这些文章共享一个 common procedure，就把共性说清，再点出代表方法之间真正不同的地方。不要变成 `paper A did this, paper B did that` 的堆砌。
> "你能不能找到规律... 主要是干什么，然后这样的方法可以参见..."

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

**L6 — 例子和术语不能把读者注意力带偏。** 如果两个模态或两个概念之间的关系不是常识，就先解释为什么 relevant；否则读者会误以为你在讨论另一类问题。
> "你在这里反复强调 PPG 到 ECG 反而让人眼球落到那边... 会让人产生一些无必要的思考"

**L7 — 核心术语优先沿用领域标准定义；相对性词要说清比较基准。** 如果 survey 已经定义了 `source` / `target` / heterogeneous transfer，就不要自己重新发明一套更模糊的说法。像 `missing` 这种词，也要说清楚是相对谁 missing；对它自己的 setup 来说如果是完整的，就不要轻易叫 missing。
> "你都已经找到了一本 survey paper... 它里面一定把 source 和 target 定义了"

**L8 — 对最接近的 prior work，必须明确写出 why not direct apply。** 只说 application 不同不够；要把它依赖的监督、共享变量、模态假设或任务前提写清楚，否则读者会默认“别人已经做过了”。
> "你一定要在这个B里面强调一下我跟他的不同... 他们不能 direct apply on the task"

---

### 【措辞与语气】

**T1 — 批评他人：diplomatic 且精准。** 说 "room for improvement"，不说 "has a deficit"；但 diplomatic 不等于范围含糊。
> "你真不行"和"还有 improvement space"说的是同一件事，语气截然不同

**T2 — 自身局限：用 limitation，不用 failure。** 表述为情境性约束（"在某条件下受限"），不说"我们的方法有问题"。

**T3 — 重心比对错更重要。** 句子可以都不错，但重心放错，照样被批。
> "没有 delivered 错，你的重心 delivered 错"

**T4 — 英文优先用常用词。** 不是必要术语的词不要故作高级；像 `closed set` 这种如果读者会停下来想，就换成更直接的说法或先定义。
> "`closed set` what do you mean closed set"

**T5 — 缩写、protocol label 和技术短语必须首现解释。** 如果缩写或标签不是领域里公认的常识，就不要直接丢给读者；先写全称，或用一句白话说明它到底指什么。
> "`CSDI` 是不是应该先写全称... `pooled window-level protocol` / `complete channel setting` 我也不一定懂"

---

### 【Reviewer Response 专属】

**R1 — 每条都必须正面回应，包括你不同意的。**

**R2 — 感谢语只在每个 reviewer 末尾出现一次。** 不要在每条 response 前面都说谢谢。

**R3 — 不同意就直说，给出理由。** 含糊回避比直接说"我们不同意，因为…"更差。

**R4 — 只改被要求的内容。** 主动添加其他改动可能引入新问题。

---

### 【研究方法论】

**M1 — 方法论描述要先讲 reasoning，不要写成 project report。** 不能只说"做了什么"或 `I did this, then I did that`；要先说原则是什么、为什么这样设计，再说具体操作细节。
> "你要 synthesize 到一个方法论的阶段... 你的原则是什么，为什么"

**M2 — 写作中必须明确记录所有方法选择。** 包括数据采样策略。凡是做了的决定，write-up 里都要写出来，不能遗漏。
> "那个easy hard mediocre没有在你的write up里提到，你需要提到"

**M3 — 不能假设读者知道你数据集的内容。** 必须主动交代数据集背景，不能让读者自己猜。
> "这一段是不是应该解释一下你的dataset里通常有些什么东西"

**M4 — 结果与预期矛盾时，解释必须真正站得住脚。** 给了等于没说的解释照样会被批。
> "I know you explained it, but I don't think that explanation really justify — that's my point"

---

### 【发稿前】

**S1 — 发之前通读一遍，检查前后一致性。** 读两遍可能不够。

**S2 — 同类错误不能重复出现。** 被指出过的问题，下次发稿前要主动扫全文。

**S3 — 语法错误是作者的完全责任，不能找借口。** 发之前必须清查干净。
> "你take responsible，故意留的，为什么找理由，为什么要留那个语法错误"

---
