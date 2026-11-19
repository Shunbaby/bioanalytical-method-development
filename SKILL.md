---
name: bioanalytical-method-development
description: Develop and audit LBA and LC-MS/MS bioanalytical methods.
version: 0.2.6
author: User (WeChat), Hermes Agent
license: MIT
platforms: [linux, macos, windows]
metadata:
  hermes:
    tags: [bioanalysis, LBA, LC-MS, method-development, validation, SOP, ADC, DAR]
    related_skills: [biologic-bioanalysis-compendium, antibody-lc-ms-quantitation, lc-ms-sample-preparation]
---

# 生物分析方法开发（LBA + LC-MS/MS）

面向大分子、小分子、ADC 和生物标志物的方法开发与审核。覆盖 **LBA、LC-MS/MS、hybrid LBA-LC-MS** 三条平台路线，以及 ADC 的 DAR/游离 payload 口径、SOP 模板和放行检查。不是法规原文的替代品；申报前以 ICH M10、FDA/EMA/NMPA 现行指南和 site SOP 为准。

## When to Use

- 为某个分析物选择 LBA、LC-MS/MS 或 hybrid 平台，并说明理由。
- 写 LBA 方法开发方案：抗体配对、标准品、校准曲线、基质、hook、选择性。
- 写 LC-MS/MS 方法开发方案：特征肽/完整蛋白/游离 payload、内标、提取、色谱、MRM。
- 审核 ADC 的生物分析策略：总抗体、偶联抗体、总 payload、游离 payload、DAR/DLD。
- 起草或审核生物分析 SOP、运行接受标准、偏差处理、ISR 和数据完整性检查。
- 排查低信号、高背景、hook、基质效应、残留、精密度差、稳定性失败。

**Don't use for:** 替代专用 ADA/免疫原性方法；临床剂量选择；纯法规申报结论；没有明确分析物的“帮我建个方法”。

## 第一原则：先定分析物和 context of use

在选平台之前，先写清楚这五行；写不清就不要开始优化：

| 问题 | 必须写出的内容 |
|---|---|
| 测什么 | 总抗体 / 偶联抗体 / 完整 ADC / 总 payload / 游离 payload / 特征肽 / 生物标志物 |
| 基质 | 人/猴/鼠血浆、血清、组织匀浆、尿；抗凝剂 |
| 范围 | LLOQ、ULOQ、预期暴露、稀释需求 |
| 目的 | PK、TK、PD、BE、稳定性、DAR 表征、诊断 |
| 法规环境 | 探索性 vs 注册；GLP/GCP；ICH M10 是否适用 |

**同一“药物浓度”可能指四种不同分析物。** 不先定义，后面的 LBA/LC-MS 之争没有意义。

## 平台选择（先看分析物，不看仪器）

| 场景 | 首选 | 原因/限制 |
|---|---|---|
| 完整大分子、有可靠抗体对、需要高灵敏 | **LBA** | 信号是结合事件；受 target/ADA/药物干扰；测的是“可结合部分” |
| 小分子 payload、游离药物、代谢物 | **LC-MS/MS** | 质量特异性；需分离、内标、基质效应控制 |
| 蛋白质/多肽，无好抗体或需区分亚型 | **LC-MS/MS（特征肽）** | 需酶解、特征肽、SIL 内标；不能区分完整与片段除非先分离 |
| 低丰度蛋白、复杂基质、需要高灵敏 | **Hybrid LBA-LC-MS** | 免疫富集 + LC-MS 读出；试剂和富集仍是瓶颈 |
| 总抗体 vs 偶联抗体 | LBA（不同捕获/检测策略） | 总抗体包含 DAR0；偶联抗体只算 DAR≥1，通常不随 DAR 线性变化 |
| DAR 分布 | HIC / native MS / LC-MS | 平均 DAR 不等于分布；高疏水 payload 会使 HIC 失效 |
| ADA/免疫原性 | 专用 ADA 方法 | **ICH M10 不覆盖免疫原性**；不要用 PK 方法代替 |

### 选择规则

1. **能明确质量/结构** → LC-MS/MS 优先；**能明确结合/活性** → LBA 优先。
2. 需要“游离”浓度 → 先解决分离（平衡透析、超滤、SPE、免疫富集），再谈平台。
3. 需要“总”浓度 → 先确认是否包含 DAR0、结合蛋白、复合物。
4. 两个平台都可用时，用 **正交验证**：LBA 测结合，LC-MS 测质量；不要用其中一个“校正”另一个而不说明分析物差异。

