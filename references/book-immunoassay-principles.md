# 参考书笔记：《免疫检测原理与应用》

> 本章是章节级摘要与工作映射，不是原书译文，也不替代原书。引用/申报时以原书和现行法规为准。

## 1. 书目信息

| 项目 | 信息 |
|---|---|
| 中文书名 | 《免疫检测原理与应用》 |
| 英文原书 | *The Immunoassay Handbook: Theory and Applications of Ligand Binding, ELISA and Related Techniques*，4th Edition |
| 原书主编 | David Wild（副主编 Rhys John、Chris Sheehan、Steve Binder 等） |
| 原书出版 | Elsevier，2013；1036 页；77 章；ISBN 978-0-08-097037-0 |
| 中文出版 | 人民卫生出版社，2021-01；871 页；ISBN 978-7-117-30352-1 |
| 中文主译 | 李金明、何建文 |
| 资源入口 | Elsevier：https://shop.elsevier.com/books/the-immunoassay-handbook/wild/978-0-08-097037-0 ；人卫电子书：http://books.ipmph.com/books/detail/2044509.shtml |

## 2. 全书结构（9 部分，77 章）

### Part 1 免疫检测基础

- 如何使用本书；免疫检测入门：免疫计量法（sandwich）、竞争法、均相法、定标。
- 性能指标：灵敏度、精密度/不精密度、特异性/交叉反应、准确度/偏倚。

### Part 2 免疫检测类型

- 竞争性与非竞争性（含 ELISA）原理；小分子非竞争法（anti-complex/选择性抗体）。
- 均相免疫检测；侧向层流；环境分析物；游离分析物；定性检测；传染病抗体；微球多重（Luminex xMAP）；微流控/微阵列；SPR；数字 ELISA；免疫组化/免疫细胞化学。

### Part 3 免疫检测组成

- 抗体：多克隆、单克隆、片段、双特异、嵌合/人源化、重组、偶联物。
- 信号系统：放射性、酶、荧光、时间分辨荧光、化学发光、生物发光、颗粒/纳米标记、亲和素-生物素、信号放大。
- 固相/分离系统；偶联方法；标准化与校准；校准曲线拟合（4PL/5PL、加权、锚点、主曲线）。

### Part 4 免疫检测开发

- ELISA 开发实用指南；方法评价；免疫检测干扰；IVD 产业中的开发。
- 干扰：异嗜性抗体、HAMA、类风湿因子、生物素、交叉反应、hook effect；识别/证明/预防。

### Part 5 免疫检测实施

- 样本采集、受试者准备、标本处理；实验室质量保证（IQC/EQA）；POCT；问题原因分析指南。

### Part 6 临床化学之外

- 兽医诊断；药物开发中的配体结合分析（LBA）：非临床/临床 PK、PD、免疫原性。

### Part 7 临床应用

- 甲状腺、肾上腺、骨/钙、生殖、妊娠、生长激素、糖尿病、血液、心脏标志物、肿瘤标志物、过敏、自身免疫、胃肠、肝炎、HIV、病毒/细菌/寄生虫、TDM、药物滥用。

## 3. 对 Skill D 最重要的 12 条

1. **先定格式**：大分子双表位用免疫计量（sandwich）；小分子/单表位用竞争法；均相法不需分离但易受基质干扰。
2. **游离分析物是独立问题**：free hormone/free drug 需要分离/计算，不能从总浓度推算；结合蛋白、温度、pH 都会改变 free。
3. **性能指标要分开报告**：灵敏度（LoD/LoQ）、精密度、特异性/交叉反应、准确度/偏倚；不能用一个“灵敏度”概括。
4. **校准曲线不是越复杂越好**：4PL/5PL + 适当加权；看回算偏差/残差；锚点不能当定量点；主曲线/校正品要区分。
5. **干扰要主动设计**：异嗜性抗体、HAMA、RF、生物素、交叉反应、hook；用阻断剂/稀释/换表位/正交方法。
6. **样本处理是分析前变量**：抗凝剂、采血管、血清分离胶、溶血/脂血、储存/冻融都能造成假低/假高。
7. **ELISA 开发是系统优化**：包被/检测浓度、封闭、缓冲液、孵育、洗涤、信号/背景；不要只调一个因素。
8. **方法评价要跟临床/既有方法比对**：初步筛选、成本效益、临床样本比对、最终评估；不是只做精密度。
9. **LBA 在药物开发中要 fit-for-purpose**：PK/PD/免疫原性目的不同；关键试剂、cut point、drug tolerance 要专门验证。
10. **ADA 不是 PK**：screening/confirm/titer/NAb；cut point、灵敏度、drug tolerance、干扰；不能套 M10 的校准曲线/QC。
11. **质量保证贯穿全过程**：IQC/EQA、批接受、趋势、偏差、CAPA；POCT 还要培训/质控。
12. **TDM/临床解释需要临床背景**：参考区间、敏感度/特异度、ROC、阳性/阴性预测值；分析结果不等于临床结论。

## 4. 与 D 现有文件的映射

- LBA 格式/抗体/曲线/基质/hook：`references/lba-development.md`
- ADA/免疫原性：`references/immunogenicity-ada.md`
- 生物标志物 fit-for-purpose：`references/biomarker-fit-for-purpose.md`
- 校准/加权/LLOQ：`references/calibration-range.md`
- 关键试剂/批间/转移：`references/critical-reagents-and-transfer.md`
- 小分子 LC-MS 与 LBA 的边界：`references/small-molecule-lc-ms.md`、`references/broader-analytes.md`

## 5. 使用边界

- 原书是免疫检测/临床检验的宽口径专著，不是 ICH M10 的替代；药物申报的 LBA/ADA 仍以 M10、FDA/EMA/NMPA 免疫原性指南为准。
- 临床章节用于理解分析物/干扰/参考区间，不用于给出具体患者诊断或剂量。
- 本章不提供原书全文；需要原文请通过出版社/图书馆合法获取。
