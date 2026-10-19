# rev 7 交接（2026-10-16，写给 compact 之后的下一个 context）

> **2026-10-18 更新**：rev 8 已写成，本文件的作用已被 `REV8_CHECKLIST.md`（逐条改动清单、含用户 2026-10-17/18 的全部
> 裁定）取代；下文只作历史。与 rev 8 不一致之处以 rev 8 为准：决定 17 不再存 declaration（:38-40、:77-78 的"重放对
> record 类型多余但无害"已随 rev7-C2 作废，披露两处差别的时间是 2026-10-15 19:53、用户 20:12 确认）；rev6-C6 (i) 用户
> 2026-10-17 接受、rev6-C14 委托作者；§5.8 (18) 扩范围（重开的 light 块与 `lemma (in LF)`）在 rev 8 头部列为待汇报。

> **2026-10-17 更新**：rev 7 **已写完**——§0-§7.5 由另一处写成（文件已是 rev 7 且在 §7.5 后留 `<!-- CONTINUE -->`），
> §8-§11 由本会话按本文件补完（Edit 替换该标记）。本文件剩下的作用是核对清单。下一步：rev 7 短核查 workflow
> `record-plan-rev7-check`（已起跑，见 §7 末）结果到后，按其 author_fixes 出 rev 8（若需要）并汇报；仍待用户：rev6-C6+C14
> 两条知晓、§7 预期批量签字、TAT 统一文案与 phantom 处置；D2/D3 等 light 施工完成后再议。

**读这个文件的目的**：在不丢任何决策的前提下，把 `LOCALIZED_RECORD_PLAN.md` 从 rev 6 改成 rev 7，然后起一次只针对
rev 7 改动部分的短核查（不是全面评审），再向用户汇报。**计划文档一律手工改写，不用脚本**（CLAUDE.md）。用户授权：
计划文档本身的措辞/组织/术语、命名例外的处置由作者自决；设计决策与一切用户可见文案（报错文案、测试预期、新 ML 名、
对别的项目的要求）必须先提案。所有行为断言都是按源码推断、未实跑（Isabelle 不可用，且绝不运行 `isabelle build`）。

## 0. 当前文件状态

- `LOCALIZED_RECORD_PLAN.md` = **rev 6**（2026-10-15 写）加三处小改：决定 17 的 declaration 扩展已批、决定 20 的
  concealed def 事实别名已批、`Ctr_Sugar.transfer_ctr_sugars` 名字已批（头部"待批"只剩 §7 预期批量签字）。
- 评审记录（`ai-artifacts/reviews/`）：`2026-10-14-reexam-decision17.md`、`2026-10-14-reexam-sec5_2c.md`、
  `2026-10-15-brainstorm-synthesis.json`（+ `-designs-and-critiques.json`）、`2026-10-15-debate-q3-q4-q5-verdicts.md`
  (+ `.json`)、`2026-10-15-ctr-sugar-tvar-form.md`、`2026-10-15-rev5-review.json`、`2026-10-15-rev6-check.json`、
  `2026-10-15-r6c16-verification.md`、`2026-10-15-parent-resolution-brainstorm.json`。
- 探针文件已归档 `ai-artifacts/probes/`（不提交）。
- 提取 JSON 里的裁判文本的办法（python3 -I）：`d=json.load(open(f)); v=d['result']['verdict']`；字段
  `must_discuss_with_owner`、`author_fixes`、`dropped`、`probes`、`summary`；`d['result']['rounds'][i]` 有
  `challenge/defense/rebuttal`。brainstorm JSON：`d['result']['synthesis']` 的 `mechanism`、`forms_table`、
  `r1_argument`、`owner_decisions`、`residues`、`plan_changes`、`probes`。

## 1. rev 6 短核查（`wf_935c4c96-b23`，38 agent，`reviews/2026-10-15-rev6-check.json`）的结论与处置

裁定：架构成立、未达开工条件。**rev 7 必须吸收它的全部 author_fixes（R6-C1 至 R6-C15，各条的 fix 文本在 JSON
的 `verdict.author_fixes` 里，逐条照做）**。要点：

