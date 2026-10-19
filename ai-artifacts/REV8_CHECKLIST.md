# rev 8 改动清单（2026-10-17，作者按节整理；写 rev 8 时从上到下逐条勾）

> **rev 9 已写成（2026-10-18 晚，compact 之后）**：`LOCALIZED_RECORD_PLAN.md` 现为 rev 9，按 `reviews/2026-10-18-rev8-check-verdict.md`
> 的 17 组 author_fixes 与 J-1 手改，R8-C2 (a)、R8-C7（等提供方探针）、R8-C13（知晓）与"敲定后再开工、等 light 全部完成"
> 都已写入头部、§8 第 1 步与 §11。作者自决项：R8-C1 的 fixture 组织选 (a)（里程碑 4 fixture import theory 层 fixture，决定 1
> 加 `sessions Localized_Record_Theory_Test`）；R8-C16 (2) 的"匿名 Induct 条目"措辞不统一（两个都不改）；R8-C16 (9) 探针 (b)
> 的消费者去掉决定 17。未做（不是本计划的事）：记忆文件里的日期（需用户批准才改；本文件 :23-37 的旧日期也保留原样、以 §11
> 为准）。下一步：§7 签字表（`REV9_SIGNOFF_TABLE.md`）、通知 datatype 会话。
> **2026-10-18 晚续**：签字表已全部签字（第一类 7 条仍接受、第 8-12 条逐条接受、其余"都接受"），§7 预期冻结、§5.8 (18)
> 第二部分已知晓、计划里不再有"待用户知晓"。datatype 会话已通知并回了两次：datatype 只能给隐藏参数换新鲜名（记决定 19 (a)）；
> 转述用户在它那边的两条裁定，用户在本会话"都确认"——git 分支链（本项目基于 `local_type_abbrev`、`local_datatype` 在后、
> D2 作废）与决定 9 改为引用 `Typedecl.fixed_names`（里程碑 1 多一条依赖）——已写进 §0 第 3/5 条、决定 1/9/10、§7 preface、
> §7.2、§8 第 0(u)/1/3/4 步、§9、§11。仍待用户：首次提交的"提交"；R8-C7（等提供方探针）；记忆文件里 phantom type 裁定的日期
> （10-17 evening → 10-18 10:25 本地）需批准才改。待办：迁移方案批准后按其 §5 写细 §0 第 5 条、决定 1 的 `tools/`、§8 第 3
> 步、§9。**从现在起不开工任何代码**：等全部未决项定下、light 全部完成、迁移落地（用户 2026-10-18）。

> **compact 之后的第一步（2026-10-18 用户令"再次检查，准备 compact"时写）**：
> 1. 读本文件头部与 `reviews/2026-10-18-rev8-check-verdict.md`（rev 8 短核查的裁决正文，17 组 author_fixes 逐条有行号）。
> 2. **用户 2026-10-18（compact 之后）已裁**：R8-C2 选 (a)——隐藏参数在全局 record 里保留块里的名字与 sort，只给用户
>    声明为 record 参数的块固定类型变量换新鲜名（用户"赞同你的建议"；决定 15 与 §11 要注明这偏离了早先裁判"相对块固定
>    变量保持新鲜"的字面条件及理由）；R8-C7 等 local_type_abbrev 自己的探针（其 §7.1 第 1 项）结果再裁（用户"赞同你的建议"；
>    探针前先把第 6e 行的观测与探针 P11 的第三半写成"预期值待裁"的记录行）；R8-C13 的 overloading 半作者从头讲过后，
>    用户 2026-10-18 答"知晓"——rev 9 的 §5.8 (24)(ii) 写"用户 2026-10-18 知晓"。**用户同日另裁（常设）**："把所有问题都敲定后再开工，而且必须等 light locale 全部完成后再开工"——
>    推翻裁判"rev 9 后即可开工里程碑 1"的说法；里程碑 1 也不开工，直到全部未决项（含 datatype 的 `Typedecl.fixed_names`、
>    R8-C7、§7 签字）定下且 light 施工全部完成。另两件未决：§7 预期批量签字（rev 9 后给表）、首次提交的"提交"。datatype
>    会话转来的两条发现（下文）由用户在那边裁，其中 `Typedecl.fixed_names` 一条若采纳会改本计划决定 9（里程碑 1 的
>    `err_fixed_params`），写代码前要拿到答案。
> 3. 写 rev 9：按 verdict.md 的 author_fixes 手工改 `LOCALIZED_RECORD_PLAN.md`（现为 rev 8，2012 行）；R8-C2 相关处
>    （决定 19 (a)、决定 4、§3.7、第 6e 行的名字）在用户答之前标"待用户"、不定；R8-C13 的 overloading 半按 §0 第 7 条
>    写入 §5.8 (24)(ii) 标"待用户知晓"；头部"待用户"列表加上述三件；§11 加 2026-10-18 的 rev 8 短核查、TAT 采纳全局
>    `typedef_overloaded`、datatype 两条发现。裁判说 rev 9 不需要再评审。
> 4. rev 9 写成后：通知 datatype 会话（它按决定 19 镜像设计，已承诺只读）；给用户 §7 签字表（只列与 datatype 不同的行与
>    评审新增的行，其余批量签；签后冻结）。
> 5. 常设规矩（CLAUDE.md 与计划 §0 第 7/9 条）：用户可见文案、设计改动、对别的项目的要求先提案；解释先本质再从零、不造词；
>    计划文档手工改；记忆改写逐次批准；agent 用 Opus、复用结果；永不 `isabelle build`，REPL 重启先问；日期一律本地
>    UTC+8。D2/D3 等 light 施工完成后再议、不主动联系 light；对 TAT record 的承诺（补丁落地后发最终签名）在决定 6。