### 复杂体系先看这张表

| 体系 | 首选 | 关键控制 |
|---|---|---|
| 血浆大分子 | LBA | 抗体对、target/ADA 干扰 |
| 血浆小分子/payload | LC-MS/MS | 内标、基质效应、残留 |
| 组织/肿瘤 | LC-MS/MS（或 LBA） | 匀浆效率、蛋白/重量归一化、异质性 |
| 游离药物 | 分离 + LBA/LC-MS | 膜吸附、平衡时间、pH/温度 |
| 内源性标志物 | LC-MS/MS | surrogate matrix、基线扣除、fit-for-purpose |
| ADC 核心分析物 | LBA + LC-MS/MS | 总/偶联/游离分开；DAR/DLD |
| 寡核苷酸/AOC/LNP | 杂交 LC-MS/hELISA | 完整/总/游离；±Triton；PCR 不等于完整 |

详细选择树见 `references/complex-systems.md`；ICH M10 逐项失败与处理见 `references/ich-m10-validation-troubleshooting.md`。

### 常见问题路由

| 问题 | 先看 |
|---|---|
| 线性范围、LLOQ/ULOQ、曲线/加权 | `references/calibration-range.md` |
| LBA 方法开发/试剂/hook | `references/lba-development.md` |
| LC-MS/MS 前处理/内标/MRM | `references/lc-ms-development.md` |
| 小分子 pKa/logP/logD、色谱柱、流动相、质谱参数 | `references/small-molecule-lc-ms.md` |
| LC-MS 手册章节/稳定性/基质/残留/挑战分子 | `references/book-lc-ms-bioanalysis-handbook.md` |
| 免疫检测原理/ELISA/游离分析物/干扰 | `references/book-immunoassay-principles.md` |
| 进阶前处理 SLE/SALLE/在线 SPE/磷脂去除 | `references/sample-preparation-advanced.md` |
| HRMS/代谢物鉴定/反应性代谢物/手性 | `references/hrms-metabolite-id.md` |
| 临床 LC-MS/TDM/LDT/参考区间 | `references/clinical-lc-ms.md` |
| ICH M10 Q&A 具体解释 | `references/m10-qa.md` |
| ELISA 实操/包被/封闭/干扰 | `references/elisa-development.md` |
| 完整蛋白/抗体 LC-MS/top-down/PTM | `references/protein-lc-ms.md` |
| 数据完整性/Part 11/LIMS/自动化 | `references/data-integrity-automation.md` |
| 靶向生物标志物 LC-MS/替代基质 | `references/targeted-biomarker-lc-ms.md` |
| FDA/EMA/NMPA 区域法规差异 | `references/regional-regulatory.md` |
| AOC/双抗 专项 | `references/aoc-bispecific.md` |
| Hybrid LBA-LC-MS | `references/hybrid-lba-lc-ms.md` |
| ICH M10 验证项失败 | `references/ich-m10-validation-troubleshooting.md` |
| ADC 选哪些分析物/法规 | `references/adc-clinical-pharmacology.md` |
| ADC DAR/PK/毒性 | `references/adc-dar-pk-tox.md` |
| ADC free payload | `references/adc-free-payload.md` |
| 组织/游离/内源/寡核苷酸/LNP | `references/complex-systems.md`、`references/oligonucleotide-lnp.md` |
| DBS/组织/蛋白结合/双抗/基因细胞 | `references/broader-analytes.md` |
| 生物标志物 fit-for-purpose | `references/biomarker-fit-for-purpose.md` |
| ADA/免疫原性 | `references/immunogenicity-ada.md` |
| 关键试剂/方法转移/再验证 | `references/critical-reagents-and-transfer.md` |
| 其他常见问答 | `references/faq-index.md`（43 问） |

### 临床前 vs 临床（方法差异）

| 项目 | 临床前 | 临床 |
|---|---|---|
| 基质/种属 | 动物血浆、组织；多物种 | 人血浆/血清；固定抗凝剂 |
| 试剂 | 通用 anti-Fc/anti-ID 可用 | anti-ID/靶点捕获；临床级试剂 |
| 验证 | 探索性可 fit-for-purpose；GLP 全项 | 注册研究按 M10 全项 + ISR |
| 范围/干扰 | 高浓度、稀释多 | 个体差异、target/ADA 干扰 |
| 桥接 | 种属/基质变更做部分验证 | 平台/site 变更做交叉验证 |

