# 生物标志物：fit-for-purpose 验证

> 来源：FDA《Bioanalytical Method Validation for Biomarkers》最终指南（2026-04）；ICH M10 明确 biomarker 不在其范围内。不要把 PK 的 M10 全套硬套到所有 biomarker。

## 1. 先定 context of use（COU）

| 问题 | 影响 |
|---|---|
| 用于监管决策/标签？ | 需要 full validation，接近 M10 |
| 仅内部 go/no-go？ | fit-for-purpose，验证范围可减小 |
| 诊断/预后/药效？ | 需要临床验证/切点，超出纯分析验证 |
| 内源性基线？ | 需要基线、昼夜、饮食、疾病影响 |

## 2. PK vs biomarker

| 项目 | PK assay | Biomarker assay |
|---|---|---|
| 分析物 | 给药分子 | 内源/外源标志物 |
| 空白基质 | 通常无分析物 | 常含内源分析物 |
| 校准品 | 标准品 | 可能无纯标准品/需 surrogate |
| 范围 | 暴露范围 | 生理/病理范围 |
| 验证 | M10 | fit-for-purpose；监管决策时 full |
| 关键 | 准确度/精密度 | 选择性、基线、临床意义 |

## 3. 验证元素

- 选择性/特异性：内源干扰、相关蛋白、药物、抗试剂抗体。
- 准确度/精密度：加标回收、混合基质、个体基质。
- 校准：surrogate matrix、标准加入法、背景扣除。
- 稀释线性/平行性。
- 稳定性：冻融、室温、长期、全血/血浆。
- 批接受/ISR：按 COU 决定。
- 临床性能：切点、敏感性、特异性（如用于诊断）。

## 4. 平台选择

| 分析物 | 首选 | 备选 |
|---|---|---|
| 蛋白标志物 | LBA | hybrid LC-MS |
| 小分子标志物 | LC-MS/MS | LBA |
| 低丰度蛋白 | hybrid/IA-LC-MS | 高敏 LBA |
| 内源代谢物 | LC-MS/MS | — |

## 5. 常见问题

**Q：biomarker 能不能直接套 M10？**
A：不能。M10 明确不覆盖 biomarker；FDA 2026 要求 fit-for-purpose，监管决策时 full validation。

**Q：空白基质含内源分析物怎么办？**
A：用 surrogate matrix、标准加入法、背景扣除；证明 surrogate 与真实基质可比。

**Q：biomarker 方法需要 ISR 吗？**
A：按 COU 和法规要求；监管决策/关键终点通常需要，探索性可减少。

## 6. 边界

- 本文件不覆盖诊断试剂注册或临床验证统计。
- 不能把“可测”当成“有临床意义”；COU 决定验证级别。