> **状态（2026-10-18 午后）**：rev 8 短核查**已完成**：`reviews/2026-10-18-rev8-check.json`，裁决正文
> `reviews/2026-10-18-rev8-check-verdict.md`（readiness、3 条要用户的事、17 组 author_fixes、13 条 dropped、13 条探针）。
> 裁定：**rev 9 落实里程碑 1 相关修法后即可开工里程碑 1**，不必再全面评审；要用户的三件都只关里程碑 4：R8-C2（隐藏
> 参数在全局 record 里保留块里的名字还是换新鲜名——计划两处说法矛盾；裁判建议保留名字、只给声明为参数的块固定变量
> 换名）、R8-C7（record 之前已有无限定词 interpretation 时，块内再定义带隐藏参数的 record，其短名从下一条命令起读成
> theory 副本、子 record 静默得到闭合父——建议等 local_type_abbrev 自己的探针结果再裁）、R8-C13 的 overloading 半
> （§5.8 (24)(ii) 对 `overloading` 块同样成立，待知晓）。**下一步**：按 verdict.md 的 17 组 author_fixes 手工出 rev 9
> （R8-C1 fixture 拆三份、R8-C14 两段代码片段与引用、R8-C11 §7.2 清单最紧要；R8-C2 相关处等用户答后改）；再给 §7 签字表。
> 原短核查 workflow 记录：task `wpot5obix`，run `wf_9aee7e55-2af`，脚本
> `~/.claude/projects/-home-qiyuan-Current-MLML/0cd9041e-cfe3-441b-b445-452ffe63754d/workflows/scripts/record-plan-rev8-check-wf_9aee7e55-2af.js`
> （输出在同一会话目录的 tasks/ 下；JSON 结构 result.verdict{ready_to_start, must_discuss_with_owner, author_fixes, dropped,
> probes, summary}、result.merged、result.rounds）。结果到后：存 `reviews/2026-10-18-rev8-check.json`，按 author_fixes 出
> rev 9（若需要），按"先结论、再要用户裁的事、再作者修法"汇报；之后给 §7 批量签字表（只列与 datatype 不同的行与评审
> 新增的行）。用量撞顶时 `Workflow({scriptPath, resumeFromRunId})` 续跑、复用已完成 agent。
> **datatype 会话 2026-10-18 转来两条待用户裁的发现**（它的 rev 1 评审，`contrib/local_datatype/ai-artifacts/reviews/
> 2026-10-18-rev1-review.json`；都不是决定，由它报用户）：(1) 本计划决定 9/19 只用 `Variable.polymorphic` 定义"块固定的
> 类型变量"，而 local_type_abbrev 私有的 `fixed_names` 还要求 `Variable.is_declared`，对以 `_` 结尾的名字（`'a_`）两者分类
> 不同（`Name.declare` 存清理后的名、`is_declared` 查原名，name.ML:93-110、variable.ML:185）；裁判建议请 local_type_abbrev
> 导出 `Typedecl.fixed_names : Proof.context -> typ -> string list`，datatype 与 record 都调它——若用户同意，决定 9 的
> 定义改为引用它（设计改动，需用户批）；(2) datatype 构造里的 typedef 留下随每次 registration 重放的 `type_alias`，与
> 本计划决定 19 (c) 不同；裁判建议 local_type_abbrev 的 typedecl.ML 加一个只在 ML 里用的 Config 让 `basic_decl` 跳过
> alias——与 record 无关、只记。

来源标记：R7-Cn = rev 7 短核查（`reviews/2026-10-17-rev7-check.json`，16 组 author_fixes）；Mnn = 考古
（`reviews/2026-10-17-rev7-archaeology.json`，54 条成立）；Nn = 作者通读笔记（scratchpad `self_consistency_notes.md`）；
U = 用户 2026-10-17 当日裁定（本地日期）。**计划文档一律手工改写**。日期约定：全文用用户本地日期（UTC+8），§11 开头注明。

## 用户 2026-10-17 的裁定（必须写入）
- rev6-C6 (i) 字段记号不随 record 出块：接受（"很好，我认为可以接受。这就是合理的行为"）→ §5.8 (10) 依据 B：决定 2(b) 加决定 16 (i)，用户 2026-10-17 接受。
- rev6-C14：委托作者修、不动设计 → §5.8 (14) 按真实范围写全，依据 B（用户 2026-10-17 委托作者处置、不改设计）；第 23 行与探针 (o) 核。
- R7-C2：核实通过（`reviews/2026-10-17-r7c2-cost-verification.md`，CONFIRMED WITH NOTES），用户"验证通过则支持"→ **删存下的 declaration，3E 之后一次 `map_contexts`**；两条注记写进 §5.8 (4)（`[cases del]` 后加回要补 `case_names`）与决定 21（通配键实例随之与 theory 层 record 相同）。
- R7-C8：用户委托（与测试相关、不改设计）→ 决定 1 五个 session：加 `Localized_Record_Theory_Test`（`tests/Theory`，只 import Main；fixture theory + 每个新父形式一个 theory；typed API 两行放 port-only theory）、`Localized_Record_Golden_Messages`（`tests/Messages`，`threads = 1`，捕获代码在本 session 自己的 theory）。
- R7-C4：按名字排序已批；在前/在后待辩论 `wf_ed1080ae-844`（用户直觉在后）。
- 两条给 local_type_abbrev 的通知：已批、已发、已被采纳（它 §4 已改；回折打印留在它那边由用户另定）。
- TAT：文案定稿 `The field `type_parameters[1]` declares `'b`, which is not used.`（InvalidField，gen 时，COMMON.md §4 a328367）；共享 helper `check_type_parameters_used` 已在 std/common.py（TAT record 实现，Record 已接入，parent 用到的参数算已用）；Datatype 接入归 quotient type 会话；phantom type 用户在 datatype 会话裁"一律拒绝"；兜底义务已由 TAT 落实。用户说"转"后已转 mlml-98、datatype。
- local_type_abbrev 确认：我们里程碑 4 依赖它的里程碑 **1-3**（§8 第 4 步前置改）；接口是 `Typedecl.abbrev` 自动分流；局部全名 `local.p`。

