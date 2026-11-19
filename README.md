# 生物分析方法开发（LBA + LC-MS/MS）

一个面向生物分析（bioanalysis）的 Agent Skill，覆盖 **LBA、LC-MS/MS 和 hybrid LBA-LC-MS** 三条平台路线，以及 ADC 的 DAR、游离 payload、SOP 模板、方法验证和放行检查。

- **版本**：0.2.6
- **格式**：Agent Skills（`SKILL.md` + `references/`）
- **语言**：中文为主，保留英文术语和法规名称
- **许可**：MIT，见 `LICENSE`

## 适用场景

- 为某个分析物选择 LBA、LC-MS/MS 或 hybrid 平台，并说明理由。
- 设计 LBA 方法：抗体配对、标准品、校准曲线、基质、hook、选择性。
- 设计 LC-MS/MS 方法：特征肽、完整蛋白、游离 payload、内标、提取、色谱、MRM。
- 审核 ADC 生物分析策略：总抗体、偶联抗体、总 payload、游离 payload、DAR/DLD。
- 起草或审核生物分析 SOP、运行接受标准、偏差处理、ISR 和数据完整性检查。
- 排查低信号、高背景、hook、基质效应、残留、精密度差、稳定性失败。

## 不适用

- 替代专用 ADA/免疫原性方法。
- 临床剂量选择或法规申报结论。
- 没有明确分析物的“帮我建个方法”。

本 skill 不是法规原文的替代品。申报前以 **ICH M10、FDA/EMA/NMPA 现行指南**和 site SOP 为准。

## 安装

### Hermes

```bash
git clone <repo-url> ~/.hermes/skills/research/bioanalytical-method-development
```

如果已经有该目录，改用复制：

```bash
cp -a bioanalytical-method-development ~/.hermes/skills/research/
```

安装后在 Hermes 中确认：

```bash
hermes skills list | grep bioanalytical-method-development
```

或在会话中加载：

```text
skill_view(name='bioanalytical-method-development')
```

### 其他 Agent Skills 主机

把整个目录放到主机的 skills 扫描路径下，确保 `SKILL.md` 位于该 skill 目录根部。不同主机的路径不同，以其文档为准。

## 目录

```text
bioanalytical-method-development/
├── SKILL.md
├── references/
│   ├── lba-development.md
│   ├── lc-ms-development.md
│   ├── ich-m10-validation-troubleshooting.md
│   ├── adc-free-payload.md
│   ├── adc-dar-pk-tox.md
│   ├── calibration-range.md
│   ├── sample-preparation-advanced.md
│   └── ...（共 30 个专题）
├── README.md
└── LICENSE
```

## 参考文件

`references/` 下共 30 个专题文件，覆盖：

- LBA 与 LC-MS/MS 方法开发
- ICH M10 验证与排障、Q&A
- ADC 的 DAR、总/偶联/游离 payload、临床药理
- 小分子 LC-MS、蛋白 LC-MS、HRMS 代谢物鉴定
- 寡核苷酸/AOC/LNP、双抗、生物标志物
- 免疫原性/ADA、关键试剂与方法转移
- 数据完整性与自动化、区域法规
- 两本 LC-MS/免疫分析专著的章节级笔记

## 版本与许可

MIT License。引用或再分发时请保留 `LICENSE` 和来源说明。

## 维护

修改 `SKILL.md` 或 `references/` 后：

```bash
git add .
git commit -m "Update bioanalytical-method-development v0.2.6"
git push
```

如果要把版本号一起更新，先改 `SKILL.md` frontmatter 的 `version` 字段，再提交。
