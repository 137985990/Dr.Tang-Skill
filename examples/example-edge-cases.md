# 示例：边缘情况

这个文件覆盖两种特殊场景，避免所有示例都太标准：

1. **差一点就能发，但有一个致命问题** — 整体看起来不错，但有一处会被唐老师直接批
2. **证据不足的情况** — skill 应该说"不确定"而不是乱给结论

---

## 场景 1：差一点就能发，但有一个致命问题

### 输入

**用户请求：** 帮我检查一下这段 introduction 第三段，我觉得已经改得不错了。

**草稿：**

> To address these challenges, several recent studies have proposed cross-domain transfer methods for fatigue detection [16–22]. These approaches adapt models trained on laboratory datasets to real-world deployment conditions by aligning feature distributions across domains. Representative methods include adversarial training [16], optimal transport [18], and contrastive alignment [21], each demonstrating improved generalization across subjects and environments.
>
> Despite these advances, a fundamental limitation remains: existing methods assume that the sensor configuration in the target domain matches that of the source. In practice, this assumption is rarely satisfied, as different deployments rely on different sensor subsets, sampling rates, and electrode placements. Our previous work [23] demonstrated that incorporating cross-source modality alignment significantly improves transfer performance under heterogeneous configurations.

### Skill 输出

#### 能不能发

🟡 改完这一项就能发

---

#### Blocking Issues

- **"our previous work [23]" 在 related work 里引出自己的工作但没有上下文（P5 + 基本写作规范）**
  - 问题：Related work 里突然提到 "our previous work"，但读者到这里还没有被介绍过这个工作是什么。这个引用会让审稿人问：你们之前的工作是什么？它在 introduction 里介绍过吗？还是只在这里提了一句就结束了？
  - 这是唐老师会直接问的问题："没有人是你肚子里的蛔虫。"
  - 改法：要么在 introduction 里先介绍 [23]（建立对话），然后在 related work 里说"在此基础上"；要么从这里删掉，改成只描述"本文所提出的方法"而不引用自己的前作。

---

#### 建议改（不影响能否发出）

- 第一段的三个方法（adversarial training / optimal transport / contrastive alignment）列举了但没有说每种方法的局限，直接过渡到第二段的"fundamental limitation"有点跳。可以加一句过渡。

---

### 说明

这个例子说明：一段话可以逻辑清楚、表述准确、引用充分，但仍然有一个结构性问题会被直接批——"our previous work" 没有铺垫。整体质量已经不错，但这一处足以让唐老师提出修改要求。

---

## 场景 2：证据不足，skill 应该说不确定

### 输入

**用户请求：** 我没有聊天记录，但我想了解唐老师对"methodology 写法"有什么偏好。

### Skill 输出

#### 能给出的

内置的已知唐老师偏好（P1–S2）覆盖了 introduction、related work 和 reviewer response 的规律，这些是多次录音中反复出现的高频模式。

#### 无法可靠给出的

关于 **methodology 写法**的偏好，现有材料中出现次数不足以建立稳定规律。以下是目前的情况：

- 在录音中，唐老师提到过"design justifications 应该放在 methodology 里，而不是 related work"（出现 2 次，中置信度）
- 但关于 methodology 段落的具体写法（如公式呈现方式、算法描述层级、实验设置格式），录音中未有明确反复指导

**当前建议：** 对于 methodology 写法，使用通用学术写作规范，不将其标注为"唐老师的已知偏好"。如果你有涉及 methodology 的聊天记录，提供给 skill 后可以提炼更有依据的判断。

#### 置信度说明

| 内容 | 置信度 | 原因 |
|---|---|---|
| Introduction / Related work 规则 | 高 | 多次录音中重复出现 |
| Reviewer response 规则 | 高 | 多次录音中重复出现 |
| Methodology 写法 | 低-中 | 录音中出现次数少，部分为情境性评论 |
| 邮件沟通风格 | 无数据 | 录音语料中无覆盖 |

---

### 说明

这个场景展示了 skill 应该做到的事：**证据不足时，说不确定，而不是用泛泛的写作建议填充答案**。

如果 skill 对 methodology 给出一套看起来合理但没有唐老师原话支撑的"偏好"，用户可能把通用建议误认为是导师的真实要求——这比不给答案更有害。
