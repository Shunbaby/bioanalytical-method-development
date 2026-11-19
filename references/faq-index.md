# 常见问题索引（先查这里）

> 用法：先找问题；答案给结论和下一步，细节点进对应 reference。不是法规原文。

## A. 平台选择

**1. LBA 和 LC-MS/MS 怎么选？**
LBA 测“结合/活性”，LC-MS 测“质量/结构”。大分子有可靠抗体对优先 LBA；小分子/游离 payload 优先 LC-MS；需要质量特异性但又有富集需求用 hybrid。详见 `SKILL.md` 平台表。

**2. 什么时候用 hybrid LBA-LC-MS？**
没有好抗体对、LBA 受 target/ADA 干扰、需要区分完整/片段/修饰，或低丰度蛋白需富集时。详见 `references/hybrid-lba-lc-ms.md`。

**3. 小分子可以用 LBA 吗？**
可以，但通常不如 LC-MS；只有高特异抗体且交叉反应可控时才考虑。游离 payload 首选 LC-MS/MS。

**4. 总浓度和游离浓度怎么选？**
先定义“游离”是未共价偶联，还是未结合蛋白；两者前处理不同。游离需先分离，不能从总浓度推算。详见 `references/complex-systems.md`。

**5. 抗体药和 ADC 的“浓度”一样吗？**
不一样。ADC 至少有六种口径：总抗体（含 DAR0）、偶联抗体（DAR≥1）、偶联 payload、总 payload、游离 payload、DAR/DLD；抗体药通常只有抗体浓度。详见 `references/adc-clinical-pharmacology.md`。

**6. DAR 用什么方法？**
HIC 看分布，native MS 看完整质量，LC-MS 看 payload/肽段；平均 DAR 不能代替 DLD。详见 `references/adc-dar-pk-tox.md`。

**7. 生物标志物能套 M10 吗？**
不能直接套。FDA 2026 要求 fit-for-purpose；监管决策/关键终点才接近 full validation。详见 `references/biomarker-fit-for-purpose.md`。

**8. ADA 能套 M10 吗？**
不能。ADA 用免疫原性指南，分层 screening/confirm/titer/NAb。详见 `references/immunogenicity-ada.md`。

## B. 范围、曲线、验证

**9. 线性范围怎么定？**
先用 Cmax/Ctrough 定 LLOQ/ULOQ，再用宽范围 scouting 验证；高/低端留 2–5 倍余量。详见 `references/calibration-range.md`。

**10. LLOQ 怎么定？**
低于预期最低浓度（trough/终末相）；LC-MS 要求 S/N≥5、峰形可积分；LBA 最低校准品准确度/精密度达标。不是越低越好。skill 明确给出 LC-MS 的 S/N≥5，不要声称 skill 没写。

**11. ULOQ 怎么定？**
高于预期最高浓度（Cmax/早期相）；LBA 必须低于 hook 阈值；LC-MS 无残留/饱和；太高就验证稀释。

**12. 校准曲线要几个点？**
至少 6 个非零水平，常 6–8 个，对数间隔，含 LLOQ/ULOQ 和决策点；标准品独立配制。LLOQ/ULOQ 的接受限比中间点更宽（LC-MS LLOQ ±20%；LBA LLOQ/ULOQ ±25%），不是更严格。

**13. 4PL/5PL、加权怎么选？**
LBA 常用 4PL/5PL；LC-MS 常用线性/二次。加权常用 1/y² 或 1/x²；看回算偏差和残差，不只看 R²。

**14. 准确度/精密度接受标准？**
LC-MS：±15%（LLOQ ±20%）；LBA：±20%（LLOQ/ULOQ ±25%）。QC 至少 67% 在范围内，每水平 ≥50%。

**15. 选择性 vs 特异性？**
选择性：空白/个体基质中能否准确定量；特异性：结构类似物/代谢物/靶点是否干扰。两者都要做。

**16. 基质效应 vs 回收率？**
基质效应是离子化被抑制/增强；回收率是提取损失。回收率低但稳定可接受；基质效应要看 IS 归一化后的个体差异。

**17. Carryover 怎么控？**
高浓度后空白 ≤20% LLOQ；洗针、空白针、改管路/进样量。LBA 还要查洗板和孔间污染。

**18. 稀释线性 vs hook？**
稀释线性看高浓度稀释后是否准；hook 看高浓度信号是否反而下降。LBA 高浓度先查 hook，LC-MS 查残留/基质。

**19. 稳定性要做哪些？**
室温、冻融、长期、Stock/工作液、全血/血浆；游离 payload 还要做 ex vivo 释放。

**20. ISR 怎么做？**
真实样品重复分析；至少 67% 两次结果差 ≤20%；覆盖 Cmax、消除相、异常/稀释样品。ISR 是 study sample analysis，不是 validation batch；样本量按 M10 要求，失败要调查，不要挑样。

