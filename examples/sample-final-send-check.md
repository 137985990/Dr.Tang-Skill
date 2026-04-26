# 示例：临门一脚检查（场景 C）

这是场景 C 的独立示例。场景：稿子基本改完，只想在发给唐老师前快速确认有没有致命问题。

---

## 输入

**用户请求：** 帮我做一次发给唐老师前的最终检查，这段 related work 我已经改过两遍了准备发了。

**草稿：**

> A growing body of work has explored fatigue detection using multi-modal physiological signals [1–8]. These approaches leverage EEG, ECG, and PPG signals to capture complementary aspects of cognitive and physical state, achieving strong performance under controlled conditions.
>
> Recent advances in domain adaptation have further improved cross-subject generalizability [9–15]. Methods such as domain-adversarial training and instance reweighting align feature distributions across subjects, enabling models trained on source subjects to transfer to new targets.
>
> However, existing domain adaptation methods assume that the same sensor modalities are available in both source and target domains. In practical deployment scenarios, sensors are often impractical due to noise, missing segments, and device-specific differences. This limitation motivates our proposed framework, which addresses cross-source modality transfer under heterogeneous sensor configurations.

---

## Skill 输出

### 能不能发

🟡 改完下面这一项就能发

---

### Blocking Issues

- **"sensors are often impractical"（触发 L4 / L1）**
  - 这个表述有两个问题：第一，"impractical" 太强——传感器不是"不实用"，而是在真实部署中"面临挑战"；第二，"noise, missing segments, and device-specific differences" 是后果，不是"impractical"的直接原因，因果链缺一步。
  - 最小改动：把 "sensors are often impractical due to noise, missing segments, and device-specific differences" 改为 "sensor streams are often degraded or intermittently unavailable due to noise, missing segments, and device-specific configuration differences"

---

### 最小改动建议

原句：
> sensors are often impractical due to noise, missing segments, and device-specific differences

改为：
> sensor streams are often degraded or intermittently unavailable due to noise, missing segments, and device-specific configuration differences

改了这一处，这段可以发。

---

## 备注

这个例子展示了场景 C 的核心特点：

- **只报真正的 blocking issue**，不展开全文分析
- 第一段和第二段虽然还有可以打磨的空间（比如第二段 citation 较多但每篇没有单独解释），但这些是"建议改"级别，不是"必须改才能发"
- 场景 C 的用途是临门一脚，不是全面审稿——如果想要完整审查，用场景 B

---

## 对比：如果用场景 B 审同一段

场景 B 会额外指出：
- 第二段 [9–15] 中每篇的具体贡献没有解释（P6）
- "strong performance under controlled conditions" 应有 citation 支撑（L2）
- 第三段最后一句 "which addresses cross-source modality transfer under heterogeneous sensor configurations" 在 related work 里引出自己的方法，边界稍显模糊（P5）

这些是"建议改"项，不影响当前能否发出。