## Procedure

### 1. 写 context of use（COU）

输出：一页 COU，含分析物、基质、范围、目的、法规环境、可接受误差。
完成标准：另一个人能只看 COU 就选平台，不需要猜。

### 2. 做分析物可行性

- 标准品/对照品：来源、纯度、分子量、盐型/水合、活性。
- 大分子：是否有配对抗体、表位是否冲突、种属交叉、靶点干扰。
- 小分子/ payload：稳定性、内酯/开环、光/热/pH 敏感、是否易与蛋白共价结合。
- ADC：总抗体、偶联抗体、总 payload、游离 payload 是否分开；DAR 是否随时间变化。

完成标准：列出“测不到/测不准”的三个最大风险，并给缓解方案。

### 3. 选平台并写理由

用上面的平台表；输出：首选平台、备选平台、为什么、失败后的切换条件。
完成标准：不能只写“因为我们有某某仪器”。

### 4. 方法优化（DOE，而不是单因素试错）

- LBA：抗体对浓度、包被/检测比例、封闭液、缓冲液、孵育时间、MRD、读数窗口。
- LC-MS：提取回收率、内标加入时机、色谱柱/梯度、离子源温度、MRM 碰撞能、残留。
- Hybrid：富集抗体/磁珠、洗脱条件、酶解/释放、LC-MS 读出。

完成标准：每个关键因素有可接受范围，不是只有一个“最佳点”。

### 5. 预验证（pre-validation）

至少做：校准曲线 3 条、QC 低/中/高、空白/零标、6 个个体基质、稀释线性、hook/平行性、短期稳定性。
完成标准：LLOQ 的 S/N、准确度、精密度达到目标；否则回到第 4 步。

线性范围（LLOQ/ULOQ、校准点、稀释、LBA vs LC-MS）设置见 `references/calibration-range.md`。

### 6. 正式验证（按 ICH M10 / 适用指南）

至少覆盖：

- 校准曲线与 QC（按平台）：LC-MS/MS 校准/QC ±15%（LLOQ ±20%）；LBA 校准 ±20%（LLOQ/ULOQ ±25%）、QC ±20%；两者均需至少 6 个非零水平、≥75% 校准标准、≥67% QC、每水平 ≥50%
- 准确度与精密度（至少 5 个浓度；按平台接受标准）
- 选择性/特异性（个体基质、溶血/脂血、target/ADA 干扰）
- 稀释线性、hook effect（LBA）、平行性（LBA）
- 基质效应/回收率（LC-MS）、MRD（LBA）
- 残留（≤20% LLOQ）
- 稳定性（室温、冻融、长期、Stock、全血/血浆）

完成标准：每个参数有原始数据、接受标准、偏差记录；不要只写“符合 M10”。

### 7. 样品分析与生命周期

- 分析批：校准曲线 + QC + 空白 + 样品；按 SOP 排布。
- 失败批：先判定是分析失败还是样品问题；不得任意重跑。
- 试剂批更换：做 bridging/再验证。
- 数据：审计追踪、原始图谱、积分参数、偏差、CAPA。
- ISR：真实样品再分析，至少 67% 在 ±20%；属样品分析，不是验证批。

完成标准：每批有 run acceptance 记录；每个异常有编号和结论。

### 8. 变更与再验证

- 新基质/种属：部分验证（选择性、提取、稀释、稳定性）。
- 新范围：校准曲线 + LLOQ/ULOQ + 稀释线性。
- 新平台：交叉验证（同批样品、Bland-Altman/回归），不能直接换算。
- 关键试剂换批：bridging；新 site：方法转移。

完成标准：变更前后有对比数据，接受标准预先定义。

## LBA 速查

### 格式

- **Sandwich**：大分子、多价抗原；捕获/检测抗体表位不冲突。
- **Competitive**：小分子、肽、只有一个表位；标准品与样品竞争。
- **Bridging**：ADA（但 ADA 方法另属免疫原性）。
- **Direct/indirect**：研究级、筛选；注册级优先 sandwich/competitive。

### 关键控制点

- **Hook effect**：高浓度信号下降；稀释后复测，报告 hook 阈值。
- **Target interference**：可溶性靶点遮蔽表位；加抗靶点抗体/酸解离/稀释。
- **Drug interference**：ADA/药物复合物；不要用总抗体方法代替游离药物。
- **MRD**：最低必需稀释；必须证明基质效应被消除。
- **曲线**：4PL/5PL；加权 1/y²； anchor points 不能当定量点。
- **试剂**：批间差异、偶联批号、抗原纯度；关键试剂要有 bridging。