## 用户 2026-10-17 下午至 10-18 的裁定（续；临时目录已失效，此处为唯一记录）
- rev7-C4 终裁："建议在后"——隐藏参数排在声明参数之后（`declared @ hidden @ [zeta]`），隐藏参数之间按名字排、**用块里的名字**（用户确认）。辩论 `reviews/2026-10-17-hidden-param-order-debate.json`（裁判建议在前、优势不大）。计划 :958、:1191 改 `"(nat, 'a) l.lpb"`；第 10 行预期 `(bool, nat) l.lpq`、`('b, nat, 'z) l.lpq_scheme`、`(bool, int, nat) l.lpc`、`bool I.lpq` 印 `(bool, nat) l.lpq`；文档写明"_scheme 里插在 'z 之前"；位置不随 `Generic_Target.define`，只有隐藏参数之间的名序随它。
- M33 两条 class 块偏离（record 常量不是 class 操作、无类约束；instantiation 参数认领对字段不起作用）："接受这两条差异" → §5.8 新 (24)，依据 B（决定 2(b)、3）；第 8/9 行加孪生观测。
- U5 `typedef_overloaded`："建议同样地做" → 决定 11 扩展：`local_add_record` 在 lthy 上算 `overloaded orelse Config.get lthy Typedef.overloaded` 传给 `extension_definition`；§7.3 第 12 行加块内 `declare [[typedef_overloaded]]` 行（孪生：同块裸 typedef、theory 层同写法）；无新文案、无新导出。
- 用户提议 TAT 在 TAT_Std.thy（或 theory 头）加 `declare [[typedef_overloaded]]`、删各 node 的 overloaded 机制：作者分析已按用户要求转 mlml-98 与 TAT record（2026-10-17）；用户 2026-10-18 在 TAT 会话采纳（quotient type 会话转述）：TAT_Std.thy 一行 declare，Typedef/QuotientType 由 quotient type 会话、Record 由 TAT record 会话删机制；本计划决定 11 不受影响（rev 9 的 §11 记一笔）。
- 用户要求通知 datatype 会话做同样的块固定类型变量扩展（改 BNF）：已发；datatype 会话 [4aa7ce] 已被用户指定负责，立项 `contrib/local_datatype/ai-artifacts/LOCAL_DATATYPE_PLAN.md` rev 1（只改 `bnf_fp_def_sugar.ML` 的 `define_co_datatypes`，入口换新鲜名、出口加局部缩写；镜像我们六点；落地后通知）。rev 8：§0 第 5 条改四个项目；决定 19 第 3 条写"stock datatype 拒绝；local_datatype 落地后消失"。
- M43 决定 19 第 3 条："同意"列为决定 2(b) 的第三条有利偏离。
- M44(2) 无字段使用的参数经 synonym 作父："确认"不支持（作者裁定成立，§10 去掉"待确认"）。
- M17 §0 第 7 条新写法："好"；"与测试相关且不改变设计"作常设授权；图例删"内部形状"。
- M12 "努力减少差异和代价"："先别写成常设规则" → 只记 §11（2026-10-14）作背景。
- M14/U3 知晓类事项："按你建议的来" → 可先写进正文、标"待用户知晓"、汇报必提。
- M15 REPL 重启："(b)" → 逐次批准：agent 每次重启 Isa-REPL 前先问用户（§0 第 6 条）。
- M09 repo："赞同你的建议" → 挂 MLML submodule、分支改 `main`、首次提交在 rev 8 与短核查之后由用户说"提交"（计划、reviews、两份交接/清单；`.gitignore` 排除 `ai-artifacts/probes/`；主仓库 "Bump localized_record"）。
- M58 签字形式："这个你自己定" → 作者定 (2)：只列与 `datatype` 不同的行与评审新增的行，其余批量签；签字后预期冻结、再改重新请示。
- M08 TAT 节点过渡期指引："不要指引。等计划完成就好"（用户 2026-10-18）→ 不发；§11 记：2026-10-14 回退分支上的请求于 2026-10-18 撤回，过渡期 TAT agent 看 Isabelle 原文，扩展落地后报错消失。
- light 通报（2026-10-18）：窄变体保留、作为里程碑 3 第一项之后的单独一步（草案 `LIGHT_LOCALE_M3_KEEP_K_PLAN.md` §7）；第一项只处理已带 K 的定理（K′ = K + d）；D3 四问现答 (a)-(d)；theory 层 `assumes` 块的 `p.cases` 是 theory 副本、要等窄变体加 theory 副本落点；裸 `datatype` 抛 `TERM`、探针用 `(plugins del: code)`；窄变体批准时间 2026-10-14 09:47 UTC（本地 10-14），计划里的 10-15 改正。不回信（D2/D3 等 light 施工完成）。
- 头部已改为 rev 8 头部；正文仍 rev 7；用户未答"保留还是撤回"。

## 头部
- 版本 rev 8；状态段改写（rev 7 短核查 + 考古的结论；R7-C2 删重放；日期更正）。
- :24-25 "决定 17 的存下的 declaration 扩展（D6）" 标撤回（R7-C2）。
- :31 删 "rev6-C6+C14 两条按文档授权以依据 B 记入"；改为"rev6-C6 (i) 用户 2026-10-17 接受；rev6-C14 用户 2026-10-17 委托作者处置"。（M02/R7-C1）
- 待办/待批：加 TAT 兜底义务已落实的说明（M04）；加 repo 归属待答（M09）；签字形式待选（M58）；两条 local_type_abbrev 通知已发（M18）；D2 选项全列（M25）；回折打印无人排期（M49）；对 TAT record 的承诺（M06）；"待汇报" §5.8 (18) 扩范围（R7-C1）；R7-C4 顺序；U5 typedef_overloaded 待裁；M33 待裁；M43 待明确；M44(2) 待确认；M17 授权边界待确认；M12/M14/M15 待确认。
- D5 作者自决（以不改变设计为限）（M17）。
- 用户批准事项段：决定 4 的 tag 加 "块内 info 的 case tag 与 name hint 已批 2026-10-14（'赞同打上'）"（M40）。

## 术语表
- R1/R2：改为说明句（评审英文报告的标签，计划不用），§0 第 1 条标题加"（即决定 2(a)，theory 层字节不变）"，其余 15 处改写为"决定 2(a)/决定 2(b)"，§10 :1411 留一处"（评审报告称 R2 relaxation）"（M42）。
- 匿名背景登记 :74-75：改为"3E 写 theory；3E 之后一次 `map_contexts` 写当时打开的各层；不存不重放；块内 notes 只打 tag"（R7-C2）。
- 命名例外 :71-73：用反驳方理由（别的命令写的条目不算，即使在通配键下；record 四条规则在 Induct 表里只以 3E 与 map_contexts 的无条件对象存在）（R7-C10）。
- 加单答案读者（time_fun/code_pred/Nunchaku）（M40 C26）；"TFree 形式"定义；统一"theory 上的 unnamed context"、"匿名背景登记"用词；"background theory"（M55）。
- 复审编号行加 rev7-C*（`wf_1706a31f-824`）。

## §0 硬约束
- 第 1 条：标题加决定 2(a)。
- 第 3 条：接口清单加 `Named_Target.is_theory`、`Symtab.get_first`、`Name_Space.get_names`、`Name_Space.the_entry`、`Facts.space_of`、`Facts.defined`、`Global_Theory.facts_of`、`Thm.trim_context`（若仍用）、`Morphism.binding`、`Context.mapping`、`varifyT`；"以 §3 为准"→"以 §2 决定 20 与 §3 为准"（R7-C11）。加 M13 句："record 在 light 块里只经标准接口工作，light 不需为 record 改代码；本项目不要求 light 改其计划；light 块里的语义、已知差异、测试（§5.6、§7.4）是本项目自己的事（用户 2026-10-13）；对 light 的要求只限 light 必须改代码/工具的事（决定 10 工具层、决定 21 窄变体），先经用户批准。"
- 第 4 条：§3.11 与 :117 加 ":221-231"（M26）。
- 第 5 条：D2 说明加 local_type_abbrev 私有树/expression.ML 叠加问题（M48）；provider 里程碑 4（决定 17 头部跳过）与 §5.8 (21) 的关系（R7-C14）。
- 第 6 条：加 Isabelle 可用性由用户通知（引原话 2026-10-12 "现在 isabelle 不可用。可用后我会给你通知"）；REPL 重启条件（rev3-C25 建议，待用户确认）（M15）。
- 第 7 条：改写授权边界（M17，待用户确认措辞）；加 M14 句（未答事项不先写进修订；先讲本质再从零讲）；"对别的项目（light、local_type_abbrev、TAT）的要求"（R7-C11）。
- 新第 9 条（待用户确认读法）："努力减少差异和代价"（用户 2026-10-14 原话）（M12）。
- 新第 10 条 工作方法：Opus、复用已有结果、英文只读 agent、复审程序（每条新辩护人、裁判定开工条件）、中文从零汇报、手工改计划、记忆改写需批准（M15）。
- 图例 :165-166：删"内部形状"；"作者自决"覆盖用户逐项委托的事项（M17/M41）。

