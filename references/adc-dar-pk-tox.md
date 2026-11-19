# ADC 的 DAR、PK 与毒性口径

> 来源：Tang et al. 2025 系统综述/meta 分析（DOI 10.1007/s10555-024-10231-5）；Lucas et al. 2018 综述（DOI 10.3390/antib7010010）。前者是临床汇总，后者含临床前/临床 PK 证据；两者都不能外推到未上市构建。

## 1. 核心分析物（五类 + 偶联 payload）

| 分析物 | 包含 | 不包含 | 方法 |
|---|---|---|---|
| 总抗体 TAb | 所有抗体，含 DAR0 | 不代表偶联抗体/ADC | LBA 抗 IgG/抗 CDR |
| 偶联抗体 | DAR≥1 | 通常不随 DAR 线性变化；不是摩尔 ADC | LBA anti-payload 捕获 + anti-Fc/anti-ID 检测 |
| 偶联 payload | 共价 payload 质量 | 不代表总/游离 payload | LBA anti-Fc/anti-ID 捕获 + anti-payload 检测；或 LC-MS |
| 总 payload | 偶联 + 游离 | 不代表活性游离 | 释放 + LC-MS/MS |
| 游离 payload | 未偶联/已释放 | 不代表总 payload | 分离 + LC-MS/MS |
| DAR/DLD | 平均载荷/分布 | 平均 DAR 不代表均一性 | HIC/native MS/LC-MS |

## 2. DAR 的定义与计算

```text
DAR_avg = Σ(n · A_n) / ΣA_n
```

- `A_n` 是载荷为 n 的物种峰面积/丰度；平均 DAR 是加权平均。
- 平均 DAR 4 可以是均一 DAR4，也可以是 DAR0 与 DAR8 的混合；必须报 DLD。
- `C_conjugated Ab / C_total Ab` 不是 DAR；它只反映“至少带一个 payload 的抗体比例”。
- DAR 需要偶联 payload 摩尔浓度与完整 ADC 摩尔浓度：`DAR = (C_conjugated payload/MW_payload) / C_ADC,molar`。
- 体内 DAR 会随脱偶联/降解下降；基线 DAR 不能代替全程。

## 3. DAR 测量方法

| 方法 | 得到 | 限制 |
|---|---|---|
| HIC | 平均 DAR + DLD | 高疏水 payload 可能分不开/峰重叠 |
| Native MS | 完整物种质量 | 离子化不完全会低估平均 DAR（约 10% 量级） |
| LC-MS（还原/酶解） | 重链/轻链载荷物种 | 需去卷积；偶联位点影响 |
| UV/吸光度 | 平均 DAR | 需要 payload/抗体消光系数；不能给分布 |
| 疏水相互作用/反相 | 分布 | 方法依赖；不能跨构建比较 |

## 4. DAR 与 PK

- 高 DAR 可能增加疏水性/聚集、被 MPS 识别、加快清除；但受 linker、偶联位点、payload、靶点影响。
- 2018 综述引用的 maytansinoid 数据：DAR 2–6 的清除相近、体内疗效较好；DAR 平均 10（7–14）清除更快、疗效下降。
- 这是**构建/模型依赖**的结论；不能把“DAR 越高越差”当普遍规律。
- 总抗体 t½ ≠ ADC t½；总抗体包含 DAR0，清除通常更慢。

## 5. DAR、linker 与毒性（2025 meta 分析）

- 40 项临床试验、7,879 例、11 个 FDA 批准 ADC。
- 可裂解 linker 的 ≥3 级 composite AE：47% vs 不可裂解 34%。
- 调整 DAR 后，不可裂解 linker 仍与较低毒性相关（any AE p=0.002）。
- 较高 DAR 与较高 ≥3 级毒性概率相关；可裂解性与 DAR 有交互。
- 较高系统游离 payload 浓度与较高 DAR 相关（p=0.043）；作者认为游离 payload 是主要驱动因素。
- 证据边界：汇总水平、研究间异质性高（I² 多 >50%）、DAR 是产品级、不能做个体预测；T-DXd 是极端例子，不是所有可裂解 linker 的代言。

## 6. 生物分析策略

### 总抗体

- 捕获：抗 IgG/抗 CDR；检测：抗 IgG。
- 会测 DAR0；不能代表 ADC。
- 注意 target/ADA 干扰。

### 偶联抗体

- anti-payload 捕获 + anti-Fc/anti-ID 检测。
- 测 DAR≥1 的抗体；通常不随 DAR 线性变化，不能当摩尔 ADC 浓度。
- 与总抗体的差值不是自动的 DAR0；不同 assay 标准品/表位不同，不能直接相减。
- 高 DAR 物种可能优先清除；结果不是“平均 DAR”。

### 偶联 payload

- anti-Fc/anti-ID/target 捕获 + anti-payload 检测；或 LC-MS。
- 信号随每个抗体的 payload 数增加（DAR-sensitive）；必须用 DAR 匹配标准品。
- 可换算 payload 质量/抗体摩尔；不能直接当游离 payload。

### 总 payload

- 释放：酶/酸/还原；确认释放完全。
- LC-MS/MS：payload 或 linker-payload 通道；避免源内碎裂。
- 不能回答游离 payload。

### 游离 payload

- 先分离（SPE/LLE/蛋白沉淀/超滤）；再加内标。
- 控制 ex vivo 释放：低温、抑制剂、快速处理。
- 内酯/开环、光/热敏感要单独验证。

### DAR/DLD

- HIC 是常用；高疏水 payload 需 native MS/LC-MS 正交。
- 报告平均 DAR + 分布 + 方法；不能只报平均值。
- 批次/时间点比较需同一方法、同一标准品。

## 7. 常见错误

1. 把总抗体当 ADC：暴露偏高，半衰期偏长。
2. 把 ADC/总抗体比值当 DAR：只说明偶联抗体比例。
3. 只报平均 DAR：隐藏 DAR0/高 DAR 尾部。
4. 用游离 payload 通道测总 payload：linker-payload 源内碎裂导致假高。
5. 跨构建比较 DAR：linker/payload/偶联化学/剂量都不同。
6. 把临床前 DAR-PK 结论直接外推到人。
7. 把 meta 分析的关联写成个体因果。
