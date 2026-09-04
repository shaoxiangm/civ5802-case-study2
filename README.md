# CIV5802 Case Study 2 — J19 / J20

2026-09-04 本地 sandbox03 原样备份。此次上传不修改模型、需求、信号参数，也没有重新运行仿真。

## 文件

- `sandbox03/SUMO_case_study_2_MIAO/`：四套 AM/PM baseline、signal optimization 工程及原有 corrected baseline 测试工程。
- `sandbox03/J19_J20_project_record.txt`、`sandbox03/_validation/`：历史工程记录和验证记录。
- `sandbox03/SUMO_case_study_2_MIAO.zip`：原文件夹已有的旧压缩包，作为历史文件保留；未假定它与当前工程相同。
- `sandbox03_snapshot_2026-09-04.zip`：此次重新打包的完整 sandbox03 快照。

## 重要：当前输出不是完整的正式结果

上传前核对当前 `outputs/queue.xml`：

| 场景 | 当前时间步数 | 最后记录时间 |
| --- | ---: | ---: |
| J19_J20_AM_baseline | 0 | 无有效时间步 |
| J19_J20_AM_signal_optimization | 346 | 345 s |
| J19_J20_PM_baseline | 315 | 314 s |
| J19_J20_PM_signal_optimization | 566 | 565 s |

历史记录中曾报告完整运行至 4200 s，但当前输出已不匹配该历史记录。不得将此备份中的短运行输出直接用于最终报告，亦不得把历史验证日志当成此次输出的验证证明。后续需要在保护备份的前提下重新完整运行并复核结果。

现有时间设置：需求 0–3600 s，仿真 0–4200 s；后 600 s 为排空期，不是前置预热期。最终分析应明确逐车指标的需求车辆范围与排队指标的时间窗口，避免将实际延迟插入至 3600 s 之后的需求车辆误删。

## 运行入口

使用 SUMO-GUI 打开相应场景目录内同名 `.sumocfg`。运行会写入该场景的 `outputs/`，请先备份现有结果。工程是否完整运行、输出是否有效，需要以新运行的 XML 和日志为准。

此仓库为私有项目备份，不代表已完成最终提交检查。报告 DOCX 和老师的原始 PDF 不在此次 sandbox03 备份范围内。
