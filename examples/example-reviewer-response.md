# 示例：Reviewer Response 预审

这是 Reviewer Response 场景的完整预审示例。这是和 paper introduction 不同的高频使用场景。

---

## 输入材料

**用户请求：** 帮我按唐老师的标准检查一下这个 reviewer response，明天要提交了。

**草稿：**

> **Response to Reviewer 1:**
>
> We thank the reviewer for the insightful comments and suggestions. We have carefully considered all the feedback and made revisions accordingly.
>
> **Comment 1:** The paper lacks justification for the choice of the U-Net architecture.
>
> We thank the reviewer for raising this important point. We have added a paragraph in Section 3.2 explaining the rationale for using U-Net, citing [REF1] and [REF2] to support this choice.
>
> **Comment 2:** The cross-domain evaluation is not convincing. Only two datasets were used.
>
> We thank the reviewer for this valuable suggestion. We acknowledge that expanding the evaluation would strengthen the paper. However, due to the limited availability of public fatigue detection datasets with compatible sensor configurations, we were unable to include additional datasets at this time. We hope this explanation is satisfactory.
>
> **Comment 3:** How does the method handle the case where all modalities are missing simultaneously?
>
> We have added a discussion of this edge case in Section 4.4.
>
> We thank the reviewer again for the thorough and helpful review.

---

## Skill 输出

### 审稿结论

🟡 改完这几项再发

主要问题：感谢语重复出现了四次；Comment 3 没有正面回答问题；Comment 2 的回应措辞含糊。

---

### 必须改

- [ ] **感谢语重复（触发 R2）**
  - 位置：opening、Comment 1 前、Comment 2 前、末尾
  - 问题：感谢语出现了 4 次。唐老师明确要求：每个 reviewer 只在最后说一次感谢，不要在每条 response 前面都说。
  - 依据：R2 — 感谢语只在末尾出现一次
  - 改法：删除 opening 的感谢、删除 Comment 1 和 Comment 2 前面的感谢，保留最后一句。

- [ ] **Comment 3 没有回答问题（触发 R1）**
  - 位置：Comment 3 的 response
  - 问题：问题是"当所有模态同时缺失时，方法怎么处理"，但 response 只说"我们在 4.4 节加了讨论"，没有给出实际答案。读者（和导师）会认为你没有正面回应这个问题。
  - 依据：R1 — 每条评论必须正面回应，不能只说"我们加了讨论"
  - 改法：在 response 里直接回答这个问题（哪怕是一句话的技术解释），再说"详见 4.4 节"。

- [ ] **Comment 2 末尾"I hope this explanation is satisfactory"（触发写作语气规则）**
  - 位置：Comment 2 response 末尾
  - 问题：唐老师明确说过不要用这类"我希望你满意"的措辞，显得不专业。
  - 依据：Reviewer Response 规范 — 不用 "I hope this satisfies you" 类表达
  - 改法：直接删除这句话，或改为"We believe these additions adequately address the reviewer's concern."

---

### 建议改

- [ ] **Comment 2 的回应可以更有力**
  - 当前回应承认了局限但语气偏弱。可以说明你用了哪些可用数据集，为什么这已经是当前条件下能做到的最充分的验证，而不是只说"数据集不够"。

---

### 可以不改

- Comment 1 的回应内容没有问题，格式正确，加了具体引用和位置说明。

---

### 重写建议

**感谢语（全文统一处理）**

删除前三处，只保留末尾一句，改为：

> We thank Reviewer 1 for the careful and constructive review.

**Comment 3 回应**

原文：
> We have added a discussion of this edge case in Section 4.4.

建议改为：
> When all modalities are simultaneously missing, our method defaults to [具体机制描述，例如：using only the available cross-domain alignment signal without modality-specific reconstruction]. This edge case is rare in the target deployment scenario because [原因]. We have added a discussion of this case and its limitations in Section 4.4.

---

### 审稿依据

使用了 SKILL.md 内置的已知唐老师偏好（R1–R4）。高置信度判断。
