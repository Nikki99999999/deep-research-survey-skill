# 证据卡与跨阶段交接

为每个可核查断言分配稳定 ID，例如 `E001`。同一断言在报告、写作提纲和幻灯片中沿用该 ID；改写事实范围或统计口径时另建卡片，并说明关系。短任务可直接在报告附录列卡；长任务可保存任务专属登记文件。

## 最小字段

| 字段 | 记录什么 |
|---|---|
| `id` | 在本次研究中唯一、后续交接保持不变的标识 |
| `claim` | 一句可核查的事实，或明确标注为推断的判断 |
| `source` | 原件的 URL、书目信息或获准保存的项目内资料标识；保留来源类型 |
| `locator` | 页码、章节、表号、段落、时间戳或精确到可复查位置的定位 |
| `date` | 资料发布日期或数据覆盖期；未知则写“未知” |
| `accessed_at` | 在线资料实际访问日期；未访问原件时写“未核验” |
| `certainty` | 已核原件、有限支持、推断、冲突、待核等状态及理由 |
| `boundary` | 样本、地区、时间、测量口径、利益关系或不能外推之处 |
| `contributor` | 谁找到、整理或提出该断言；不暗示其为来源作者 |
| `synthetic` | 是否为虚构、演示或测试材料，明确 true/false |

可加 `excerpt`（短摘录）、`method`、`related_ids` 和保存副本的校验值。校验值只能表明文件字节未变，不能证明内容真实。来源只有 URL 时仍要打开原文核对；URL 可访问也不能证明引用与断言相符。

## 示例（纯虚构）

```yaml
id: E001
claim: "示例资料在第 2 页报告了一个测试值。"
source: "fixtures/demo-source.md"
locator: "第 2 页，表 1"
date: "未知"
accessed_at: "未核验"
certainty: "合成示例，不可用于真实结论"
boundary: "仅演示字段格式；不存在实际测量结果"
contributor: "示例编写者"
synthetic: true
```

## 写作与 PPT

作者将每个事实性段落或页面映射到一张或多张卡片，保留 `id`、`claim`、`certainty`、`boundary` 和 `synthetic`。标题和图表也属于事实断言；图表需标出数据期、分母和来源。若页面只有目录或操作步骤，可标为“无事实断言”，写出理由，交由审查者判断；不能通过删掉证据标识来规避核查。

审查记录至少覆盖四项：断言是否全部映射、原件是否支持对应表述、相关关系有没有被夸成因果、边界是否仍可见。审查者实际阅读过的原件与内容版本应记入记录。内容改动后重审受影响的断言；若没有独立审查者，状态保持“待审”。

## 对接 PPT Studio 的机器检查

上面的 YAML 卡片只是便于人阅读的交换示例，不能直接充当 PPT Studio 的机器检查 JSON。交接时按接收方的 [evidence handoff contract](https://github.com/Nikki99999999/ppt-studio-skill/blob/main/references/evidence-handoff-contract.md) 转换为 `schema_version: 1` 的 `evidence_registry.json`，其中 `entries` 以证据 ID（如 `E001`）为键。每条来源使用 `source.kind: local` 并提供项目内 `path` 与实际 `sha256`，或使用 `source.kind: ref` 指向 `references` 中登记的项目内 `snapshot`、`sha256` 和 `accessed_at`。单独的网页 URL 不足以通过离线核查；只有取得授权且可合法保存时才制作快照。

幻灯片的事实证据项需沿用 `id`、与卡片一致的 `claim`、`source: "ref:E001"` 和相同的 `synthetic` 值，并在可见内容中保留来源及适用边界。接收方要求的内容指纹和审查状态应由实际审查流程生成；不能把格式转换、哈希或自填批准当作独立审查。字段细节和版本要求以接收方规范为准。
