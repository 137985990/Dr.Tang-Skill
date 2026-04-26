# 改稿快速判断规则

在发给唐老师之前，用这个 checklist 过一遍。每条是一个具体判断点，而不是模糊的"好好写"。

---

## 发送前必过 checklist（任一不通过 = 不能发）

### Introduction / 论证段落

- [ ] **每段是否只有一个中心论点？**
  - 测试：用一句话概括这段的核心主张，能做到吗？
  - 如果概括后发现"其实说了两件事"，这段要拆

- [ ] **第一段是否以 urgency 收尾？**
  - 测试：结尾那句话是描述困难，还是说明为什么这个 gap 必须现在解决？
  - 困难描述 ≠ urgency

- [ ] **段与段之间逻辑是否可以跟上？**
  - 测试：从上一段最后一句，到下一段第一句，中间有没有需要读者自己猜的步骤？

- [ ] **有没有"一杆子打死"的 claim？**
  - 识别特征："所有…""没有人…""绝大多数…"
  - 处理：加 citation，或改成"many""most existing approaches"并说明原因

- [ ] **有没有不同性质的问题被混在一起？**
  - 典型：data unavailability（信号断了）≠ measurement degradation（信号存在但质量差）

### Related Work

- [ ] **每篇引用是否用自己的话解释了？**
  - 测试：把引用那句话单独拎出来，没读过那篇文章的人能理解吗？

- [ ] **每篇引用是否说明了与自己工作的关系？**
  - 错误模式：只说别人做了什么，但不说为什么和自己相关

- [ ] **Related work 有没有再次陈述问题？**
  - 问题在 introduction 里说，related work 说别人的工作

### Reviewer Response

- [ ] **每一条 reviewer 评论都有对应回应吗？**
  - 包括：你不同意的那条，也要正面说清楚你不同意在哪

- [ ] **感谢语是否只出现在每个 reviewer 回应的末尾？**
  - 不要在每条 response 前面都写 "We thank the reviewer for..."

---

## 高风险词/句型识别表

遇到以下词型时，立刻检查是否有问题：

| 词/句型 | 风险 | 检查方向 |
|---|---|---|
| "all sensors / all methods / all prior work" | 泛化 claim | 是否有 citation？能否缩小范围？ |
| "battery limitations" | 特定传感器才有 | 缩小范围 + 加 citation |
| "impractical" | 过强 | 改用 "challenging in real-world deployment" |
| "missing modality" | 有特定含义 | 是否真的是 modality 完全缺失？ |
| "transform" | 可能被读成 augment | 确认操作本质 |
| "operational" | 太模糊 | 解释清楚 operational 指什么 |
| "we are the first to..." | 高风险 novelty claim | 验证文献，能否改用 "to the best of our knowledge"？ |
| 结尾无 urgency | Introduction 典型缺陷 | 加上"为什么 gap 必须现在解决"的句子 |
| 感谢语出现多次 | Reviewer response 格式错误 | 保留末尾一次，删除其他 |

---

## 常见"正确但无点"的写法

这类写法读起来没错，但唐老师会问"这段到底想说什么"：

- 罗列了 3-5 个困难（噪声、电池、缺失、漂移…）但没有统一的论点
- 每句话是对上一句的补充，但全段没有中心落点
- 描述了一个事实，然后直接转到下一个事实，没有因果连接

**修法：** 先写一句"这段想说的是：\_\_\_\_"，然后检查后面每句话是否在支撑这个中心。

---

## Reviewer Response 快速检查

1. 列出所有 reviewer comments（标好编号）
2. 对照自己的 response，每条打勾
3. 检查有没有漏掉的
4. 找到所有"We thank the reviewer"出现的位置 → 只保留每个 reviewer 末尾那一处
5. 找出你不同意的评论 → 是否清楚说明了"we respectfully disagree because..."？