- **R6-C1（blocker）**：THEN 分支 `map_contexts` 步的"关可见性、关 simp_trace"包装要放进施加到每个 context 的函数体
  内（`fn _ => fn ctxt => ctxt |> Config.put Raw_Simplifier.simp_trace false |> Context_Position.set_visible false
  |> Proof_Context.note_thmss "" [(Binding.empty_atts, six)] |> snd |> Config.restore Raw_Simplifier.simp_trace ctxt
  |> Context_Position.restore_visible ctxt`），因为存下的第 0 层 context 继承 theory 层 `declare [[simp_trace]]`，
  否则 theory 层多打 "Adding rewrite rule"，破 R1。§0.3 加 `Context_Position.restore_visible`、`Config.restore`；
  §7.1 加 `declare [[simp_trace]]` 行并做变异检查。
- **R6-C2**：决定 17 的存下的 declaration 只在 heavy locale 与 class 被存下重放；light 不存（`light_standard_declaration
  (K true)`），light `end` 后只靠 3E 的 theory 写；theory target（含 theory 上的无名 context、instantiation、
  overloading）走 `theory_declaration` 两边都写并与 3E 合并；bundle 存并随 unbundle 重放。按 target 逐行写进决定 17；
  §5.6/§7.4：重开的 light 块里 `thm p.simps` 是 Unknown fact（`thm LF.p.simps` 可用）；§5.8 (18) 扩到重开的 light 块与
  `lemma (in LF)`。
- **R6-C3**：决定 19 的三项后果，用户已裁（见 §3 下文）。
- **R6-C4**：§5.8 (5)/(9)/(19) 与决定 21 的改写（随 R6-C16 的批准大部分缩成 typedef/datatype 孪生的注记）。
- **R6-C5**：用户 2026-10-16 裁定接受为已知差异（见 §3）。
- **R6-C6**：§5.7 bundle 改成表（预测）；18c 行改为预计成功（插件在 theory 侧 `Named_Target.theory_map` 跑，不碰
  bundle 的禁区）；新增第 25 行（测试用插件，两种日志：Theory_Data 块内立刻可见、Generic_Data 到 `end` 才可见）。
- **R6-C7**：§7.1 消息行要用能捕获 tracing 的通道、单开 `options [threads = 1]` 的 session；golden 直接 `ML_file`
  light 的 `tests/Golden/golden.ML`（`Golden.recording`/`check`/`thms_dump` 的单条 idiom），不需 light 导出
  `thm_entry`、里程碑 0 不等 D2；theory export 行删、改 ML 内列；CONTROL 记每个清单文件内容 digest 加 HOL heap 的
  `isabelle_sources` digest。
- **R6-C8/C9**：第 2b 变异检查改成"按 context 的表"，映射到它模拟的写者；4b、7e-7j、8b、9b 的观测量与预期按 JSON；
  第 22 行用 `local_setup ‹Local_Theory.background_theory (Record.add_record …)›` 的判别 leaf 代替不可能的交换。
- **R6-C10**：§8 探针 (j) 的 datatype 换成 typedef 或带 attribute 的 lemma（code 插件先崩）；探针标 [树; 里程碑; 消费者]；
  新增 (v) record 模式的 code_pred、(w) `context fixes n begin context assumes "0 < n"` 里的 typedef、(x) assumes
  块里的 copy_bnf/nitpick；探针 (q) 进第 1 步前置。
- **R6-C11**：标签前缀 rev3-/rev4-/rev5-/rev6-；"theory 上的 unnamed context"、"匿名背景登记"统一用词；§11 补用户
  原话（D6："批准第 1, 2 条 / D6 已知晓，请你继续"）；§0 第 5 条"D2 在 §8 第 1 步前定"。
- **R6-C12**：`Global_Theory.name_thm Global_Theory.unofficial1 ((name, 0), pos)`（下标 0）；`induct_cases_rules`
  改为分支前建一次的共享值（两个子表：四条 Induct 条目、simps/iffs），ELSE 的 name-hinted 原始规则在 target 步 2 前
  建一次、declaration 捕获其 trim_context、3E 施 theory_attributes 再 unofficial2；`finish six : theory -> theory`。
