# 措辞如何改变意思

这是带上下文的表达选择，不是个人高频词榜。句型是可选工具；先确认它承担的关系，再选择是否使用。来源编号见 [source-notes.md](source-notes.md)。

## 亲自提供或修改的英文：学她怎样使意思落地

### 从价值标签到参与关系：with、from the beginning、shaping

2026-05-05 的本人候选改写包含 `designed with students from the beginning`，下一句以 `structured co-design sessions` 解释活动，并列出学生参与塑造的功能、AI 互动语言和界面。[F1b]

这里有三种具体信息：谁共同设计、何时参与、参与改变什么。若稿件只写 student-centered，把这些事实补出来比再加 deeply participatory 更有用。只有真实开展或计划共同设计时才能迁移这一关系；时态跟随实际进度。

**构造的改句示范，非原话：**

> Students will help design the prompts and interface from the beginning of the design phase. Their input will inform these design choices; it will not extend to every research decision.

这一例里的参与范围是假设给定的事实，不是来自原候选稿。正式改稿中用作者实际提供的范围，不能由 co-design 推出参与全部决策。

### 从技术名词串到动作：brings together、studies how、combining

新闻研究段的真实变化包括：[D1]

| 原片段 | 回稿片段 | 承担的工作 |
|---|---|---|
| `experiments with virtual and augmented reality` | `research brings together artificial intelligence (AI) and immersive technologies` | 先校正研究范围及技术关系 |
| `a more intuitive understanding of manufacturing processes` | `make complex systems easier to understand, model, and control` | 明确研究对象与可理解的用途 |
| `in combination with artificial intelligence` | `combining AI with virtual and augmented reality` | 用动作表达组合，减少插入性名词结构 |
| `Additionally` | `Most recently` | 从并列补充变成近期工作的定位 |

回稿还单独用 `studies how` 引出用途。这些是一次可确认的选择，适合说明她怎样处理公众研究介绍。方法节应直接写具体操作；不能因为这些词确由她采用，就把全文改成 brings together 或从广泛研究兴趣开头。

### 压缩的保留条件：shorten … maintain the same logic

她在概念稿邮件中要求 `shorten it but maintain the same logic`，也说明自己补了 what/how 并删除可能误导系统类型的 conversational。[F1a]

压缩时保留“做什么 → 如何做 → 为什么有用”的必要联系，删掉绕述和重复。若短到只剩技术名词与愿景，意思已经丢失。conversational 在那一稿会导致错误归类；真实对话系统中仍可能准确。

新闻段由两句 43 词变为三句 56 词，说明解释清楚有时需要加一句。[D1] 会议中她要求 short sentence，又补充“但不是很 short”。[T1f] 可操作的尺度是朗读时读者能否保持主语、动作和关系，而不是固定词数。

**构造的拆句示范，非原话：**

> The source data contain EEG and ECG, whereas the target data contain only ECG. Shared ECG measurements provide the input for learning source-domain relationships. We use these relationships to estimate EEG in the target setting.

三个句子先后承担设置、桥梁与操作；仅在这些确为本文事实时采用。若短句之间失去指代和因果，保留必要从句反而更清楚。

## 她怎样提问题：问题必须改变作者下一步的写法

| 有据表达或动作 | 在原情境里做什么 | 迁移到论文指导 |
|---|---|---|
| `what do you mean by richer` [T1a] | 比较维度不清，无法理解 richer 与 scarce 的关系 | 先查关键词究竟指数量、通道还是信息；确定以后直接改成具体所指 |
| `if my understanding is correct` [D3] | 暴露暂定理解，让作者纠正模拟对象/行为的误读 | 复述一个真实的歧义，再问决定性问题；理解明确时直接陈述 |
| `This sounded just a problem definition` [D2] | 表格完成了题目描述，却未清楚完成方法演示 | 先说这段实际做了什么，再补它本来应展示的操作 |
| `this might need references` [D2] | 对一个具体方法列表提出有保留的支撑要求 | 指明哪项判断需要什么支持；是否须在此重复引用按上下文判断 |
| `I don't think we know` [D3] | 指出行为反应仍是未知，不能先写进模拟假设 | 区分已知机制、研究假设和待观察效果，再调整结论范围 |

保留“先读出了什么，再指出哪里不成立”的反馈次序，使用清楚、直接的中文或英文。她在讨论中允许作者据证反驳她尚未读过的技术判断。[T1e] 因此，skill 的反馈也要说明判断所依据的材料，遇到未知不装作已经知道。

## 技术词保留它真正区分的对象

录音中的 missing segment、incomplete modality 等词会引出不同的任务预期。[T1c] 修改时先辨认本稿是哪种情况：零散时间点缺测、整通道未采集、已有通道跨域变化，还是其他条件。然后选足够精确的说法。

**构造的例子，非原话：**

- 通道中零散采样没记录：`missing observations within an otherwise available channel`。
- 当前目标数据从未采 EEG：`EEG is not collected in the target setting`。
- 估计信号与实测信号：分别写 `estimated EEG`、`recorded EEG`，使后文评价的对象清楚。

这些不是唐老师的专属术语表，也不覆盖所有论文设定。论文应定义自己的操作；不要为避免重复而把 imputation、augmentation、translation、generation 无条件轮换。

## 连接和强度取决于关系，不能凭熟悉的词补出来

疲劳监督稿先承认既有处理 reliability 的价值，再解释 accessibility 为什么仍是另一条件；用 provided that 给转移知识的价值附上适配条件。AIGC 监督稿先承认既有历史综述的共同视角，再说明共同框架和贯穿例子给读者增加什么。[U1、U2]

对应写法是“已有能力及其条件 → 当前未覆盖的条件 → 本文回应”。这是可采用的关系，不证明 although、while、provided that 是个人高频词。只有真有转折才用 However；只有因果已解释才用 therefore。

她曾要求把 striking 收敛，也要求核对实际部署文献，而非直接说 none。[T1g、T2] 修改 strong/first/novel/reliable 等词时，先确定比较基准与证据：

- 已有组件的整合可以贡献于设置、框架或验证；把创新对象写明，不能自动改成新算法，也不因组件已有就否定贡献。
- 证据不足以证明首次，就删除“首次”或缩到确已核实的范围；`a few` 也需要文献支持。
- 只在特定传感配置验证，就写该配置；不能扩成 any real-world environment。

保留原本有根据的强结论。谨慎并不等于每句加 may、potentially 或 we believe。

## 语法处理

亲笔快速评论中存在非标准语法，那是原话的记录，不是论文应复制的句法。新英文使用规范冠词、时态、搭配与主谓一致。日常邮件的称呼、礼貌结束语、缩写和表情不进入论文风格。一般英文规范与上面可归属的表达选择分别看待。
