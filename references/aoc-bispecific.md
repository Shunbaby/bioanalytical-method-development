# AOC 与双特异性抗体：专项分析策略

> 工作手册，不是法规原文。AOC 不是“ADC 换 payload”，双抗也不是“普通 mAb 加一个臂”；分析物必须按结构拆开。

## 1. AOC 的结构与分析物

AOC = 抗体 + linker + 寡核苷酸（ASO/siRNA）。siRNA 常见：sense 链共价偶联，antisense 链非共价杂交。

| 分析物 | 含义 | 方法 | 注意 |
|---|---|---|---|
| 总抗体 | 所有抗体，含未偶联 | LBA 抗 IgG/抗 Fc | 不代表 AOC 暴露 |
| 偶联抗体/OAR | 带寡核苷酸的抗体 | 原生 SEC-MS/SCX-MS、CZE-MS | OAR 不是平均 DAR；分布要看 |
| 偶联/关联 antisense | 仍与抗体结合的 payload | 免疫捕获 + 变性 IPRP-HRMS | 非共价，前处理可能解离 |
| 游离 antisense | 已释放 payload | 杂交捕获 + LC-MS/MS | 避免 proteinase K 造成假释放 |
| sense 链/linker | 偶联部分/代谢物 | IPRP-HRMS、LC-MS/MS | 与 antisense 分开 |
| 完整 AOC | 完整复合物 | 原生 SEC-MS/SCX-MS | 灵敏度低；用于形态/稳定性 |

## 2. AOC 的方法要点

- **OAR**：原生 SEC-MS/SCX-MS 或 CZE-MS；HIC/RP 对 AOC 常因电荷/疏水性差异不足而分不开。
- **游离 ASO**：杂交捕获 LC-MS/MS；有研究显示 proteinase K 消化可造成约 0.1% Fab-ASO 转化为游离 ASO，去除该步可避免假高。
- **IPRP-HRMS**：负离子模式，分离 sense/antisense；离子对试剂污染要管理。
- **qPCR**：测核酸拷贝，不等于完整 AOC；不能区分游离/偶联。
- **组织**：匀浆/提取效率、内源核酸干扰；血浆与组织分别验证。

## 3. 双特异性抗体的分析物

| 分析物 | 含义 | 方法 |
|---|---|---|
| 总抗体 | 所有含 Fc/框架的分子 | LBA 抗框架/抗 Fc |
| 完整双抗 | 两个臂都可结合 | 双靶点 bridging LBA；两个 anti-ID |
| 单价/单臂结合 | 只有一个臂可结合 | 单功能 LBA；靶点 + anti-IgG |
| 游离/未结合 | 未占位的臂 | 需分离/竞争；不能从总浓度推算 |
| 错配/半分子/游离臂 | 生产/体内异质性 | native MS、肽图、臂特异性 LC-MS |
| 域特异性 ADA | 针对某一臂/框架 | 域特异性 ADA 方法 |

## 4. 双抗方法策略

- **Intact assay**：两个靶点/两个 anti-ID 分别捕获/检测；证明两个臂同时可及。
- **Total assay**：抗框架/抗 Fc；包含无功能/错配分子。
- **Mono-functional assay**：一个靶点/anti-ID + anti-human IgG；测单臂结合，但不等于完整。
- **IA-LC-MS**：抗独特型/靶点富集 + 臂特异性特征肽；可区分臂、错配、截断。
- **Native MS/肽图**：看错配、半分子、PTM；不能替代定量。

## 5. 干扰与稳定性

- 可溶性靶点/ shed target 遮蔽表位；加抗靶点抗体、稀释、酸解离。
- 药物-靶点复合物可能被 LBA 识别为“总”或“游离”，取决于试剂。
- 双抗的臂交换/错配可能在体内发生；总抗体稳定不代表完整双抗稳定。
- ADA 可能针对一个臂；域特异性 ADA 比总 ADA 更有解释力。
- 前处理（DTT/酶/低温）可能改变臂间二硫键；要证明不人为解离。

## 6. 验证边界

- AOC/双抗没有单一“通用”指南；按 M10 的适用部分 + 模态专门指南 + COU。
- 总抗体、完整分子、游离 payload 是不同分析物；接受标准要分别预设。
- 关键试剂（抗 ID、杂交探针、捕获抗体）换批要 bridging。
- 方法转移/平台变更要交叉验证；不能把总抗体结果当完整 AOC。

## 7. 常见错误

1. 用总抗体代表 AOC/双抗。
2. 用 HIC/RP 测 AOC 的 OAR，峰分不开还硬积分。
3. 游离 ASO 前处理用 proteinase K，造成假释放。
4. qPCR 结果当完整 AOC 浓度。
5. 双抗只做总抗体，不证明两个臂可同时结合。
6. 不评估错配/半分子/游离臂。
7. ADA 只做总 ADA，不看域特异性。

## 8. 来源

- Bioanalytical approaches for AOC therapeutic proteins, PMID 38607350.
- Bioanalytical challenges in complex antibody modalities, PMID 33037499.
- *Bioanalysis in the Age of New Drug Modalities*, PMC8093172.
- Free ASO from Fab-ASO by hybridization LC-MS/MS, PMID 39041663.
- AOC native SEC-MS/SCX-MS application notes (Waters, 2025); CZE-MS AOC/ADC paper, PMID 37381585.
- FDA bispecific antibody development guidance; FDA 2024 ADC guidance.