- **R6-C13**：决定 20 否决 `Facts.dest_static` 的理由改正（它强制全部 lazy 事实、跳过动态事实；concealed 不是理由）；
  扫描写明 `Name_Space.get_names (Facts.space_of (Global_Theory.facts_of thy))` 过滤 `not (Facts.defined prev name)`；
  别名数约 631（300 字段）；前缀外的名字跳过并注释（不用 Fail）。
- **R6-C14**：§5.8 依据标签改正；命名例外 = (2)、(3) 的 Spec_Rules 部分、(15)、(19)；(13) 依据 B；(14)(15)(16)(18)
  引 "D6, owner acknowledged 2026-10-15"；字段 mixfix 记入 (10) 依据 B。
- **R6-C15**：每行孪生或理由；第 21 行拆 21a-d；第 2 行 `blast dest: l.p.iffs[THEN iffD1]`；新增 9c、8c、13b。
- **R6-C16**：用户 2026-10-16 接受（见 §3）。

## 2. 用户对 rev 6 核查四件事（D1-D4 of that check）的处置

- **R6-C16 接受**（2026-10-16），形式：块内四条 cases/induct 事实的 `Local_Theory.notes` attribute 列表改为
  `[Rule_Cases.case_names ["fields"], Thm.mixed_attribute (apsnd (Rule_Cases.default_consumes 0))]`——只打 tag、
  不写 Induct 表。**不能用** `Thm.rule_attribute`：`Attrib.partial_evaluation`（generic_target.ML:376；attrib.ML:348-351）
  对排在 mixed attribute（`case_names`）之后的 static rule attribute 报 "Mixed dynamic attribute followed by static
  rule"，块内每次 record 都会死；也不能把它挪到 `case_names` 前面绕开（tag 会被烘进存下的定理一次，导出/实例化的副本
  丢 tag）。存下的 declaration 按已批原样保留（含重放；重放对 record 类型多余但无害；它的**立即施加**成了块内 Induct
  条目的唯一来源，不能去）。后果：决定 21 的三类失败对 record 按构造消失（record 自己的类型只经 3E 与 declaration
  写 Induct）；"写在 notes 之后"的顺序依赖对 record 类型不再要紧；record 侧不再依赖 light 的窄变体（typedef/datatype
  孪生仍依赖）。核实报告 `reviews/2026-10-15-r6c16-verification.md`（含 6 项逐条、与 datatype 的精确差别、探针）。
  rev 7 改动清单（核查 JSON 的 R6-C16 fix 文本）：头部、术语表、§1、决定 2(b)/3（块内四条 Induct attribute 的例外）、
  §3.1（第二份 attribute 列表）、决定 17 的顺序 bullet（对 record 键不再承重）、§10（否决 `map_contexts` 的理由消失）、
  决定 21 缩成 typedef/datatype 孪生并删 §8 第 1 步的 record 侧窄变体前置、§5.3-5.7 删 Induct THM/归错句、§5.8 删 (5)(9)
  的 record 部分、保留 (19) 的 Spec_Rules 半、(4)(7) 改写、§0.3 加 `Rule_Cases.default_consumes`、2b 与 7c-7j 的 record
  列成普通 gate 行；精确点：只有 cases 副本引起 (i)-(iii)，induct 副本只引起顺序依赖。
- **R6-C5 接受为已知差异**（2026-10-16）：`instantiation T :: random/full_exhaustive` 块内、`instance` 证明之前定义、
  字段类型含 `T` 的 record 拿不到 quickcheck 生成器实例（record.ML:1768-1780 只在命令时查 theory 的 class 代数；
  arity 在 `instance` 证明后才写回 theory，class.ML:703-705、:746-747）。理由是 stock 自己的规则（theory 层 record 写在
  `instantiation T :: random` 之前同样拿不到），不是 datatype 同形；绕法：record 放在 `instance` 之后或 `end` 之后。
  **只针对 instantiation**（唯一让局部 class 代数领先 theory 的块）；`context begin`、locale、class、light、bundle、
  overloading 不碰 arity，无此问题。加测试行 8c（① instance 前、② instance 后、③ end 后三个 record，观测
  `Sorts.has_instance`，① 与 ③ 的 `quickcheck [random]` 对照）。§5.8 (17) 依据改为 B（用户裁定），§5.4 删"datatype 同"。
