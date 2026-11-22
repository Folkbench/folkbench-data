# 公开快照字段字典

版本：1.0。机器可读的完整字段白名单见 [schema.json](schema.json)。新增字段先更新此文档和 CHANGELOG，再发布兼容消费者。时间使用 UTC，date 为北京时间日期。缺失值保持 null，不填零。

## snapshot.json 与每日导出接口

| 字段 | 类型 | 说明 |
| --- | --- | --- |
| `schema_version` | `1.0` | 导出契约版本，首期 1.0。 |
| `snapshot_version` | string | 来源内容摘要；时间和归档日期不参与内容去重。 |
| `date` | string | 北京时间归档日期；不代表所有记录的测量日期。 |
| `published_at` | string | 该归档或来源行的实际发布时间，UTC。 |
| `source_collected_at` | string | 来源采集时间，UTC。 |
| `policy` | `public-snapshot-includes-display-samples-and-existing-placement` | 固定公开边界：沿用现行排序。 |
| `boards` | array<object> | 来源已公开的同名标识、名称或计数。 |
| `rankings` | array<object> | 来源已公开的同名标识、名称或计数。 |
| `integrity` | array<object> | 来源已公开的同名标识、名称或计数。 |
| `models` | array<object> | 来源已公开的同名标识、名称或计数。 |
| `stations` | array<object> | 来源已公开的同名标识、名称或计数。 |

## rankings

| 字段 | 类型 | 说明 |
| --- | --- | --- |
| `date` | string | 北京时间归档日期，与完整快照 date 相同，不参与来源内容去重。 |
| `model_id` | string | 来源已公开的同名标识、名称或计数。 |
| `model_name` | string | 来源已公开的同名标识、名称或计数。 |
| `station_slug` | string | 来源已公开的同名标识、名称或计数。 |
| `station_name` | string | 来源已公开的同名标识、名称或计数。 |
| `channel_id` | string | 来源已公开的同名标识、名称或计数。 |
| `group_name` | string | 来源已公开的同名标识、名称或计数。 |
| `position` | integer | 来源顺序，不按综合分重新排序。 |
| `rank_published` | integer / null | 主站公布的名次；未排名为 null。 |
| `evidence_status` | string | 原样保留来源标签。 |
| `catalog_only` | boolean | 主站是否标记为仅收录。 |
| `release_kind` | `published` / `illustrative` | 来源发布类别，published 或 illustrative。 |
| `overall_bps` | integer / null | 分数单位 bps；来源不是 published 时为 null。 |
| `availability_bps` | integer / null | 分数单位 bps；来源不是 published 时为 null。 |
| `connectivity_bps` | integer / null | 分数单位 bps；来源不是 published 时为 null。 |
| `stability_bps` | integer / null | 分数单位 bps；来源不是 published 时为 null。 |
| `latency_p95_ms` | integer / null | 来源已公开的同名标识、名称或计数。 |
| `status_windows` | array<string> | 公开状态窗口；JSON 为数组，CSV 用 | 连接，不强补缺失窗口。 |
| `sample_size` | integer / null | 公开样本数；缺失为 null。 |
| `input_price` | number / null | 公开输入价格；未发布为 null。 |
| `output_price` | number / null | 公开输出价格；未发布为 null。 |
| `price_currency` | string / null | 输入价币种。 |
| `price_unit` | string / null | 输入价单位。 |
| `output_price_currency` | string / null | 输出价币种，独立于输入价。 |
| `output_price_unit` | string / null | 输出价单位，独立于输入价。 |
| `price_source` | string / null | 公开目录的价格来源。 |
| `price_recorded_at` | string / null | 公开价格记录时间。 |
| `measured_at` | string / null | 来源公开的测量时间，不补造。 |
| `snapshot_version` | string | 来源内容摘要；时间和归档日期不参与内容去重。 |
| `method_version` | string | 来源方法/发布投影版本，详见 METHODOLOGY.md。 |
| `observed_window` | string | 来源窗口原文；不强行解析为统一 24 小时。 |
| `published_at` | string | 该归档或来源行的实际发布时间，UTC。 |

## integrity

| 字段 | 类型 | 说明 |
| --- | --- | --- |
| `run_id` | string | 主站已公开的汇总标识；不是新增的原始运行记录。 |
| `model_id` | string | 来源已公开的同名标识、名称或计数。 |
| `station_slug` | string | 来源已公开的同名标识、名称或计数。 |
| `group_name` | string / null | 来源已公开的同名标识、名称或计数。 |
| `client_mode` | string | 来源已公开的同名标识、名称或计数。 |
| `agree` | integer | 公开的一致题数。 |
| `total` | integer | 公开的可比较题数；不是请求数。 |
| `input_tokens_min` | integer / null | 公开输入 Token 最小值；缺失为 null。 |
| `input_tokens_max` | integer / null | 公开输入 Token 最大值；缺失为 null。 |
| `reasoning_median` | number / null | 公开思考 Token 中位数，允许小数。 |
| `identified_model_id` | string / null | 公开模型指纹识别结果；缺失为 null。 |
| `probe_keys` | array<string> | 仅匿名公开题目 ID（folk-加8位十六进制）；不含私有题目 key。 |
| `measured_at` | string / null | 来源公开的测量时间，不补造。 |

