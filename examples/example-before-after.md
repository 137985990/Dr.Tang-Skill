# 示例：改稿前后对比

这个示例展示同一段话在预审前后的变化。用来理解 skill 输出后"改到什么程度才算过关"。

---

## 场景

Paper introduction 第二段。目标：解释为什么现有方法在实际部署中不够用。

---

## 改前（原始草稿）

> Multi-modal physiological sensing has advanced significantly with the development of wearable technology. EEG, ECG, PPG, and other sensors are now widely used in fatigue detection research. However, collecting high-quality multi-modal data is challenging due to sensor noise, battery limitations, missing data segments, and individual differences across devices and scenarios. The resulting data are richer but also more variable and harder to process. Most existing approaches treat this as a multivariate time-series learning problem.

---

## Skill 预审输出

### 审稿结论

🔴 现在不能发

主要问题：没有中心论点；包含两个无 citation 泛化 claim；与前后段逻辑连接不清。

### 必须改

- [ ] **无中心论点（触发 P1）**
  - 这段罗列了 4 个挑战（noise / battery / missing / individual differences）但没有中心落点。读完整段，读者不知道"这段的结论是什么"。
  - 改法：先决定这段的核心主张是什么（例如：现有方法假设传感器数据永远可用，但现实中这个假设经常不成立），再用后面的句子支撑这一主张。

- [ ] **"battery limitations" 泛化（触发 L1 + L2）**
  - 不是所有传感器都有电池问题。这句话如果没有 citation 支撑，审稿人可以举 motion-powered 传感器反驳。
  - 改法：删除，或缩小范围 + 加 citation。

- [ ] **"richer but also more variable" 矛盾未解释（触发 P1 / P2）**
  - "richer" 和 "more variable/harder to process" 是相反方向的描述，放在一起没有解释逻辑关系，读者困惑。
  - 改法：解释为什么更丰富的数据反而更难处理，或者删去"richer"只说难处理的原因。

### 建议改

- [ ] 最后一句"Most existing approaches treat this as a multivariate time-series learning problem"与前面的挑战描述没有连接，突然出现。要么建立逻辑连接，要么移到下一段。

---

## 改后（修改版）

> Multi-modal physiological sensing has achieved strong performance in controlled laboratory settings. However, most existing approaches implicitly assume that sensor streams are continuously available and of consistent quality — an assumption that frequently breaks down in real-world deployment. In practice, wireless sensors experience intermittent connectivity, motion artifacts degrade signal quality, and sensor configurations vary substantially across deployment contexts [REF1, REF2]. These conditions produce data that cannot be reliably used by methods designed for clean, lab-collected inputs. The core challenge, therefore, is not collecting more data — it is building methods that remain effective when the data they receive is incomplete or degraded.

---

## 改动说明

| 改动 | 对应的审稿问题 | 对应的唐老师偏好 |
|---|---|---|
| 第一句明确说明 lab 表现好 | 为后面的转折铺垫 | P2（逻辑铺垫） |
| 第二句确立中心论点（assumption breaks down） | 取代了原来的事实罗列 | P1（每段一个核心论点） |
| 删除"battery limitations"，改为 intermittent connectivity + motion artifacts | 删除无 citation 泛化 claim | L1, L2 |
| 加了 [REF1, REF2] | 为 challenges 的存在提供支撑 | L2 |
| 删除"richer but more variable"矛盾表述 | 消除逻辑矛盾 | P1 |
| 末尾用一句话收束整段的核心论点 | 段落有明确落点 | P1 |
| 移除了 multivariate time-series 那句（放到下段） | 与本段逻辑无关 | P2 |

---

## 关键点

改前的每句话都不是错的。  
改后的每句话都在服务同一个中心论点。  

这是唐老师最常批的那类问题："没有一句话是错的，但没有抓到东西。"