- **R6-C3**（里程碑 4，决定 19 的三项后果）：
  (a) 打印 `'a l.p` 而非 `p`：**接受为差异**；改进若做，放 `contrib/local_type_abbrev` 统一做回折（`typ_uncheck`
  对局部缩写；局部缩写存的右边是展开形式 `('a, unit) l.p.p_ext`，与 record 打印翻译看到的类型相同，先折成 `p` 后
  record 的翻译不再碰到），record 侧不另做；interpretation 后的全局缩写 `I.p` 不回折（Pure 对全局缩写一律不回折）。
  §1 范围外加一句"回折打印由 local_type_abbrev 统一做"。删 rev 6 决定 19 里"record 不依赖回折打印"一句，改为"隐藏
  参数情形下 record 类型的打印依赖那边的回折；未做之前记为差异"。
  (b) 名字冲突：由 local_type_abbrev 计划 **rev 2**（2026-10-15）的决定 5/17 决定——读头部期间重名跳过取第一个
  （决定 17），但 `locale m = l1 + l2` 在第二遍之后严格建 locale context 时仍报 `Duplicate type name declaration
  "local.q" vs. "local.q"`（那边测试第 8 行）。record 只引用、不另立规则；加一行测试与那边第 8 行对照。
  (c) `I.p` 作父：被决定 22 取代（见 §3）。
- **R6-C6+R6-C14 的两条知晓**：**用户尚未表态**（多次提醒未答）。内容：(i) 字段 mixfix 经 target `notation`，heavy
  locale（无 registration）`end` 后与普通 bundle `end` 后到 `unbundle` 前 theory 层没有字段记号，theory 层 interpretation
  或 class 自我 registration 后变全局——依据 R2 与决定 16 (i)，记入 §5.8 (10)；(ii) `local.foo` 打印还发生在 class 块
  与有无限定词 interpretation 的 locale 里，含 record 自己的六条事实（`local.p.simps`）；查找不变。**rev 7 先按裁判
  建议写入（依据 B），头部标"待用户知晓"**，汇报时再提一次。
- 其余作者处置：D1 插件回 theory 侧（已在 rev 6）；D2（与 light 的工具层共存）、D3（决定 21 的依赖确认）**等 light
  施工完成后再议，不向 light 发任何通知**（用户 2026-10-15）；D4 性能 gate（threads=1、只 gate theory 层探针、块内
  比值、AFP 不进 gate）与 D5（§6 范围收窄）作者自决，已在 rev 6。

## 3. 新决定 22：父 record 按类型解析（头脑风暴 `wf_0caab246-07c`，`reviews/2026-10-15-parent-resolution-brainstorm.json`）

**规则**：`add_record_cmd` 的 `read_parent` 读到 `Type (name, Ts)` 后：若 `name` 是 record 名（`get_info` 命中），照
stock 原样用 `(Ts, name)`；否则用 `Proof_Context.cert_typ ctxt`（默认模式，查 proof context 的 tsig，含 local_type_abbrev
的 `local.p` 与全局 `I.p`、synonym）展开，再在 record 表里找**唯一一个**其 record 类型（`mk_recordT (map #extension
(get_parent_info thy (SOME (map TVar vs, name)))) HOLogic.unitT`，与 `add_record` 随后建子 record 用的同一函数）与之
`Type.raw_match` 且每个参数都被确定的 record；找不到就把 stock 的 `(Ts, name)` 原样传下去，stock 自己报 stock 的错。
**为什么必须匹配**：Pure 存缩写右边时已完全展开（`Type.add_abbrev` 用 `mode_syntax`，`normalize = true`，type.ML:239、
:694-704），顺着名字追不到 record 名。代码：两个私有函数 `record_of_type`（约 14 行）、`resolve_parent`（约 9 行）放
`add_record` 的 local 块（:2296）`read_parent` 之前，`read_parent` :2301 一行改 `SOME (resolve_parent ctxt (Ts, name))`；
不加文案、不加 ML 名、typed API（`add_record`/`local_add_record`）仍收 record 名不解析（Optics 用读到的父名造常量）；
TAT 走 `add_record_cmd` 自动获得新形式。代码草稿在 brainstorm JSON `synthesis.mechanism[1]`（注意用 `maxidx_of_typ T + 1`、
`Symtab.get_first`、`map_filter` 计数守卫，避免 `the` 与保留字 `open`）。