## §1
- 放置原则 :143-147 改写（R7-C2：3E 唯一 theory 写者；map_contexts 唯一 context 写者；不存不重放）。
- :158 范围句加"（命名例外除外，§5.8）"（R6-C14 fix 10 原文）（M40）。
- :161 范围外改为有条件："TAT 侧拒绝未使用的类型参数归 TAT 各 node class 会话落实（已落实于 common.py，2026-10-17）"（M04）。
- 回折打印归 local_type_abbrev，无人排期（M49）。
- 目标句可引用户立项原话"要走最正确最优雅的哪怕是困难的路"（M11）。
- 决定 19 作为与决定 22 并列的例外列入范围（M47）。

## §2 决定
- 决定 1：五个 session、目录 `tests/{Golden, Messages, Theory, Test, Light, golden}`、"每个 session 一个目录（sessions.scala:908-924）"（R7-C8）；repo 归属待用户（已 git init、零提交、master）（M09）；薄包装标"D2 选项 (a) 拟议"（M25）；对 TAT record 的承诺放决定 6。
- 决定 2(b) :189："最新"→"定义时最新（之后用户自己登记的规则会赢，与 stock 一致）"（R7-C2 核实）；有利偏离清单待 M43 确认后扩。
- 决定 3：加"常量封闭是背景构造的前提；决定 19 放宽 err_extra_frees 时须保持"（M33）。
- 决定 4 :225-226："declaration 取其 trim_context…两处写入相等"→"3E 与 map_contexts 步对同一值"（R7-C2）；tag 加 2026-10-14 name hint 批准（M40）。
- 决定 5：无改。
- 决定 6：加对 TAT record 会话 [355583] 的承诺（补丁落地后发最终导出名与签名；TAT RECORD.md §6 已按现签名写）（M06）。
- 决定 8：加"不走 `Local_Theory.declaration`（§10）"（M36）。
- 决定 10：加历史（rev 1 同步清单 2026-10-12 批、2026-10-13 越界撤回、同日搁置、2026-10-15 并入 D2）；D2 问题陈述与 (a)(b)(c) 全列、用户未选（M13/M25）。
- 决定 11：加 `typedef_overloaded`（待用户裁 U5：target 侧读一次传入 `overloaded`）。
- 决定 14 :282：加 `_Tuple_Iso` 别名 binding `record_qualify (Binding.qualify false "p_ext" (Binding.name "p_ext_Tuple_Iso"))`（M55）。
- 决定 15：无改（插件句）。
- 决定 16 (i)：加四个条件（不批量、polarity true、常量先于 notation 否则静默丢弃 sign.ML:420-423、同全名）、残余、binder 注；§10 加被否 (b) 与 rev3-C44（M35）。
- 决定 17：整体改写（R7-C2）：状态行；删按 target 分流 bullet，换 map_contexts bullet（须达第 0 层，local_theory.ML:169-179；reset :167）；删 :354-356、:364 重放句、:366-367 重审句；tag-only bullet 加 bundle/unbundle 失败模式、put_consumes 注、bundle 收益、"第 1 行与 §7.4 核 tag；§7.1 golden 只覆盖 THEN"、精确句（只有 cases 副本引起 (i)-(iii)，left_var_prem；induct 副本 right_var_concl 只影响顺序）（M20/M21/R7-C9）；代价 bullet 加可观察差别、del_att、print 命令、case_tac（M21）；"theory 里没有条件副本"→"Induct 表里没有…（条件形式的事实仍在 theory）"（R7-C10）。
- 决定 19：(b) 加 #args 顺序（待辩论）、强制 sort 句（class 块为 base sort，class.ML:339-343；record.ML:1866/:594/:605/:2343）、按名序引 generic_target.ML:265-272（R7-C4）；两条缩写写入顺序定死（全局 `Sign.add_type_abbrev` 先于 target 步 1 的局部路径，否则 `Bad number of arguments`，预测）（R7-C3）；(a)/(b) 加例外例子 `('a, nat) ph`、全名父换新鲜名、err_extra_frees 原有洞（M47）；规则 3（datatype 报 Locally fixed 而 record 成功）标"待用户明确"（M43）；"方向与规则已批"收窄；提供方决定 2/3/5/8/17 各一句，日期 2026-10-15，提 `Type.add_abbrev_fixed`（M48）；"决定 19 的背景全局缩写不按构造保证"理由过时（R7-C4 6）。
- 决定 20：无大改；:414 退路改指 §10 "退路（不是否决）"小节（R7-C16）。
- 决定 21：恢复 rev 6 应急条款（light 否决/改形使 7c-7j 孪生列无法转绿则回到用户；里程碑 1 开始核探针 (e)，缺则报用户），注"rev5-C4 作者修法，rev 7 误删"（M24）；light 裁定原文引用 + 三种 K + light 测试 1 + 可观测性 + (c) + 9 (i)/§5.6 修订 + 指向 §4 第 14-15 项 + 不打 generic_target.ML + 提前日程的提议 + 2026-10-16 count_of 修订（信息）+ 路径 ai-artifacts/LIGHT_LOCALE_HANDOFF.md（M23/R7-C11）；(ii) 规则句（THM 只在导出副本第一前提无 Var 时；4b/9b/7g 的 fixes n 形式属 (i)）（R7-C6）；instantiation/overloading 嵌套层列入 (i)/(ii)；通配键实例注记（R7-C2 核实 note 2）；D3 待办加"附 light 不需 record 就能跑的 typedef 孪生验收行（rev5-C12 第 7 项）"（M24）。
- 决定 22：:435-436 限定 `I.p`/`local.p` 为里程碑 4 隐藏参数形式，无隐藏参数时 `p`/`i.p`/`I.p` 是 type_alias 走 stock 路径（`i.p` 标预测）（R7-C5）；:455-457 加 theory 层 `I.lp` 与无限定词 interpretation 后的 `lp`（M45）；:461 无隐藏参数时打印 `nat I.p`；第二错误清单加 add_parents sort 检查（R7-C13）；代码改 `varifyT idx (mk_recordT …)` 形式，`Ts` 从 `Vartab.lookup tyenv (a, idx)` 收，守卫 `length Ts = length args`；"约 14 行"保留（R7-C12）；:463-465 通知已发（M18）；§10 加被否：头必须是缩写的额外判断；支持 qph 填值（作者裁定，待用户确认）（M44）；成本应急（先比 `fst (#extension info)` 与 `last_extT`）（M46）。