## LC-MS/MS 速查

### 分析物策略

| 分析物 | 前处理 | 读出 |
|---|---|---|
| 完整蛋白 | 免疫富集/除高丰度 | 完整质量或特征肽 |
| 特征肽 | 变性/还原/烷基化/酶解 | 肽段 MRM |
| 游离 payload | 蛋白沉淀/SPE/LLE | payload MRM |
| 总 payload | 释放/酶解/酸解 | payload 或 linker-payload MRM |
| 生物标志物 | 视丰度而定 | 特征肽/完整蛋白 |

### 关键控制点

- **内标**：SIL 肽/蛋白优先；加样前加；必须与目标共洗脱。
- **LLOQ**：S/N ≥5，峰形可积分；空白无干扰。
- **酶解**：变性/还原/烷基化要完整；酶比例、时间、温度固定；做消化完全性检查。
- **色谱**：保留时间、峰形、残留；高有机相洗针。
- **基质效应**：柱后灌注 + 个体基质；IS 归一化后仍要评估。
- **源内碎裂**：linker-payload 可能落进 payload 通道；降低源温、优化 MRM、独立通道。
- **稳定性**：游离 payload 的 ex vivo 释放、内酯/开环、光/热敏感。

## ADC 专属口径（证据见 references/adc-dar-pk-tox.md）

### 核心分析物（含偶联 payload）

| 分析物 | 包含什么 | 不代表什么 |
|---|---|---|
| 总抗体 TAb | 所有抗体，含 DAR0 | 不等于偶联抗体，也不等于 ADC 暴露 |
| 偶联抗体 | DAR≥1 的抗体 | 通常不随 DAR 线性变化；不是摩尔 ADC 浓度 |
| 偶联 payload | 共价连接在抗体上的 payload 质量 | 不等于总 payload；不能回答游离 payload |
| 总 payload | 偶联 + 游离 | 不等于活性游离 payload |
| 游离 payload | 未偶联/已释放 | 不等于总 payload；受分离和稳定性影响 |
| DAR/DLD | 平均载荷 + 分布 | 平均 DAR 不等于分子均一性 |

### DAR 的三条硬规则

1. **平均 DAR 是加权平均**：`DAR_avg = Σ(n·A_n)/ΣA_n`；平均 4 可以是均一 4，也可以是 0 与 8 的混合。
2. **ADC/总抗体比值不是 DAR**：需要偶联 payload 摩尔浓度与完整 ADC 摩尔浓度；只有两个浓度不能算 DAR。
3. **DAR 会随体内时间下降**：脱偶联/降解使平均 DAR 下降、游离 payload 上升；基线 DAR 不能代替全程 DAR。

### PK/毒性证据（2025 meta-analysis）

Tang et al. 2025（*Cancer Metastasis Rev* 44:18；DOI 10.1007/s10555-024-10231-5）汇总 40 项临床试验、7,879 例、11 个 FDA 批准 ADC：

- 可裂解 linker 的 ≥3 级 composite AE 为 47%，不可裂解为 34%；调整 DAR 后，不可裂解 linker 仍与较低毒性相关。
- 较高 DAR 与较高 ≥3 级毒性概率相关；可裂解性与 DAR 存在交互。
- 较高系统游离 payload 浓度与较高 DAR 相关；作者认为游离 payload 是毒性的主要驱动因素（这是关联/解释，不是个体因果）。
- 证据边界：批准 ADC 的汇总、研究间异质性高、DAR 是产品级而非患者级、不能外推到未上市构建。

2018 年综述（Lucas et al., *Antibodies* 7:10；DOI 10.3390/antib7010010）补充：高 DAR 可能增加聚集、加快清除、改变 PK/PD；DAR 2–6 的 maytansinoid ADC 在临床前显示更好的治疗指数，但这是构建/模型依赖的结论。

### 生物分析策略

- **总抗体**：LBA 抗 IgG/抗 CDR；注意 DAR0 和药物干扰。
- **偶联抗体**：anti-payload 捕获 + anti-Fc/anti-ID 检测；测 DAR≥1；通常不随 DAR 线性变化。
- **偶联 payload**：anti-Fc/anti-ID 捕获 + anti-payload 检测，或 LC-MS；DAR 敏感；用 DAR 匹配标准品。
- **总 payload**：先释放（酶/酸/还原），再 LC-MS/MS；确认释放完全。
- **游离 payload**：先分离（SPE/LLE/蛋白沉淀），再 LC-MS/MS；避免 ex vivo 释放。
- **DAR/DLD**：HIC、native MS、LC-MS；高疏水 payload 用 HIC 可能分不开，需正交。