**用户处置（2026-10-16）**：
1. **接受规则及其全部后果**（新接受输入：全局 synonym 及链条任意参数顺序；`"nat p tv"`；`(nat, unit) p_scheme`；
   `(nat, unit) p_ext`；`⦇x :: nat⦈`/`(| x :: nat |)`；丢掉写出类型变量的 synonym `'x qd`；里程碑 4 起 `local.p`、`i.p`、
   `I.p`、无限定词 interpretation 后的 `p`。仍拒绝且文案不变：非 record 类型、more 位置非 unit 的 `p_scheme`、
   `"nat p foo_ext"`、`logic`、`"logic q9"`、letbinds 系 synonym、ill-sorted `"t s"`、缺参数、schematic 变量、`qph`）。
2. **接受"仍拒绝但文案变了"的一类**：父是 synonym 且另有第二个错误（重复字段、`more` 字段名、多余类型变量、record 名
   重复、`definition` 内部错）时，报第二个错误的 stock 现成文案而非 `Unknown parent record`；没有新文案；决定 7 为先例。
   记进 §0 第 1 条或 §5.1，列出可能在父解析后触发的检查（err_dup_record、err_extra_frees、err_dup_fields、
   err_bad_fields、add_parents 的 sort 检查、definition 内错；块内另有决定 9 的 err_fixed_params、决定 13）。
3. **决定 19 改措辞**：隐藏参数 = record 的 **record 类型**里出现的未声明块固定类型变量（字段类型 + 解析出的父按参数
   实例化后的扩展类型）；例外：只落在父的"无字段使用的参数"位置的块固定变量不算隐藏参数，保留 stock 的 `Extra free
   type variable(s)`。另两句：决定 19 (a) 的换新鲜名也覆盖父参数里的块固定变量；背景的全局缩写与 `make_info` 的参数
   表出自同一份参数列表。删"块内以带隐藏参数的父建子 record 预计报 Unknown parent record "local.p"，read_parent 要解析
   局部条目"一句（决定 22 覆盖）。实现：第 0 步算隐藏参数时 `spec_frees` 的来源加上 `get_parent_info` 给出的实例化扩展
   类型。
4. **残余接受**（§5.8，依据 B）：有"无字段使用的参数"的 record（`record ('a,'b) ph = w :: 'b`）经 synonym 作父
   （`qph = "(nat, bool) ph"`）仍报 stock 的 `Unknown parent record "T.qph"`——展开丢了 `nat`，任何只读类型签名的设计
   恢复不了；填值是对父信息说谎或平添参数，不做；绕法按 record 名写全参数 `"(nat, bool) ph"`；块内 `record 'b lpb =
   g :: "'a ⇒ 'a"`（隐藏 `'a`、无字段用的 `'b`）同理，绕法 `"('a, nat) l.lpb"`。AFP 一例（Dependent_SIFUM_Refinement/
   CompositionalRefinement.thy:1417）。**用户同时裁定（2026-10-16）：TAT 的所有 type node 要在自己的 evaluation 里拒绝
   "声明了却没有任何字段/构造子/表示类型使用的类型参数"，文案统一**（见 §5）。