## §3
- 3.1：步 4 删 declaration 相关、`case_names_fields` 改 `Rule_Cases.case_names ["fields"]`（N8）、加"consumes 0 是手写复述"注（M21）；步 5 ELSE 删 declaration，3E 之后加 map_contexts 步；3E 注释改"the only theory write of the record's Induct rules"；顺序总结加 map_contexts（R7-C2）。
- 3.7：`record_of_type` 改 varifyT 版；:610-611 列 `varifyT` :221；read_parent 不变。
- 3.9：规模句去 declaration，加 map_contexts。
- 3.11：加 :221-231（M26）。

## §4
- :713 "经决定 7 能读回"限定无隐藏参数（R6-C3/M53）。
- 表：补 `l.x`/`l.p.x`、`l.p_scheme`/`I.p_scheme`、`p.p_ext`/`I.p_ext`/`I.p.p_ext` 各格；加"按 binding 命名的碰撞"解释与 `l.simps` vs `l.p.simps` extern 规则（M59）。
- :726-728 改写：父写法按参数形式（`nat l.p`、`'a l.p`、`nat I.p`），指向 §5.1 新接受输入；保留"全部组合都可以"；引 type.ML:286（R7-C5/N5）。

## §5
- 5.1：:740/:742 golden 项名改（R7-C11 6）；新接受输入加里程碑 4 的 theory 层形式（R7-C13 8）；共享树上决定 2(a) 依赖 light §3.5 恒等保证，由 §7.1 对照比较把关（M27）；父解析行指 Record_Parent_Forms。
- 5.2：bullet 改题"名字、事实与记号经 target 的部分（决定 2(b)）"；mixfix 句改（块内与各 interpretation 生效；无 registration 时 `end` 后不生效；theory 层 interpretation 后全局；§5.8 (10)，用户 2026-10-17 接受）（R7-C1/M02）；"比 datatype 强"加 Spec_Rules 头、决定 19 规则 3（待明确）、父写法参数形式与块内名、里程碑 4 继承（R7-C13/M40/M43）；:774 "最新"→定义时最新。
- 5.3：datatype 孪生句改（普通 datatype 崩 dest_equals；`(plugins del: code)` 预计通过，条件副本归 nat 下干扰 cases m，探针 (e) 定）（R7-C6）；删"与 3E 合并"句（R7-C2）；别名不改查找、transfer_facts 改打印；父写法一句。
- 5.4：删合并句；加 forms 第 36 行 `lp` 在 instantiation 可用一句（R7-C3）；父写法一句；quickcheck 例外加 overloading（R7-C11 5）。
- 5.5：一条 cases 条目（3E 的）；父写法 `nat c.p`/`nat p`；class `end` 后 `nat c.p` 即使 nat 非 c 实例也接受（预测，R7-C4）；M33 两条偏离（待裁）。
- 5.6：:839-840 "与其它 target 相同"；light theory 副本 Spec_Rules 合并成一行（M51）；父写法一句（重开块经重放的别名拿回 `p`）；共享假定加 case_tac 取规则自身变量（induct_tacs.ML:48-50，待 D3 写进两边）（M27）。
- 5.7：:863 open_bundle 列六条事实名"无（`Attrib.global_notes ""` 带 `Binding.empty_atts`，bundle.ML:229-231；预测）"（R7-C7/M54）；:865 `unbundle`/`include` 格"3E 的规则"；:872 只删 Induct 半、留 Spec_Rules/eq_spec 半（R7-C2 核实）；:874-875 替身插件成功机制（R7-C7/M01）；plain end 格理由"命名只在打开的层，bundle.ML:247-256"；:854 加"（字段 mixfix 一行用户 2026-10-17 接受）"。
- 5.8 头 :881-883：命名例外清单 = (2)、(3) 的 Spec_Rules 部分、(15)、(19)；删 (22)（N3/M03/R7-C14）。
  - (1)：删"替换了命名副本"（R7-C2）。
  - (3)：A 加 Spec_Rules 部分；删括号句；残余加裸 `'z ch_ext`/`p_inner` case 分析、typedef/code 实例 Spec_Rules（M60）。
  - (4)：只留 `assumes`/`[cases del]` 句；加"现在删后保持删除"；加加回配方（补 `[case_names fields]` 或 `Record.the_info`）；加 `I.p.cases` 句（M22）；引"用户确认接受 R6-C16（2026-10-15 20:12 本地，披露两处差别之后）"。
  - (6)：两行情形限 heavy locale/class/theory target 带 assumes；light 副本合并（spec_rules.ML:110-114；binding.ML:217, :224-225）；嵌套 assumes 层加条件实例行（M51）。
  - (7)：加 (4) 的撤法；light 里删除经重开与 interpretation 仍保持（R7-C14 4）。
  - (10)：依据 B（决定 2(b) 加决定 16 (i)），用户 2026-10-17 接受；加 bundle 两句（plain bundle / open_bundle；`[simp]`/`[iff]` 在 unbundle/include 或 open_bundle end 无名生效；D6 rev5-C16）（R7-C14 5）。
  - (13)：B（决定 15，D1）。
  - (14)：B，拆两部分（D6 知悉 rev5-C30 部分 2026-10-15；rev6-C14 扩范围部分，用户 2026-10-17 委托作者处置、不改设计）；引"决定 20 的 transfer_facts（用户已批）"（R7-C1）。
  - (15)：加"D6 知悉，rev5-C32"。
  - (16)：B，D6 知悉 rev5-C31；无隐藏参数的 record 每种打印形式都是 record 名为头、走 stock 路径；有隐藏参数时 `nat l.p` (20)（R7-C5 6）。
  - (17)：加 record.ML:1797-1799、:1817-1818、quickcheck_common.ML:398-405；范围加 overloading；加不修的理由（需 instantiation 私有数据违决定 2，或 end 时重查违决定 2(a)）（R7-C11/M19）。
  - (18)：B，拆两部分（light interpretation 部分 D6 rev5-C33；重开块与 `lemma (in LF)` 部分依据 light 设计，待汇报）（R7-C1）。
  - (19)：删 Induct 半或改写无顺序理由（M21/R7-C2）。
  - (20)：加 theory 命名 target 里的打印（块内 `'a T.r`、`end` 后 `nat r`）（R7-C3）；回折打印无人排期、是否立项由用户定（M49）。
  - (21)：B，rev6-C3 (b)，用户 2026-10-15；最终严格 `Duplicate type name declaration` 加第二行 `The above error(s) occurred while activating facts of locale instance …`（stock locale.ML:529 的 `handle ERROR` 接 :455-456 的 `activate_err`；rev 8 误写 :806，R8-C8 改）（M48）；头部跳过随 provider 里程碑 4；本例无实例时头部不登记副本；决定 19 :392-394 同限定（R7-C14 2）；provider 的放宽（扩到严格建 context）**已定**：provider 决定 17 只在头部读取期间跳过、头部之后一律严格（用户 2026-10-18 确认），第 10 行预期不随之变（R8-C8）。
  - (22)：拆成多条各自标依据：无字段使用参数残余 B 用户 2026-10-17；`"t q8"` ill-sorted 文案 B 文案变化类；不回折 B rev6-C3 (a)/(20)；开放 interpretation 不造 `I.p` B（provider 决定 2）；报错引全名 B 决定 22；短名遮蔽 **E**（待 P11 与 provider 决定 5 探针；源码预测重放的局部副本赢，与 provider 决定 5 矛盾，若全局赢则报用户与 provider）（R7-C3/M47）；加 provider 决定 3 的 sort 依赖（P9）（M48）；"evaluation"→"gen 时"（M05）；TAT 已落实；作者裁定不支持 qph 填值（待用户确认）（M44）。
  - 新条目（里程碑 4）：带隐藏参数的 record 只能以带参数的全局名到达之处——heavy locale `end` 后 theory 层（:387-388）；嵌套 `context fixes y :: 'd` 层结束后的外层与重开的 `context l begin`（B，provider 决定 2，LOCAL_TYPE_ABBREV_PLAN.md:158、row 3 :517；绕法 `'x l.r`）；class `end` 后 theory 层（provider row 5 :519；绕法 `nat c.p`）；provider 决定 3 sort 依赖 E 探针 P9（R7-C4 2）。
  - 新条目 #args 顺序残余（M47，随辩论结论）。
  - 新条目 (24) M33 两条 class 偏离（待用户裁）。
  - (23) 不变。