Free payload 的定义、分离、避免人为释放、ex vivo 释放证明和验证清单见 `references/adc-free-payload.md`。

## SOP / 运行接受

`references/sop-template.md` 是通用 SOP 模板，不是任何公司的受控文件。使用时必须替换为 site 的职责、仪器、试剂、偏差和质量体系。

最低 run acceptance：

- 校准曲线至少 6 个非零水平；≥75% 标准在平台标准内（LC-MS ±15%，LLOQ ±20%；LBA ±20%，LLOQ/ULOQ ±25%）。
- QC ≥67% 在平台标准内（LC-MS ±15%，LLOQ ±20%；LBA ±20%），每个水平至少 50%。
- 空白/零标低于 LLOQ；残留 ≤20% LLOQ。
- 稀释 QC 在平台标准内；ISR ≥67% 在 ±20%。
- 任何偏差有记录、影响评估和结论；不得“只重跑直到通过”。

> 这些是工作摘要，不是法规原文；以 ICH M10、FDA M10（2022）/2026 生物标志物指南、EMA 和当地监管最新版本为准。

## Pitfalls

1. **把 LBA 和 LC-MS 的数字直接对比**：一个测结合、一个测质量；分析物不同，不能互校。
2. **用总抗体代表 ADC**：总抗体包含 DAR0，暴露会偏高；ADC 清除可能更快。
3. **用平均 DAR 代表分布**：必须同时报 DLD；否则批次/时间点不可比。
4. **游离 payload 假高**：源内碎裂、linker 水解、分离不全、ex vivo 释放。
5. **LBA hook 未查**：高浓度信号下降，稀释后复测；不要只在高浓度报“低”。
6. **LC-MS 内标加得太晚**：提取/酶解损失无法校正；SIL 内标要尽早加。
7. **基质效应只看 pooled matrix**：个体基质、溶血/脂血、不同抗凝剂都要看。
8. **稳定性只做短期**：冻融、长期、全血/血浆、Stock、冻干都要覆盖。
9. **把 ADA 方法套 M10**：M10 不覆盖免疫原性；ADA 用专门指南。
10. **SOP 写成“符合法规”**：没有可执行步骤、接受标准、偏差路径和记录，等于没写。

## Verification

交付前逐项检查：

- [ ] 分析物定义清楚（总/偶联/游离/完整/DAR）
- [ ] 平台选择有理由，有备选和切换条件
- [ ] LBA 有抗体对、MRD、hook、target/ADA 干扰方案
- [ ] LC-MS 有内标、提取、色谱、MRM、基质效应、残留方案
- [ ] ADC 有总抗体/偶联抗体/总 payload/游离 payload/DAR 的口径
- [ ] 校准/QC/ISR/稀释/稳定性接受标准齐全
- [ ] SOP 有职责、步骤、偏差、记录、版本
- [ ] 每条关键结论有来源或标“待核”

## References

