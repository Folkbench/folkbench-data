# Folkbench Data · AI API 中转站公开快照

每日归档 Folkbench 主站公开展示的榜单、模型、站点目录和探针汇总。

**排序沿用主站规则，包含合作档位与运营加分。这里提供公开快照，不是原始运行记录，也不能用来复算评分。**

[在线榜单](https://folkbench.com/rankings?utm_source=github&utm_medium=data-repo&utm_campaign=folkbench-data&utm_content=nav-rankings) · [公开探针汇总](https://folkbench.com/arena?utm_source=github&utm_medium=data-repo&utm_campaign=folkbench-data&utm_content=nav-arena) · [方法说明](https://folkbench.com/methodology?utm_source=github&utm_medium=data-repo&utm_campaign=folkbench-data&utm_content=nav-method)

## 文件

首份归档发布后，`latest/` 包含：

| 文件 | 内容 |
| --- | --- |
| rankings.json / rankings.csv | 全部公开榜单行，包含仅收录与未验证行 |
| integrity.json / integrity.csv | 主站当前公开的探针汇总；不含原始运行记录 |
| models.json | 公开模型目录与官方参考价格 |
| stations.json | 与主站公开目录相同范围的站点及安全等级 |
| snapshot.json | 版本化完整快照，与每日导出接口一致 |
| manifest.json | 文件 SHA-256、行数、来源版本和发布时间 |

历史目录：`daily/YYYY/MM/DD/`。JSON/CSV 字段见 [SCHEMA.md](SCHEMA.md)，计算和排序边界见 [METHODOLOGY.md](METHODOLOGY.md)。首次启用前不放占位数据。

## 阅读数据

- `position` 是来源顺序，`rank_published` 是来源公布的名次；不能按综合分重新排序后声称复现主站。
- `evidence_status` 原样保留主站来源标签。
- 分数单位为 bps：10000 = 100%。未知数值保留 null，不能填成零。
- 探针只表示快照收录的最新公开汇总，不表示过去 24 小时的执行次数。`probe_keys` 只有匿名公开题目 ID，不公开题面、回答或私有基线。
- 不同模型保留各自的窗口与版本。导出时间、归档日期与测量时间不是同一概念。

## 更新与更正

主站每天北京时间 20:30 尝试生成快照，分发任务随后归档。GitHub 调度可能延迟；以 manifest 中的实际时间为准。相同来源内容跳过，失败时保留上次成功结果，因此不是每个日期都有文件。

历史日期目录只新增，不覆盖。更正以 `corrections/YYYY-MM-DD.md` 追加，并更新 CHANGELOG；需要修订数据时另发有独立版本的新归档，不覆盖旧文件。每月 1 日发布上一完整月份的实际归档合集，缺失日期不补造。

CSV 使用 UTF-8 BOM；数组以 `|` 分隔。可能触发表格公式的文本单元格前加单引号，数值不变。程序比对时仅对这些文本单元格去掉保护前缀。JSON 是无损结构化表示。

## 引用与许可

数据许可为 [CC BY 4.0](LICENSE)。引用格式：

> 数据来源：Folkbench，folkbench-data，归档日期 YYYY-MM-DD，快照 snapshot_version，CC BY 4.0。

请附仓库链接。中转站名称、Logo 和第三方材料不随数据许可授权。数据不保证服务未来表现。

[提交纠错](https://folkbench.com/corrections?utm_source=github&utm_medium=data-repo&utm_campaign=folkbench-data&utm_content=corrections) · [申请收录](https://folkbench.com/vendor-join?utm_source=github&utm_medium=data-repo&utm_campaign=folkbench-data&utm_content=vendor-join) · [产品与客户端](https://github.com/Folkbench/folkbench)

## 使用这份数据的站点

以下六个公开快照视图每天只读取本仓库的已归档快照生成；排序按站点规则，含合作档位与运营加权。

- [AI 中转站排行](https://folkbench.github.io/relay-rank/)：按模型的每日公开快照与历史名次
- [中转站检测周报](https://folkbench.github.io/integrity-weekly/)：模型身份探针的每周汇总
- [AI 中转站对比](https://ai-relay-bench.github.io/)：同一模型在各中转站的并排对比
- [AI API 价格对比](https://aiapi-rank.github.io/)：中转站公开标价与官方参考价
- [AI 中转站大全](https://ai-zhongzhuan.github.io/)：站点目录、公开资料与新手指南
- [模型检测快照](https://ai-model-check.github.io/)：每日模型身份探针汇总

## English

Folkbench Data archives public snapshots of the main site's rankings, catalog and published probe summaries. Existing ordering includes partnership tiers and operator bonuses. These files are published summaries, not raw runs, and cannot be used to recompute scores. Historical archives are immutable. Private runs, prompts, answers and credentials are excluded. Data is licensed under CC BY 4.0; names, logos and third-party materials are excluded.