5. **落在里程碑 1**（用户委托作者自决；作者定里程碑 1：与 target 无关、theory 层 synonym 立刻可用、里程碑 1 golden
   核恒等；块内形式里程碑 4 测；§8 第 4 步的"read_parent 解析 local.p"变为只是测试行）。
6. **不导出解析函数、AFP 三个拷贝 `read_parent` 的包（Optics、Clean、Isabelle_DOF）我们不管**（用户："我们不管"）。
   §5.8/§10 记一笔即可。

**plan_changes**（照 brainstorm JSON `synthesis.plan_changes` 逐条做）：§2 新决定 22；决定 19 改写；§3.7 `read_parent`
一行改 + 两个私有函数；§3.9 约 +24 行；§4 末段"父按缩写名解析"改为"按类型解析"；§5.1 偏离表加一行（按构造：stock 接受
的输入不求值新代码；找不到时 stock 的值与文案）、新接受输入清单、文案变化的一类；§5.2-5.6 各一句块内父的写法；§5.8 新
条目（无字段用的参数残余；短名遮蔽随 provider 决定 5/17，待探针；开放 interpretation 不造 `I.p`——`interpretation I: l
id` 报 `Undefined type name`，绕法写实例类型或 `"'b l.lp"`；AFP 拷贝；(16) 加"每种打印形式都能读回作父"）；§6 一句"不加
文案"；§7.1 golden 行（接受行：`"(nat, bool) ph"` 父为 `([nat, bool], T.ph)`、`record 'c d = "('c::order, nat) ph" + y
:: 'c` 的 `'c` 得 sort order、`"n p"`；拒绝行全列：n、nat、"nat list"、"nat ⇒ nat"、"nat p list"、qn、"nat tv"、
"('a, 'z) p_scheme"、"(nat, bool) p_scheme"、"'z qs"、"(nat, bool) p_ext"、"⦇x :: nat, … :: 'z⦈"、"nat p foo_ext"、
qph、logic、"logic q9"、qsyn、"t s"、缺参数的 p、"'a"、"?'x p"）；§7.2 新 leaf `tests/Test/Record_Parent_Forms.thy`
（每个新接受行与写 record 名的孪生比 `Record.get_info` 的父/args/sorts、`get_recT_fields`、`print_record`；变异检查 =
在 stock 副本上跑正行必须全红 `Unknown parent record`）；§7.3 第 6 行扩成 6b（块内形式）/6c（块内负行：41、42、44、40），
第 9、10 行里程碑 4 转正，第 8/24 行与 experiment 行加一句；§7.4 light 块/重开/interpretation 各一句；§7.5 计时父带
synonym 的子 record；§8 第 0 步加探针 P1-P11（P1 核 `Type.lookup_type` 的 Abbreviation 存展开形式；P2 `(nat, bool) ph`
与 sort；P3 全部拒绝行文案；P4 `read_typ_abbrev` 对 `⦇x :: nat⦈`/`p_scheme`/logic 的返回；P5 synonym 不查 sort；P6 用
导出的 `Record.get_info`/`get_hierarchy` 原型 `record_of_type`；P7 `print_record q1` 可用（默认模式读）；P8 决定 7 的
先例文案；P9-P11 里程碑 4：`local.lp` 的展开与 sort、`I.lp` 的产生、无限定词 interpretation 后的遮蔽）；§8 第 1 步含
解析器，第 4 步删"解析 local.p"加决定 19 修订；§10 加被否方案（默认模式重读、逐层追缩写、解析进共享内部、无前判的
匹配、mode_syntax 证书化、Sign.typ_match、用 record 自己的缩写当模式、gen_local_add_record 放置、失败重跑保文案、typ
版 typed API、缩写名→record 表、请 Pure/provider 存未展开右边、现在导出）；§11 引这次 agent team。
**forms_table 全文**在 brainstorm JSON `synthesis.forms_table`（46 行），写 §5.1/§7 时照抄。

## 4. 与 light / local_type_abbrev / TAT 的交互状态

- light（会话 "Isabelle locale 代数标准方法 (3) [5d6b67]"）：确认两条共享假定（无 tag 规则按 stock 归档、`get_casesT`/
  `get_inductT` 不按 K 过滤；里程碑 3 读者侧 discharge 对无 light 前提的条目恒等——设计，落地时再核）；要求 record 的两个
  hunk 不与其 :185-193、:221-225（ctr_sugar.ML）、:72-74（typedef.ML）相邻→record 放结构末尾；它的 `check_stock_diff.sh`
  在 record 碰树前会红→串行；light 里程碑 1 已提交（a4258d8）；窄变体（决定 21）原则上接受、落里程碑 3、尚未写进 light
  计划（记在其未跟踪的 handoff 日志）。**D2、D3 等 light 施工完成后再议，现不发通知。**
- local_type_abbrev（会话 "Pure 加'局部类型缩写' [b988e0]"）：计划 rev 2（2026-10-15）；决定 5（`local.q` 全名、块内严格
  定义）、决定 17（头部重名跳过取第一个）、决定 2（开放 interpretation 不造副本）、决定 3（保留块固定变量的 sort）；
  record 计划决定 19 的提供方；`Typedecl.abbrev` 自动分流到局部路径，新增 `Proof_Context.add_type_abbrev`；它的 §4 末段
  对 record 父读取文案的预测写错（应是 `Unknown parent record "local.q"` 且决定 22 后被接受）——**只作文档性请求、尚未发**。
- TAT 类型参数检查（用户 2026-10-16 裁定，记忆 `tat-type-nodes-reject-unused-type-params.md`）：已通知 TAT record
  [355583]、datatype [4aa7ce]、quotient type [22ac2e]、mlml-98 [e237e6]（框架编辑者）；e0c78c 是 AoA 会话、已拒。
  quotient type 提议统一文案 `` The type parameter `'a` is declared but not used. ``（InvalidField，`type_parameters[i]`）
  与 common.py 的 gen 时词法扫描；datatype 提出 phantom type 惯用法（`HOL/Library/Phantom_Type.thy:11`）会被挡、请用户
  权衡（硬拒 / 显式开关 / 警告）、它倾向在 ML evaluation 里用权威解析。**文案与 phantom 处置待用户在它们的会话里定**；
  若无人落实，record 会话之后要实现。
- TAT 的 `'a answer` 类型（datatype 会话 FYI）与 mlml-98 的 CODEX_SCHEMA_PLAN 改动与本会话无关，已回复说明。

## 5. 待用户的事（汇报时再列）

- R6-C6+R6-C14 的两条知晓（§2）。
- §7 全部测试预期的批量签字（rev 7 稳定后一次给表：场景、观测量、依据决定、datatype 孪生）。
- TAT 统一文案与 phantom 处置（在 TAT 各会话里答）。
- 决定 22 的 plan_changes 里的两处小文案：§6 一句"不加文案"无需批；`print_record` 不回折为既有行为。

## 6. 写 rev 7 的顺序建议

1. 读 rev 6 全文（约 1100 行，分两次 Read）。
2. 先改决定 17/21/22/19/15/20/4 与 §3.1（结构性），再 §5.8（依据标签、新旧条目），再 §7/§8（行与探针），最后头部、
   术语表、§0.3 接口清单（加 `Thm.mixed_attribute`、`Rule_Cases.default_consumes`、`Context_Position.restore_visible`、
   `Config.restore`、`Proof_Context.cert_typ`、`Type.raw_match`、`Symtab.get_first`、`Name_Space.get_names`、
   `Facts.space_of`、`Facts.defined`）、§10、§11。
3. 起短核查 workflow（4 批评者、合并上限 16、辩护+反驳、裁判；模型 opus/xhigh；英文；只读），模板见本会话脚本
   `record-plan-rev6-check-wf_935c4c96-b23.js`（路径在 `~/.claude/projects/-home-qiyuan-Current-MLML/2e667b2d-…/workflows/scripts/`）。
4. 汇报：先结论，再要用户裁的事，再作者修法；中文、从零讲、不用比喻和临时代号。
