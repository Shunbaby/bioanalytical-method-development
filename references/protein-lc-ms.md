# 蛋白/抗体 LC-MS：bottom-up、middle-down、top-down

> 工作手册，不是法规原文。蛋白 LC-MS 的“测到质量”不等于“定量正确”；先定分析物形态，再选定层级。

## 1. 三个层级

| 层级 | 测什么 | 优势 | 限制 |
|---|---|---|---|
| Bottom-up（特征肽） | 酶解后的替代肽 | 灵敏度高、QqQ 成熟、动态范围宽 | 丢失 PTM/完整信息；酶解不完全会偏 |
| Middle-down（亚基） | IdeS/还原后的 Fab/Fc/轻链 | 保留部分结构；可看亚基变体 | 亚基分离/去卷积要求高 |
| Top-down（完整蛋白） | 完整分子/蛋白形式 | 保留 PTM、截断、糖型、序列变体 | 灵敏度低；电荷态多；去卷积难 |

选择：**低浓度临床样本优先 bottom-up；要区分 proteoform/糖型/截断用 top-down 或 middle-down；两者常需正交。**

## 2. Bottom-up 工作流

1. 免疫富集（抗 IgG/抗 ID/靶点）或蛋白沉淀；内标尽早加。
2. 变性（尿素/GuHCl）、还原（DTT/TCEP）、烷基化（IAM）；避免过度烷基化。
3. 酶解：胰蛋白酶/Lys-C；酶:蛋白比例、时间、温度固定；做消化完全性检查。
4. 选唯一特征肽：BLAST 查同源性；避免漏切/修饰位点；必要时选多条肽。
5. SIL 肽/ SIL 蛋白内标；共洗脱；校正酶解和提取。
6. LC-MRM（QqQ）或 HRMS；监测至少 2 个跃迁。

关键：**酶解完全性**和**肽段唯一性**是方法成立的前提；只优化 MRM 不够。

## 3. Top-down / middle-down

- 完整蛋白用 HRMS（QTOF/Orbitrap）；QqQ 不适合完整大蛋白定量。
- 电荷态分布：可求和主要电荷态，或去卷积为中性质量；两种算法结果可能不同，需固定。
- 去卷积参数（质量范围、同位素宽度、阈值）要预先写进 SOP。
- 完整蛋白灵敏度受分子量/电荷态分散限制；已发表的完整 mAb HRMS 方法在非临床可到约 50 ng/mL 量级，但不是通用承诺。
- Middle-down：IdeS 切 IgG、DTT 还原，测 Fab/Fc/轻链；适合糖型、截断、ADC payload 分布。
- Native MS：保留非共价复合物；用于完整 AOC/ADC 形态，但灵敏度/溶剂兼容性更差。

## 4. 定量与特异性

- 线性范围、LLOQ、QC、稀释、残留、基质效应仍按 M10 思路验证。
- 内标：bottom-up 用 SIL 肽；top-down 用 SIL 蛋白/类似物；无同源内标时用结构类似物并说明。
- 选择性：目标蛋白 vs 内源同源蛋白、截断体、PTM 变体、药物-靶点复合物。
- 完整蛋白定量可能无法区分轻链交换/错配；需要肽图或 native MS 正交。
- 糖型/PTM 异质性会导致峰展宽/去卷积失败；先做正交表征。

## 5. 验证与边界

- M10 适用于蛋白药物 PK 方法；但完整蛋白方法的部分参数（如平行性）需按平台说明。
- 关键试剂（捕获抗体、酶、SIL 肽）换批要 bridging。
- 方法转移/平台变更（QqQ↔HRMS）要做交叉验证，不能直接换算。
- 临床低剂量/低浓度可能 LBA 或 hybrid 更合适；不要为了“新平台”牺牲灵敏度。

## 6. 常见错误

1. 只做 bottom-up，却声称能区分 proteoform。
2. 酶解不完全，替代肽不能代表总蛋白。
3. 特征肽不唯一，内源同源蛋白干扰。
4. 完整蛋白去卷积参数随手改，批间不可比。
5. 用 QqQ 做完整 mAb 定量，灵敏度/质量精度不足。
6. 不评估糖型/PTM 对定量信号的影响。
7. 平台变更不做交叉验证。

## 7. 来源

- EBF perspective on LC-MS(/MS) for biotherapeutic and biomarker proteins (2025), PMC11801335.
- Kang et al., *Biomed Chromatogr* 2020; DOI 10.1002/bmc.4633.
- *Handbook of LC-MS Bioanalysis* (Wiley 2013), protein/peptide chapters.
- Hybrid immunocapture LC-MS review (2024), DOI 10.4155/bio-2023-0261.