## §6
- 不变（决定 22 不加文案；R6-C13 文本："min(physical cores, 8)" 不属此节——放 §7.5）。

## §7
- 前言 :1000-1003：列两个新 session；签字形式待用户选、"签字后固定"规则（作者拟议）（M58）。
- 7.1：消息 session 名；"捕获装在消息 session 自己的 theory 里"（isabelle_process.ML:125-140）；父 record 行加 **fixture 定义段**（照 forms_table SETUP：p0、p、c、ph、s、t、foo_ext 与全部 synonym q1…）（N7/M45）；拒绝行变红映射全列（M46）；加 `record 'a p = x :: 'b` golden 报错行（M40）；`lookup_thm` 列或 NONE（含 exhaust/injects）、"不记 serial 值、只记序关系"、`ML_Syntax.print_typ/print_term`、私有表经行为覆盖、`a__`/`p_ext_Tuple_Iso` stock 基线行、CONTROL 归因规则（M52）；R6-C1 变异检查 = 代码变体由用户在共享树多构建一次；stock 上在 theory 内的模拟只作正对照；探针 (y) 标 [stock; 0] 对照 + [shared; 1]（R7-C9 6）；serial 序关系项；export_theory.ML:123-124、:186-188 引用（R7-C11 7）。
- 7.2：加 `Localized_Record_Theory_Test`；fixture 叶 `Parent_Forms_Fixture.thy`；每个新接受形式与每个文案变化行一个叶；typed API 行放 `Parent_Forms_Typed_API.thy`（port-only）；变异检查 = 用户用 stock-isabelle 构建、每个正叶分别以 `Unknown parent record "Parent_Forms_Fixture.<head>"` 失败（thy_info.ML:252-287）（R7-C8）；正行显式列（含 q2/q3 链"按 record 声明顺序"）（M45）；第 30/35 行孪生文本比较（M46）；`"t q8"` 行（R7-C13 9）；qd 行孪生 `record ('c::order) d' = "nat p" + y :: 'c`；第 13b 指针；工具形状 D2。
- 7.3 各行：
  - 第 1 行：加 `Thm.get_tags` 实际顺序（`p.cases`、`p.cases_scheme`、`p.induct`、`p.induct_scheme`，预计 `[name, consumes "0", case_names "fields"]`）（R7-C9 3）；Spec_Rules 每常量一条等式条目（x、x_update、make）（M59）；打印 `⦇x = 1, y = 2⦈` 在重开后、theory 上 context 块里（M59）。
  - 1b 不变；新 1c 块内 `declare p.cases [cases del]` + print_induct_rules + `cases r`（M22）。
  - 第 2 行：命名 value 项；另一 locale 变体（M60）。
  - 2b：改成真表（变体 × 观测 context → 重施位置、leaf、取反值）；共用观测量；M1（tag-only 列表回退）各位置含 7h THM；M2（立即施加缺失）只定义层与外层，取反值 `Failed to apply initial proof method`/`Unable to figure out induct rule`；重开/interpretation 格为 3E 格；删"错位""3E 不重放之处"；两种顺序句只留 Spec_Rules；可选构建改"用 ELSE notes 换回 stock 列表的代码构建一次"（R7-C9 1）。
  - 第 3 行：理由改 3E 格。
  - 第 4 行：`record c3 = "nat I.p" + w :: nat`（N6/R7-C5）；`J.p.simps`、J 后 value、`I.big.simps`、警告捕获（M59）；P6 计数（I: la 1，J: la 2）（M60）。
  - 4b：外层 = map_contexts 格，重开 = 3E 格（R7-C9 2）；fun 观测量（M40 C21）。
  - 第 5 行：interpretation 前后（M59）；P6 计数；`[cases del]` 后重开/interpretation 保持删除、无 assumes 变体、`I.p.cases`（M22）。
  - 第 6 行：无 datatype 孪生理由；6b 在 l0 定义 q1；6c：`"(nat, bool) r_scheme"` → `Unknown parent record "T.l0.r_scheme"`、`"nat list"` → `Unknown parent record "List.list"`，删或重标 `"nat r_scheme"`，第 44/40 行（R7-C13）；新 **6d**（子在父块外：l6/p6/c6、bundle 变体 b6/pb/cb；重开、interpretation、`locale m6 = l6`、unbundle、class `d = c + …`、sublocale 后观测 `hd find_casesT` aconv `c6.cases` 等；孪生 theory 层 par6/ch6；变异 = `local_setup` 重加忽略 morphism 的父规则 declaration；预期绿）（R7-C2）；新 **6e**（里程碑 4：fixture l/lp/I；#args 含隐藏 'a；`get_parent = SOME ([TFree 'a], "T.l.lp")`；`⦇g = f, k = 0⦈ :: d` 类型检查；孙 record；`context l begin` 子；`record (in l)`；theory 层 `"I.lp"` 与 `"nat l.lp"` 同父；class/instantiation/light/experiment 变体；R7-C3 通过条件与变异（交换两缩写写入顺序→`Bad number of arguments`）；负行 forms 41/42/44、40 记录；`definition f :: "r ⇒ nat"`）（R7-C13/R7-C3/M46）。
  - 第 7 行：7b 孪生措辞；7c-7d 加变体后 gate 值；7e/7i 变体后值待 light 答；7g 封闭 class 例文；7i 例文、孪生探针 (w)；7k 例文（record 之前 theory 上 `context fixes c assumes "0 < c"` 里 global_interpretation）、预期；删"决定 17 (d)"（N4）；export_code/quickcheck（M60）。
  - 第 8 行：8b 例文（含 `fixes n :: nat` 层，D3 标在孪生列）；8c fixture（`typedef t … code_datatype Abs_t`、可执行 `random_t`、p1/instance/p2/end/p3、has_instance 假/真/真、`quickcheck [random]`、full_exhaustive 第二类型、"无 t 类型字段则无此缺口"）（R7-C15）；父行 `"nat p"`/synonym qa（R7-C13）；M33 孪生行（待裁）。
  - 第 9 行：class `end` 后 `typ "nat p2"`（孪生 `record 'b p2 = h :: 'b`）；9b 用 4b 整表观测、写 `fixes n :: nat`；9c 例文与理由；父行 `"nat c.p"`/`"nat p"`。
  - 第 10 行：#args 观测；例外行（`record ('a,'b) ph` theory 层，块内 `"('a, nat) ph"` → `Extra free type variable(s) 'a`，孪生 (i) theory 层同命令、(ii) `"(nat, 'a) ph"` 成功得隐藏 'a）；嵌套层子行与孪生 `record 'd r2 = w :: 'd`；lpb 行移 6e；`m = l1 + l2` 预期两行；lz 的 typ/print_record/simproc（M59）。
  - 第 13 行：13b 预期（每个 registration 前缀下 `<prefix>.p.select_convs`；重开与再 interpretation 无错无重复警告；孪生 §7.5 (1)）。
  - 第 15 行：不变。
  - 第 16 行：unnamed context 放置、`private definition` 孪生、`record (in -)` 嵌套负行（M40）；指向探针 (ab)。
  - 第 17 行：不变。
  - 第 18 行：按 §5.7 新格；18c 预计成功；加"unbundle 在 theory 层与 locale 内，`Thm.rule_attribute` 变体预期在 unbundle 失败"（M22）；experiment 加父行。
  - 第 19 行：theory 层 record 代码完整对照（M59）。
  - 第 20 行：免检格逐格写（(2) `context -` retrieve 空；(15)/(19) 导入格装置；(3)(13) 无格）。
  - 第 21 行：21a/c/d 各 datatype 孪生、21b 理由。
  - 第 22 行：不变。
  - 第 23 行：class 变体、无限定词 interpretation 变体、本 record `p.simps`、两个 record 变体（已有）。
  - 第 24 行：父行 `"nat l.p"`、导入 theory 的 synonym、`"nat I.p"`（R7-C13）。
  - 第 25 行：不变。
  - 新：恶意字段 mixfix 报错行（M35）；const_lines 对照行；CE2 子观测（M59）；T7 可选 TAT Record node 以 q1 作父（M46）。