## models

| 字段 | 类型 | 说明 |
| --- | --- | --- |
| `id` | string | 来源已公开的同名标识、名称或计数。 |
| `name` | string | 来源已公开的同名标识、名称或计数。 |
| `vendor_id` | string | 来源已公开的同名标识、名称或计数。 |
| `vendor_name` | string | 来源已公开的同名标识、名称或计数。 |
| `family` | `language` / `image` / `video` | 来源已公开的同名标识、名称或计数。 |
| `status` | `measured` / `pending` | 来源已公开的同名标识、名称或计数。 |
| `station_count` | integer | 来源已公开的同名标识、名称或计数。 |
| `official_price` | object / null | 官方参考价格对象；没有已公开参考价时为 null。 |

### official_price

| 字段 | 类型 | 说明 |
| --- | --- | --- |
| `currency` | string | 来源已公开的同名标识、名称或计数。 |
| `unit` | string | 来源已公开的同名标识、名称或计数。 |
| `input` | number / null | 来源已公开的同名标识、名称或计数。 |
| `output` | number / null | 来源已公开的同名标识、名称或计数。 |
| `cache_read` | number / null | 缓存读取参考价格。 |
| `source_label` | string | 公开来源名称。 |
| `source_url` | string / null | 公开参考来源 URL，移除查询参数和 fragment，拒绝商业跳转。 |
| `verified_at` | string | 公开参考价格的核验时间。 |

## stations

| 字段 | 类型 | 说明 |
| --- | --- | --- |
| `slug` | string | 来源已公开的同名标识、名称或计数。 |
| `name` | string | 来源已公开的同名标识、名称或计数。 |
| `profile_url` | string | 无参数的主站档案地址，数据文件中不加 UTM。 |
| `listing_status` | `tested` / `catalog_only` | 来源 tested 表示常规收录，catalog_only 表示仅收录；不是额外的实测保证。 |
| `measurement_status` | `source_tagged` / `not_available` | source_tagged 表示榜单有来源实测标签；not_available 表示没有此类行。 |
| `first_listed_at` | string / null | 公开资料中的首次收录日期；未知为 null。 |
| `data_security_level` | integer | 来源公开等级 0–4，须结合有效性读取。 |
| `data_security_validity` | `current` / `expired` / `not_verified` | current / expired / not_verified。 |
| `checked_at` | string / null | 公开安全核验日期。 |
| `subject_present` | `yes` / `no` / `unspecified` | 主体信息存在状态，不含主体名称、材料或联系方式。 |
| `domestic_payment` | `yes` / `no` / `unspecified` | 公开境内支付支持状态。 |
| `overseas_payment` | `yes` / `no` / `unspecified` | 公开境外支付支持状态。 |
| `invoice` | `yes` / `no` / `unspecified` | 公开发票支持状态。 |
| `customer_service` | `yes` / `no` / `unspecified` | 公开客服支持状态，不导出联系方式。 |
| `refund` | `supported` / `not_supported` / `conditional` / `contact_required` / `unspecified` | 公开退款支持状态。 |

## boards

| 字段 | 类型 | 说明 |
| --- | --- | --- |
| `model_id` | string | 来源已公开的同名标识、名称或计数。 |
| `snapshot_version` | string / null | 来源内容摘要；时间和归档日期不参与内容去重。 |
| `method_version` | string / null | 来源方法/发布投影版本，详见 METHODOLOGY.md。 |
| `observed_window` | string / null | 来源窗口原文；不强行解析为统一 24 小时。 |
| `published_at` | string / null | 该归档或来源行的实际发布时间，UTC。 |
| `rows` | integer | 来源已公开的同名标识、名称或计数。 |

## manifest.json

包含 schema_version、snapshot_version、date、published_at、source_collected_at、exported_at、sources（与 boards 相同）及 files 数组。每个 files 项包含 path（本目录文件名）、sha256（该文件最终字节的 SHA-256）和 rows（数据行数）。manifest 不对自身计算哈希。exported_at 固定为快照发布时间，使重试产生相同字节。

## CSV

rankings.csv 与 integrity.csv 对应同名 JSON 数组，字段顺序固定。UTF-8 BOM；空单元格表示 null，布尔值为 true/false，数组用 | 连接。危险公式前缀的文本加单引号保护；只在比对这些文本时移除保护前缀。

## 边界

榜单包括全部公开行，未验证、仅收录不删除。探针只包含主站已公开汇总，不增加数据库原始运行明细、题面、回答、私有基线或商户联系方式。站点来自公开目录，不从榜单拼凑。商业关系字段不在首期契约中。