- `references/calibration-range.md` — 线性范围六步法、LBA/LC-MS 差异、校准点与稀释。
- `references/adc-free-payload.md` — ADC free payload 的口径、分离、防释放、验证与常见错误。
- `references/adc-clinical-pharmacology.md` — FDA 2024 ADC 指南、assay panel、何时可精简、DAR/游离 payload。
- `references/hybrid-lba-lc-ms.md` — hybrid 适用、workflow、酶解、验证与边界。
- `references/biomarker-fit-for-purpose.md` — biomarker 的 COU、fit-for-purpose、与 M10 的边界。
- `references/immunogenicity-ada.md` — ADA 分层、cut point、drug tolerance、与 PK 的关系。
- `references/critical-reagents-and-transfer.md` — 关键试剂换批、方法转移、交叉验证、再验证。
- `references/oligonucleotide-lnp.md` — 寡核苷酸/LNP-RNA 的平台选择与前处理。
- `references/faq-index.md` — 43 个常见问题的短答案与路由。
- `references/lba-development.md` — LBA 格式、试剂、曲线、基质、验证和排障。
- `references/lc-ms-development.md` — LC-MS/MS 分析物、内标、提取、色谱、MRM 和排障。
- `references/small-molecule-lc-ms.md` — 小分子 pKa/logP/logD、色谱柱/流动相选择、ESI/APCI、MRM、基质效应、残留和稳定性。
- `references/book-lc-ms-bioanalysis-handbook.md` — 《LC-MS 生物分析手册》章节地图：全血稳定性、前处理、LC/MS 最佳实践、IS、基质、残留、DBS、挑战分子。
- `references/book-immunoassay-principles.md` — 《免疫检测原理与应用》章节地图：格式、性能指标、游离分析物、校准、干扰、ELISA、LBA/ADA。
- `references/sample-preparation-advanced.md` — SLE/SALLE/在线 SPE/磷脂去除/特殊基质/挑战分子的前处理。
- `references/hrms-metabolite-id.md` — HRMS、代谢物鉴定、反应性代谢物、前药/酰基葡萄糖醛酸苷/N-氧化物/手性。
- `references/clinical-lc-ms.md` — 临床 LC-MS/TDM/LDT 验证、参考区间、IQC/EQA。
- `references/m10-qa.md` — ICH M10 Q&A 的具体解释（替代基质、5% 储备液、ISR 等）。
- `references/elisa-development.md` — ELISA/LBA 实操：抗体对、包被/封闭、缓冲液、曲线、干扰、验证。
- `references/protein-lc-ms.md` — 蛋白/抗体 LC-MS：bottom-up、middle-down、top-down、PTM、去卷积。
- `references/data-integrity-automation.md` — ALCOA+、21 CFR Part 11、LIMS、CDS、自动化与检查清单。
- `references/targeted-biomarker-lc-ms.md` — 靶向生物标志物 LC-MS：COU、替代基质、内源基线、FFP 验证。
- `references/regional-regulatory.md` — FDA/EMA/NMPA/PMDA 区域法规差异与申报检查。
- `references/aoc-bispecific.md` — AOC 的 OAR/游离 ASO 与双抗的完整/总/单臂/错配分析。
- `references/adc-dar-pk-tox.md` — ADC 核心分析物、DAR/DLD、PK/毒性和证据边界。
- `references/sop-template.md` — 通用生物分析 SOP 模板与运行检查清单（示例，不是受控文件）。
- `references/acceptance-and-troubleshooting.md` — 接受标准、偏差处理、LBA/LC-MS 排障矩阵。
- `references/ich-m10-validation-troubleshooting.md` — ICH M10 每个验证项的失败原因、排查与解决。
- `references/complex-systems.md` — 组织、游离、内源标志物、ADC、寡核苷酸/LNP 等复杂体系的选择树。
- `references/broader-analytes.md` — DBS、组织、游离药物/蛋白结合、双抗、基因/细胞治疗的扩展口径。

## External anchors

- ICH M10 Bioanalytical Method Validation: https://www.ich.org/page/bioanalytical-method-validation
- FDA M10 Bioanalytical Method Validation and Study Sample Analysis (2022): https://www.fda.gov/media/162903/download
- NMPA adoption of ICH M10 Q&As/FAQs (2023): http://english.nmpa.gov.cn/2023-07/04/c_940295.htm
- FDA Clinical Pharmacology Considerations for ADCs (2024): https://www.fda.gov/regulatory-information/search-fda-guidance-documents/clinical-pharmacology-considerations-antibody-drug-conjugates-guidance-industry
- FDA Bioanalytical Method Validation for Biomarkers (2026): https://www.fda.gov/regulatory-information/search-fda-guidance-documents/bioanalytical-method-validation-biomarkers
- FDA Immunogenicity Testing of Therapeutic Protein Products (2019): https://www.fda.gov/regulatory-information/search-fda-guidance-documents/immunogenicity-testing-therapeutic-protein-products-developing-and-validating-assays-anti-drug
- AAPS ADC bioanalysis white paper (2026): https://doi.org/10.1208/s12248-026-01268-1
- Hybrid immunocapture LC-MS review (2024): https://doi.org/10.4155/bio-2023-0261
- EBF protein LC-MS perspective (2025): https://pmc.ncbi.nlm.nih.gov/articles/PMC11801335/
- AOC bioanalytical approaches review: https://pubmed.ncbi.nlm.nih.gov/38607350/
- 21 CFR Part 11: https://www.ecfr.gov/current/title-21/chapter-I/subchapter-A/part-11
- Tang et al. 2025: https://doi.org/10.1007/s10555-024-10231-5
- Lucas et al. 2018: https://doi.org/10.3390/antib7010010