- 7.4：块例文 `light_locale LN … begin context fixes n :: nat assumes "0 < n" begin record pn … end … end`、`Exported_Premises.count_of`、整表（R7-C15 10）；`end` 后 `length (retrieve_global …) = 1` 头 nprems 0（M51）；父行（块、重开、`interpretation I: LF {1}`、`lemma (in LF)`）（R7-C13）；重开 mixfix、Syntax_copy、fun 模式（M59）；`Thm.get_tags`（块内副本同孪生无 K tag；`end` 后 `LF.p.cases` consumes "1" 加 exported_premises）（R7-C9 3）。
- 7.5：标"作者自决（用户委托 2026-10-15）"；(6) 改写（record 名父多一次 get_info 查找；synonym 父无 stock 基线，多付 cert_typ 加 `Symtab.get_first` 线性扫描，"按表的键序"）；可选预过滤 `last_extT`（R7-C12）；基线：清单内容 digest 加 HOL heap `isabelle_sources` digest；digest 变或 >10% 都"报两个数字由用户选（接受，或用户构建只差 stock record.ML 的副本、同一窗口交替量）"；Record_Benchmark Finished 行作信息；(4)/(5) 含向 registration 传播的注（M41/M54）；T8 计时 HOL-Algebra 与 Record_Benchmark 的子 record（M46）；"min(physical cores, 8)" 若适用（R6-C13）。

## §8
- 探针标签：里程碑字段 = 本项目步骤，light 里程碑进树字段；(e)(q) 重标；(y) 用 shared；P1-P7 [stock; 0]；P8 [stock 与 shared; 0/1]；P9-P11 [shared; 4]（R7-C16 4）。
- (a0) 恢复：决定 3 的 `define` 路线缩写分支与打印故障实证（c 在嵌套 scope 右边 x + 1 对闭 d；`Consts.the_abbreviation`；`Thy.l.c 3` 打印；interpretation 后 `Scratch.I.c`；theory 层孪生；预期不符即停报用户）（M32）。
- (c)：对照预期（r1_again/r1_nopos/r2_interleaved = r1；r2_batched 可能不同；binder 各路线都失败）与畸形 mixfix 文案探针（M35）。
- (e)：`datatype (plugins del: code)` 在 theory 上 assumes 块能否通过（预计通过、nat 下多一条）。
- (g)：重标 [stock; 0; 决定 15、第 1 行] 只留 T 形式项；dest_ctr/`@{datatype rc_ext}`/time_fun 移"刻意不跑"（R7-C16 3/M40）。
- (i)：预期值（theory 层 `find_casesT nat` 头为 foo 的实例副本；locale 孪生保持 nat.exhaust）（M60）。
- (j)：第二半改为 3E + 一次 map_contexts 的 `local_setup` 模拟，同样位置核（R7-C2 核实）。
- (m)：加封闭 class 变体（预计 THM）；普通 datatype 孪生崩 dest_equals。
- (s)：恢复 Typedecl.abbrev/const_alias/type_alias/notation 项（M40）。
- (t)：主形式 = stock 上 `local_setup`（Spec_Rules.add 加忽略 morphism 的 declaration）模拟，里程碑 0；预期头（record 类型无条件原规则；c 类型按 eq_thm_prop 不变；Spec_Rules 头条件）；消费者 §5.8 (19)、4b 的 G 格；去 7k（R7-C16 5/R7-C11 4）。
- (w)：消费者改 7i。
- (z)：heavy locale theory 副本格换为 theory 上 `context fixes n :: nat assumes "0 < n"` 的 theory 副本（theory_target_notes 保留 attribute）；加 [shared; 3; §7.4] light theory 副本格 consumes "1"（R7-C9 5）；加 unbundle 副本（M22）。
- (aa)：stock 上复现 R7-C2 机制（par/locale declaration 重施 `par.cases_scheme`/ch/interpretation；预期 `hd find_casesT ch` = `par.cases_scheme`、`fields a more`）；作第 6d 行负对照。
- (ab)：theory 层 `private record`/`qualified record` 的 stock 文案（outer_syntax.ML:239-241 预测 `Parse.!!!` 在 private 处失败）；§7.1 :1057 指第 16 行加 (ab)。
- P4 恢复预期值（`Type ("T.q1", [])`、`Type ("T.p.p_ext", [nat, unit])`、`Type ("T.p_scheme", [nat, unit])`）（M45）。
- P11 拆两半（unnamed context 半为通过条件：`read_typ_abbrev "r"` = `local.r`、d 的父等于孪生 `"'a T.r"`、`end` 后 `"nat r"` 读为 `T.r`、instantiation 同；重开半记录）（R7-C3）。
- 刻意不跑清单加 (g) 移出的三项。
- 第 1 步：`Record_Parent_Forms` 路径改新 session；stock 跑由用户构建；R6-C1 代码变体构建；CONTROL 归因规则；对 TAT record 的承诺（M06）。
- 第 3 步：两边重核两个文件的约定（M26）。
- 第 4 步：前置改 provider 里程碑 **1-3** 提交并打到共享树（叠加方式随 D2）；指向第 6e 行；每行用 lp；#args 顺序与 sort 检查项（R7-C4 5）；通知承诺（M49）。

