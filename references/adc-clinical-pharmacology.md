# ADC 临床药理与生物分析策略

> 主要来源：FDA《Clinical Pharmacology Considerations for Antibody-Drug Conjugates》最终指南（2024-03）；AAPS ADC Working Group 更新建议（2026）；ICH M10。具体申报以最新法规和 Pre-IND 沟通为准。

## 1. 先定“测哪几种 ADC 物种”

| 分析物 | 定义 | 常用方法 | 关键点 |
|---|---|---|---|
| 总抗体 TAb | 所有抗体，含 DAR0 | LBA（target/anti-ID/anti-Fc 捕获）或 hybrid LC-MS | 包含裸抗；不等于 ADC |
| 偶联抗体 | 至少一个 payload 的抗体（DAR≥1） | LBA：anti-payload 捕获 + anti-Fc/anti-ID 检测 | 通常**不随 DAR 线性变化**；反映“带 payload 的抗体”，不是摩尔 ADC |
| 偶联 payload | 共价连接在抗体上的 payload 质量 | LBA：anti-Fc/anti-ID 捕获 + anti-payload 检测；或 LC-MS | **DAR 敏感**；信号随每个抗体上的 payload 数增加 |
| 总 payload | 偶联 + 游离 payload | 释放 + LC-MS/MS | 不能回答游离 payload |
| 游离 payload | 未共价偶联/已释放的小分子 | 分离 + LC-MS/MS | 需证明无 ex vivo 释放 |
| DAR/DLD | 平均载荷 + 分布 | HIC/native MS/LC-MS | 平均 DAR 不等于均一性 |

> 关键区分：**偶联抗体 assay 通常不 DAR-sensitive；偶联 payload assay 才 DAR-sensitive。** 两者不能互称。

## 2. FDA 2024 的核心要求

FDA 要求根据 ADC 的构成和临床阶段，选择能回答以下问题的 assay panel：

- 总抗体、偶联抗体、游离 payload 的 PK；
- 游离 payload 的药理活性代谢物；
- 暴露–反应（ efficacy/safety）关系；
- 内在因素（肾/肝损伤）对游离 payload 的影响；
- QTc 评估：通常测游离 payload 和活性代谢物；
- 免疫原性（ADA）；
- DDI。

### 什么时候可以少做

FDA 给的是“可讨论”的例子，不是自动豁免：

- 若游离 payload 用足够灵敏的方法仍检测不到，可讨论是否还需要测；
- 若 ADC 只是载体，且总抗体与 ADC 高度相关，可讨论是否还需要总抗体；
- 但必须用早期临床数据、暴露–反应和 safety 数据支持，不能凭体外数据自行删。

### 游离 payload 的灵敏度

FDA 明确：游离 payload 方法要足够灵敏，能检测到**临床上可能有意义的小幅暴露变化**。不能只满足于“能测到”，要能支持 QTc/安全窗/暴露–反应。

## 3. AAPS 2026 的 assay 术语

AAPS 将 ADC assay 分成：

1. **Conjugated payload assay**：测 payload 数量；anti-Fc/anti-ID/target 捕获 + anti-payload 检测；信号随 DAR 增加；结果可换算 payload 质量/抗体摩尔。
2. **Conjugated antibody assay**：anti-payload 捕获 + anti-Fc/anti-ID 检测；测“至少带一个 payload 的抗体”；通常不随 DAR 线性变化。
3. **Total antibody assay**：测所有抗体，包括 DAR0。
4. **Free payload assay**：LC-MS/MS 为主；需分离、稳定、选择性。

### 方法选择

- Total antibody：LBA 或 hybrid LC-MS 都可；LBA 更常用。
- Conjugated antibody：LBA；注意 capture 表位可及性和 DAR 对信号的影响。
- Conjugated payload：LBA 或 LC-MS；若用 LBA，必须用 DAR 匹配标准品。
- Free payload：LC-MS/MS；LBA 仅在特异抗体可用时考虑。
- DAR/DLD：HIC/native MS/LC-MS，不能只报平均 DAR。

## 4. 按阶段选 panel

| 阶段 | 最低建议 | 目的 |
|---|---|---|
| 发现/候选 | 总抗体、偶联 payload、free payload（如可测）、DAR | 筛选稳定性/暴露 |
| 临床前 TK | 总抗体、偶联抗体/偶联 payload、free payload、DAR | 毒理暴露/种属比较 |
| FIH | 总抗体、偶联抗体、free payload、DAR；活性代谢物按需 | 安全起始剂量、暴露–反应 |
| 后期 | 根据前期相关性精简；保留能支持标签/安全性的 assay | 人群 PK、内在因素、DDI、QTc |

## 5. 常见问题

**Q：总抗体和 ADC 哪个更能代表疗效？**
A：不能一概而论。总抗体包含 DAR0；ADC/偶联抗体更接近有效载荷暴露。要看靶点、linker 稳定性、DAR 和暴露–反应。

**Q：能不能只测总抗体？**
A：只有在 ADC 作为载体、总抗体与 ADC 高度相关、且有临床数据支持时才可讨论；不能默认。

**Q：偶联抗体 LBA 结果为什么不能直接算 DAR？**
A：它测的是“带至少一个 payload 的抗体”，不是每个抗体的 payload 数；需要偶联 payload 与抗体摩尔浓度。

**Q：free payload 测不到，能不能不测？**
A：需用足够灵敏的方法确认；若确实低于 LLOQ，记录方法灵敏度并说明临床意义，不能只用“测不到”草率删除。

## 6. 边界

- FDA 指南针对**细胞毒小分子 payload 的 ADC**；其他 payload（如免疫刺激、放射性、蛋白毒素）不能直接套。
- 本文件不构成申报承诺；panel 精简必须与监管沟通。
- DAR 是产品表征，不是 PK 浓度；不能拿 DAR 代替暴露。
