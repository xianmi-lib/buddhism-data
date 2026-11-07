# buddhism-data — 显密文库佛教数据库（公开发布快照）

[显密文库](https://www.xianmi.co/buddhism/) 佛教文献与传播时空数据库的公开数据仓：发布**版本化数据快照**（数据 + JSON Schema + 许可），供研究、引用与社区协作。页面在线浏览与数据下载见站点 `/buddhism/` 板块；本仓管版本化、可发现性与协作入口。

## 数据包（`data/`）

| 文件 | 内容 | 规模（v0.2 快照） |
| --- | --- | --- |
| `core-v0.1.json` | 共享内核：人物/地点/来源统一注册表 | 4,397 人（deprecated 160）· 160 地 · 300 来源 |
| `texts-v0.1.json` | 四藏经目（大正藏/卍续藏/巴利/甘丹二藏）+ 跨藏平行对照 + 佛典术语 | 16,017 部 · 3,442 对照 · 5,030 术语（藏语 Wylie 非空 690，其中 S-DILA-MVP 来源 628，许可见下） |
| `history-v0.1.json` | 宗派传统与关系（部派/汉传/藏传/南传、师承法脉） | 96 传统 · 46 事件 · 1,861 关系 · 2,179 断言 |
| `chronology-v0.1.json` | 纪年基座：中国年号/佛历/藏历绕迥换算 | 1,315 年号 + 3 BE + 2 绕迥 |
| `periods-v0.1.json` | 区域历史时期参照表（人物 `active_period` 与事件时段的共用基座） | 90 时期 |
| `backbone-v0.2.json` | 传播事件主干（Atlas Profile） | 68 作品 · 72 文本版本 · 6 实物 · 100 事件 · 73 案例 |
| `samples-v0.1.json` / `samples-texts-v0.1.json` | Atlas / Texts Profile 手写样例（Schema 演示） | 12 案例 · 5 部样例 |
| `schema-*.json` | 各包的 JSON Schema（Draft 2020-12）：core / texts / history / chronology / atlas；`periods-v0.1.json` 无独立 Schema（发布管线参照表校验，`activePeriod` 定义住 `schema-core`） | 5 份 |

## 数据纪律（使用须知）

- 每条公开事实字段带来源断言（`source_ids`/`assertion_ids` 溯源：引文、URL、定位、访问日期）；`traditional_account`（传统记载）与 `modern_scholarship`（现代研究）等证据等级分标，传统叙事不冒充同期史料。
- 未知日期与坐标为 `null`，不为展示猜值；公元纪年没有 0 年。
- 人物 `active_period` 为活动时期（对应 `periods-v0.1.json` 区域时期段）；`derivation` 随值给出推断方法（`life_date_mapping` / `colophon_dynasty` / `relation_envelope` / `manual_hint`）与依据，使用时请注意它是推断区间而非直接记载。
- 数据为草稿深度（`source_checked` 为编辑抽检口径，非外部专家审定）；引用时请保留此限定。
- 废弃实体带 `deprecated` 标注（只增不删），含身份合并的墓碑形态（`reason: "absorbed"`，`absorbed_by` 指向吸收后实体）与抽取残留/孤儿存根等；引用前请检查。
- 数据中引用的外部来源内容按各自许可处理（如 Wikidata 坐标 CC0；CBETA 题署元数据按其站点条款；版权书籍仅存定位不存内容）。

## 许可

数据以 **CC BY 4.0** 释出（见 `LICENSE`）：可自由引用、再分发与衍生（含商用），须署名并注明数据版本。署名建议：

> 显密文库佛教数据库（xianmi.co/buddhism），buddhism-data 快照 <版本或提交号>

引用藏语 Wylie 子集（S-DILA-MVP）时，另须满足下方「例外」小节的署名要求。

### 例外：藏语 Wylie 子集（CC BY-NC-SA 4.0）

> 本数据库总体遵循 CC BY 4.0，其中 `texts-v0.1.json` terms 段标有 `S-DILA-MVP` 来源之 `tibetan_wylie` 藏语字段继承 CC BY-NC-SA 4.0 许可协议分标。

该子集（v0.2 快照为 628 条，按 `provenance.source_ids` 含 `S-DILA-MVP` 机器可过滤）的藏语 Wylie 转写采自**法鼓文理学院（Dharma Drum Institute of Liberal Arts, DILA）佛学规范数据库**所收录之《翻译名义大集》（Mahāvyutpatti）TEI 数字化版本，许可与义务如下：

- **许可**：CC BY-NC-SA 4.0（知识共享「署名-非商业性使用-相同方式共享 4.0 国际」；底本为 9 世纪梵藏汉古典辞书，属公有领域）。再分发该子集或含其衍生的数据库、以及商业性使用，须遵守其 NC（非商业性）与 SA（相同方式共享）条款。
- **署名（中文）**：藏语术语（Wylie）对照数据采自法鼓文理学院佛学规范数据库所收录之《翻译名义大集》（Mahāvyutpatti）TEI 数字化版本，依 CC BY-NC-SA 4.0 许可协议再利用。感谢法鼓文理学院（DILA）之数字化贡献。
- **署名（英文）**：Tibetan Wylie terminology equivalents in `texts-v0.1.json` are sourced from the Mahāvyutpatti TEI P5 digital edition published by the Dharma Drum Institute of Liberal Arts (DILA) Buddhist Authority Database (https://glossaries.dila.edu.tw/), licensed under CC BY-NC-SA 4.0. We gratefully acknowledge DILA's contribution to Buddhist digital humanities.

## 版本与更新

本仓为**发布快照仓**：主开发仓持续集成，达到里程碑后在此落版本化快照。后续快照带 git tag 与变更说明。

- **v0.2（2026-11-07，同步自主开发仓 0af5ff3）**：Core 身份合并收口（89 对重复身份吸收）与文本日期修复；新增 `periods-v0.1.json`。逐文件变更：
    - `core-v0.1.json`：人物 4,396→4,397、来源 299→300；`deprecated` 67→160（absorbed 110 · misextracted_residue 48 · orphan_stub 2）；人物新增 `active_period`（1,248 人）
    - `texts-v0.1.json`：藏语 Wylie 非空 62→690（其中 `S-DILA-MVP` 来源 628 条，许可见「许可」节）；经目/对照/术语总数不变（16,017 / 3,442 / 5,030）
    - `history-v0.1.json`：关系 1,863→1,861、断言 2,181→2,179（身份合并的回填）
    - `schema-core-v0.1.json`：新增 `activePeriod` 定义与 `person.active_period` 字段
    - `periods-v0.1.json`：**新增**，90 条区域历史时期参照表（人物 `active_period` 的共用基座；无独立 JSON Schema，由发布管线参照表校验，`activePeriod` 定义住 `schema-core`）
    - 其余 8 个文件（backbone / chronology / samples×2 / schema-atlas / schema-chronology / schema-history / schema-texts）与 v0.1 逐字节相同
- **v0.1（2026-11-03）**：首发快照（Core/Texts/History/Chronology 四包 + 5 份 Schema + backbone/samples）。