**21. 平行性是什么？**
稀释后响应/浓度与稀释倍数成比例；LBA 看平行性，LC-MS 看稀释线性；不平行常提示 hook/基质/抗体问题。

**22. 关键试剂换批怎么办？**
Minor 做一次对比；Major（新克隆/新供应商/生产方法变）至少 3 批对比，必要时部分验证；保留旧批做 bridging。详见 `references/critical-reagents-and-transfer.md`。

**23. 方法转移怎么做？**
同批 QC + 真实样品、平行设计、预定标准；平台/ site 变更要做交叉验证，不能只跑 QC。

**24. 什么时候做部分验证？**
新基质/种属/范围/平台/关键试剂 major 变更；做受影响参数，不是全套重做，但要有理由。

## C. ADC

**25. 总抗体和偶联抗体有什么区别？**
总抗体含 DAR0；偶联抗体只测 DAR≥1。总抗体暴露通常更高、t½ 更长；不能拿总抗体代替 ADC。

**26. 偶联抗体 LBA 是不是 DAR-sensitive？**
通常不是。anti-payload 捕获 + anti-Fc 检测测的是“至少带一个 payload 的抗体”，不随 payload 数线性增加；偶联 payload assay 才 DAR-sensitive。

**27. 偶联抗体和偶联 payload 怎么区分？**
偶联抗体测“带 payload 的抗体分子”；偶联 payload 测“抗体上 payload 的质量/数量”。前者通常不 DAR-sensitive，后者 DAR-sensitive。

**28. 平均 DAR 和 DLD 有什么区别？**
平均 DAR 是加权平均；DLD 是分布。平均 4 可以是均一 4，也可以是 DAR0+DAR8 混合；必须报分布。

**29. Free payload 怎么定义？**
未共价偶联/已释放的小分子，可能仍结合血浆蛋白；若测“未结合蛋白”，需超滤/平衡透析并报 fu。详见 `references/adc-free-payload.md`。

**30. 怎么证明没有人为释放？**
空白基质加高浓度 ADC，按全流程处理，证明 free payload 不显著增加；再加已知 free payload 证明回收不受影响。

**31. 总 payload 怎么测？**
先释放（酶/酸/还原），再 LC-MS/MS；证明不同 DAR 下释放完全；不能直接当游离 payload。

**32. 组织里的 payload 怎么归一化？**
匀浆后按蛋白/重量归一化；验证匀浆效率/均匀性；游离 payload 还要防匀浆过程释放。详见 `references/complex-systems.md`。

**33. Free 和 protein-bound 怎么区分？**
超滤/平衡透析测未结合部分；注意膜吸附、平衡时间、温度/pH；不要用总浓度乘 fu 反推 free。

## D. 复杂体系

**34. 寡核苷酸用什么平台？**
Hybridization ELISA/MSD、LC-MS（IP-RPLC）、hybridization LC-MS、qPCR；按完整/总/代谢物选择。详见 `references/oligonucleotide-lnp.md`。

**35. LNP-RNA 怎么测？**
RiboGreen ±Triton 区分总/封装 RNA；qPCR 不能区分封装/游离；脂质 LC-MS 需分离和内标；还要看 anti-PEG/补体/dsRNA。

**36. 双抗/多抗怎么测？**
至少测完整/活性形式；可能需要总、bound、unbound 多个 assay；用两个靶点/anti-ID 表位设计。详见 `references/complex-systems.md`。

**37. 微量/ DBS 可以吗？**
可以，但要验证血细胞比容、卡纸/提取回收、稳定性、桥接；不能直接把血浆方法缩短体积。

## E. 运行与异常

**38. 样品高于 ULOQ 怎么办？**
用已验证稀释倍数稀释；加 dilution QC；不要外推曲线。

**39. 样品低于 LLOQ 怎么办？**
报告 <LLOQ；不要填 0 或 LLOQ/2；若大量低于 LLOQ，说明范围/灵敏度不足。

**40. 批失败能不能重跑？**
先判定分析失败 vs 样品失败；按 SOP 预设规则重跑；不得挑点/挑样直到通过；记录原始值/重跑值/选择理由。

**41. 临床前和临床方法有什么不同？**
基质/种属、灵敏度、试剂（anti-ID vs 通用 anti-Fc）、法规环境不同；临床前方法不能直接桥接到临床而不做交叉验证。

**42. 个体基质/批次数要多少？**
按 M10/平台：LC-MS 选择性常 6 个个体基质，LBA 常 10 个；准确度/精密度两者均至少 5 个浓度；LBA 常 6 批、LC-MS 常 3 批；以现行指南/协议为准。

**43. 这个 skill 不能回答什么？**
临床剂量选择、ADA cut point 统计/申报结论、诊断试剂注册、未公开产品数据不能回答；ADA 的边界和分层策略可回答。遇到超范围问题要拒答或转专家。
