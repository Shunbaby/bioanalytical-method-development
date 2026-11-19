# 寡核苷酸 / LNP-RNA 生物分析

## 1. 平台

| 平台 | 测什么 | 优点 | 限制 |
|---|---|---|---|
| Hybridization ELISA/MSD | 完整/总寡核苷酸 | 高灵敏、通量 | 不能区分截短代谢物；探针特异 |
| LC-MS（IP-RPLC） | 完整 + 代谢物 | 特异、宽范围 | 灵敏度较低；离子对试剂污染 |
| Hybridization LC-MS | 完整/部分代谢物 | 灵敏 + 特异 | 探针设计、通量、成本 |
| qPCR/RT-qPCR | 核酸序列 | 极高灵敏 | 不能区分完整/片段；LNP 封装/游离 |
| LC-FLD | 荧光标记 | 灵敏 | 需标记；不能测未标记 |

## 2. 选择

- ASO/siRNA PK：hybridization LC-MS 或 hybridization ELISA；代谢物用 LC-MS/HRMS。
- 组织/细胞内：提取 + hybridization LC-MS；注意回收和归一化。
- LNP-RNA：先破膜/±Triton 区分封装 vs 游离；RiboGreen 测总 RNA，不区分完整性。
- qPCR 只能回答“序列拷贝”，不能回答“完整/封装”。

## 3. 关键问题

### 提取

- 蛋白ase K/酚氯仿/SPE/杂交捕获；回收率、基质效应、短链丢失。
- siRNA 双链：需分离 AS/SS；LNA/PNA 探针提高 Tm。

### 色谱/质谱

- IP-RPLC（如 DMCHA/乙酸铵）改善保留；负离子 ESI；多电荷/钠 adduct。
- 代谢物 n-1/n-2 可能共洗脱/同分异构；HRMS 有帮助。

### LNP

- RiboGreen ±Triton：总 RNA vs 封装 RNA；
- 不能只用 qPCR 说“封装”；
- 脂质 LC-MS 需分离与内标；
- anti-PEG、补体/CARPA、dsRNA、翻译蛋白 ADA 单独考虑。

## 4. 常见错误

1. 用 qPCR 代替完整分子定量。
2. 不区分封装/游离 RNA。
3. 不查短链代谢物交叉。
4. 不看离子对试剂对 MS 的污染。
5. 把血浆方法直接套组织。