## §10
- 删 :1423-1424（map_contexts 设计 3 否决）；加"存下并重放的 declaration（D6 第 1 条；rev7-C2 后否决：重放把父的规则顶到块外子 record 之上）"（R7-C2）。
- 新小节"退路（不是否决）"：决定 20 的手写别名清单退路、删 typedef 规则的选项 B（附 Q3 裁判两个条件：经 `Typedef.get_info_global` 的 #Abs_cases/#Abs_induct 找规则、NONE 时响亮失败）（M39/R7-C16 7）。
- :1398-1399 改写为实际提案（Toplevel.local_theory 注册 + raw_theory 包 add_record_cmd + map_contexts 自动重施；"限定词语义无用"论点未采纳；引用户原话"要走最正确最优雅的哪怕是困难的路"）（M11）。
- :1406-1407 加"连带否决：每常量一个 nested scope 的 define、define 给封闭常量加背景路线给五个应用形式常量的混合"及理由；加"第一个理由只按源码核过、实证为探针 (a0)"（M31/M32）。
- 六条事实头脑风暴其余被否 [4]-[11]（延迟列表编码；Thm.map_tags 整 tag 复制；无 tag 的块内 info（用户 2026-10-14 "全部按你的建议来"选项 (ii) 被否）；从 Local_Theory.notes 返回值取 info；stock 登记加同名 target notes（Duplicate fact declaration）；stock 登记加无名 notes/非 pervasive declaration（Ignoring duplicate rewrite rule）；检查已登记事实选 info；在一次性 context/theory 里求值 attribute）；`context -` 缺口的被否修法（退出再 init theory target；拒绝 `context -` 里的 record），用户 2026-10-14 接受为已知限制（M30）。
- typedef info 被否路线（Typedef.interpretation；transform_info 纯函数；重跑 add_typedef；Context.>>；重新初始化块；拷私有槽；设计 3 的守卫 ext_def 遍历）；light 带 transfer_info / 提升 typedef.ML:69 merge 两个被否（用户 2026-10-15 "建议 record 自有 / 赞同"）（M28/M29）。
- 字段 mixfix 被否 (b) 一律 notation（用户先批后换 "4. 好"）与 rev3-C44 预校验（M35）。
- rev3-C11 `bottom_locale_of` 白名单与全名测试；rev3-C36 可替换 morphism 钩子（用户"先记下来然后搁置"）；rev3-C7 schematic Ctr_Sugar 条目；被弃的测试/指标提案（rev3 C29/C33/C42(a)(d)/C17(c)/C24/C27；rev4 C27(b)(c)/C28/C5）合一条（M37）。
- 决定 8 用 `Local_Theory.declaration` 安装打印翻译（作者 2026-10-12）（M36）。
- 把 record 语义/已知差异/测试写进 light 计划（rev 1 决定 10；用户 2026-10-13 撤回）（M13）。
- 决定 22 加：头必须是缩写的判断；支持 qph 填值（作者裁定、待用户确认）（M44）。
- record 侧回折打印（用户 2026-10-15 否决，归 local_type_abbrev）（M49）。
- :1420-1422 Q4 条目按 Spec_Rules 理由重题（R7-C16 7）；:1429 不写"在背景步 3E 之后"，解释头脑风暴旧编号；:1451 决定 19 全局缩写理由过时（R7-C4 6）；旧 pervasive=true 设想（M38，若 R7-C2 删则并入"存下的 declaration"条目）。
- 性能被弃提案（M37/M41）。

## §11
- 开头：日期约定（用户本地 UTC+8）；C 表（各轮编号→JSON 文件）；中继注（Q3 委托之争的来由）；第 7e 行依据注；决定 15 头部标签（R7-C16 9）。
- 2026-10-11：加用户原话"要走最正确最优雅的哪怕是困难的路"与被否的最小补丁三件（M11）；syn_names 探针日期 2026-10-11（M55）。
- 2026-10-12：性能数字两栏重写（theory 层 / 新 locale；11.2 s 是单 scope 二次方 define；1.8 s 是逐常量未批量形式、非采纳形状；性能不是否决 define 的理由）（M34）；repo 归属问题首次提出。
- 2026-10-13：决定 10 越界撤回与搁置（M13）；决定 3 辩论裁判的 12 条改动与两条待提偏离（M33）。
- 2026-10-14：决定 19 批准（本地日期 10-14）；TAT 节点指引请求（回退分支，M08）；"努力减少差异和代价"（M12）；R1/R2 承诺（M42）；放置原则头脑风暴 `wf_50483b4f-eab` 归 10-14（M19）；light 建议不相邻 :185-193、:221-231 原文（M26）。
- 2026-10-15：rev 6 写在 D6 之前的纠正与规则（M14）；D6 五条知悉清单；rev 5 依据 C 来自合并者对委托的理解（R7-C11 5）；R6-C5/C16/C3 裁定在 10-15（晚）；light 裁定原文与 2026-10-16 count_of 修订。
- 2026-10-17：决定 22 接受、TAT 裁定、落里程碑 1、"我们不管"（10-17 早）；rev 7 短核查与考古结论；R7-C2 核实；用户当日裁定（rev6-C6 (i) 接受、rev6-C14 委托、R7-C8 委托、按名序、辩论、通知批准、"转"、phantom 一律拒绝、TAT 落实）。

## REV7_HANDOFF.md
- :38-40、:77-78 改（R7-C2）；§5 加 (18) 汇报行；:72 日期；或整体标"已被 REV8_CHECKLIST.md 取代"。

## 其他
- 记忆文件 `tat-type-nodes-reject-unused-type-params.md`：日期 2026-10-17、状态更新——**等用户批准**。
