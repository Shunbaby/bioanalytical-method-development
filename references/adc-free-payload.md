# ADC free payload 生物分析

> Free payload 不是“总 payload 的一小部分”。它是未共价偶联/已释放的小分子，可能仍结合血浆蛋白；必须定义操作口径。

## 1. 先定义“free”

| 口径 | 含义 | 方法 |
|---|---|---|
| 未共价偶联 payload | 未与抗体共价连接，可能结合蛋白 | 中性提取 + LC-MS/MS |
| 未结合蛋白 payload | 超滤/平衡透析后的游离部分 | 超滤/平衡透析 + LC-MS/MS；报 fu |
| 总 payload | 偶联 + 游离 | 释放 + LC-MS/MS |

报告必须写清楚是哪一种；不能把“未偶联”叫成“游离”。

## 2. 方法选择

- 首选 **LC-MS/MS**：小分子、质量特异、可区分 payload/linker-payload/代谢物。
- LBA 仅在有个高特异抗体且交叉反应可控时考虑；不能测 Total payload 代替 free。
- 分离：中性 pH 的 PPT/SPE/LLE；避免酸/碱水解、酶解、还原剂。
- 超滤：测“未结合蛋白”时用；注意膜吸附、平衡时间、温度、pH。

## 3. 不能人为释放 payload

- 避免酸沉淀/强酸复溶：酸敏 linker 会断。
- 避免蛋白酶/酯酶：可能释放 payload。
- 避免 DTT/TCEP：二硫键 linker 会断。
- 避免高温、长时间放置；冰上、快速离心、立即分装。
- 采血/离心/冻融也可能释放；冰镇管、规定抗凝剂、避免溶血。
- 先做 linker 稳定性预实验，再定前处理。

## 4. 证明“没有人为释放”

必须做：

1. 空白基质加高浓度 ADC，按完整流程处理，测 free payload。
2. 与零时/对照比较，证明无显著增加。
3. 加已知 free payload，证明回收率不受 ADC 影响。
4. 酸敏/酶敏 linker 分别做条件挑战。
5. 若无法证明，方法只能报“总可提取 payload”，不能报 free。

## 5. LC-MS/MS 条件

- 内标：SIL payload 优先；加样前加；与目标共洗脱。
- MRM：至少 2 通道；区分 payload 与 linker-payload。
- 源内碎裂：检查 linker-payload 是否落进 payload 通道；降低源温/改通道/色谱分离。
- 残留：高浓度总 payload 后空白 ≤20% LLOQ；单独 run、洗针、空白针。
- 基质效应：个体基质、溶血/脂血、抗凝剂；IS 归一化后仍要评估。

## 6. 稳定性与吸附

- 光/热/pH 敏感；低吸附管；避免反复冻融。
- 验证室温、冻融、长期、全血/血浆、Stock。
- 内酯/开环、酰基葡萄糖醛酸化物等代谢物单独考虑。

## 7. 验证清单

除常规准确度/精密度、选择性、基质效应、回收率、稀释、残留、稳定性、ISR 外：

- [ ] selectivity vs 偶联 payload：ADC 不贡献游离信号
- [ ] ex vivo release：采样/处理不产生假 free payload
- [ ] linker 稳定性挑战
- [ ] 超滤膜吸附/平衡（如测未结合）
- [ ] 代谢物干扰
- [ ] 同时间点与总抗体/偶联抗体/总 payload 同研究

## 8. 常见错误

1. 用总 payload 代替 free payload。
2. 酸沉淀把 linker 打断，free 假高。
3. 只测血浆，不测靶组织。
4. 用平均 DAR 推 free payload。
5. 不同研究/剂量/时间点拼接。
6. 不证明“无 ex vivo 释放”。
