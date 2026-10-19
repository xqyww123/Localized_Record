# Localized record 实施计划 rev 9

状态：2026-10-18。日期约定：全文用用户的本地日期（UTC+8），§11 同。rev 8（2026-10-18 上午写成，吸收 rev 7 的短核查
`wf_1706a31f-824` 与 98-agent 决策考古 `wf_ad866c4c-eda` 的全部修法，§11）经 38 个 agent 的短核查（`wf_9aee7e55-2af`，
`reviews/2026-10-18-rev8-check.json`，裁决正文 `reviews/2026-10-18-rev8-check-verdict.md`）裁定架构成立、无 blocker、
17 组作者修法，三件要用户的事都只关里程碑 4。rev 9 吸收全部修法与用户 compact 之后的裁定：隐藏参数在全局 record 里
保留块里的名字与 sort、只给声明为参数的块固定变量换新鲜名（R8-C2 (a)；决定 19、3、15）；"无限定词 interpretation 在
先时同块子 record 静默得到闭合父"等 local_type_abbrev 自己的探针再裁（R8-C7；§5.8 (22) (b)）；§5.8 (24)(ii) 的
overloading 半用户知晓（R8-C13）；§7.1 的 fixture 拆成 theory 层、块、里程碑 4 三份（R8-C1）；第 2b 行的 M2 模拟改用
`local_setup`（R8-C3）；决定 19 的写入顺序只在 theory naming 的 target 里可观察、变异挪到那两个叶（R8-C4）；第 6e 行
拆成五个叶，实例与前缀避开 fixture 已有的 registration、fixture 字段不重名（R8-C5、C6、C9）；新增第 5b 行（R8-C10）；
§7.2 清单补消息 session 与 Benchmarks 的 `-d`、第 18 行补 overloading 子行（R8-C11）；决定 21 改引 light 的原话
（R8-C12）；§5.8 (3)/(17)/(24)/(25) 的范围（R8-C13）；两段代码片段补定义、`overloaded` 记录的写法（R8-C14）；日期按
转录改正、术语统一（R8-C15、C16）。**用户同日另裁："建议把所有问题都敲定后再开工，而且我们必须等 light locale 全部
完成后再开工"**——里程碑 1 也等下文"待用户"全部定下、light 施工全部完成（§8 第 1 步）。

**rev 9 的骨架一句话**：record 的逻辑内容全部在 background theory 里用 stock 代码建；经 target 的是名字（常量、类型、
事实的别名）、六条带 attribute 的事实的名字与 tag、以及 Spec_Rules 的块内副本；四张单答案表（typedef 的 info、Induct 的
按类型表、Ctr_Sugar、Spec_Rules）在 record 存在的每个 context 里都给 theory 层 record 会给的那个答案——命名例外除外
（§5.8）——靠"背景写之后把 theory 新增的键补进每个打开的 context；record 自己的四条 cases/induct 规则只经两个写者进
Induct 表：背景步 3E 写 theory，随后一次 `map_contexts` 写当时打开的每一层，不存、不重放（Pure 自己的 `named_theorems`
就是这个形状），块内 notes 的 attribute 只打 tag 不登记；Spec_Rules 在 theory 里补写 stock 条目"保证（§1）。父 record
按它代表的 record 类型解析（决定 22）。块固定的类型变量作隐藏参数、排在声明参数之后、保留块里的名字与 sort（决定 19）。

**用户批准的事项（2026-10-12 至 10-18）**：独立 repo、旧 API 不改、`split_args` 保持原本行为、新接口命名
（2026-10-12）；决定 3 的形状与决定 2 的形状、§7.5 阈值（当时编号 §7.2）、子选择 1-5 与 7（第 6 项是提问）
（2026-10-13）；六条事实的分派、块内 info 的 case tag 与 name hint（"赞同打上"）、theory 层的 `map_contexts` 步、
`context -` 形式的术语更正与已知限制、保持决定 2(b)（否决带名字的全局登记）、决定 2(b) 三处措辞、rev4-C6 阻塞依赖
light 里程碑 3、与 light 串行、§6 统一渲染规则、决定 19 的方向与"声明为参数的块固定变量保持为参数、不声明直接用的成为
隐藏参数"（2026-10-14）；§0 第 4 条两次放宽（typedef.ML 的 `transfer_info`、ctr_sugar.ML 的 `transfer_ctr_sugars`，名字
已批）、两个 hunk 归 record、决定 17 重开/Induct 写入位置/Ctr_Sugar 与 Spec_Rules 分治（决定 15）三项委托作者裁定（"没有
否决意见"）、决定 20 的 concealed def 事实别名（D6 第 2 条）、rev6-C16 tag-only attribute、rev6-C5 接受为已知差异、
rev6-C3 三项（2026-10-15）；决定 22 的规则与新接受输入、文案变化类、决定 19 改措辞、残余、落里程碑 1 作者自决、解析
函数不导出（2026-10-17 上午）；rev6-C6 (i) 接受为合理行为、rev6-C14 委托作者修不动设计、rev7-C2 删存下的 declaration
（核实通过后支持）、rev7-C8 委托作者、隐藏参数之间按名字排、两条给 local_type_abbrev 的通知、TAT 文案转发（2026-10-17
下午）。**撤回**：决定 17 的存下的 declaration 扩展（D6 第 1 条，2026-10-15 批）随 rev7-C2 于 2026-10-17 撤回。
**用户对复审的处置**：D1（插件回 theory 侧）作者裁定；D2（与 light 的工具层共存）随 2026-10-18 的 git 分支链作废
（§0 第 5 条、决定 10）；D3（决定 21 的依赖确认）等 light 施工完成后再议，现不向 light 发通知；D4（gate 范围）作者
自决；D5（§6 措辞）作者自决，以不改变设计为限。
**用户 2026-10-18 另裁**：隐藏参数排在声明参数之后、按块里的名字排（辩论后，"那么建议在后"）；class 块里 record 的
常量不是 class 操作（§5.8 (24)(i)）与 instantiation 块里字段名形如类参数不被认领（(24)(ii)）接受；块内 `declare
[[typedef_overloaded]]` 照 `record_codegen` 的做法在 target 侧读一次传入（决定 11）；"同一块里 `datatype` 拒绝而 record
接受"列为决定 2(b) 的第三条有利偏离；无字段使用的参数经 synonym 作父不支持（§10）；§0 第 7 条的授权边界新写法；"努力
减少差异和代价"先不写成常设规则（只记 §11）；只需知晓的事项可先写进正文、标"待用户知晓"；agent 重启 Isa-REPL 逐次
批准（§0 第 6 条）；repo 挂 MLML submodule、分支改 `main`、首次提交由用户说"提交"；§7 签字形式由作者定；2026-10-14
回退分支上的 TAT 节点指引请求撤回（"不要指引。等计划完成就好"）；记忆文件改写批准；datatype 侧的同类扩展由用户指定
datatype 会话另立项目 `contrib/local_datatype`。compact 之后：R8-C2 选 (a)；R8-C7 等提供方探针再裁；R8-C13 的
overloading 半知晓；"所有问题敲定、且 light 全部完成后再开工"。当晚：§7 签字表全部签字（第一类 7 条已接受的差异仍
接受、第 8-12 条逐条接受、其余批量签；预期冻结，§7）；datatype 会话转述的两条裁定在本会话确认——补丁系统改 git 分支链，
本项目的分支基于 `local_type_abbrev`、`local_datatype` 在本项目之后、D2 作废（§0 第 5 条、决定 10）；决定 9 改为引用
local_type_abbrev 导出的 `Typedecl.fixed_names`，里程碑 1 因此依赖它的那次修订。
**待办**：迁移方案（`ai-artifacts/ISABELLE_GIT_MIGRATION_PLAN.md`）批准后按其 §5 写细 §0 第 5 条、决定 1 的 `tools/`、
§8 第 3 步、§9；Isabelle 可用后（由用户通知）§8 第 0 步的探针与 golden；light 里程碑 3（typedef/datatype 孪生的
rev4-C6；窄变体为其第一项之后的单独一步）；`contrib/local_type_abbrev` 里程碑 1-3 与 `Typedecl.fixed_names` 的导出
（决定 9、19；它承诺三文件补丁出来时通知本项目）；D3 等 light 施工完成后正式议（light 2026-10-18 已主动给出 D3 四问的
现答，决定 21）；补丁落地后把最终导出名与签名发 TAT record 会话（决定 6）；碰共享树前通知 light。
**待用户**（用户 2026-10-18：全部定下、且 light 全部完成，才开工里程碑 1）：首次提交的"提交"一声；R8-C7——先解释
后定义时同块子 record 静默得到闭合父（§5.8 (22) (b)、第 6e-iv 行、P11 第 (3) 半）：等 local_type_abbrev §7.1 第 1 项的
探针结果后裁，(a′) 记为残余 / (b′) 经批准请提供方改其决定 5 第三点；迁移方案（`ai-artifacts/ISABELLE_GIT_MIGRATION_PLAN.md`
rev 2）的批准在迁移会话，批准后本计划的细节由作者按它写（待办）。只记不裁：datatype 会话转来的第 (2) 条发现——datatype
构造里的 typedef 留下随 registration 重放的 `type_alias`，与本计划决定 19 (c) 不同，裁判建议提供方的 typedecl.ML 加只在
ML 里用的 Config 让 `basic_decl` 跳过 alias——与 record 无关。**待用户知晓**：无（§5.8 (18) 第二部分已于 2026-10-18 晚
随签字表第 12 条知晓）。

本文是把 Isabelle2025-2 的 `record` 包（`src/HOL/Tools/record.ML`）从 theory 级命令移植为 local theory 命令的
计划：移植之后 `record` 在 `locale … begin`、`context … begin`、`instantiation … begin`、`class … begin` 和 light
locale 块里都能用，theory 层的行为与今天字节相同。项目是独立 repo `contrib/localized_record`，依赖 light locale
项目（`contrib/light_locale`）。

### 术语表

按 Isabelle 自己的用法；light 的术语以 light 计划的术语表为准。

- **theory 层**：`Named_Target.is_theory lthy` 为真的 target，即级别 1 的 theory target。它包括普通的 theory 层
  命令，也包括 **`context -` 形式**（`context - begin … end`，名字位置写减号，把 theory 自身当 named target 打开，
  target_context.ML:25-26；发行版与 afp-2026-05-13 零使用）。代码里的判据 `theory_level` 就是它。
- **theory target**：`Named_Target.theory_init` 建的 local theory（naming 是 theory 的 naming 加 `mandatory_path ""`）；
  一条 theory 层命令的 lthy 由 toplevel 以它建、命令结束后 `exit_global` 丢弃（target_context.ML:29-33）。
- **theory 上的 unnamed context**：theory 层的嵌套 `context … begin … end`（Isar-ref 的 "unnamed context"），级别 2，
  沿用 theory target 的 operations。
- **块**：`locale`/`context`/`class`/`instantiation`/`overloading`/`light_locale`/`bundle`/`experiment` 的
  `begin … end`。**定义块**：定义某个 record 的那个块，连同它当时打开的各层 context；**外层**指内层 `end` 之后仍
  打开的层。
- **background theory**：一个 local theory 背后的全局 theory。**背景步**：本计划里一次 `background_step`（§3.1）
  调用——`Local_Theory.background_theory_result` 加随后的 context 补写。**target 步**：作用在 lthy 上的一组
  `Local_Theory.*` 操作。背景步按位置命名：1、2、2E、3T、3E（§3.1）。
- **theory 副本**：target 登记一条事实或 declaration 时写进 theory 的那一份。heavy locale 与 class 的 theory 副本
  不带 attribute（`locale_target_notes`，generic_target.ML:445-451）、locale 有 `assumes` 时带条件；theory target
  （含 theory 上的 unnamed context、`instantiation`、`overloading`）的 theory 副本带 attribute、嵌套 `assumes` 时带
  条件。**块内副本**：同一次登记写进打开的 context 的那一份。**registration 副本**：`Locale.add_facts` 施到已有
  registration（class 的自我 registration、record 前后的 interpretation）时经非空实例化重建的那一份，tag 全部丢失。
- **原始证明结果**：`Goal.prove_sorry_global` 的直接返回值——无 hyps、derivation 无名、无 name hint。
- **derivation name**：证明体里给证明节点起的名字（`Thm.derivation_name`），决定 `thm_deps` 看到什么。
  **name hint**：thm 的 tags 里键为 `"name"` 的一项（`Thm.get_name_hint`），simplifier 的规则名、Sledgehammer 的
  事实名读它；两者独立。
- **数据表**：`Record.Data` 与 `Iso_Tuple_Thms` 两个 `Theory_Data`。**四张单答案表**：typedef 的 info 表
  （`Typedef.Data`）、Induct 的按类型索引的 cases/induct 表、Ctr_Sugar 的构造子表、Spec_Rules 表——都是
  Generic_Data；它们"只取一个答案"的读者分别取 `hd`、取最新一条、按类型名取一条、取头一条（Spec_Rules 另有取全部行的
  读者：Sledgehammer、theory export）。
- **命名例外**：按 record **自己的名字或类型**去查某张单答案表时，某个 context 里给不出 theory 层 record 的那个答案
  的情形，按 §5.8 的条目编号列出并注明涉及哪张表。只算 record 命令自己的写入造成的差别：别的命令写进表里的条目（例如
  typedef/datatype 孪生在通配键下的条件副本，决定 21）不算，即使它们恰好匹配 record 的类型；record 自己的四条规则在
  Induct 表里只以 3E 与 `map_contexts` 步写的无条件对象存在，不会有带前提的副本（rev6-C16）。
- **匿名背景登记**：决定 17 的做法——不造事实名，把 record 自己的四条 cases/induct 规则连同 stock 的 attribute 列表
  写进 theory 的 Induct 表（背景步 3E），再用一次 `Local_Theory.map_contexts` 施进当时打开的每一层；不存 declaration、
  不重放；块内 notes 登记这四条事实时只打 tag。
- **单答案读者**：只取一个答案的工具——`cases`/`induct` 方法与 `case_tac`/`induct_tac`（Induct 表最新一条）、
  `fun`/`primrec`/`time_fun` 的模式完备性与 `Ctr_Sugar.dest_ctr`（Ctr_Sugar 按类型名取一条）、`code_pred` 与 Nunchaku
  （Spec_Rules 取头一条）、`copy_bnf`/Nitpick 读 typedef info（取 `hd`）。
- **TFree 形式**：Ctr_Sugar 条目里的类型用 stock 写入时的自由类型变量（`'a`）表示；与之相对的是经 morphism 导出后
  的 schematic 形式（`?'a`）。本计划的条目都是 TFree 形式（决定 15）。
- **`info` 里六条带 attribute 的定理**：决定 4 的对象；块内与 target 登记的六条事实是不同的值。
- **record 类型**：一个 record 的名字所代表的类型——它的扩展类型沿 more 位置嵌套、末端为 `unit`；`record 'a p = x :: 'a`
  的 record 类型是 `('a, unit) Thy.p.p_ext`。**扩展类型**：`p_ext`。**隐藏参数**：决定 19。
- **Generic_Data 的可见性事实**：proof context 的 Generic_Data 副本在 context 创建时复制、以后不刷新
  （context.ML:586-606、:849）；写进 background theory 的 Generic_Data 在已打开的块里看不见。Theory_Data 经
  `Proof_Context.theory_of` 读，立刻可见。
- **heavy locale**：标准 locale。**无 hyps**：`Thm.hyps_of` 为空。
- 评审的英文报告里把 §0 第 1 条叫 "R1"、把决定 2(b) 叫 "R2"；这两个标签是评审 agent 起的，本计划不用（作者 2026-10-14
  对用户的承诺），正文一律写"决定 2(a)，theory 层字节不变"和"决定 2(b)，块内与 `datatype` 一致"。
- **块固定的类型变量**（决定 9 定义）。**隐藏参数**（决定 19 定义）。
- 复审编号：rev3-C*（`wf_c4edfeb3-0ed`）、rev4-C*（`wf_602fd792-fc7`）、rev5-C*（`wf_18116d0a-779`）、rev6-C*
  （`wf_935c4c96-b23`）、rev7-C*（`wf_1706a31f-824`）、rev8-C* 与裁判加项 J-1（`wf_9aee7e55-2af`）；考古条目 M*
  （`wf_ad866c4c-eda`）。各轮 JSON 见 §11 的表。

## 0. 硬约束

1. **Isabelle 原本行为不变（即决定 2(a)，theory 层字节不变）**（用户 2026-10-12）。theory 层写 `record`，产生的
   类型、常量、定义、事实（名字、命题、attribute、tag、derivation name）、公理、`Defs`、数据表、代码生成、`Spec_Rules`、
   `Ctr_Sugar` 登记、语法表、消息输出与今天字节相同；stock 接受的输入在任何地方的行为不变；record 包自己的报错文案
   不变。两类允许的变化：Pure 命令分派层的文案随命令种类必然改变（§5.1）；stock **拒绝**的输入可以变为接受（决定 7、
   决定 22 的先例，§5.1 列清单），其中仅因父 record 拼写而被 stock 拒绝、又另有第二处错误的输入，改后报第二处错误的
   stock 现成文案（用户 2026-10-17 裁定，§5.1）。`split_args` 的后缀比较原样保留（决定 7）。在共享树上，这条还依赖
   light 计划 §3.5 的恒等保证（无 `exported_premises` tag 的定理在 light 改过的 rule_cases/induct/induct_tacs 路径上
   与 stock 行为相同），由 §7.1 的共享树对照比较把关。
2. **旧 ML API 一个不改**（用户 2026-10-12）。`signature RECORD` 里现有的每个名字保持类型与语义；新能力一律新增
   名字（决定 6）。`Record.add_record … : theory -> theory` 的调用者（发行版 SPARK、`HOL/Examples/Records.thy`；
   AFP 的 Circus、Clean、AutoCorres2、Isabelle_DOF、Optics）不需要任何改动；它的父参数仍是 record 名（决定 22）。
3. **补丁不含 light 专用代码**。性质：`record.ML` 用到的每个接口都在 stock 副本里，外加 §3.10、§3.11 两个新导出与
   local_type_abbrev 导出的 `Typedecl.fixed_names`（决定 9，里程碑 1 起；它在链上本项目之下，§0 第 5 条）；
   不读 `Locale.is_light`，不依赖 light 的任何函数。record 在 light 块里只经 `Local_Theory` 的标准接口工作，light 不需要
   为 record 改代码；所以本项目不要求 light 改它的计划，light 块里的语义、已知差异与测试（§5.6、§7.4）是本项目自己的事
   （用户 2026-10-13："既然不需要改代码，你为何需要改其计划呢？如果是新增测试的话，也应该是你来做啊"）；对 light 的
   要求只限于 light 必须改代码或工具的事（决定 21 的窄变体；决定 10 的工具层已随 git 分支链作废），且先经用户批准。用到的接口（举例，
   以 §2 决定 20 与 §3 为准）：`Named_Target.is_theory`、`Local_Theory.background_theory_result`、
   `Local_Theory.map_contexts`、`Local_Theory.declaration`、`Local_Theory.notes`、`Local_Theory.full_name`、
   `Typedecl.abbrev`、`Local_Theory.const_alias`/`type_alias`/`notation`、`Proof_Context.note_thmss`、
   `Proof_Context.transfer_facts`、`Proof_Context.alias_fact`/`Global_Theory.alias_fact`、`Proof_Context.cert_typ`、
   `Global_Theory.facts_of`、`Facts.space_of`/`defined`、`Name_Space.get_names`/`the_entry`、`Morphism.binding`、
   `Context.mapping`、`Global_Theory.name_thm`/`name_thms` 与 `unofficial1`/`unofficial2`、
   `Thm.theory_attributes`/`proof_attributes`、`Thm.mixed_attribute`、`Rule_Cases.case_names`/`default_consumes`、
   `Context_Position.set_visible`/`restore_visible`、`Config.put`/`restore`/`get`、`Typedef.overloaded`、`Type.raw_match`、
   `varifyT`、`Symtab.get_first`、`Typedef.get_info_global`、`Typedef.transfer_info`、`Typedecl.fixed_names`（local_type_abbrev
   的导出）、
   `Ctr_Sugar.default_register_ctr_sugar_global`、`Ctr_Sugar.transfer_ctr_sugars`、`Spec_Rules.add`/`add_global`。
   上游单位是 `record.ML` 加两个 hunk。本阶段不测没有 light 补丁的 Pure 上的行为。
4. **改动的文件**（用户 2026-10-15 两次放宽）：`src/HOL/Tools/record.ML`；`src/HOL/Tools/typedef.ML` 只增 signature
   一行（`val get_info_global` :17 之后）与一个函数（最后一个 stock 函数之后、`end;` :370 之前）；
   `src/HOL/Tools/Ctr_Sugar/ctr_sugar.ML` 只增 signature 一行（`val transfer_ctr_sugar` :46 之后）与一个函数（`end;`
   :1272 之前）。两个 hunk 纯增加、stock 自己不调。不改 Pure、不改 `Record.thy`、不改任何调用者、不改别的包。放宽
   的理由：两张表的数据槽私有、没有公开写入口能到达已打开的 context（`reviews/2026-10-14-reexam-sec5_2c.md`、
   `reviews/2026-10-15-debate-q3-q4-q5-verdicts.md` 的 Q5）。里程碑 4 另依赖 `contrib/local_type_abbrev` 的 Pure 补丁
   （决定 19）。
5. **四个项目在一条 git 分支链上**（用户 2026-10-18 确认——先在 datatype 会话与迁移会话定、本会话确认；方案
   `ai-artifacts/ISABELLE_GIT_MIGRATION_PLAN.md` rev 2 决定 3，方案本身待批）：`pristine → user_patches → light_locale →
   local_type_abbrev → localized_record → local_datatype → …`，分支名带发行版前缀（`Isabelle2025-2/localized_record`），
   每条分支只从链上前一条 merge，patch 文件是两个发布 tag 之间的 diff，每个 conda 包依赖链上前一个包。本项目的分支基于
   `local_type_abbrev`（在它有内容之前从 `light_locale` 的同一 commit 出发，之后 merge 即可，迁移方案决定 3）；
   `local_datatype` 基于本项目、只从本项目 merge。于是 light 与 local_type_abbrev 的改动在本项目之下是天然的，不再有
   "允许差异 = 各项目清单之并"与叠加顺序的问题；typedef.ML 与 ctr_sugar.ML 与 light 里程碑 3 的 hunk 不相交（light 改
   typedef.ML:72-74 与 ctr_sugar.ML:185-193；本项目的函数按 light 2026-10-15 的建议放结构末尾，不与 :185-193、:221-231
   相邻；light 里程碑 3 的 hunk 定形后两边重核两个文件），真正重叠时由 git merge 报冲突、人工解；local_datatype 只改
   `bnf_fp_def_sugar.ML`，与本项目无文件重叠。本项目碰共享树之前先通知 light（本项目的承诺）。与 light 串行（决定 10）。
   迁移方案批准后，§8 第 3 步、§9 与决定 1 的 `tools/` 按它的 §5 写细。
6. **agent 永不运行 `isabelle build`**（任何 session、任何 flag）。改 `record.ML` 只有重建 HOL heap 才生效
   （§8 第 1 步），重建由用户运行。Isabelle 是否可用由用户通知（用户 2026-10-12："现在 isabelle 不可用。可用后我会
   给你通知"），别的会话的消息不算。Isa-REPL 服务器启动会重建共享的 HOL heap（§8 第 1 步），所以本项目里 agent 每次
   重启 Isa-REPL 之前先问用户、逐次批准（用户 2026-10-18 选此项，rev3-C25）；`isabelle ML_process` 只加载已有 heap、
   从不构建，可以直接用。
7. **用户可见的一切与设计决策先提案**：设计决策（含评审修法里会改变设计的那些）、新报错文案与渲染（§6）、测试里的
   预期行为（§7 的预期批量签字）、新 ML 接口的名字、对任何别的项目（light、local_type_abbrev、local_datatype、TAT 各
   会话）的要求，都要用户批准后才算定。作者自决的范围：计划文档自身的措辞、组织、术语（用户 2026-10-14）；命名例外的
   处置（用户 2026-10-15）；用户逐项委托的事（D4 性能 gate；D5 与文档相关且不改变设计的；rev6-C14；与测试相关且不改变
   设计的，用户 2026-10-17 答 rev7-C8 时给的常设授权；§7 签字的形式），一律以不改变设计为限。已经摆给用户、用户尚未
   回答的事项，即使落在作者自决的范围内，也不先写进计划修订、不当作已定；先讲本质、再从头讲一遍、给完整上下文，等
   回答之后再写（用户 2026-10-15）。只需用户知晓、没有选项的后果，可以先写进 §5.8 并标"待用户知晓"，汇报时必须再提，
   用户答后去掉标记（用户 2026-10-18）。摆给用户、尚未回答的选项在正文里标"待用户裁"。（措辞用户 2026-10-18 批。）
8. **块内行为的判定标准**（用户 2026-10-14）：用户按本意使用新功能——在支持的块里定义 record，然后在块内、外层、
   `end` 之后的 theory 层、重开的块、interpretation、导入的 theory 里使用它——会碰到的任何行为问题是**缺陷**，必须修；
   只有按本意使用碰不到的（内部表示如证明节点、tag；无人使用的写法如 `context -` 形式）才能记为**已知差异**。
   "与 `datatype` 同形"不是豁免。§5.8 的每一条注明它凭什么留下。
9. **工作方法**（用户历次裁定的汇总）：agent 一律用 Opus（用户 2026-10-13），已有的结果复用、不重跑；评审与头脑风暴
   的 agent 用英文、只读、不运行任何 `isabelle` 命令；评审程序是批评者→合并→每条一名新辩护人加一名新质询者→裁判定
   开工条件；向用户汇报用中文、先讲本质再从零讲、不用比喻和临时代号；计划文档一律手工改写；记忆改写逐次批准。
   §0 第 7 条说的"先讲本质、再从头讲一遍"适用于每一次解释。

## 1. 目标与范围

**目标。** `record` 成为 `Outer_Syntax.local_theory` 命令，一条命令在任何 target 下走同一条代码路径（除决定 16 的
一处结构性判断 `theory_level`，用在两个位置）。立项时用户定的标准（2026-10-11）："我认为需要走正经移植，要走最正确
最优雅的哪怕是困难的路"——被否的最小补丁路线见 §10 第一条。

**放置原则**（头脑风暴 `wf_50483b4f-eab` 的综合，作者 2026-10-15 采纳；rev5-C1、C25 与 rev6-C16 修正）。record 的
逻辑内容——扩展类型的 typedef、全部常量与定义、全部定理的证明、数据表、代码生成——与块无关，在 background theory 里用
stock 代码建（§3）。在此之上，四张单答案表在 record 存在的每个 context 里都要给 theory 层 record 会给的那个答案
（命名例外除外，§5.8）。一次写只到一侧：stock 背景代码只写 theory；target 的 note 或 declaration 写打开的 context、
外加一份经变换的 theory 副本。所以：

- 背景写之后，命令把 theory 新增的键补进每个打开的 context——typedef 的 info 与 Ctr_Sugar 条目经 `background_step`
  的两个 transfer；theory 层的六个 attribute 列表经 `map_contexts`。
- record 自己的四条 cases/induct 规则只经两个写者进 Induct 表（决定 17）：背景步 3E 以 stock 的 attribute 列表写
  theory；紧接着一次 `Local_Theory.map_contexts` 把同样的 attribute 施进当时打开的每一层（含存下的第 0 层）。不存
  declaration、不重放：之后出现的每一个 context（重开的块、interpretation、导入的 locale 或 theory、`lemma (in l)`、
  `unbundle`）都从已含 3E 写入的 theory 重建（rev7-C2，核实报告 `reviews/2026-10-17-r7c2-cost-verification.md`）。
  块内 notes 登记这四条事实时只打 tag、不登记（rev6-C16），所以 Induct 表里不会出现 record 规则的条件副本（条件
  形式的事实 `la.p.cases` 仍在 theory 的事实表里，只是不登记），决定 21 的三类失败对 record 自己的事实按构造不发生。
- Spec_Rules：target 写之后，命令在 theory 里再写 stock 的条目，写在 target 的副本之后，使它在 Item_Net 里最新（决定 15）。
  这一半靠写入顺序。
- 用户按名字拿到的东西跟着 target 走（决定 2(b)）：常量与类型的别名、事实的别名、字段 mixfix 的记号、六条带 attribute
  的事实的名字与 tag（`[simp]`/`[iff]` 的登记也在块内）。simpset 与 claset 是"每个成员都贡献"的集合，少一条只是少一点
  自动化，record 的 simproc 读 Theory_Data 照常重写，所以 `[simp]`/`[iff]` 按决定 2(b) 留在 target；这条线把
  cases/induct 与 `[simp]` 分开的依据是表怎么被读。

**范围内。** `record.ML` 的移植（§3）；typedef.ML、ctr_sugar.ML 各一个导出函数（§3.10、§3.11）；父 record 按类型解析
（决定 22）与块固定的类型变量作隐藏参数（决定 19，里程碑 4）；本 repo 的工具与测试（§7，含 light 块的测试 §7.4）；
补丁文件（§9 的分发单位）。

**范围外。** 上游提交（另议）；分发（§9，另立计划）；`datatype_record`（HOL-Library 的另一个包）；Nitpick、Nunchaku、
Predicate_Compile、Ctr_Sugar 插件等工具自身的任何改动（record 只保证它们读的表在每个 context 里都是 theory 层的
内容）；Statespace/SPARK/AutoCorres2 等消费者的任何改动，AFP 调用者不进 gate（复审 D4，作者自决）；record 的新功能；
Pure 的局部类型缩写（`contrib/local_type_abbrev`，决定 19 依赖它）与局部缩写的回折打印（若做，归该项目在类型层统一
做，record 不另做，用户 2026-10-15；目前无人排期，是否另立项由用户定）；`datatype` 的同类扩展（`contrib/local_datatype`，
用户 2026-10-18 指定 datatype 会话负责）；TAT 侧对"未使用的类型参数"的拒绝——用户 2026-10-17 裁定由 TAT 各 node class
会话落实，无人落实则本会话之后实现；已于 2026-10-17 至 10-18 由 TAT 落实（§11）。

## 2. 决定

状态：**已批**（用户日期）、**待批**、**作者裁定**（用户委托辩论后由作者裁定）、**作者自决**（文档；用户授权的命名
例外；用户逐项委托且不改变设计的事项，§0 第 7 条）、**搁置**。"随 X"表示状态随决定 X。rev 3 的决定 12 删除；决定 18
删除；决定 3、4、9、10、15、16、17 的内容替换、编号保留；新增 19、20、21、22；决定 17 在 rev 8 改为不存 declaration。

1. **repo 与组织**（名字已批 2026-10-12；修订已批 2026-10-13；两个测试 session 作者按委托加 2026-10-17；工具项随迁移
   方案定形，2026-10-18）：`contrib/localized_record`，独立 git repo，挂为 MLML 的 submodule、分支 `main`（用户 2026-10-18）；现已
   `git init`、零提交，首次提交（计划、`reviews/`、交接与清单文件；`.gitignore` 排除 `ai-artifacts/probes/`）等用户说
   "提交"（rev 8 的短核查已过，用户尚未说），主仓库同时做一次 "Bump localized_record"。目录：`README.md`；`ROOT`（只含测试 session，
   每个 session 一个目录，sessions.scala:908-924：`Localized_Record_Golden`、`Localized_Record_Golden_Messages`（消息
   行，`options [threads = 1]`）、`Localized_Record_Theory_Test`（只 import `Main`，可在 stock 副本上构建，里程碑 1 的
   gate）、`Localized_Record_Test`、`Localized_Record_Light_Test`，见 §7；不设 session `Localized_Record`；不设
   `tests/Base`）；`tools/signature_additions.txt`（列 `RECORD local_add_record`、`RECORD add_record_cmd`、`TYPEDEF
   transfer_info`、`CTR_SUGAR transfer_ctr_sugars`）；其余工具（改动文件清单、patch 生成、签名核对、golden 元数据）按
   迁移方案 §5 的框架，待其批准后定形——原拟议"对 light 脚本的薄包装"（D2 选项 (a)）随分支链作废；
   `patches/Isabelle2025-2/`（从发布 tag 生成）；`tests/{Golden, Messages, Theory, Test, Light, golden}`；`ai-artifacts/`（含 `reviews/`、`probes/`，探针与结果不提交）。对 light 项目的依赖：基线树是打了 light 补丁的 `contrib/Isabelle2025-2`；stock 行为
   的探针经 light 的 `tools/stock-isabelle` 在 stock 副本上跑；golden 由 `Localized_Record_Golden` 以 `ML_file` 载入
   light 的 `tests/Golden/golden.ML`，复用 `Golden.recording`、`Golden.check`、`Golden.thms_dump`（每条定理一行
   `Golden.thms_dump [(name, th)]` 的写法，Golden_Transfer.thy:15），record 的额外列在包装里追加，不需要 light 导出
   `thm_entry`、里程碑 0 不等迁移落地（§8 第 0 步核 `ML_file` 路径可被 session 接受）；golden session 不能 import
   `Test_Support`（Test_Support.thy:13、:135）；`Localized_Record_Test` 与 `…_Light_Test` 经 `sessions Light_Locale
   Light_Locale_Test` 加限定的 theory 名引入 `Light_Locale_Test.Test_Support`、不作 parent（经 parent heap 继承的 hook
   捕不到输出），加 `-d contrib/light_locale/tests`，前者因此也加载 `Light_Locale.thy`；`Localized_Record_Test` 另加
   `sessions Localized_Record_Theory_Test`，里程碑 4 的 fixture 以限定名 import 那边的 theory 层 fixture（§7.1）。
   "localized" 是 Isabelle NEWS 对
   typedef 同一改动的用词（NEWS Isabelle2009-2）。
2. **语义基线**（形状已批 2026-10-13；(b) 的措辞 2026-10-14 批改；Ctr_Sugar、Induct 两句随决定 15、17）：
   (a) theory 层字节不变；(b) 块里，**名字的可见性（常量、类型、事实的别名）、六条带 attribute 的事实的名字与
   `[simp]`/`[iff]`、Spec_Rules 的块内登记**的行为与同一块里的 `datatype` 一致；其余内容（类型、常量、def 与 def 事实、
   数据表、typedef 的事实与 info、十条不带 attribute 的事实、`ext_*` 事实、代码、Ctr_Sugar 条目）在每个 context 里
   全局、无条件、不重放；三项有利偏离：record 自己的四条 cases/induct 规则在 theory 与每个相关 context 里是**定义时
   最新**的无条件规则（决定 17；之后用户自己登记的规则会压过它，与 stock 一致），Spec_Rules 在 theory 里的头一条是
   stock 的条目（决定 15），record 接受块固定的类型变量——声明为参数或不声明直接用——而 stock `datatype` 拒绝（决定 19，
   里程碑 4 起；用户 2026-10-18 明确列入；`contrib/local_datatype` 落地后此项消失）——命名例外见 §5.8。块内四条
   cases/induct 事实的 attribute 只打 tag、不登记 Induct（rev6-C16，用户 2026-10-15 批），是 (b) 的唯一例外。
   两条冲突时以 (a) 为准。不加任何 target 专用代码去模仿 `datatype` 的失败：record 的结果是统一路径给什么就是什么
   （§5.5、§5.7）。
3. **基础构造**（已批 2026-10-13；六条事实的分派已批 2026-10-14；`background_step`、阶段函数与补写随决定 15、17）：
   按 §3.1——背景步 1、target 步 1、背景步 2，然后按 `theory_level` 分支：theory 层一个背景步 3T（stock :2238-2288，
   含 stock 自己那一次 14 条的 `note_thmss`）加一个 `map_contexts` 步；块内一个背景步 2E、一个 target 步 2、一个背景步
   3E、一个别名步。每个背景步经同一个私有组合子 `background_step`，它跑 stock 代码后把 theory 的 typedef info 与
   Ctr_Sugar 表补进每个打开的 context。背景步里是 stock 的 `extension_definition`（含 stock `do_typedef` 经
   `Named_Target.theory_map_result`、`Iso_Tuple_Support` 全部）、stock 的常量声明与 `Global_Theory.add_def`、stock 的
   `Goal.prove_sorry_global` 证明、stock 的 `note_thmss`、stock 的数据表写入、`add_code`、stock 的 `add_ctr_sugar`
   （插件在新开的 theory target 里跑）与 `add_spec_rule`，都在 stock 自己的 `Sign.qualified_path false binding` 之下。
   阶段 3 只有一个函数 `finish`（§3.6），THEN 与 ELSE 只差六条对象的来源。
   - 六条带 attribute 的事实（`induct_scheme`、`induct`、`cases_scheme`、`cases`、`simps`、`iffs`）：theory 层由
     stock 的两次 `Global_Theory.note_thmss` 原样登记并填 `info`（决定 2(a) 按构造：登记的对象、`info` 的对象、simpset
     与 Induct 表里的对象都出自 stock 自己的调用）；随后 `Local_Theory.map_contexts` + `Proof_Context.note_thmss ""`
     （空 binding，不造名）把同样六个 attribute 列表施进当时打开的 context——为 `context -` 形式与继续使用返回 lthy
     的 ML 调用者；`Named_Theorems.declare`（named_theorems.ML:89-100）是同样做法。块内经 `Local_Theory.notes`
     （决定 2(b)），四条 cases/induct 的 attribute 列表换成只打 tag 的（决定 17）。
   - 常量封闭是背景构造的前提：stock 的 `err_extra_frees`（:2341-2346）与决定 9 保证 record 的常量不含块固定的类型
     变量，所以才能在 background theory 里建；决定 19 放宽 `err_extra_frees` 时必须保持这一点：隐藏参数在背景里成为
     全局 record 的类型参数、保持块里的名字与 sort，声明为参数的块固定变量换新鲜名，常量因此仍是封闭的全局常量——
     同一个名字在 background theory 里只是一个全局类型参数的名字（决定 3 辩论裁判 2026-10-13 的条件 8：常量保持封闭）。
   - 为什么不在块的 lthy 里建逻辑内容（rev 3，rev3-C1 至 C4）：`Goal.prove_sorry lthy` 丢掉
     `Drule.export_without_context`，自由变量不变 schematic；带 `assumes` 的块里 typedef 的局部副本带块假设作 hyps，
     surjectivity 证明失败；`Typedef.add_typedef lthy` 把类型变量声明进 context，随后 `Typedecl.abbrev` 报 `Locally
     fixed type arguments`；类型经 morphism 后 TFree 变 TVar。
   - 为什么六条事实经 target 而十条不经：十条没有任何 target 侧意义；六条的名字与 `[simp]`/`[iff]` 要在定义块内生效，
     而全局登记进的是 Generic_Data、在打开的块里不可见。它们在块内的短名经事实别名（决定 20）解决。
4. **数据表与 `info`**（随决定 3；块内 info 的 case tag 与 name hint 已批 2026-10-14（"赞同打上"）；rev5-C5 定 tag
   顺序；rev6-C12 定写法）：`Record.Data`（:392）与 `Iso_Tuple_Thms`
   （:78）保持 `Theory_Data`、一行不改，背景步里由 stock 代码写入，读取经 `Proof_Context.theory_of ctxt`，处处立刻
   可见。`info` 里六条带 attribute 的定理：theory 层是 stock `note_thmss` 返回的对象；块内照 stock `apply_facts` 的
   三段（global_theory.ML:318-342；`Proof_Context.note_thms` 同形，proof_context.ML:1132-1141）但不命名 derivation：
   四条 cases/induct 规则 = 原始证明结果 → `Global_Theory.name_thm Global_Theory.unofficial1 ((name, 0), pos)`
   （打 name hint，`name` 是 `Local_Theory.full_name lthy (record_qualify (Binding.name "induct_scheme"))` 等，下标 0
   是 stock 单定理事实的下标，thm_name.ML:61）→ `Thm.theory_attributes atts`（stock 的 attribute 列表，这一步同时把
   规则写进 theory 的 Induct 表，决定 17）→ `name_thm unofficial2`；于是 info 对象的 tag 是 `[name, consumes,
   case_names]`、Induct 表里的对象是 `[consumes, case_names, name]`，两者与 stock 的 theory 层相同；`simps` =
   `sel_convs' @ upd_convs'`（背景步 2E 登记的对象）经 `name_thms unofficial2 (simps 名, pos)` 得带下标的 hint，`iffs`
   = 登记过的 `ext_inject` 同法。带 hint 的四条原始规则在 target 步 2 之前算一次，3E 与随后的 `map_contexts` 步对
   同一值施同一份 attribute 列表，两处写入因此相等（`Induct` 的 attribute 自己 `Thm.trim_context` 存入，induct.ML:313）。
   与 theory 层 `info` 的唯一差别是证明节点（§5.8 (1)）。
5. **代码生成**（已批 2026-10-13）：stock 的 `add_code`（:1782-1820）在 `finish` 里原样跑，连同
   `Code.declare_datatype_global`、`equal` 实例、`ensure_sort_record`；:2238 的 `declare_default_eqns_global
   derived_defs` 原样。任何块里 record 立刻有完整代码。一处改动：:1783 的 `Config.get_global thy codegen` 改为
   `add_code` 多收一个 `bool` 参数，由 target 侧以 `Config.get lthy codegen` 读出传入，使块内
   `declare [[record_codegen = false]]` 生效；theory 层两者相同。`add_code` 的 `simps` 参数是决定 4 的 `simps` 对象
   （stock 传的是第二次 note 返回的 `simps'`，:2286）。`add_code` 的内部证明不依赖全局 simpset 里有 `p.simps`。例外：
   `instantiation` 块里 `instance` 之前的 record 得不到待证 sort 的生成器实例（§5.8 (17)）。
6. **ML API**（已批 2026-10-12；`add_record_cmd` 导出 2026-10-13）：旧名全部保留。新增
   `Record.local_add_record : {overloaded: bool} -> (string * sort) list * binding -> (typ list * string) option ->
   (binding * typ * mixfix) list -> local_theory -> local_theory`，旧 `add_record` = `Named_Target.theory_map o
   local_add_record`（前缀 `local_` 的先例是 `Attrib.local_notes`）；两者的父参数仍是 record **名**加参数，不做决定 22
   的解析（AFP 的 Optics 用读到的父名造常量，解析进共享内部会把它干净的 `Unknown parent record` 变成后面一个难懂的
   失败；ML 调用者总有 record 名可写）。另导出字符串级的 `add_record_cmd : {overloaded: bool} -> (string * string
   option) list * binding -> string option -> (binding * string * mixfix) list -> local_theory -> local_theory`
   （今天私有，:2367；TAT 会话 2026-10-13 转达的要求：TAT 以 `Toplevel.local_theory NONE NONE (Record.add_record_cmd …)`
   造与命令相同的 transition，并依赖 `{overloaded}` 参数、`get_extension` 与扩展类型的 stock 命名——三者都保持；决定 22
   的解析在 `add_record_cmd` 的读取路径里，TAT 自动得到全部新形式）。`ISO_TUPLE_SUPPORT` 不变。对 TAT 的承诺
   （2026-10-14）：补丁落地后把最终导出的名字与签名发给 TAT record 会话 [355583]；TAT 的 RECORD.md §6 已按现签名写，
   最终若不同由 TAT 改。
7. **`split_args`**（已批 2026-10-12）：只**加**一条接受条件 `Proof_Context.intern_const ctxt name = field`，放在
   原有后缀测试 `can (unsuffix name) field` 之前；后缀测试原样保留。
8. **打印翻译**（作者自决 2026-10-12）：stock 的 `Sign.print_translation`（:2056）留在背景步 1 末尾，一行不改；不走
   `Local_Theory.declaration` 安装（§10）。
9. **块固定的类型变量，里程碑 4 之前的过渡行为**（文案已批 2026-10-12；放置随 §3.7；定义改为引用 `Typedecl.fixed_names`
   用户 2026-10-18 确认——先在 datatype 会话批准、本会话确认；决定 19 落地后退役）。
   定义：**块固定的类型变量**是 local_type_abbrev 导出的 `Typedecl.fixed_names : Proof.context -> typ -> string list`
   （签名以它最终导出的为准）对该类型给出的那些类型变量——它的判据是 `Variable.polymorphic` 不能泛化**且**
   `Variable.is_declared`（与 `Variable.export` 保留 TFree 的条件同一个，variable.ML:526-529）；对以 `_` 结尾的名字
   （`'a_`）两个判据分类不同（`Name.declare` 存清理后的名、`is_declared` 查原名，name.ML:93-110、variable.ML:185），所以
   不自己用 `Variable.polymorphic` 复述一遍，本项目与 `contrib/local_datatype` 都调它，三个项目对"块固定"只有一个定义。
   落在集合里的：locale `fixes` 的类型里的、class 的 `'a`、`instantiation` 的 arity 变量、`assumes` 里的；块内更早的多态
   `definition` 引入的不算（`Local_Theory.reset` 丢掉那条命令的辅助 context；§8 探针 (h) 核）。这个集合在 theory 层
   为空。后果：里程碑 1 依赖 local_type_abbrev 带这个导出的修订先 merge 进本项目的基分支（§0 第 5 条；用户 2026-10-18
   接受这条依赖；该导出的请求在 local_type_abbrev 会话、待其自查）。过渡行为：`local_add_record` 对每个声明的类型参数
   `(a, S)` 查 `Typedecl.fixed_names lthy (TFree (a, S))`，非空则拒绝（stock `datatype` 的同类检查是
   bnf_fp_def_sugar.ML:2305-2310、typedecl.ML:52-57），作 stock `errs`（:2359）的最后一项 `err_fixed_params`，在 :2365 的
   包装之内（§6）；字段类型或父参数里的块固定类型变量照 stock 报 `Extra free type variable(s)`。内部扩展类型变量 `zeta` 由 `local_add_record` 选为 `#1 (Name.variant "'z" (fold (Name.declare o #1)
   alphas (Variable.names_of lthy)))` 传入 `definition`（:1881 的改动点，§3.6；块里已用 `'z` 时否则
   `Typedecl.abbrev` 报错）；theory 层与 stock 值相同。
10. **与 light 的时序与工具**（串行已批 2026-10-14；工具层问题随补丁系统迁移到 git 分支链作废，用户 2026-10-18 确认——
    先在 datatype 会话与迁移会话定、本会话确认）。历史：rev 1 的决定 10 是一张要 light 计划同步写入 record 语义与测试的
    清单（用户 2026-10-12 批），2026-10-13 用户裁定越界撤回（"既然不需要改代码，你为何需要改其计划呢？如果是新增测试的
    话，也应该是你来做啊"，§0 第 3 条），同日只剩工具层一项并搁置（"现在先记下来然后搁置"），2026-10-15 并入复审 D2；
    2026-10-18 用户把整个补丁系统改成 git 分支链（`ai-artifacts/ISABELLE_GIT_MIGRATION_PLAN.md` rev 2，方案本身待批），
    D2 的三个选项——(a) 请 light 把 `check_stock_diff.sh`、`make_patches.sh`、`record_golden_metadata.sh` 参数化为按顺序
    的项目列表、三个项目按顺序分层生成补丁并做 `patch -F0` 往返检查；(b) record 拷贝并改 light 的脚本；(c) 冻结 light
    的工具、各自手工重生成——都失去对象，不再请 light 改任何脚本。内容：record 里程碑 0（探针、stock 副本上的 golden）
    可先做；里程碑 1（第一次改共享树）等 light 三个里程碑全部完成并提交、迁移落地、头部"待用户"全部定下；性能基线与
    共享树的对照比较在 light 落地后取。工具层：本项目的分支 `Isabelle2025-2/localized_record` 基于 `local_type_abbrev`
    分支、只从它 merge（§0 第 5 条）；patch 文件 = 基发布 tag 与本项目发布 tag 之间的 diff，由迁移方案 §5 的工具生成，
    往返一致由构造保证。仍与迁移无关的一项：§7.1 的消息行需要 light 把 `Test_Support` 的捕获（Test_Support.thy:103-119）
    移到不 import `Light_Locale` 的 theory 并把输出通道做成参数——仍是对 light 的一项要求、先经用户批准；或按 §8 探针 (u)
    由 `isabelle build_log -v -T` 代替。在迁移落地之前本项目不碰共享树。决定 1 的 `tools/` 随迁移方案批准后定形。
11. **配置读法与计时**（已批随决定 5；rev5-C27；`typedef_overloaded` 用户 2026-10-18 批）：`codegen` 在 target 侧读
    一次传入；同法，`local_add_record` 在块的 context 上算 `{overloaded = #overloaded overloaded orelse Config.get lthy
    Typedef.overloaded}`（`overloaded` 是 `{overloaded: bool}` 记录，record.ML:30、:2313）并把它作为 `overloaded` 传给
    `extension_definition`（:1900；一路到 `Typedef.add_typedef`，:105，含 `p_inner<i>` 的 typedef）——否则块内 `declare
    [[typedef_overloaded]]` 对 record 的扩展类型 typedef 不生效，因为那个 typedef 在 background theory 新开的 theory
    target 里跑、读不到块的 context（typedef.ML:155；record.ML:104-105），而同一块里裸 `typedef` 读得到；theory 层
    `Config.get lthy` 读到的就是全局值，"标志 ∨ 开关"与 stock 的结果相同（决定 2(a) 按构造）；不加文案、不加导出
    （`Typedef.overloaded` 已导出，typedef.ML:23）。`record_timing` 的
    `timeit_msg`/`timing_msg` 照 stock 用 background theory 的 context，每个计时器留在它原来包的那段 stock 代码外（阶段拆分
    后 trfuns/tyabbrs 的计时器量得少了，只在 `record_timing` 开时可见）。
12. （删除。rev 3 要改 simproc 的证明 context；现在 simproc 一行不改。）
13. **与 record 常量同名的块参数**（已批 2026-10-13：照 `datatype` 拒绝）：在块内 target 步 2 的别名步里，每次
    `const_alias` 之前，若 `Variable.lookup_fixed lthy` 命中该短名，调 `Variable.add_fixes_binding [b]` 让
    Isabelle 自己报 `Duplicate fixed variable(s): "x"`；检查的集合恰是被加别名的集合（选择子、`more`、更新、
    `make`/`fields`/`extend`/`truncate`、`p_ext`、`Rep_p_ext`/`Abs_p_ext`、`_Tuple_Iso` 常量——AFP ISQ_Quantities 按名
    用它们；300 字段的 record 约 631 条别名，含内层 `p_inner<i>` 的 `Rep`/`Abs` 则 673）。不对整张短名表整体调
    `add_fixes`：那会改变 stock 对重复字段、字段名 `make`、`x` 与 `x_update` 并存、`more` 的报错文案。代价：拒绝发生
    在背景步之后，白跑一次证明；命令是事务性的，不留痕。渲染两行（§6）。
14. **命名**（已批 2026-10-13，子选择 7）：背景步跑在 `background_theory_result` 装好的 naming 下（target 的
    background naming 经 lthy 的 naming 变换，local_theory.ML:225-236），里面 stock 自己的 `Sign.qualified_path
    false binding` 让一切 stock 命名的东西自动得到 `Thy.l.p.…`。target 步的每个 binding 用一个私有函数
    `record_qualify` 加上 record 限定词——对 `Binding.path_of (Binding.qualify_name false binding "")` 逐段
    `Binding.qualify`，按 `Binding.name_spec` 的拼接（binding.ML:215-218）逐字重现 `Name_Space.qualified_path`
    （name_space.ML:484-485）。具体：常量别名 `record_qualify (Binding.name base)`；`Rep_p_ext`/`Abs_p_ext` 用
    `record_qualify (#Rep_name (Typedef.default_bindings (Binding.name "p_ext")))`；`p_ext` 的类型别名
    `record_qualify (Binding.name "p_ext")`；`_Tuple_Iso` 常量的别名 `record_qualify (Binding.qualify false "p_ext"
    (Binding.name "p_ext_Tuple_Iso"))`（stock 在 `p_ext` 限定词下命名它，iso_tuple_support.ML:124）；六条事实
    `record_qualify (Binding.name "simps")` 等；事实别名的 binding
    按条目自己的 suppress 标记逐段重建再套 `record_qualify`（决定 20）；两个类型缩写**不**加 `record_qualify`——
    `Typedecl.abbrev` 用 `Local_Theory.full_name lthy binding` 得到同样的 `Thy.l.p`。
15. **Ctr_Sugar 与 Spec_Rules**（作者裁定 2026-10-15，依辩论 `wf_7013bfb2-e81` Q5 的裁判；插件位置依复审 D1 改回
    theory 侧）。两张表分治，因为它们坏的方式不同：
    - **Ctr_Sugar**：theory 在每个分支都由 stock 自己的 `add_ctr_sugar`（`default_register_ctr_sugar_global (K true)`
      on `record_ctr_sugar …`，插件在新开的 theory target 里跑，ctr_sugar.ML:221-231）写，`background_step` 用
      `Ctr_Sugar.transfer_ctr_sugars`（§3.11）把 theory 的表补进每个打开的 context。不经 target 的 declaration，
      locale 里不存任何 Ctr_Sugar 的东西，不重放。于是 theory、每个打开的层、以后重开或重建的 context、
      interpretation、导入的 theory 拿到的都是 theory 层 record 那一条（stock 的 TFree 形式）。插件自己的数据（AFP
      Constructor_Funs 的常量与规则；Lazy_Case 对 record 提前返回）在定义块内到 `end` 才可见（§5.8 (13)）。
    - **为什么插件不在块内跑**（rev 5 曾如此）：Constructor_Funs 用 `Symtab.update_new` 的 pervasive declaration 存
      自己的数据（constructor_funs.ML:61-67），在 locale 里该 declaration 被存下，重开或 interpretation 时重放到已有
      该键的表上，预计抛未捕获的 DUP；class 块里 record 命令自身就抛；HOL 里没有插件，这一步无测试可触。进 §10。
    - **Spec_Rules**：块内 target 步 2 `Spec_Rules.add Binding.empty Spec_Rules.equational [head] [rule]`（块内读者
      要看到：sledgehammer_fact.ML:319、nunchaku_collect.ML:498），背景步 3E 末再写一次 stock 的 `add_spec_rule`
      （:1835-1837）进 theory，让 stock 的条目成为每个常量的头一条（Item_Net 最新在前；code_pred 取头，
      predicate_compile_data.ML:210-212）。不给 Pure 的 spec_rules.ML 加写入口（Item_Net 的并集会把块内定义的
      导出规格带进 context 成为最新）。残余见 §5.8 (6)、(15)。
    - 为什么不保持 2026-10-13 的"Ctr_Sugar 经 target"：heavy locale 带 `assumes` 时 theory 副本的 exhaust 带条件，
      theory 层 `fun f where f ⦇la.x = a⦈ = a` 预计在 `pat_completeness`（:26 要恰两个 schematic 变量）失败到第一次
      interpretation；theory 上带 `assumes` 的 unnamed context 永远修不了；父在块内的 theory 层子 record；diamond
      import 时 Ctr_Sugar 的 merge 取第一个父的值（ctr_sugar.ML:182）。这些都没有 `datatype` 孪生可作豁免。
    - 共享假定：stock 的 `default_register_ctr_sugar_global` 保持 stock（把 literal 写进 theory 数据 :229、只经过滤
      器跑插件 :230）；§7.1 的 Ctr_Sugar golden 行会抓住改动。
    - 对 Q5 裁判条件 [7] 字面的偏离（rev 9，随 R8-C2 (a)）：裁判写的是"决定 19 让背景 record 的类型变量相对块固定的
      类型变量保持新鲜，否则存在 locale 里的 Spec_Rules declaration 可能含块固定的 TFree，interpretation 会加上按类型
      特化的头行"。用户 2026-10-18 选的决定 19 (a) 只给声明为参数的块固定变量换新鲜名，隐藏参数保留块里的名字。条件
      要防的事仍按构造不发生：存下的规则全部出自 stock 代码、经 `Drule.export_without_context` 与 `Global_Theory.name_thm`
      的路径已做成 schematic（drule.ML:244-257、global_theory.ML:404-407），Spec_Rules 的头从这些规则算出
      （record.ML:1835-1837），没有块固定的 TFree 能进去；同一个名字在 background theory 里只是全局类型参数的名字。

16. **theory 层的结构性判断 `theory_level`**（已批 2026-10-13；两处随 2026-10-14）：`val theory_level =
    Named_Target.is_theory lthy` 读一次，**两处**使用，理由同一个——stock 在 theory 层的形状与 local API 在 theory 层
    给出的形状不同：(i) 字段 mixfix（背景步 2）：`theory_level` 时把 `field_syntax` 原样传进背景声明（stock :2063
    不动），否则 `NoSyn` 声明、每字段一次 `Local_Theory.notation true Syntax.mode_default [(Const (c, T), mx)]`，
    按字段顺序——Pure 自己 `background_foundation`（带 mixfix）与 `locale_foundation`（`NoSyn`）的分法。这条路与
    stock 结果相同的四个条件（作者 2026-10-13，用户批 (a)）：不合并成一次批量 `notation`、polarity 为 `true`、常量先
    声明后 `notation`（否则 `Sign.notation` 静默丢弃 mixfix，sign.ML:420-423）、用同一个全名。残余：块内记号的作用域
    见 §5.8 (10)；binder 形式的字段 mixfix 今天在 theory 层就报 `Bad type of binder`，两条路相同。(ii) 背景步 2
    之后的那个 if/else（§3.1 第 4 步）：THEN 跑 stock :2238-2288，ELSE 走 target。别名、匿名背景登记、Spec_Rules 的
    块内处理全在 ELSE 里，不单独判断。两处读同一个值。theory 上的 unnamed context（级别 2）与 `instantiation`、
    `overloading` 块里 `is_theory` 为假、走 ELSE：别名多余但无害（指向自身；`Name_Space.alias` 对已有访问名不改
    `intern`/`extern` 的结果；决定 20 的 `transfer_facts` 另有打印上的副作用，§5.8 (14)），mixfix 经 `notation`（语法表
    相同，§8 探针 (c)）。不读 `Locale.is_light`、不判 locale/class/light。
17. **匿名背景登记：theory 层与每个相关 context 里的 `cases r`/`induct r`**（作者裁定 2026-10-15，依 Q3、Q4 的裁判，
    用户 2026-10-15 无否决意见；存下并重放的 declaration 用户 2026-10-15 批（D6 第 1 条）、2026-10-17 随 rev7-C2 撤回，
    改为 3E 之后一次 `map_contexts`——一个 Opus agent 核实代价只是计划文字（`reviews/2026-10-17-r7c2-cost-verification.md`），
    用户"验证通过则支持"；块内 notes 的 tag-only attribute 用户 2026-10-15 批（rev6-C16）；替换 2026-10-13 批的"接受为
    已知差异"）。缺陷：heavy locale、class 块之后 theory 层对 record 值裸写 `cases r`/`induct r`，Induct 表在 record
    类型下只有 typedef 全局登记的 `Abs_p_ext_cases`/`Abs_p_ext_induct`（typedef.ML:259-271），静默选中它，目标里出现
    `r = Abs_p_ext y`，`case (fields a)` 报 `Undefined case: "fields"`；父在 theory 层、子在块内时静默选中父的
    `cases_scheme`；嵌套 `assumes` 层里定义的 record，外层、重开的块与 interpretation 拿到带 `A ⟹` 的条件副本。
    `datatype` 在前两处响亮失败、在后一处同样拿到条件副本。修法三部分：
    - **theory 写**：块内背景步 3E 构造 info 时的 `Thm.theory_attributes`（决定 4）把四条规则连 stock 的 attribute
      列表写进 theory 的 Induct 表，不造事实名。这是 stock `apply_facts`"命名、施 attribute、再命名"（global_theory.ML:
      318-342）的中段，决定 2(b) 把事实名给了 target。这是 record 四条规则**唯一**的 theory 写者。
    - **3E 之后一次 `map_contexts`**：紧接背景步 3E，
      `Local_Theory.map_contexts (fn _ => fold (fn (th, atts) => #2 o Thm.proof_attributes atts th) (induct_rules ~~ induct_atts))`
      对（带 unofficial1 hint 的）四条原始规则在当时打开的每一层施 stock 的 attribute 列表——`map_contexts` 作用于每个
      存下的层与当前 context，含存下的第 0 层（local_theory.ML:169-179）；`reset` 把改过的、存下的最顶层交给块内后续
      命令（`top_of`，:160、:167；target_context.ML:37）——非嵌套的块里它就是第 0 层；`map_contexts` 改过每一个存下的层，
      所以在任何嵌套深度结论都成立，内层 `end` 时 `end_nested` 从改过的存下层恢复外层（:452-456）。不存 declaration、
      不重放。之后出现的每一个 context 都从已含 3E 写入的 theory 出发：重开的 `context l begin`（`Locale.init` =
      `init_global thy`，stock locale.ML:574-586，shared :923-938）、`interpretation`/`global_interpretation`/`sublocale`/
      class 的自我 registration（只重放存下的
      tag-only notes）、导入 `l` 的 locale、导入的 theory（Induct 的 merge 是 Item_Net 并集）、`lemma (in l)`（从 theory
      重建）、bundle 的 `unbundle`/`include`/`open_bundle`（包内容没有 Induct 写）、light 块（本来就是这个做法）、
      theory target 与 instantiation/overloading 的 `end`（`exit_global` 给 theory）。Pure 自己的 `Named_Theorems.declare`
      （named_theorems.ML:94-96）与 `Entity.define`（entity.ML:52-57）正是"写 theory 一次、`map_contexts` 一次、不存"的
      形状。放在紧接 3E 之处还是 target 步 2 末尾效果相同（中间没有别的 Induct 写），取紧接 3E。
    - **为什么不再存 declaration**（rev7-C2）：rev6-C16 之后重放不再增加任何覆盖（上一条），而每次重放都把这个
      record 的四条规则顶成最新——对 theory 层定义的子 record 是静默错误：父 `l.p` 在块内、子 `record c = "nat l.p" + y
      :: nat` 在 theory 层，重开 `context l begin` 或 `interpretation I: l` 之后，`proof (cases r)` 对 `r :: c` 选中父的
      `l.p.cases_scheme`（父的 scheme 规则匹配一切子 record 类型；`Item_Net.update x = cons x (remove x)`，
      item_net.ML:78；取最新在前，:46；`cases` 按类型统一检索并顺序尝试，induct.ML:504-516），`case (fields a b)` 不报错
      但 `b` 是剩余扩展而不是 `y`（预测）。删掉重放同时消掉了原 §5.8 (4) 的两处差别（theory 层 `[cases del]` 被重开
      加回；用户自己登记的 `[cases type: l.p]` 规则被重开压下），theory 只剩一个写者，本决定不再按 target 分流，代码净
      减 3-5 行。实际会重放的地方比 rev 7 列的还多（`sublocale`、`subclass`、theory 层 `unbundle`、另一个 locale 里的
      `unbundle`、`include`、`context … includes`），一并消失。
    - **块内 notes 的 attribute 只打 tag、不登记**（rev6-C16）：四条 cases/induct 事实在 ELSE 的 `Local_Theory.notes`
      里用 `[Rule_Cases.case_names ["fields"], Thm.mixed_attribute (apsnd (Rule_Cases.default_consumes 0))]`——
      `default_consumes 0` 正是 stock Induct attribute `mk_att` 的定理一半（induct.ML:307-314、:327、:332、:336），
      登记的事实 tag 与顺序与 stock 一字不差（两棵树都如此；shared rule_cases.ML:216-218 对无 K tag 的规则给 `consumes
      0`；`Rule_Cases.consumes 0` 不是严格等价，`put_consumes` 会覆盖，所以这里是手写复述，第 1 行与 §7.4 核 tag，
      §7.1 的 golden 只覆盖 THEN），但不往 Induct 表写。**不能**用 `Thm.rule_attribute`：`Local_Theory.notes` 经
      `Attrib.partial_evaluation`（generic_target.ML:376），只改定理的 attribute 排在既改 context 又改定理的 `case_names`
      之后会报 `Mixed dynamic attribute followed by static rule`（attrib.ML:348-351），块内每次 `record` 都会死（bundle
      块不是当场死，而是到 `unbundle` 才死：`bundle_notes` 跳过 partial evaluation、`unbundle` 走 `Local_Theory.notes`，
      bundle.ML:128、:135）；也不能把它挪到前面绕开——那会把 `consumes` 烘进存下的定理一次，经 morphism 重建的副本会
      丢光 tag。效果：Induct 表里不再出现 record 规则的条件副本（条件形式的事实 `la.p.cases` 仍在 theory 的事实表里，
      只是不登记），决定 21 的三类失败对 record 自己的事实按构造不发生：(i) theory 上带 `assumes` 的 unnamed context 的
      `q.cases` 副本不再归到 `nat` 下；(ii) locale 内嵌套 `context assumes "1 < k"` 里 record 命令不再抛 THM；(iii) 之后
      的 interpretation 不再抛 THM；bundle 的 `unbundle`/`include` 既不抛错也不归错键。精确地说，只有 cases 副本会引起
      (i)-(iii)——cases 表按第一前提的第一个 Var 归档（`left_var_prem`，induct.ML:123-124、:229）；induct 副本按结论的
      Var 归档（`right_var_concl`，:127、:230），从不抛错、只影响顺序。record 侧不再依赖 light 的窄变体。对 record
      自己的类型，Induct 条目只经 3E 与 `map_contexts` 步产生。
    - 健全性：四条规则是 background theory 的全局定理、无 hyps，record 的 cases/induct 不依赖 locale 假设；`Thm.proof_attributes`
      只写 Induct 的数据槽（`case_names` 是 `Thm.mixed_attribute`，不碰 context）、不打印、不动 simpset，无需 rev6-C1
      那样的守卫（核实报告 §3）。
    - 代价与可观察差别：heavy locale、class 块之后 theory 层 cases/induct 比 `datatype` 强（决定 2(b) 的有利偏离）；
      `[simp]`/`[iff]` 仍不在 theory 层生效（决定 2(b)；class 与有 registration 的 locale 例外，§5.5），形成"cases/induct
      生效、`[simp]` 不生效"的不对称，理由见 §1；块内四条事实不带登记一半的 attribute，与 `datatype` 的 `d.exhaust`
      不同，可观察之处只有：`print_induct_rules` 不列块内副本、导出与实例化处的副本不进表、`case_tac (m :: nat)` 不再被
      条件副本劫持；块内 `declare p.cases [cases del]` 照样按命题删得掉（`del_att` 按命题匹配）；`print_locale!`、
      `print_bundles` 的输出相同。light 带谓词的块之后 `cases r` 不需链 `LF_axioms`（§5.6）；有 `assumes` 时 theory 层
      `declare l.p.cases [cases del]` 撤不掉匿名规则（命题多一个前提，del 按命题匹配），撤法：以无条件命题写一条
      lemma 再 `declare … [cases del]`；无 `assumes` 时删得掉且**保持**删除（不再被重开或 interpretation 加回，与
      theory 层 record 相同）；删后想加回时 theory 副本 `l.p.cases` 的 attribute 已被 Pure 剥掉（generic_target.ML:
      445-447，shared :561-563），要补 `[case_names fields]` 或用 `Record.the_info` 取原规则（§5.8 (4)）。
    - 旧 §10 条目"匿名背景登记需再一处 theory_level"作废（rev 5 的 if/else）；`reviews/2026-10-14-reexam-decision17.md`
      第 3 节对"忽略 morphism 的 declaration"的否定随 rev7-C2 失去对象（不再有 declaration）；§10 原"把匿名规则
      `map_contexts` 进每个打开的层而不存 declaration"的否决条目撤销，改为本决定。
18. （删除，见 §2 开头。）
19. **块固定的类型变量作参数**（方向与"声明为参数的块固定变量保持为参数、不声明直接用的成为隐藏参数"这条规则已批
    2026-10-14；"同一块里 `datatype` 拒绝而 record 接受"——记为决定 2(b) 的有利偏离——用户 2026-10-18 明确；里程碑 4；
    rev5-C8、C36 修正提供方；rev6-C3 与决定 22 改措辞用户 2026-10-17 批；参数顺序：隐藏参数之间按名字排用户 2026-10-17
    定，声明参数在前、隐藏参数在后、按块里的名字排用户 2026-10-18 定——辩论 `wf_ed1080ae-844`，
    `reviews/2026-10-17-hidden-param-order-debate.json`，裁判倾向在前、优势不大，用户选在后；隐藏参数保留块里的名字与
    sort、只给声明为参数的块固定变量换名——R8-C2 (a)，用户 2026-10-18）：不再拒绝。提供方是独立项目
    **`contrib/local_type_abbrev`**（计划 rev 4，2026-10-18；改 Pure 的 type.ML、proof_context.ML、typedecl.ML；独立
    conda 包；本项目依赖它的里程碑 1-3，提供方 2026-10-17 确认）：`type_synonym`/`Typedecl.abbrev` 在右边含块
    固定类型变量时自动分流到局部路径（`Type.add_abbrev_fixed`），新增 `Proof_Context.add_type_abbrev`，局部条目全名按
    proof context 的命名为 `local.p`，条目存在 proof context 的类型签名里、右边存展开形式；没有 `Local_Theory.type_abbrev`。
    引用它的决定：决定 2（开放的 interpretation 不造副本；每个 TFree 都已声明）、决定 3（块固定变量存的 sort 等于块里
    读到的 sort，不一致时响亮报 `Ill-sorted instantiation`）、决定 5（块内严格定义、`local.q` 全名）、决定 8（闭合的
    像给出全局 `Thy.I.p`）、决定 17（头部读取期间重名跳过、取第一个）、决定 20（内容一致的重复副本静默接受、不一致
    报其 §6 第 2 条；用户 2026-10-18 裁定、文案已批）。三处改动只作用于 record 自己的说明里的块固定类型变量（第 0 步
    算一次，同决定 9），theory 层集合为空、三处都是恒等：
    - (a) 用户声明为参数的块固定类型变量保持为参数，背景里用新鲜名建全局 record：换名是对字段类型与父参数的一次代换，
      只换声明为参数的块固定变量（父参数里的同一个变量一起换，否则背景的 `Typedecl.abbrev` 报 `Locally fixed type
      arguments`），每个新鲜名是对 `Variable.names_of lthy` 与全部参数名的 variant；隐藏参数从不换名，所以"隐藏参数之间
      按块里的名字排"按构造成立；`Typedecl.abbrev` 照常（块内 `'a p`）。datatype 侧（datatype 会话 2026-10-18 回复）
      结构上做不到同样的事：BNF 在块自己的 lthy 里构造，固定的 `'a` 过不了其中 typedef 的 `global_type`
      （typedecl.ML:44-56）与 BNF 自己的 `Variable.polymorphic`/`mk_TFrees`，所以 `contrib/local_datatype` 给隐藏参数也换
      新鲜名；两边的差别只在 theory 层事实陈述里的类型变量名（record 印 `?'a`、datatype 印 `?'b`），全局类型的写法
      `nat l.t2` 两边相同，由 datatype 的计划记为已知差异；
    - (b) **隐藏参数** = 出现在 record 的 **record 类型**里的未声明块固定类型变量——字段类型里的，加上解析出的父 record
      经参数实例化后的扩展类型里的（`get_parent_info` 给出；不读 record 自己的扩展类型，那是循环）；`err_extra_frees`
      （:2342-2346）对它们放行。例外（保持 stock）：只落在父的某个**无字段使用**的参数位置的块固定变量不出现在 record
      类型里，不算隐藏参数，stock 的 `Extra free type variable(s)` 照旧（硬算成隐藏参数会让 record 类型缺它、子 record
      的缩写走 stock 路径并预计与背景的全局缩写相撞）；例：theory 层 `record ('a, 'b) ph = w :: 'b`，块内 `record d =
      "('a, nat) ph" + y :: nat` 报 `Extra free type variable(s) 'a`，而 `"(nat, 'a) ph"` 成功、`'a` 成隐藏参数。
      **参数顺序**：全局 record 的参数表 = 声明参数按头部顺序 @ 隐藏参数按名字（短名在前、再字典序：`TFrees.keys` 的
      顺序，term_items.ML:75、:136 的 `fast_string_ord`，library.ML:956；与 `Generic_Target.define` 给定义补额外类型变量
      时相同，generic_target.ML:265-267、:272；只借它的名序，不借它"放前面"的位置）；`_scheme` 再加 `'z`，所以隐藏参数
      落在声明参数与 `'z` 之间，用户文档必须写明这一句并带 `('b, 'z, nat) l.lpq_scheme` 误绑的例子（§5.8 (25)）。这一份
      参数列表同时喂给背景的全局缩写（`Sign.add_type_abbrev`）、`make_info` 的 `#args`、`alphas_ext`（`_ext` 也按它）、
      打印翻译与 `print_record`。
      名字与 sort：每个隐藏参数就是说明里那个 TFree，名字与块里的 sort 都不变（class 块里是 base sort，class.ML:339-343；stock 在
      record.ML:1866、:594/:605、:2343 一路保持），预测后果：class `end` 之后 `nat c.p` 即使 `nat` 不是 `c` 的实例也被
      接受。块内 `Typedecl.abbrev` 分流到局部缩写 `p = 'a l.p`、`'z p_scheme = ('a, 'z) l.p_scheme`（`syntax = true`
      declaration，interpretation 时经 morphism；实例化后仍含 schematic 变量时按提供方决定 2 不造 `I.p`，Pure 报
      `Undefined type name`，写出实例类型即可）；
    - (c) 有局部缩写时不加全局 `l.p` 的 `type_alias`。
    - **两条缩写的写入顺序**（rev7-C3；范围按 R8-C4）：全局缩写 `…p`/`…p_scheme` 必须写在 target 步 1 的
      `Typedecl.abbrev`（局部路径）**之前**，这样 `local.p` 后写、赢得短名 `p`——后写的条目赢短名（`declare` 用
      `update_list`，`transfer_syntax` 的合并只把本地没有的 theory 名字补到前面，name_space.ML:141-142、:593；
      proof_context.ML:430-440）。顺序只在 background naming 就是 theory 自己的 naming 的 target 里可观察：theory 上的
      unnamed context（target_context.ML:26，`mandatory_path ""` 不加段）、`instantiation`（class.ML:718）、`overloading`
      （overloading.ML:202）——那里全局条目 `T.r`/`T.lp` 与局部条目争同一个短名，反过来写时块内 `r` 解析成全局条目、报
      `Bad number of arguments for type constructor: "T.r"`（预测；`T` 是所在的 theory）。heavy locale、light 块与
      experiment 里强制的 locale 段让顺序无害（§4）；class 块预计同（第 6e 行的 class 变体核）；bundle 不固定类型变量。
      作者取的写法：target 步 1 开头、只在有隐藏参数时，用一次独立的 `Local_Theory.background_theory` 写全局缩写
      （自动得到 background naming，local_theory.ML:225-235），然后才 `Typedecl.abbrev`；§3.1 第 2 步与 §8 第 4 步按此
      写；变异检查放在 theory naming 的两个叶（第 6e-v 行）。
    例子（`locale l = fixes f :: "'a ⇒ 'a"`）：`record 'b lpq = gq :: "'a ⇒ 'a"  h :: 'b`，`'b` 声明、`'a` 隐藏，全局
    `('b, 'a) l.lpq`，块外 `(bool, nat) l.lpq`、`('b, nat, 'z) l.lpq_scheme`；`interpretation J: l Suc` 之后 `bool J.lpq`
    = `(bool, nat) l.lpq`；同块子 record `('b, 'c) lpc = "'b lpq" + k :: 'c` 的全局参数表 `('b, 'c, 'a)`，块外
    `(bool, int, nat) l.lpc`。无声明参数的例子：`record p = g :: "'a ⇒ 'a"`，`'a` 隐藏；`record d = p + k :: nat` 的
    record 类型 `('a, unit l.d.d_ext) l.p.p_ext` 含 `'a`（`d_ext` 只有 `'z` 一个参数，record.ML:1544、:1865-1866），
    所以 `d` 也得到隐藏参数 `'a`，块内写 `d`、块外写 `nat l.d`。父的解析由决定 22 负责（父写全名时参数里只有声明为
    参数的块固定变量换新鲜名）。落地前按决定 9 的过渡行为拒绝。本决定同时保证 Spec_Rules 条目与六条事实里不出现
    块固定的 TFree：存下的规则全部出自 stock 代码、已做成 schematic（drule.ML:244-257、global_theory.ML:404-407），
    Spec_Rules 的头从这些规则算出（record.ML:1835-1837）。对 `datatype` 的偏离：同一块里 `datatype 'a t1 = T1 'a` 报
    `Locally fixed type argument "'a" in datatype specification`（bnf_fp_def_sugar.ML:2305-2310）、`datatype t2 = T2
    "'a ⇒ 'a"` 报 `Extra type variables on right-hand side`（:2335-2338），record 里程碑 4 起两种都接受——决定 2(b) 的
    第三条有利偏离（用户 2026-10-18）；`contrib/local_datatype` 落地后此偏离消失。打印：带隐藏参数的 record 类型在
    块内印成 `'a l.p`、重开块里同、theory 层 interpretation 后印 `nat l.p`（record 自己的打印翻译从全局名与全部参数
    重建，record.ML:801-823；没有 `p` 的 type_alias）——用户 2026-10-15 接受为已知差异（§5.8 (20)），改进若做归
    local_type_abbrev 的回折打印统一做（在类型层对局部缩写回折，就先于 record 的打印翻译起效，record 不另做；目前无人
    排期）。两个带隐藏参数的同名 record 在 `locale m = l1 + l2` 里的冲突由 local_type_abbrev 的决定 5（块内严格定义）、
    17（头部读取期间跳过重名、取先登记的；随其里程碑 4 才有）与 20（内容一致的副本静默接受，不一致报其 §6 第 2 条）
    决定，record 只引用（§5.8 (21)；§7.3 第 10 行与那边 §5 第 8 行对照）。
20. **块内事实别名**（已批 2026-10-15；集合的导出随 rev5-C9；concealed 的 def 事实也加别名改了原批文字，用户
    2026-10-15 批）：背景登记的事实在块内取得与 theory 层相同的短名。别名集合**从背景步实际新增的事实导出**，只在
    ELSE：扫两次 theory 事实名字空间——`Name_Space.get_names (Facts.space_of (Global_Theory.facts_of thy))` 过滤掉区间
    前已 `Facts.defined` 的名字（含动态事实）——分别覆盖背景步 1-2E 与 3E 新增的；断言每个名字在 `Local_Theory.full_name
    lthy binding` 之下，不在的跳过并加代码注释（不用 `Fail`，它逃出 :2365 的包装）；别名 binding 按条目自己的 suppress
    标记逐段重建再套 `record_qualify`（typedef 的非强制 `p_ext` 限定词由此自动得到）。不用 `Facts.dest_static`：它强制
    全部 lazy 事实并跳过动态事实（facts.ML:222-239）。覆盖十条、`ext_*`、`p_ext_def`、concealed 的 def 事实（用户写
    `p.make_def`、`p.x_def`；别名保持 concealed，name_space.ML:534-543）、`_Tuple_Iso` 的 def、`p_ext` 与每个
    `p_inner<i>` 的 typedef 事实、typerep 与 `add_code` 的实例事实、3E 里插件造的事实（HOL 无；AFP Constructor_Funs 的
    名字在前缀下）；`extension_definition` 不改。机制照 Pure 的 `Local_Theory.add_thms_dynamic`（local_theory.ML:
    302-314），合成一个私有函数：先 `Local_Theory.map_contexts (fn _ => fn ctxt => Proof_Context.transfer_facts
    (Proof_Context.theory_of ctxt) ctxt)`（整表合并，遍历全部可见事实，与 `named_theorems` 同价；`Facts.alias` 要求
    条目已在本地表里，name_space.ML:537），再一个与 `const_alias`/`type_alias` 同种的 declaration（`syntax = true,
    pervasive = false`，local_theory.ML:399-404；`add_thms_dynamic` 用 `syntax = false`，这里用 `true` 为了 light 存
    下它）对全部别名对做 `Context.mapping (Global_Theory.alias_fact b' name) (Proof_Context.alias_fact b' name)`，
    `b' = Morphism.binding phi b`。放在背景步 3E 之后。效果：块内 `p.select_convs`、`select_convs`、`p.make_def`；
    `end` 后 theory 层仍只有 `l.p.select_convs`——只对**没有 registration 的 heavy locale** 成立：class 的自我
    registration 与已有的 interpretation 会把别名带到 theory 层（`c_class.p.select_convs`、`I.p.select_convs`，
    预测）；重开块时重放；`interpretation I: l` 产生别名 `I.p.select_convs`（指向同一事实对象）；theory 上的 unnamed
    context 与 `instantiation` 里是同名重加、无害；light 存 `syntax = true` 的 declaration，重开与 interpretation 时
    重放（§5.6）。六条事实不加别名：后加的别名会排到访问名列表前面（name_space.ML:141-142、:534-543），在 heavy 块里
    遮住带 attribute 的块内副本。退路（§10"退路（不是否决）"）：按 stock binding 手写清单、全名读返回对象的 name hint。代价：块内每个
    record 两次事实名字空间扫描、一次 `transfer_facts`（每个打开的层）、约 40 条（两字段）到数百条（300 字段）别名；
    theory 层零代价；§7.5 量。副作用见 §5.8 (14)。
21. **嵌套 `assumes` 层导出副本的 Induct 归档（rev4-C6）**（已批 2026-10-14：阻塞依赖；D3 的确认等 light 施工后正式议，
    用户 2026-10-15；rev6-C16 后对 record 自己的事实消解）：对 record **自己的**六条事实，rev6-C16 让块内 notes 不再
    登记 Induct，三类失败——(i) theory 上带 `assumes` 的 unnamed context 的条件副本归到 `nat`（或裸类型变量时归到通配
    键）下干扰别的类型的 `cases`；(ii) `THM "No variables in major premise of rule"`：locale 内嵌套 `context assumes
    "1 < k"`、theory 上对闭命题的 `context assumes`、theory 上双层嵌套的外层；(iii) registration 副本丢掉全部 tag
    （`Thm.instantiate_frees` 后 `Thm.generalize` 置 tags 为空）、interpretation 时抛 THM——都不再发生，record 侧不再
    依赖 light 的窄变体。精确地说只有 cases 副本会引起 (i)-(iii)（`left_var_prem` 归档，induct.ML:123-124、:229）；
    induct 副本按 `right_var_concl`（:127、:230）归档，只影响顺序。THM 的规则句：只在导出副本的第一前提里没有 Var 时
    发生——嵌套假设只用外层的 Free 或是闭命题；`fixes n :: nat assumes "0 < n"` 形式（第 4b、9b、7g 行）导出后 `n` 成
    `?n`，属 (i) 类而不是 THM；`instantiation`/`overloading` 内的嵌套层同样分属 (i)/(ii)（class.ML:731；overloading.ML:
    210；第 18e 行核 overloading 那一半）。仍成立的是 `typedef`、`datatype` 在同样位置的同类失败——它们由 light 的
    **窄变体**处理，light 自己的原话（主仓库 `ai-artifacts/LIGHT_LOCALE_HANDOFF.md` 条目"`record` 会话的请求与裁决
    （2026-10-15）"）：「只在证明 context 之上有至少一层嵌套 `assumes` 时打标签；K = 生成那一份副本时导出加上的前提数」，
    原本不带标签的定理也打。用户批的是 light 作者 09:32:05 的这一版重述，不是 09:09:43 的"只给命名 target 之上的嵌套
    `assumes` 块粘上的前提打"（`LIGHT_LOCALE_PLAN_REV37.md` §8 第 3 步，窄变体的唯一陈述处）；rev 5 至 rev 8 引的是被
    取代的那句，rev 9 改正。light 对我们 2026-10-14 请求的裁定（用户在 light 会话，2026-10-14 17:47 本地）：接受窄变体、
    落 light 里程碑 3
    （其计划 §4 第 14-15 项）；K 分三种情形（嵌套块的 theory 副本；`standard_notes` 第 j 层按每层前提数；heavy locale 的
    theory 副本，谓词前提在最前）；普通 heavy locale 事实不打 tag，light 测试 1 含义不变；tag 只经 `Thm.get_tags`/
    `eq_thm_strict`/`rule:` 可观察；(c) 点在同一改动里核；light 决定 9 (i) 与 §5.6 届时修订；要求我们把依赖注指向其
    §4 第 14-15 项、不打 generic_target.ML（本项目遵守）；它可以提前日程。light 2026-10-16 又把 K 修订为 K = count_of th
    + 新粘的前提数（覆盖导入 light 的 heavy locale 的嵌套层；对 7c-7j 的孪生 count_of 为 0，值不变，只作信息）。light
    2026-10-18 的通报：窄变体**保留**，作为里程碑 3"第一项"之后的单独一步，已写进其草案 `ai-artifacts/
    LIGHT_LOCALE_M3_KEEP_K_PLAN.md` §7（主计划条目随草案评审加入），落地前先实测波及面（HOL 约 86、AFP 约 733 处会粘
    前提的嵌套 `assumes` 块）；第一项只处理已带 K 的定理（每份副本 K′ = K + d，其他 tag 不保，与 stock 一致），所以
    7c-7j 的孪生列与探针 (e)/(q) 仍等窄变体；theory 上 `assumes` 块里的 `p.cases` 是 theory 副本，还要等窄变体加
    theory 副本的落点。**D3 四问的现答**（light 2026-10-18；正式确认仍等 light 施工完成）：(a) 变体已入 light 计划
    （草案 §7）；(b) K 经登记/激活 morphism 以 K + d 存活；(c) 非 `Named_Target` 的 target 与 bundle 的覆盖留给窄变体
    那一步定（第一项里 bundle 与 declaration 路径保持 stock；`Locale.add_facts` 存进 target context 的记录副本第一项已
    覆盖；light 草案 `LIGHT_LOCALE_M3_KEEP_K_PLAN.md` §7 的待决点 (5)"bundle 与非命名 target"——第 8b、18e 行的孪生列
    标 D3 指的就是它）；(d) ctr_sugar.ML:221-225 不在其范围。D3 时另附：light 不需 record 就能跑的 typedef 孪生验收行（rev5-C12
    第 7 项；对 light 的要求，须用户批准）。**应急**（rev5-C4 作者修法，rev 6 写入、rev 7 误删、rev 8 恢复）：若 light
    评审否决或改形使 §7.3 第 7c-7j 行的 `typedef`/`datatype` 孪生列无法转绿，本决定回到用户；record 不加绕法、不打
    generic_target.ML；里程碑 1 开始时在共享树重跑探针 (e)，缺则报用户。注记：删掉重放（决定 17）后，record 自己的块
    被重开时不再把 record 规则顶回通配键下条件副本之上——这与 theory 层 record 相同，归本决定与窄变体处理。§7.3 第
    7b、7e-7k 行的 record 列是普通 gate 行；第 7c、7d 行只有孪生列；这些行的孪生列都以窄变体那一步落地（含 theory 副本
    落点）为前置（7f、7h 的孪生列另待 light 对 (iii) 的正式确认）；裸 `datatype` 在带假设的块里崩在 code 插件的
    `dest_equals`（`TERM`），探针与孪生写 `datatype (plugins del: code)`。
22. **父 record 按类型解析**（头脑风暴 `wf_0caab246-07c` 的综合；规则、新接受输入、文案变化类、残余用户 2026-10-17
    接受；落里程碑 1 作者自决；解析函数不导出；不支持无字段使用的参数经 synonym 作父——作者裁定，用户 2026-10-18
    确认）。stock 的 `read_parent`（:2298-2302）用 `Proof_Context.read_typ_abbrev`
    （缩写模式，`normalize = false`，type.ML:240、:278-292）读父类型、取头常量为 record 名，`add_parents`（:579-596）
    查不到就报 `Unknown parent record`；record 类型本身是缩写，所以 `nat p`、`nat l.p` 可用——无隐藏参数的 record 在
    块内的 `p`、`i.p` 与 interpretation 后的 `I.p` 也是以 record 名为头的 type_alias，stock 路径本来就接受（`i.p` 为
    预测，未沿 locale.ML 追）——而任何**别的**缩写（`type_synonym q1 = "nat p"`、带隐藏参数的 record 经 interpretation
    造的 `I.p`、块内带隐藏参数的 `local.p`，后两者里程碑 4 起）都被拒。规则：**父写的是哪个类型，父就是那个类型所代表
    的 record。** 头常量是 record 名——照 stock 原样（写的参数原样用）；否则把写的类型在读取 context 里用
    `Proof_Context.cert_typ`（默认模式）展开，找出唯一一个其 record 类型（用 `get_parent_info` 加 `mk_recordT` 从
    record 表现算——与 `add_record` 随后建子 record 用的是同一函数，所以"子 record 恰好扩展了写的类型"按构造成立，
    不依赖决定 19 怎样建全局缩写）经 `Type.raw_match` 匹配、且每个参数都被确定的 record；匹配不到就把 stock 原来那对
    值原样往下传，stock 自己的代码报 stock 自己的错。
    - 为什么必须匹配而不能顺缩写名追：Pure 存缩写时右边已完全展开（`Type.add_abbrev` 用 `mode_syntax`、`normalize =
      true` 证书化右边，type.ML:239、:694-704），`q1`、`I.p`、`local.p` 展开一步就落到扩展类型，没有经过 record 名的
      链条。唯一性：扩展类型构造子属于且只属于一个 record，record 类型是末端为 `unit` 的扩展类型链。record 自己的打印
      翻译（:801-826）今天就做这个反向匹配。
    - 为什么用默认模式证书化：它查的是 **proof context** 的类型签名（含 local_type_abbrev 的 `local.p` 与全局的
      `I.p`、`q1`），不需要按 target 分情况；它重复 stock 对参数的证书化（:2322-2324），stock 会拒绝的语法类型
      （`logic`、`letbinds`）照旧拒绝、文案照旧。`raw_match` 不看 sort，sort 检查留给 stock 的 `add_parents` 跑一次。
    - 解析只在 `add_record_cmd` 的读取路径（决定 6）；typed API 收 record 名不解析；不导出解析函数（AFP 的 Optics、
      Clean、Isabelle_DOF 各有一份 `read_parent` 拷贝，它们的命令仍只认 record 名，§5.8 (23)）。
    - **决定 2(a) 按构造**：stock 接受的输入头是 record 名，走原表达式，匹配代码不求值；stock 读取阶段拒绝的（未定义
      类型、参数个数、schematic 变量、非 `Type`）在解析之前就由不变的代码报出；头是 record 名而 `add_parents` 拒绝的
      （ill-sorted）文案相同；头不是 record 名且匹配失败的报 stock 的 `Unknown parent record`。**新接受的输入**（§5.1
      列）：全局 `type_synonym` 及其链条、任意参数顺序；任何展开后是 record 类型的类型表达式——`(nat, unit) p_scheme`
      （它就是 `nat p`）、扩展类型 `(nat, unit) p_ext`、record 类型语法 `⦇x :: nat⦈`；丢掉写出的类型变量的 synonym
      （`'x qd = "nat p"`，`'x` 被忽略，与 stock 在字段类型里忽略它一样）；里程碑 4 起带隐藏参数的 record 的块内
      `local.lp`、`i.lp`、theory 层 interpretation 造的 `I.lp`（闭合像，提供方决定 8）、无限定词 interpretation 之后
      theory 层的 `lp`（全局缩写 `<leaf>.lp`，第 6e-ii 行的叶；父为 `([nat], T.l.lp)`）。**文案变化类**（用户 2026-10-17 接受）：父是
      synonym 且另有第二处错误（重复字段、`more` 作字段名、多余类型变量、record 名重复、`add_parents` 的 sort 检查、
      `definition` 内部错）时报第二处错误的 stock 现成文案，而不是 `Unknown parent record "T.q1"`。**残余**（§5.8
      (22)）：有无字段使用的参数的 record 经 synonym 作父（`qph = "(nat, bool) ph"`）仍被拒，展开丢掉了 `nat`、无从恢复，
      绕法按 record 名写全参数；块内带隐藏参数又带无字段用的声明参数的 record 同理。用户 2026-10-17 说过"能支持这种
      畸形 synonym 也是很好的"，作者裁定不支持（填 `unit` 是对父信息说谎、填新鲜变量平添参数），用户 2026-10-18
      确认（§10）。打印不回折：解析出的父显示为 `nat p`、`nat l.p`，无隐藏参数的 record 在 interpretation 之后显示
      `nat I.p`（stock 对别名的行为），不显示 `q1`。
    - 代码：两个私有函数 `record_of_type`（约 14 行）、`resolve_parent`（约 9 行）加 `read_parent` 一行改动（§3.7）；
      不加文案、不加 ML 名、record.ML 之外零改动；stock 接受的输入多一次 `Symtab` 查找；synonym 作父时多一次 `cert_typ`
      与一次对 record 表的线性扫描（首个匹配即停、失败时扫完；每个被访问的 record 付 `get_parent_info`、`mk_recordT`、
      `raw_match`），§7.5 (6) 量；若实测可观，先比较 `fst (#extension info)` 与 stock `last_extT`（:285-290）给出的
      最内层扩展类型再建模式。对 local_type_abbrev 的文档性请求（它计划 §4 末段曾预测 `read_parent` 对 `Type
      ("local.q", [])` 报 `Bad parent record specification`，实为 `Unknown parent record "local.q"`，决定 22 后在 `local.q`
      展开为 record 类型时接受、否则仍报同一文案）经用户批准于 2026-10-17 发出，当日被采纳。

## 3. `record.ML` 补丁（精确改动点；行号为 stock 副本的 record.ML）

### 3.1 总形状

两个私有定义：

```sml
val theory_level = Named_Target.is_theory lthy;

(*a background step whose typedef info and Ctr_Sugar entries are also visible in every open context*)
fun background_step f lthy =
  lthy
  |> Local_Theory.background_theory_result f
  ||> Local_Theory.map_contexts (fn _ => fn ctxt =>
        let val thy = Proof_Context.theory_of ctxt
        in ctxt |> Typedef.transfer_info thy |> Ctr_Sugar.transfer_ctr_sugars thy end);
```

`map_contexts` 作用于每个存下的层与当前 context（local_theory.ML:169-179）；`background_theory_result` 已把每层
transfer 到新 theory（:217-221），所以 `Proof_Context.theory_of ctxt` 是更新后的 theory；`Local_Theory.reset` 与
`end_nested` 都从存下的层恢复（:167、:452-455），补写因此在命令之间持久。两个 transfer 带的是整表、按键合并：
context 已有的键保留、只加 theory 多出的键；两张表只增不减，context 缺的键只能来自 context 创建之后的 theory 写，
所以块里已有的条目不会被替换（light 里程碑 3 的 hunk 落地后重核）。幂等、不抛错、无需列类型名（17 字段以上的
`p_inner<i>` 一并覆盖）。

`local_add_record overloaded (params, binding) raw_parent raw_fields lthy`，按顺序：

0. **检查**（§3.7），都在 lthy 上；读 `codegen` 与 `typedef_overloaded`（决定 11）；选 `zeta` 与块固定类型变量的集合
   （决定 9）；里程碑 4 起算隐藏参数与参数顺序（决定 19 (b)，按块里的名字），只给声明为参数的块固定变量换新鲜名
   （字段类型与父参数里一次代换），隐藏参数不换名（决定 19 (a)）。
1. **背景步 1**：`Sign.qualified_path false binding` → stock `extension_definition`（:1531-1694，`extension_definition`
   自身不改；`zeta` 与 `overloaded` 由参数传入见 §3.6）→ 构造打印翻译（:1941-1957）→ `Sign.print_translation`（:2056）。
2. **target 步 1**：`Typedecl.abbrev (binding, map #1 alphas, NoSyn) recT0` 与 `Typedecl.abbrev
   (Binding.suffix_name schemeN binding, …) rec_schemeT0`（stock 在 :2058-2061 的同一位置做 `abbrev_global`，它就是
   `theory_map_result` 包的 `abbrev`，typedecl.ML:130-131）。必须在扩展阶段之后：`Sign.add_type_abbrev` 要在 lthy
   里 certify 右边的 `p_ext`。后面的 stock 代码不依赖缩写——`recT0`/`rec_schemeT0` 由 `mk_recordT` 建成
   `Type (ext_tyco, …)`（:1910-1918），只有打印翻译按名字提到它。里程碑 4 起有隐藏参数时：先用一次独立的
   `Local_Theory.background_theory` 按决定 19 的那一份参数列表写全局缩写（`Sign.add_type_abbrev`），然后才
   `Typedecl.abbrev`（它自动分流到局部路径）——顺序不能反（决定 19；只在 theory naming 的 target 里有后果）。
   `recT0`/`rec_schemeT0` 里的隐藏参数就是块固定的原变量、左边的参数只有声明的那些，所以提供方"右边含块固定变量才
   分流到局部路径"的条件按构造成立，不需要反向代换。
3. **背景步 2**：`qualified_path` → 常量声明（:2062-2066；选择子的 mixfix 按决定 16 (i)）→ `Global_Theory.add_def`
   （:2067-2070）→ 全部命题构造与十组 `Goal.prove_sorry_global defs_thy` 证明（:2073-2231，一行不改；:2233-2237 的
   结果模式改）。在 :2238 **之前**结束。
4. **一个私有值 `six_facts`**，在分支之前算一次：(事实 base name, stock 的 attribute 列表) 对，分两个子表——四条 Induct
   条目 `[("induct_scheme", induct_type_global (suffix schemeN name)), ("induct", induct_type_global name),
   ("cases_scheme", cases_type_global (suffix schemeN name)), ("cases", cases_type_global name)]`（record.ML:
   1489-1491 的值、:2250-2255 的顺序）与 `[("simps", [Simplifier.simp_add]), ("iffs", [iff_add])]`；另一份只打 tag 的
   四条列表 `[Rule_Cases.case_names ["fields"], Thm.mixed_attribute (apsnd (Rule_Cases.default_consumes 0))]`（决定 17；
   `consumes 0` 是手写复述，第 1 行与 §7.4 核 tag）。使用处：THEN 的 note 列表尾与第二次 note、THEN 的
   `map_contexts` 步、ELSE 的 notes（tag-only 列表）、ELSE 的 3E 与紧随其后的 Induct `map_contexts` 步（stock 列表）。
   ELSE 另算两个私有值，在 target 步 2 之前算一次、3E 与 `map_contexts` 步用同一值：`induct_rules` = 四条按决定 4 打过
   unofficial1 hint 的原始规则，顺序 induct_scheme、induct、cases_scheme、cases（record.ML:2250-2255 的顺序）；
   `induct_atts = map #2` 取 `six_facts` 四条 Induct 条目的 stock attribute 列表，同一顺序。
5. **`if theory_level then … else …`**（决定 16 (ii)）。两个私有阶段函数：`note_record_facts tail`（stock :2238-2255：
   `declare_default_eqns_global derived_defs` 加一次 `note_thmss`，列表 = 十条不带 attribute 的事实 @ `tail`）与
   `finish six : theory -> theory`（stock :2266-2288：`make_info`、数据表、`add_code codegen`、`add_ctr_sugar`、
   `fold add_spec_rule`）。
   - **THEN，背景步 3T**：`note_record_facts (四条 attributed 条目)` → stock 第二次 `note_thmss`（`simps`、`iffs`，
     :2257-2264）→ `finish`（六条取自本步自己的 note 结果）——即 stock :2238-2288、同一次 14 条的调用，值与 stock
     相同。随后 `map_contexts` 步：
     ```sml
     Local_Theory.map_contexts (fn _ => fn ctxt =>
       ctxt
       |> Config.put Raw_Simplifier.simp_trace false
       |> Context_Position.set_visible false
       |> Proof_Context.note_thmss "" [(Binding.empty_atts, six_noted)] |> snd
       |> Config.restore Raw_Simplifier.simp_trace ctxt
       |> Context_Position.restore_visible ctxt)
     ```
     `six_noted = map (apfst single) (四条登记后的对象配 stock 列表) @ [(simps', [Simplifier.simp_add]), (iffs',
     [iff_add])]`。关闭放在**函数体内**、对每个被施加的 context 各做一次（rev6-C1）：包在整步外面只改当前 lthy，而
     `map_contexts` 还施到存下的第 0 层 context，那份由 `init_global` 建、继承 theory 层的 `declare [[simp_trace]]`
     （config.ML:142、context.ML:612-613），`insert_rrule` 的跟踪不看可见性（raw_simplifier.ML:465-477、:514-515），
     会多打 "Adding rewrite rule"。不造名字、不进事实表、不碰 theory。普通 theory 层上 lthy 随即被丢弃，这步只服务
     `context -` 形式与 ML 调用者。
   - **ELSE，背景步 2E**：`note_record_facts []`（十条）。
   - **ELSE，target 步 2**：决定 13 的检查；每个常量一次 `Local_Theory.const_alias`（含 `more`、更新、派生、`p_ext`、
     `Rep_p_ext`/`Abs_p_ext`、`_Tuple_Iso`）；`p_ext` 一次 `type_alias`；每个带 mixfix 的字段一次 `notation`；一次
     `Local_Theory.notes` 登记六条带 attribute 的事实，binding 经 `record_qualify`，attribute 用 `Attrib.internal ⌂ o K`
     包——四条 cases/induct 用 tag-only 列表，`simps` 用 `[Simplifier.simp_add]`、输入 `sel_convs' @ upd_convs'`，`iffs`
     用 `[iff_add]`、输入登记过的 `ext_inject`（**不用** `Attrib.case_names` 源形式——它多加一个 `cases_hyp_names`
     tag，attrib.ML:564-570）；对 `sel_convs' @ upd_convs' @ derived_defs'` 每条一次 `Spec_Rules.add Binding.empty
     Spec_Rules.equational [head] [rule]`（头部计算与 stock `add_spec_rule` 共用一个私有函数）。不存任何 Induct 的
     declaration（决定 17）。
   - **ELSE，背景步 3E**：`qualified_path` → 按决定 4 构造六条对象（四条经 `Thm.theory_attributes` stock 列表——这就是
     theory 侧的 Induct 写——再 unofficial2；`simps`/`iffs` 经 `name_thms unofficial2`）→ `finish six`（含 stock
     `add_ctr_sugar`，插件 K true，与 THEN 同一段代码）。代码处注释："the only theory write of the record's Induct
     rules"。
   - **ELSE，Induct 的 `map_contexts` 步**（决定 17）：紧接 3E，
     `Local_Theory.map_contexts (fn _ => fold (fn (th, atts) => #2 o Thm.proof_attributes atts th) (induct_rules ~~ induct_atts))`
     把四条带 hint 的原始规则连 stock 列表施进当时打开的每一层（含存下的第 0 层）。不打印、不碰 simpset，无需
     rev6-C1 那样的守卫。
   - **ELSE，别名步**（决定 20，target 步）：`transfer_facts` 加别名 declaration，一个私有函数。
6. 结束。

背景步的分段为了保持 stock 的全局登记顺序：类型缩写在扩展阶段之后、常量之前；十条事实在六条之前；代码事实
（`equal_p_ext_def` 等）在六条之后；`notation` 在背景步 2 之后加产生式，中间只有 `NoSyn` 更新、不加产生式
（mixfix.ML:243-274）。theory 层：背景 1、target 1、背景 2、背景 3T、map_contexts；块内：背景 1、target 1、背景 2、
背景 2E、target 2、背景 3E、Induct 的 map_contexts 步、别名步。

### 3.2 `Iso_Tuple_Support`（:59-176）与 `extension_definition`（:1531-1694）

一行不改（`zeta` 的传入见 §3.6）。包括 :104 的 `Named_Target.theory_map_result`（背景步里它作用在纯 theory 上，与
今天相同）、:124 的 `Sign.add_path`（源码 FIXME，照旧）、:1684-1690 的 `note_thmss`。

### 3.3 数据表与读取函数（:362-611）

一行不改。`Record.Data`、`Iso_Tuple_Thms` 保持 `Theory_Data`；全部读取函数保持 `theory` 类型。决定 22 的
`record_of_type` 只读 `Data`。

### 3.4 语法层（:615-927；Record.thy 不改）

- `split_args` :621-628 多收 `ctxt`：`if Proof_Context.intern_const ctxt name = field orelse can (unsuffix name)
  field then …`，其余逐字不变（决定 7）。调用处 :651、:699 传 `ctxt`。
- `field_update_tr` :715-717 不改：派生名 `"<原文>_update"` 经 `Syntax_Phases.decode_term` 的 `check_const` 走
  name space，块内靠 `const_alias` 解析。探针 `syn_names`（2026-10-11 跑；`ai-artifacts/probes/syn_names.thy`、
  `syn_names.sym.thy`、`syn_driver.ML`、`syn_run_syn_names.ML`，stock HOL 上 `ML_process`；结果文件未存）：在 locale
  里用 `Local_Theory.const_alias` 给背景常量加别名后，`⦇x = 1⦈`、`r⦇x := 1⦈`、`x r` 的读与打印都经别名解析，与
  theory 层同形。
- 其余全部不改：`Theory.setup` 装的全局 parse translation（:728-735）、打印翻译（:740-927）、`print_record`
  （:2434-2444）。

### 3.5 simproc 与 tactic（:931-1481）

一行不改。它们经 `Proof_Context.theory_of ctxt` 读 `Theory_Data`，在块内、`end` 后、导入的 theory 里都看到无条件
的条目。`split_simp_tac` 读 `#induct_scheme`（:1408、:1444）——块内 record 的那条是决定 4 的带 tag 规则。

### 3.6 `definition`（:1841-2292）

拆成 §3.1 的阶段函数，由 `local_add_record` 用 `background_step` 依次调用、中间插 target 步；阶段之间传递的值是
stock 今天在一个函数体里顺着传的那些。每个阶段开头自己 `Sign.qualified_path false binding`（`background_theory_result`
进出各装一次 naming，local_theory.ML:225-235），末尾不必 `restore_naming`。每个 `timeit_msg` 留在它原来包的那段
代码外（决定 11）。改动点：

- :1881 `zeta` 改由参数传入（决定 9）；`extension_definition` 的 `overloaded` 参数是 `local_add_record` 按决定 11 算好
  的值（stock 原样传命令标志）。
- :2056 留阶段 1 末尾；:2057-2061（`restore_naming`、两个 `abbrev_global`）删除，改为 target 步 1。
- :2063-2064 选择子声明的 mixfix 参数：`if theory_level then field_syntax else map (K NoSyn) field_syntax`。
- :2238-2255 成为 `note_record_facts tail`；:2257-2264（`sel_upd_simps`、`sel_upd_defs`、第二次 note）留在 THEN 的
  3T 里；ELSE 的 3E 由决定 4 构造六条对象。`sel_upd_simps`、`sel_upd_defs`、`add_equalities`（:2276）、`add_splits`
  （:2279-2283）、`put_sel_upd` 照 stock 用它们今天用的对象。
- :2266-2288 成为 `finish six`；:2286 `add_code` 多传 `codegen`，`simps` 参数是决定 4 的 `simps` 对象；:2287 的
  `add_ctr_sugar` 改调 `record_ctr_sugar`（literal 抽出，值不变）。
- :2289 `restore_naming` 删除。
- `definition` 多返回 target 步需要的名字与定理：常量全名表（选择子含 `more`、更新、`make`/`fields`/`extend`/
  `truncate`、`p_ext`、`_Tuple_Iso`）、`ext_tyco` 与 typedef 的 `Rep`/`Abs` 全名（经 `Typedef.get_info_global thy
  ext_tyco`，binding 用 `Typedef.default_bindings`）、每字段 `(Const (c, T), mx)`、原始证明结果与登记后的十条、
  `ext_inject`、Ctr_Sugar/Spec_Rules 所需的 `ext`、`sel_convs'`、`upd_convs'`、`derived_defs'`。事实别名的集合由
  `local_add_record` 扫名字空间得到（决定 20），不经 `definition`。

### 3.7 `add_record`、`add_record_cmd`、命令（:2294-2444）

- `read_parent` :2298-2302 改一行：`Type (name, Ts) => (SOME (resolve_parent ctxt (Ts, name)), fold Variable.declare_typ
  Ts ctxt)`；读取仍用 `read_typ_abbrev`、`Bad parent record specification` 分支与对**写出的**参数的 `declare_typ`
  不变。两个私有函数放 `add_record` 的 local 块开头（:2296），只用更早定义的 `varifyT` :221、`get_parent_info` :602、
  `mk_recordT` :1713、`get_info` 与 `Data`（打印翻译 :804、:810 用的是同一个 `varifyT` 惯用法）：
  ```sml
  (*the record whose record type is T, with T's arguments for its parameters*)
  fun record_of_type thy T =
    let
      val idx = maxidx_of_typ T + 1;
      fun instance (name, {args, ...}: info) =
        let
          val recT =
            varifyT idx
              (mk_recordT (map #extension (get_parent_info thy (SOME (map TFree args, name)))) HOLogic.unitT);
          val tyenv = Type.raw_match (recT, T) Vartab.empty;
          val Ts = map_filter (fn (a, _) => Option.map #2 (Vartab.lookup tyenv (a, idx))) args;
        in if length Ts = length args then SOME (Ts, name) else NONE end
        handle Type.TYPE_MATCH => NONE;
    in Symtab.get_first instance (#records (Data.get thy)) end;

  (*a head that names no record stands for the record whose record type it denotes*)
  fun resolve_parent ctxt (Ts, name) =
    let val thy = Proof_Context.theory_of ctxt in
      if is_some (get_info thy name) then (Ts, name)
      else
        try (Proof_Context.cert_typ ctxt) (Type (name, Ts))
        |> Option.mapPartial (record_of_type thy)
        |> the_default (Ts, name)
    end;
  ```
  `read_fields` :2304-2310 不改，调用时 ctxt 用 lthy。
- 新 `local_add_record`（决定 6）：:2315 `Proof_Context.init_global` 删除、`ctxt` 就是 lthy；:2336 `Sign.full_name
  thy binding` → `Local_Theory.full_name lthy binding`；:2338 `get_info thy` → `get_info (Proof_Context.theory_of
  lthy)`；stock 的四条检查 :2334-2360 与 `err_dup_record` 不变；新增 `err_fixed_params` 作 `errs` 最后一项
  （决定 9，里程碑 4 起删，`err_extra_frees` 里程碑 4 起对隐藏参数放行）；:2361 `error (cat_lines errs)` 不变；在 lthy
  上读 `Config.get lthy codegen`（决定 5）与 `{overloaded = #overloaded overloaded orelse Config.get lthy
  Typedef.overloaded}`（决定 11；`overloaded` 是 `{overloaded: bool}` 记录，record.ML:30、:2313，`extension_definition`
  收它并一路传到 `Typedef.add_typedef`，:1900、:105）；然后
  §3.1 的各步；:2364-2365 的 `handle ERROR msg => cat_error msg ("Failed to define record " ^ …)` 包住检查与全部
  背景步、target 步（§6）。
- 旧 `add_record overloaded spec parent fields = Named_Target.theory_map (local_add_record overloaded spec parent
  fields)`，签名不变、父参数不解析。`theory_init` 的 naming 是 theory 的加 `mandatory_path ""`，`is_theory` 为真，
  结果与 stock 相同（§5.1）。
- `add_record_cmd` :2367-2375 改收 lthy：读参数、父、字段用临时 context（stock 的 `ctxt1`-`ctxt3` 照旧，读入错误
  一行、照 stock），把**原 lthy** 传给 `local_add_record`——不是读完类型的临时 context，否则 `Typedecl.abbrev` 的
  `Variable.polymorphic` 检查会把读入时声明的类型变量当成固定的。
- 命令 :2426-2432：`Outer_Syntax.local_theory \<^command_keyword>\<open>record\<close> "define extensible record"`，
  parser 不变。Record.thy:14 的 keyword 种类 `thy_defn` 不变。顺带效果（§5.1）：`record (in l)`；`record (in -)`
  在 theory 层就是 theory target，块内要一个可重初始化的级别 1 target（无 includes、无更早的 interpretation）；
  `private record`、`qualified record` 只在有 local scope 的地方（unnamed context、experiment）合法，别处 Pure 报
  `Missing local scope -- cannot restrict name space accesses`。
- `print_record` :2434-2444 不改（它本就按默认模式读、按展开类型识别 record，:2417-2421，是决定 22 的先例）。

### 3.8 代码生成与登记（:1717-1837）

- `add_code` :1782-1820：:1783 `if Config.get_global thy codegen` 改为 `if codegen`（新参数）；其余不改。
- `add_ctr_sugar`（:1822-1830）的 record literal 抽成 `record_ctr_sugar ctr exhaust inject sel_thms : ctr_sugar`，
  stock `add_ctr_sugar` 改为 `default_register_ctr_sugar_global (K true) o record_ctr_sugar …`（值不变）。
- `add_spec_rule`（:1835-1837）的头部计算抽成私有函数，target 版 `Spec_Rules.add` 与 theory 版 `add_global` 共用。

### 3.9 规模与不改的部分

改动约 180-230 行：`definition` 的拆分（`note_record_facts`、`finish`）与返回值、`local_add_record`（含决定 11 的两次
配置读取）、`add_record_cmd`、`read_parent` 一行、`record_of_type`、`resolve_parent`、命令注册、`split_args` 三行、
`add_code` 一处参数、`record_ctr_sugar`、`six_facts`、`record_qualify`、`theory_level`、`background_step`、事实别名
函数、决定 17 的 Induct `map_contexts` 步（约 3 行；比存 declaration 的写法净少 3-5 行）。不改：Record.thy 全部；`Iso_Tuple_Support`；数据段；全部 simproc 与 tactic；`extension_definition`；
`mk_random_eq`/`mk_full_exhaustive_eq`/`instantiate_sort_record`/`ensure_sort_record`；全部打印翻译与全局 parse
translation；`RECORD` 签名里的每个现有条目（类型不变）；`ISO_TUPLE_SUPPORT`。

### 3.10 typedef.ML：`Typedef.transfer_info`（已批 2026-10-15）

signature 加 `val transfer_info: theory -> Proof.context -> Proof.context`（`val get_info_global` :17 之后）；结构
末尾、`end;`（:370）之前加：

```sml
(*typedef info of the background theory, in a proof context; entries the context has are kept*)
fun transfer_info thy =
  Context.proof_map (Data.map (fn tab => Symtab.merge_list (K true) (tab, Data.get (Context.Theory thy))));
```

`Symtab.merge_list (K true)`（table.ML:579-580；library.ML:854-857）：只在 theory 里有的键加进来，两边都有的键保留
context 原有列表。不重复（`put_info` 的 `cons_list` 会）、不覆盖、不需要类型名、可重复调用。与 Pure 自己
`Proof_Context.transfer_facts`（proof_context.ML:64、:450-451）同样是"把 theory 的新键并进 context"，但保留 context
的值且不会失败（`transfer_facts` 遇重复会报 `Duplicate fact declaration`）。stock 不调它。合并方向由 §7.3 第 15 行
核。

### 3.11 ctr_sugar.ML：`Ctr_Sugar.transfer_ctr_sugars`（放宽与名字已批 2026-10-15）

signature 加 `val transfer_ctr_sugars: theory -> Proof.context -> Proof.context`（`val transfer_ctr_sugar` :46 之后；
复数与已有的 `ctr_sugars_of` 一致；刻意不叫 `transfer_ctr_sugar`，那是对单条记录换 theory 的现有函数）；结构末尾、
`end;`（:1272）之前加：

```sml
(*constructor table of the background theory, in a proof context; entries the context has are kept*)
fun transfer_ctr_sugars thy =
  Context.proof_map (Data.map (fn tab => Symtab.merge (K true) (tab, Data.get (Context.Theory thy))));
```

`Symtab.merge (K true)` 是这张表自己的 merge（ctr_sugar.ML:182）：两边都有的键保留 context 的，不抛错
（table.ML:539-548）。stock 不调它。放在结构末尾，不与 light 里程碑 3 的 :185-193、:221-231 共享 `patch -F0` 上下文
（light 2026-10-15 建议不相邻、例如结构末尾；本项目选末尾；light 里程碑 3 的 hunk 定形后两边重核这两个文件）。

## 4. 名字与可达性

全名 = target 的 background naming（`Named_Target.init`：theory naming 加 `Name_Space.mandatory_path (locale 的
base name)`，named_target.ML:136）+ record 自己的限定（背景步里 stock 的 `qualified_path`；target 步里
`record_qualify`），两者拼出与今天 `Thy.p.x` 同形的 `Thy.l.p.x`。访问名的规则：`Name_Space.accesses` 给出全名
去掉若干前缀段的所有后缀，强制路径段（`l`）不能去掉，`p` 是非强制限定词可以去掉；`extern` 打印第一个唯一的访问名；
interpretation 之后 theory 层打印用最新 interpretation 的前缀（`I.x r`、`⦇I.x = …⦈`、`nat I.p`），无隐藏参数的
record 经决定 7 能读回（有隐藏参数时类型印 `nat l.p`，§5.8 (20)）——stock 对无参数 locale 的 definition 与
`type_synonym` 同样行为（B，D6 知悉，§5.8 (16)）。块内副本与 locale note 只按 binding 命名，所以同一 locale 里两个
record 的 `simps` 在 `end` 之后共享访问名 `l.simps`：`Name_Space.accesses` 对两条都给出 `l.simps`，`extern` 于是退到
第一个唯一的访问名 `l.p.simps`/`l.q.simps`，只有一个 record 时才印 `l.simps`。以 `locale l` 里
`record 'a p = x :: 'a  y :: nat` 为例（§7.3 核实；最终以 §7.1 的名字空间 dumper 为准）：

| 实体 | 全名 | 块内 | `end` 之后 | `interpretation I: l 5` 之后 |
| --- | --- | --- | --- | --- |
| 类型缩写 | `Thy.l.p`、`Thy.l.p_scheme` | `p`、`p_scheme`（`type_alias`；里程碑 4 起有隐藏参数时为局部缩写，打印 `'a l.p`） | `l.p`、`l.p_scheme` | `l.p`、`l.p_scheme`，另有 `I.p`、`I.p_scheme` |
| extension type | `Thy.l.p.p_ext` | `p_ext`、`p.p_ext` | `l.p_ext`、`l.p.p_ext` | 另有 `I.p_ext`、`I.p.p_ext` |
| 字段、更新、派生、`p_ext`、`Rep`/`Abs`、`_Tuple_Iso` | `Thy.l.p.x` 等 | `x`、`p.x` | `l.x`、`l.p.x` | 另有别名 `I.x`、`I.p.x` |
| 六条带 attribute 的事实 | `Thy.l.p.simps` 等 | `simps`、`p.simps`（locale note） | `l.simps`、`l.p.simps`（无 attribute；带 `assumes` 时条件形式） | 另有 `I.simps`、`I.p.simps` |
| 十条不带 attribute 的事实、`ext_*`、def 事实、typedef 事实 | `Thy.l.p.select_convs`、`Thy.l.p.p_ext_def`、`Thy.l.p.p_ext.Rep_p_ext_inject` 等 | `select_convs`、`p.select_convs`、`p.make_def`、`p_ext.Rep_p_ext_inject`（事实别名，决定 20） | `l.select_convs`、`l.p.select_convs`、`l.Rep_p_ext_inject`、`l.p_ext.Rep_p_ext_inject`、`l.p.p_ext.Rep_p_ext_inject` | 另有别名 `I.select_convs`、`I.p.select_convs`（同一对象） |
| record 语法 | — | `⦇x = 1, y = 2⦈` | `⦇l.x = 1, y = 2⦈`（第一个字段限定、其余 base name，打印同形）；interpretation 后 `⦇I.x = …⦈` | 同左 |

theory 层写时全部退化为今天的 `Thy.p`、`Thy.p.x`、`Thy.p.simps`，无别名。父 record 按它代表的 record 类型解析
（决定 22），写法带上参数：块内可写 `'a p`、`nat p`、`'a i.p`、record 类型的 synonym，块外可写 `nat l.p`、`'a l.p`、
`nat I.p`、synonym，以及 §5.1 列的新接受形式（`p_scheme`/`p_ext` 形式、record 类型语法、无限定词 interpretation 之后
theory 层的 `nat p`）；父在块内子在块外的全部组合都可以（§5.2）。打印仍显示 `nat l.p`（type.ML:286 的缩写展开不
回折）。

## 5. 语义（用户视角）

### 5.1 theory 层

与今天字节相同（§0 第 1 条；§7.1 的 golden 把关）。逐项，"按构造"指只有 stock 代码或只动即将丢弃的 proof context，
"按论证"指靴带推理、由右列的 golden 项核：

| 偏离 stock 代码之处 | 同一性依据 | golden 项 |
| --- | --- | --- |
| 命令种类改变（`Local_Theory.init` 的 `change_begin`/`change_end_local`，local_theory.ML:416-420；`Local_Theory.new_group`，toplevel.ML:429-435 对 :477-486） | 按论证 | 名字空间 dumper 的类型空间、类型声明与缩写右边、record 造的条目按 group 的划分与按 serial 的先后（只记序关系） |
| 背景步 1 与 2 之间插 target 步 1（`Typedecl.abbrev` 在 theory target 上 = `abbrev_global`） | 按构造（typedecl.ML:130-131） | 名字空间 dumper 的类型空间、record 造的条目按 group 的划分与按 serial 的先后（只记序关系） |
| 背景步之间 naming 的恢复与重装 | 按论证（local_theory.ML:225-236 内容不变） | 定理摘要、常量的类型与 typargs、类型声明与缩写右边、全名、事实表 |
| `zeta` 的选法 | 按构造（theory 层与 :1881 同值） | 类型声明与缩写右边（`p_scheme` 右边里 `'z` 的名字） |
| `note_record_facts` + 第二次 note + `finish` | 按构造（值与 stock 相同，同一次 14 条调用） | 事实表、登记、`get_info` 的节点等式 |
| `record_ctr_sugar` literal 抽出、`add_spec_rule` 头部函数、`add_code` 的 `codegen` 参数 | 按构造（值相同） | Ctr_Sugar、Spec_Rules、代码行 |
| `map_contexts` 步与两个 transfer 施于即将丢弃的 lthy | 按构造；无额外输出靠函数体内的 visible/simp_trace 关闭 | 消息行（含 `declare [[simp_trace]]` 下的） |
| `split_args` 多一条接受条件 | 新接受的输入（stock 报错） | 报错文案行 |
| `read_parent` 对头不是 record 名的类型做解析（决定 22） | 按构造：stock 接受的输入不求值；匹配不到时 stock 的值与文案 | §7.1 的父行（接受与拒绝两组） |

`Goal.norm_result` 对相关定理陈述恒等由 §8 探针 (b) 核（只对 `fold_congs`/`unfold_congs` 可能重编号，它们留背景）。
**新接受的输入**（stock 报错、§0 第 1 条允许）：决定 7 让 `⦇T.x = …⦈` 这类经 name space 解析但不是文本后缀的字段
写法通过；`record (in l)`、`record (in -)`；决定 22——全局 `type_synonym` 及其链条作父（任意参数顺序）、任何展开后是
record 类型的类型表达式作父（`"nat p tv"`、`(nat, unit) p_scheme`、`(nat, unit) p_ext`、`⦇x :: nat⦈`、`(| x :: nat |)`）、
丢掉写出的类型变量的 synonym 作父；里程碑 4 起 theory 层还接受带隐藏参数的 record 经 interpretation 造的 `I.lp` 与
无限定词 interpretation 之后的 `lp`（§7.1 的里程碑 4 fixture 与第 6e-ii 行的叶 `<leaf>.lp`）；typed API 不在此列。**仍拒绝但文案变化的输入**（用户 2026-10-17
裁定）：父是
synonym 且另有第二处错误时，报第二处错误的 stock 现成文案——可能触发的检查：`err_dup_record`、`err_extra_frees`、
`err_dup_fields`、`err_bad_fields`、`add_parents` 的 sort 检查、`definition` 内部的错；块内另有决定 9 与 13 的检查
（无 stock 对应）。decision 7 的先例：`⦇T.x = 1, bogus = 2⦈` 从 `split_args` 的报错移到后面的失败。命令种类改变带来
的 Pure 分派文案变化（不属于 record 包的文案）：`private record`、`qualified record` 在 theory 层报 `Missing local
scope -- cannot restrict name space accesses`（stock 是外层语法错），它们只在 unnamed context、experiment 里合法。
`context -` 形式里：typedef info、Ctr_Sugar 条目、六个 attribute 的效果在块内可见（预测，§7.3 第 22 行）；Spec_Rules
条目与插件输出到 `end` 才可见（§5.8 (2)）。

### 5.2 heavy locale（含 `context l begin` 重开）

- **名字、事实与记号经 target 的部分（决定 2(b)）**：名字如 §4，块内短名靠别名（常量、类型、事实）；字段 mixfix 在
  块内与各 interpretation 里生效，无 registration 时 `end` 后 theory 层不生效、theory 层 interpretation 之后全局生效
  （`notation` 经 locale declaration；§5.8 (10)，用户 2026-10-17 接受）；六条带 attribute 的事实块内有名字、`[simp]`/
  `[iff]` 登记，theory 副本无 attribute、locale 有 `assumes` 时是 `l ?k ⟹ …`。`end` 之后 theory 层 `simp` 要加规则：
  无 `assumes` 时 `simp add: l.p.simps`；有 `assumes` 时 `la.p.simps` 带条件、theory 层用不上，改用 `la.p.select_convs
  la.p.update_convs la.p.ext_inject`（它们无条件，比 `datatype` 强）。选择子作用于构造子的形式 `l.x ⦇l.x = a, y = b⦈
  = a` 不能裸 `by simp`（与 `datatype` 孪生相同）；iff 引理 theory 层要 `blast dest: l.p.iffs[THEN iffD1]` 或 `auto iff:
  l.p.iffs`（裸 `blast dest: l.p.iffs` 报 `Ill-formed destruction rule`，classical.ML:363）。interpretation 产生
  `I.p.simps`、`I.x`、`I.p.select_convs`；Spec_Rules 的块内条目与 theory 副本（带 `assumes` 时条件形式；直接在 locale
  里定义的 record，interpretation 的实例行与 stock 行命题相同、合并，预测）。
- **比 `datatype` 强的部分**：数据表、typedef 的事实与 info、十条不带 attribute 的事实、def 事实、代码在每个 context
  全局、无条件、不重放；Ctr_Sugar 条目在每个 context 都是 theory 层那条（决定 15）；四条 cases/induct 规则在 theory
  与每个相关 context 里定义时最新且无条件（决定 17），Induct 表里没有它们的条件副本（rev6-C16）；Spec_Rules 在 theory
  里的头一条是 stock 的无条件条目（决定 15）；里程碑 4 起接受块固定的类型变量（决定 19，`datatype` 拒绝）。于是 `end`
  之后 theory 层：record 的 simproc 直接可用（`l.x (r⦇l.x := a⦈) = a`、`r⦇l.x := a, l.x := b⦈ = r⦇l.x := b⦈` 由
  `select_update`、`update` 化简 `by simp`，`datatype` 无孪生）；`proof (cases r) case (fields a)`、`induct r` 可用
  （`datatype` 一条规则都找不到）；`fun f where f ⦇l.x = a⦈ = a` 可用，带 `assumes` 的 locale 也可用（`datatype` 孪生
  预计失败到第一次 interpretation）；父在块内、子在块外的 record 可以（含带 `assumes` 的块），父写带参数的形式——块内
  `'a p`、`nat p`、`'a i.p`，块外 `nat l.p`、`'a l.p`、`nat I.p`、synonym（决定 22）；里程碑 4 起带隐藏参数的父按决定 19
  继承隐藏参数、按决定 22 解析 `local.p`/`I.p`；`value`/`export_code` 处处可用；`print_record`、`Record.get_info` 处处
  可用；块内 `copy_bnf ('a, 'z) p_ext`
  （手册的 record schema 惯用法，Datatypes.thy:2959-2969）与块内 `nitpick` 预计可用（typedef info 经 `transfer_info`
  可见；待探针，§5.8 (11)）。
- **`lemma (in -)` 与 `(in m)`**：在级别 1、无 includes、无更早 interpretation 的块里可用，它从 theory 重建该块
  （target_context.ML:38-43），重建后的 context 从 theory 取数据；嵌套层、带 includes、`instantiation`、`overloading`
  里不可用（Pure 的限制）。
- 块固定的类型变量：里程碑 4 前按决定 9 拒绝，之后按决定 19 接受；同名块参数照 `datatype` 报 `Duplicate fixed
  variable(s)`（决定 13）。

### 5.3 theory 上的 unnamed context 与 locale 里的嵌套块

theory 上的 unnamed context 沿用 theory target 的 operations（local_theory.ML:443-450）：名字无前缀、六条事实的 theory
副本带 `[simp]`/`[iff]`、代码立即生成；`is_theory` 为假、走 ELSE：别名指向自身（查找不变，决定 20 的 `transfer_facts`
改变更早块内事实的打印，§5.8 (14)）、mixfix 经 `notation`（语法表相同）、record 的四条 cases/induct 规则经 3E 写 theory、
经 `map_contexts` 步写打开的层（决定 17）；父可写块内的 `nat p`、theory 层的 synonym。带 `assumes` 的 unnamed context
（`context fixes n :: nat assumes "0 < n" begin`）：六条事实的 theory 副本带条件且无法再修复（unnamed context 不能
重开或 interpretation）；`q.cases` 的 theory 副本因 tag-only attribute 不进 Induct 表，`nat` 下不多出条目；record
自己类型下的 `cases r`/`induct r` 由决定 17 的无条件规则回答；数据表、代码、simproc、Ctr_Sugar、typedef info 不受
影响。孪生：裸 `datatype` 在同一块里崩在 code 插件 declaration 的 `dest_equals`（`TERM`；其 BNF typedef 在此之前已
通过）；`datatype (plugins del: code)` 预计通过，但 BNF typedef 的 `Abs_cases` 与 `exhaust` 的 theory 副本
`0 < ?n ⟹ …` 按决定 21 (i) 归到 `nat` 下、干扰 `cases m`——§8 探针 (e) 定。theory 上双层嵌套的外层：决定 17 的
`map_contexts` 步让外层拿到无条件规则。locale 里的嵌套块：名字带 `l.`，其余同 §5.2；嵌套 `assumes` 层里定义的 record：
外层由 `map_contexts` 步、重开与 interpretation 由 theory 里 3E 的写给无条件规则，record 命令与之后的 interpretation
不再抛 THM（rev6-C16）；Spec_Rules 见 §5.8 (15)。

### 5.4 `instantiation … begin`、`overloading`

background naming 是 theory 的（class.ML:718；overloading.ML:202），名字无前缀；`is_theory` 为假，走 ELSE，别名、
`notation`、Induct 规则的两个写者同 §5.3；父可写 `nat p` 与 synonym。嵌套的 `Class.instantiation`（`equal` 实例）在
background theory 上，与 `datatype` 在 `instantiation` 块里的做法相同。`instantiation T :: random`（或
`full_exhaustive`）块里、`instance` 证明之前定义的、字段类型含 `T` 的 record 得不到该 sort 的生成器实例（§5.8 (17)；
`overloading` 块不加 arity，没有这回事）。两种块共有的一条与 `definition` 的偏离（§5.8 (24)(ii)；instantiation 半用户
2026-10-18 接受、overloading 半用户 2026-10-18 知晓）：字段名恰好形如块头待定义的名字（`instantiation nat :: c` 的
`cc_nat`，class.ML:693-696；`overloading c0_nat ≡ "c0 :: nat ⇒ nat"` 的 `c0_nat`）时不会被认领为那个重载常量的定义——
两种块的认领都只看经 `Local_Theory.define` 的 binding（class.ML:575-577、:652-657；overloading.ML:131-134、:163-169），
record 的常量从不经过它——字段仍是普通字段，定义照旧要用户自己写，`overloading` 的 `end` 否则报 `Missing
definition(s) for parameter(s) …`（overloading.ML:183-190）。`instantiation` 的 arity 类型变量是块固定的类型变量（决定
9 / 19）；里程碑 4 起 `instantiation list :: (type) c` 里 `record lp = …` 用 `'a` 得到隐藏参数，块内写 `lp`（forms
table 第 36 行；两条缩写的写入顺序在这种 theory naming 的 target 里有后果，决定 19）。嵌套 `assumes` 层：
`theory_target_notes` 保留 attribute 的条件副本只影响 `[simp]`/`[iff]`，Induct 不受影响（tag-only）。

### 5.5 `class … begin`

record **成功**，代码完整（决定 5）。rev 3 预言的"像 `datatype` 一样失败"不成立：`datatype` 失败在 case certificate
的 `Thm.plain_prop_of`（code.ML:1222-1227），record 没有 case certificate。class 在块打开前就有自己的 theory 层
registration（class_declaration.ML:338-345），`Locale.add_facts` 把 note 连 attribute 施到已有 registration
（locale.ML:666-683），别名与记号的 syntax declaration 同样重放。所以 `end` 之后 theory 层预计：`c_class.p.simps`
在 `dest_simps` 里、theory 层的 simp 引理成功；cases 条目一条（3E 的）；短名 `p.select_convs`、`select_convs`、`x`、
`p.x` 可解析（§7.3 第 9 行写回）；父可写 `nat c.p`、`nat p`（class 前缀非强制）。class 的 `'a` 是块固定的类型变量：
第 9 行的 record 用 `'b` 作参数；`'a` 的情形里程碑 4 前按决定 9 拒绝（声明为参数时）或按 stock 报 `Extra free type
variable(s)`（不声明直接用时），里程碑 4 起分两种——声明为参数的 `'a` 按决定 19 (a) 在背景换新鲜名、仍是 record 的
参数；不声明直接用的 `'a` 作隐藏参数、带 base sort，`end` 之后 `nat c.bad2` 即使 `nat` 不是 `c` 的实例也被接受（预测，
决定 19）。与 `datatype`（更准确说与 `definition`）的一条偏离，用户 2026-10-18 接受为已知差异（§5.8 (24)(i)）：record
的常量绕过 `class_foundation`（named_target.ML:90-93），不是 class 操作、没有 `Class.const` 造的带 `'a::c` 约束的
canonical 常量（class.ML:412-424）。`instantiation`/`overloading` 块里字段名形如待定义名字的那一条见 §5.4。

### 5.6 light locale 块

安全论证的依据是 light 计划 §3.5 的恒等保证（唯一例外是其 M2）：light 改过的路径（named_target 与 generic_target
的 notes、attrib、rule_cases、induct、locale/expression、induct_tacs、里程碑 3 的 typedef.ML:72-74 与
ctr_sugar.ML:185-193，light 计划 §4 第 14-15 项；`patched_files.txt` 到里程碑 3 开始才完整）对无 tag、无 light 谓词
前提的定理与条目恒等；record 的背景步只产生这种定理与条目。共享假定（light 2026-10-15 确认；本项目单方记录，D3 后
写进两边计划）：无 tag 的规则按 stock 归档、`get_casesT`/`get_inductT` 不按 K 过滤（只有 `get_casesP`/`get_inductP`
按链入事实的位置选规则）；里程碑 3 的读者侧 discharge 对无 light 前提的条目恒等（设计，落地时再核）。另一条按源码
记录、light 尚未确认的假定（辩论 Q4 的裁判要求记下）：`case_tac`/`induct_tac` 取规则自身的变量（shared
Tools/induct_tacs.ML:48-50），D3 后写进两边。于是：

- 类型、常量、def、数据表、typedef 事实与 info、代码、Ctr_Sugar 条目：全局无条件，与 theory 层相同；simproc 与
  `fun` 在块内、`end` 后、重开后、interpretation 后、theory 层子 record 处全部可用——比 light 块里的 `datatype` 强。
- 六条带 attribute 的事实经 light notes：块内副本；theory 副本 `LF.p.simps : LF ?S ⟹ …` 带 K = 1 的 tag、
  `[simp]`/`[iff]` 保留（light 决定 9 (i)）；无谓词时无条件。四条 cases/induct 的 theory 副本只带 tag，不进 Induct。
- 别名（常量、类型、事实）、记号：`syntax = true` declaration，light 存下、重开与 interpretation 时重放。
  `interpretation I: LF t` 之后有 `I.x`、`I.p.x`、`I.p`、`I.p.select_convs`，但六条事实没有 `I.` 名（light 不重放
  事实；用 `LF.p.simps[OF I.LF_axioms]`）——§5.8 (18)。
- 决定 17 在 light 块里与其它 target 完全相同：3E 写 theory、`map_contexts` 步写打开的层，不存、不重放；light 不存
  块内副本，所以重开的 light 块与 `lemma (in LF)` 从 theory 重建：Induct 表的头是 3E 的无条件规则，`cases r`、
  `induct r` 可用；六条事实的短名 `p.simps` 等在重开块里是 Unknown fact（决定 20 的别名全部可用、重开块经重放的
  别名拿回 `p` 与 `p.select_convs`），要写 `LF.p.simps`（预测；孪生：同块 `datatype d` 重开后 `d.simps` Unknown、
  `LF.d.simps` 可用）。父写法：块内 `nat p`，重开块里同，`interpretation I: LF {1}` 之后 `nat I.p`。
- Spec_Rules：块内经 target（light 的 declaration 路径）；light 的 theory 副本与 stock 条目在 `eq_spec` 下合并成一行
  （带谓词时也合并，rev5-C32），`end` 后 `retrieve_global` 对每个选择子恰一条、头 `nprems_of` 0。
- `cases r`/`induct r`，按 context 分：theory 层 `end` 之后——最新的是 3E 的无条件规则，裸写可用、不需链 `LF_axioms`，
  与 light 块里 `datatype` 的 `cases t`（要链 `LF_axioms`）不同、与 heavy locale 里的 record 相同；`using LF_axioms
  proof (cases r)` 仍成功，但 `LF S` 作为未用前提插进各 case；要条件形式写 `rule: LF.p.cases`（链 `LF_axioms`）；
  `declare LF.p.cases [cases del]` 看不到效果（§5.8 (7)）。重开的块——同 theory 层（无块内副本）。interpretation 之后
  ——用 `I.LF_axioms` 链 `rule: LF.p.cases`，或裸 `cases r`。
- light 里程碑 3 的读者侧 discharge 与 record 无关：record 读 typedef info 只从 background theory（条目无条件）。
- light §5.6 "`record` 写在块外"的建议对 record 只剩"六条事实在 theory 层是条件形式"这一半成立。

### 5.7 `bundle`、`open_bundle`、`experiment`

**`bundle b begin … end`**（rev5-C16、rev6-C6，全部预测，作者按授权接受，字段 mixfix 一行用户 2026-10-17 接受；§7.3
第 18 行核）：bundle target 只禁
`define`、项的 `abbrev`、`theory_registration`、`locale_dependency`（bundle.ML:272-277），移植都不用，所以 `record`
预计**成功**。bundle 的 background naming 是 theory 的（bundle.ML:269），全部名字是 `Thy.p.…`，别名指向自身。各格
（列：块内 | `bundle` 的 `end` 后 theory 层 | 之后 `unbundle` 后 | `include`/`including` 内 | `open_bundle` 的 `end` 后，
bundle.ML:228-231）：

| 产物 | 块内 | `end` 后 | `unbundle` 后 | `include`/`including` | `open_bundle` 的 `end` 后 |
| --- | --- | --- | --- | --- | --- |
| 名字 | `Thy.p.…`，别名自指 | 同 | 同 | 同 | 同 |
| 六条事实的名字 | 有（命名只在打开的层，bundle.ML:247-256） | 无（bundle 存的是无名内容） | 无 | 无 | 无（`Attrib.global_notes ""` 带 `Binding.empty_atts`，bundle.ML:229-231；预测） |
| `[simp]`/`[iff]` | 生效 | 不生效 | 无名重放、生效 | 生效 | 生效 |
| record 类型的 cases/induct | record 规则（`map_contexts` 步） | 3E 的规则 | 3E 的规则（包内容不写 Induct） | 同 | 同 |
| 字段 mixfix | 有 | 无（§5.8 (10)） | 有 | 有 | 有 |
| Spec_Rules 头 | target 副本 | stock 条目 | 重放的无名等价副本在前 | 同 | 同 |
| typedef info、Ctr_Sugar、数据表、代码、simproc | 全局 | 全局 | 全局 | 全局 | 全局 |
| 插件输出（常量、事实） | theory 层 | theory 层 | 同 | 同 | 同 |
| 插件的 Generic_Data | 块内不可见（§5.8 (13)） | 可见 | 可见 | 可见 | 可见 |

bundle 的重放不写 Induct（决定 17 不存 declaration）；它重放的 Spec_Rules 是同命题的无名副本，答案不变（按 `eq_spec`
比较，不按对象）。拒绝 bundle 要 target 专用代码（决定 2）。`datatype` 孪生报 `Not possible in bundle target`，裸
`typedef` 成功，mixfix 行的孪生是 `bundle b2 begin notation f … end`。替身插件即使调 `Local_Theory.define`，bundle 里
的 record 也预计**成功**（rev6-C6）：决定 15 下插件在背景步 3E 经 `Named_Target.theory_map`（ctr_sugar.ML:230；
named_target.ML:131-144）在新开的 theory target 里跑，碰不到 bundle 的 `bad_operation`（bundle.ML:217、:272-277），其
常量是 theory 层的 `Thy.p.c`，块内按全名可读、`end` 后可用（预测；HOL 无此插件，第 18c 行用第 25 行的测试插件）。
**`experiment`**：建一个 concealed naming 的 heavy locale（experiment.ML:29-33），块内同 §5.2；
theory 层的名字 concealed 且在私有 scope，theory 层使用不是本意用法；留下的匿名 Induct 条目指向无人能写出的类型
（§5.8 (8)）。

### 5.8 已知差异、残余与依赖

每条标依据：**A** = §0 第 8 条允许（内部表示或无人使用的写法）；**B** = 用户或作者的裁定（决定号或 D 号）；**C** = 作者
按命名例外授权接受，附理由与绕法；**D** = 阻塞依赖；**E** = 按源码预测、待探针，失败即缺陷。命名例外（术语表）是其中
涉及四张单答案表、按 record 自己的名字或类型查的条目：(2)、(3) 的 Spec_Rules 部分与 Induct 部分（裸扩展类型）、(15)、
(19)。标"待用户知晓"的条目按 §0 第 7 条先写入、汇报时再提；标"待用户裁"的条目是摆给用户、尚未回答的选项。

1. **块内 info 与 Induct 表对象的证明节点**（A）：四条 cases/induct 规则的 derivation 无名，`simps`、`iffs` 的
   derivation 指向 `l.p.select_convs(i)`、`l.p.update_convs(i)`、`l.p.ext_inject` 节点而非 theory 层的 `p.induct`、
   `p.simps(i)` 节点；Induct 表里的 record 对象在每个 target 下都是 3E 与 `map_contexts` 步写的匿名对象。只在
   `Thm.derivation_name` 与下游证明（`end` 后的子 record、`split_simp_tac`、theory 层的 cases/induct、块内的
   code_simp——它依赖 `select_convs`/`update_convs`，`eval`、normalization 走 oracle 不受影响）的 `thm_deps` 可见
   （预测）。`unused_thms` 不受影响（record 的事实 kind 为 `""`）；proof export 未核。消它要造未登记的新节点。
2. **`context -` 形式**（A，命名例外，Spec_Rules）：Spec_Rules 条目与 Ctr_Sugar 插件输出写进 theory 后到 `end` 才在
   打开的 context 可见（Spec_Rules 没有只写 context 的公开入口；插件在新开的 theory target 里跑）；六个 attribute
   的效果经 `map_contexts` 可见，但那些对象的 tag 顺序是内部的。零使用。
3. typedef 自己的 `Abs_p_ext_cases`/`induct` 条目与 `add_code` 内部实例定义的 Spec_Rules 不进块的 context（A；
   Spec_Rules 部分是命名例外）：对 record 类型，每个 context 里 record 自己的无条件规则最新，单一答案不变；`Rep_*`
   规则进的是按谓词索引的表，不属四张表；`print_induct_rules` 的输出与 theory 层不同；`lemma (in -)` 重建块后它们
   出现。Induct 部分的残余（命名例外）：子 record 的裸扩展类型 `'z ch_ext` 与内层 `p_inner<i>` 在定义块打开期间没有
   任何类型规则——`cases`/`induct` 退到 `case_split`、失败（预计 `Failed to apply initial proof method`）；theory 层、
   `end` 之后、重开的块与 `lemma (in -)` 里由 typedef 的 `Abs_*_cases` 回答；根 record 的扩展类型就是它的 scheme 类型，
   由 `cases_scheme` 回答。typedef 与 code 实例定义自己的 Spec_Rules 条目只在 theory。
4. **theory 层 `[cases del]`**（B，决定 17；用户 2026-10-15 20:12 确认接受 R6-C16 时已披露、2026-10-17 随 rev7-C2
   重裁）：有 `assumes` 时 theory 层与外层 `declare l.p.cases [cases del]` 撤不掉匿名规则（命题多一个前提），撤法：
   以无条件命题写一条 lemma 再 `declare … [cases del]`；无 `assumes` 时命题相同、撤得掉，之后 `cases r` 退到
   `l.p.cases_scheme`、再到 typedef 的规则——与 stock 对 `declare p.cases [cases del]` 的行为相同（预测），并且删除
   **保持**（不再被重开或 interpretation 加回；`I.p.cases` 删除同理）。与 theory 层 record 剩下的一处差别：删后想加回
   时，heavy locale 或 class 块的 theory 副本 `l.p.cases` 已被 Pure 剥掉 attribute（generic_target.ML:445-447，shared
   :561-563），直接 `declare l.p.cases [cases type: l.p]` 加回的规则没有 `case_names` tag，要写 `declare l.p.cases
   [case_names fields, cases type: l.p]` 或用 `Record.the_info` 取原规则（预测；`type:` 收一个类型名，它是 `cases r
   type: l.p` 查表的键，induct.ML:285、:375、:905-910）。
5. （rev6-C16 后对 record 自己的事实消解；留给 `typedef`/`datatype` 孪生的记录在决定 21。）
6. Spec_Rules 的行数（E，rev5-C32 的改写、D6 知悉）：heavy locale、class 与 theory target 的块带 `assumes` 时，`end`
   之后 theory 里每个 record 常量两条（target 的条件旧条目、stock 的新条目为头）；无 `assumes` 时两条命题相同合并为
   一；light 块无论有无谓词，theory 副本与 stock 条目按 `eq_spec` 合并（spec_rules.ML:110-114；binding.ML:217、
   :224-225）；直接在 locale 里定义的 record，interpretation 的实例行与 stock 行合并；只有嵌套 `assumes` 层加条件实例
   行（(15)）；theory export 与 Sledgehammer 的分类表看到多行（无害性未实测）。
7. light 带谓词的块之后 `cases r` 不需链 `LF_axioms`、`declare LF.p.cases [cases del]` 无可见效果（B，决定 17）；撤法
   同 (4)（以无条件命题写 lemma 再 `[cases del]`，预测）；删除经重开与 interpretation 也保持，理由同 (4)：record 不存
   也不重放 Induct 的 declaration（决定 17）。
8. `experiment` 留下匿名 Induct 条目（A），无害。
9. （并入决定 21：light 里程碑 3 前 `typedef`/`datatype` 的条件 `[cases type]` 副本归错类型；record 自己的事实不受
   影响。）
10. **决定 2(b) 与决定 16 (i) 的后果**（B：决定 2(b)、决定 16 (i)；字段 mixfix 一条 rev6-C6，用户 2026-10-17 接受
    "这就是合理的行为"）：heavy locale 之后（无 registration 时）`[simp]`/`[iff]` 不在 theory 层生效（`⦇l.x = a⦈ =
    ⦇l.x = b⦈ ⟹ a = b` 不能裸 `simp`、`blast` 要 `dest: l.p.iffs[THEN iffD1]`）；字段 mixfix（如 HOL-Algebra 的
    `mult :: "['a, 'a] ⇒ 'a" (infixl "⊗ı" 70)`）在 heavy locale 的 `end` 后 theory 层不可用（写 `l.mult G x y`）、普通
    `bundle` 的 `end` 后到 `unbundle` 前不可用，theory 层 interpretation 或 class 自我 registration 之后变全局。bundle
    的两种情形（D6 rev5-C16，2026-10-15）：普通 `bundle` 里六条事实只在块内有名字，`[simp]`/`[iff]` 在 `unbundle`/
    `include` 时无名生效；`open_bundle` 在它的 `end` 时无名施加到 theory。绕法：`unbundle`、`open_bundle`、或在块外
    定义。`datatype` 的构造子 mixfix 在 locale 里同形。
11. 块内 `copy_bnf … via` 与 BNF 登记在带 `assumes` 的 heavy 块里能否成功、Nitpick 在块内是否给出 genuine（E，§8
    探针 (x)）。
12. **决定 19 的过渡拒绝**（D，里程碑 4 前）：块固定的类型变量作参数或出现在字段类型、父参数里被拒。
13. **Ctr_Sugar 插件自己的数据**（B，决定 15 / D1）：插件在 theory 侧跑，其 Generic_Data（AFP Constructor_Funs 的
    常量与规则）在定义块内到 `end` 才可见。绕法：`end` 后使用，或在块外定义 record。
14. **`local.foo` 的打印**（B，两部分）：决定 20 的 `transfer_facts`（用户已批）把 theory 的事实表整表并进打开的
    context，之后该 context 里更早登记的事实打印成 `local.foo`（`thm`、`find_theorems`；Sledgehammer 只在带 hyps 或超
    50000 条事实时显示）；按名查找不变。第一部分（D6 知悉，rev5-C30，2026-10-15）：theory 上的 unnamed context、
    `instantiation`、`overloading` 里，record 之前在块内 note 的事实（含更早 record 的六条事实）。第二部分（rev6-C14
    扩范围；用户 2026-10-17 委托作者处置、不改设计）：class 块（class 前缀非强制，class_declaration.ML:75）和有无限定词
    或非强制限定词 interpretation 的 heavy locale 里也如此，并且 record **自己的**六条事实也印成 `local.p.simps`。Pure
    自己的 `named_theorems` 同样行为（预测，§8 探针 (o)；第 23 行核；若探针显示前缀不出现，本条删）。不改设计下只能
    如实记录；换别名机制要重开 D6 第 2 条（§10）。
15. **嵌套 `assumes` 下的 Spec_Rules 头**（C，命名例外，Spec_Rules；D6 知悉，rev5-C32，2026-10-15）：locale 内嵌套
    `context assumes A` 里定义的
    record，(i) 仍打开的外层只有 `A ⟹ sel_conv`；(ii) 重开的块把存下的条件行放到 stock 行之上；(iii) 每次
    interpretation 在 theory 头加一条条件实例行。读者：Nunchaku（context 头）、code_pred（theory 头，(iii) 之后得
    空规格）、Sledgehammer 的表。理由：决定 15 的 target 路径把 declaration 存在 locale；唯一只写 context 的办法是用
    自定 operations 的一次性 `Local_Theory.init`，因依赖 Local_Theory 内部而否决。light 块预计不受影响。绕法：把
    record 定义在嵌套 `assumes` 层之外（预测，经 (6) 的合并）。
16. **interpretation 后的打印**（B，D6 知悉，rev5-C31，2026-10-15）：无隐藏参数的 record 在 theory 层 `l.x r` 打印成
    `I.x r`、`⦇I.x = …⦈`、`nat I.p`（stock 对别名的行为），经决定 7 读回；每个打印形式的头都是 record 名、走 stock 路径，
    所以都能作父读回；从不打印出来的缩写走决定 22。有隐藏参数时类型印 `nat l.p`（(20)）。
17. **`instantiation` 块里 `instance` 之前的 record 没有 quickcheck 生成器**（B，用户 2026-10-15 接受）：
    `instantiation T :: random`（`full_exhaustive` 同）块里、`instance` 证明之前定义的、字段类型含 `T` 的 record，
    `ensure_sort_record`（record.ML:1768-1780；调用处 :1797-1799、:1817-1818；quickcheck 侧 quickcheck_common.ML:
    398-405）按 theory 的 class 代数一次性判断能否派生实例，而正在证的 arity 在 `instance` 证明完成前只在块的局部代数
    里（class.ML:703-705、:746-747），所以不派生；`end` 后 `quickcheck [random]` 找不到生成器。理由：stock 自己的
    规则——theory 层把 record 写在 `instantiation T :: random` 之前同样如此；不修的理由：修它要么读 instantiation
    target 的私有数据（违决定 2，target 专用代码），要么在 `end` 时重查（违决定 2(a)）。绕法：把 record 放在
    `instance` 之后或 `end` 之后；或自己写实例。只针对 `instantiation`；`overloading` 块不加任何 arity
    （overloading.ML:193-215；R7-C11 第 5 项把它误加进来，rev 9 删），`context begin`、locale、class、light、bundle 同样
    不加 arity、不受影响。§7.3 第 8c 行。
18. **light 的 interpretation 与重开**（B，两部分）：第一部分（D6 知悉，rev5-C33，2026-10-15）：别名事实得到
    `I.p.select_convs` 等，六条事实没有 `I.p.simps`，用 `LF.p.simps[OF I.LF_axioms]`。第二部分（rev6-C2 扩范围，
    依据 light 的设计——light 不存块内副本，light 计划 :303-305、:2794、:2237-2242；用户 2026-10-18 知晓，签字表第 12
    条）：重开的 light 块与
    `lemma (in LF)` 里六条事实的短名 Unknown，写 `LF.p.simps`。六条事实不加别名的理由见决定 20。
19. **嵌套 `assumes` 下 Spec_Rules 的 declaration 重放**（C，命名例外，Spec_Rules；rev6-C4 改写）：定义 record 之后在
    theory 上带 `assumes` 的 unnamed context 里做 `global_interpretation`，重放的 Spec_Rules declaration 经导出
    morphism 把 `C ?c ⟹ sel_conv` 放到 theory 头（spec_rules.ML:160-179；assumption.ML:48-49），stock 行不重放。理由
    同 (15)：决定 15 的 target 路径把 declaration 存在 locale；locale 自己的 `definition` 在同样的 `global_interpretation`
    下同样行为（预测）。绕法：把 `global_interpretation` 做在 theory 层或没有 `assumes` 的 context 里；interpretation
    必须放在 `assumes` context 里时没有绕法。Induct 头是 3E 的无条件规则——重放的 notes 只打 tag、不写 Induct，Induct
    没有重放这回事。
20. **带隐藏参数的 record 类型的打印**（B，用户 2026-10-15 接受；里程碑 4）：块内、重开块里印成 `'a l.p`、
    `('a, 'z) l.p_scheme`（theory 命名的 target 里块内印 `'a T.r`、`end` 后印 `nat r`），theory 层 interpretation 后印
    `nat l.p` 而非 `nat I.p`（record 的打印翻译从全局名重建，没有 `p` 的 type_alias）。参数顺序：声明参数在前、隐藏
    参数按名字在后、`'z` 最后（决定 19，用户 2026-10-18）。改进归 local_type_abbrev 的回折打印统一做（在类型层对局部
    缩写回折即先于 record 的打印翻译起效）；全局缩写 `I.p` 按 Pure 惯例不回折；目前无人排期，是否立项由用户定。
21. **两个带隐藏参数的同名 record 合并**（B，rev6-C3 (b)，用户 2026-10-15；随 local_type_abbrev 的决定 5/17/20——决定
    20 用户 2026-10-18 裁定、文案已批；里程碑 4）：`locale m = l1 + l2` 时第二遍严格建 locale context，按那边决定 20 比较
    两个 `p` 副本的内容——两个展开式属于不同的全局 record 类型、内容必不同——报那边 §6 第 2 条两行 `Type abbreviation "p"
    is already defined as "…" and cannot also be defined as "…".` / `Rename it or import it with a qualifier.`，再接
    `The above error(s) occurred while activating facts of locale instance …`（stock locale.ML:529；印出的两个展开式由
    探针钉住）；`p` 先于 `p_scheme` 登记，所以报的是 `p`（那边 §5 第 8 行，其里程碑 2 的 gate）；头部读取期间的重名跳过
    （那边决定 17）随其里程碑 4 才有，本例无实例时头部不登记副本；头部之后一律严格（那边决定 17，用户 2026-10-18
    确认），第 10 行预期不再悬。第二次无限定词 theory 层 interpretation：stock 式代码下本来就报 `Duplicate fact
    declaration`（全局事实严格，global_theory.ML:300）；隐藏参数的像不同时先报那边 §6 第 2 条（其 §5 第 8f 行）；像相同
    时两个副本内容一致、按那边决定 20 接受，剩下 stock 的那条错误（预测；§7.3 第 10b 行）。无隐藏参数时 `p` 是
    type_alias、后者遮前者。record 只引用。决定 19 的同一限定。
22. **决定 22 的残余**，各自标依据：
    - 无字段使用的参数经 synonym 作父（B，用户 2026-10-17 接受残余、2026-10-18 确认不支持）：`record ('a, 'b) ph = w ::
      'b`（AFP 一例，CompositionalRefinement.thy:1417）经 `qph = "(nat, bool) ph"` 作父仍报 stock 的 `Unknown parent
      record "T.qph"`——展开丢掉了 `nat`，无从恢复，补 `unit` 是对父信息说谎、补新鲜变量平添参数（§10）；块内带隐藏
      参数又带无字段用的声明参数的 record 同理（`Unknown parent record "local.lpb"`）。绕法：按 record 名写全参数
      （`"(nat, bool) ph"`、`"(nat, 'a) l.lpb"`）。TAT 侧用户 2026-10-17 裁定所有 type node 在 gen 时拒绝未使用的
      类型参数，已由 TAT 落实（§11），上游消掉此形。
    - synonym 的 ill-sorted 实例（`"t q8"`，B，文案变化类）：报的 `Ill-sorted instantiation` 指 record 与参数而非
      synonym 名。
    - 打印不回折（B，rev6-C3 (a)，(20)）。
    - 开放的 interpretation（`interpretation K: l id`，像仍 schematic）不造 `K.lp`（B，提供方决定 2）：Pure 报
      `Undefined type name: "K.lp"`，写出实例类型或 `"'b l.lp"` 即可。
    - 报错文案引内部全名 `"local.ql"`（B，决定 22），与 stock 引 `"T.q"` 一致。
    - (a) 重开顺序的短名（E，待 §8 探针 P11 第 (2) 半；里程碑 4）：先在 `l` 里定义 `lp`、再做无限定词 interpretation、
      再重开 `context l begin`，`lp` 读成重放的局部副本 `local.lp` 还是全局 `<leaf>.lp`——源码预测局部副本赢（后写赢
      短名；提供方决定 5 自己的话是"相反的顺序不遮蔽"），若全局赢则是缺陷、报用户与提供方。theory naming 的 target 里
      `T.r` 与 `local.r` 争短名是必然行为（第 6e-v 行的通过条件：`r` 读成 `local.r`）。
    - (b) 先解释后定义的短名（按源码预测的缺陷，**待用户裁**——用户 2026-10-18 定为等提供方 §7.1 第 1 项的探针结果
      再裁；里程碑 4）：theory 层已有 `l` 的无限定词 interpretation，之后在 `context l begin` 里定义带隐藏参数的 `lp2`，
      从下一条命令起到 `end`，短名 `lp2` 解析到 theory 的副本 `<leaf>.lp2`（`i?:` 非强制前缀下是 `<leaf>.i.lp2`）。机制：
      `Local_Theory.declaration {syntax = true}` → `Locale.add_declaration` → `add_facts` → `apply_registrations` 在 theory
      里定义副本（stock locale.ML:666-690），下一次 transfer 把 theory 的新名字放到前面（提供方决定 5 第三点对每个
      `type_synonym` 都记了这条，用户 2026-10-14 在那边有条件接受——条件是其探针证明 stock 常量缩写同样如此）。record
      新增的后果：同块 `record d2 = lp2 + y :: nat` 按决定 22 得父 `([nat], T.l.lp2)`、没有隐藏 `'a`，定义处不报错，到
      `⦇g = f, y = 0⦈ :: d2` 才以 `'a` 对 `nat` 的冲突暴露——按 §0 第 8 条这是缺陷，除非用户接受。绕法：`local.lp2`
      或 `"'a l.lp2"`。范围：class 的规范 interpretation 不受影响（像是 schematic）；相反的顺序是 (a)。record 侧不加
      target 专用代码就修不了。选项：(a′) 记为残余（B），留记录行与绕法；(b′) 经用户批准请提供方改其决定 5 第三点，
      让块自己的条目到 `end` 都保住短名——那会连带改普通 `type_synonym` 的行为；若提供方的探针显示 stock 常量缩写不这样
      遮蔽，其决定 5 第三点自己退回、修法同时消掉这条。第 6e-iv 行与 P11 第 (3) 半先作记录行，预期值在裁定后写定。
23. AFP 的 Optics（Lens_Record.ML:47-51）、Clean（Clean.thy:807-811）、Isabelle_DOF（Isa_DOF.thy:3053-3057）各有一份
    stock `read_parent` 的拷贝，它们的命令仍只认 record 名（B，用户 2026-10-17："我们不管"）。
24. **class 块与 instantiation/overloading 块里与 `datatype`（更准确说与 `definition`）的偏离**（B，用户 2026-10-18 接受
    (i) 与 (ii) 的 instantiation 半、知晓 (ii) 的 overloading 半；2026-10-17 提出；依据决定 2(b)、3——逻辑内容全局、无
    target 专用代码；决定 3 辩论裁判 2026-10-13 要求提给用户）：(i) class 块里 record 的常量绕过 `class_foundation`
    （named_target.ML:90-93），不是 class 操作——没有 `Class.const`（class.ML:412-424）造的、带 `'a::c` 约束的 canonical
    常量；里程碑 4 起分两种：声明为参数的 `'a`（`record 'a bad = x :: 'a`）按决定 19 (a) 在背景换新鲜名，`#args` 一项、
    sort 是块里读到的 sort（class 块里预测为 base sort，探针 P9）；不声明直接用的 `'a`（`record bad2 = bu :: 'a`）作隐藏
    参数、带 base sort，`end` 之后 `nat c.bad2`、`c.bu :: nat c.bad2 ⇒ nat` 对不是 `c` 实例的 `nat` 也可用（预测）。
    同块 `definition f :: "'a ⇒ 'a" where "f x = cc"` 则得到 `c.f :: 'a::c ⇒ 'a::c`。(ii) `instantiation nat :: c` 块
    里，字段名恰好形如待定义的类参数（`cc_nat`，class.ML:693-696）时不会被认领为 `cc` 在 `nat` 上的定义（`instantiation_param`
    只看 `Local_Theory.define` 的 binding，class.ML:575-577、:652-657），仍是普通字段，类参数照旧待 `instance` 前定义；
    `overloading c0_nat ≡ "c0 :: nat ⇒ nat"` 块里同样：字段 `c0_nat` 不被认领（`operation` 只看 `Local_Theory.define`
    的 binding，overloading.ML:131-134、:163-169），`end` 仍报 `Missing definition(s) for parameter(s) "c0"`（:183-190），
    直到用户自己写 `definition c0_nat`（用户 2026-10-18 知晓）。两种块的机制同形，根子在 record 的常量在 background
    theory 里经 `Sign.declare_const_global` 加 `Global_Theory.add_def` 声明（record.ML:2063-2069），从不经过
    `Local_Theory.define` 的 foundation。无害：record 是数据不是要重载的操作；修它要走 `define` 式 foundation（§10 已
    否）。§7.3 第 8、9、18d 行加孪生观测。
25. **带隐藏参数的 record 只能以带全部参数的全局名到达之处**（里程碑 4）：heavy locale `end` 之后的 theory 层（B，
    决定 19；决定 19 的例子 `nat l.d`）；嵌套 `context fixes y :: 'd` 层结束后的外层与重开的 `context l begin`，当隐藏
    变量只在那一嵌套层固定时（B，提供方决定 2 与其 §5 第 3 行；绕法 `'x l.r`）；class `end` 之后的 theory 层（B，决定
    19 与提供方 §5 第 5 行；绕法 `nat c.p`）。用户要知道参数顺序（(20)）才能写出全局名；隐藏参数在 `_scheme` 类型里
    排在 `'z` 之前，写成 `('b, 'z, nat) l.lpq_scheme` 参数个数照样对、`'z` 静默绑到隐藏参数的位置（预测）——用户是在
    辩论 `wf_ed1080ae-844` 的记录（`decisive_reasons`、`owner_summary_cn`）指出这一风险之后选的在后，决定 19 要求的用户
    文档必须带这个例子；不另立条目、不加误绑的测试行。提供方决定 3 的 sort 依赖（E，探针 P9）：隐藏参数存的 sort 等于
    块里读到的 sort。

## 6. 文案

**统一规则**（已批 2026-10-14；范围按复审 D5 作者收窄 2026-10-15）：`local_add_record` 自己的检查与各步抛出的每一个
`ERROR` 都带 stock 的第二行 `Failed to define record "p"`（`cat_error`，:2365 的包装覆盖检查与全部步骤）。
`add_record_cmd` 读入阶段的错误（未定义类型、坏 sort、`Bad parent record specification`、`check_tfree`）照 stock 一行；
Pure 命令分派层的错误（`Missing local scope` 等）在包装之外。决定 22 不加任何文案。决定 13 复用 Isabelle 自己的消息：

```
Duplicate fixed variable(s): "x"
Failed to define record "p"
```

决定 9 的过渡拒绝（里程碑 4 前；文案已批 2026-10-12）照 `datatype` 的那条（bnf_fp_def_sugar.ML:2309-2310）：

```
Locally fixed type argument "'a" in record specification
Failed to define record "p"
```

其余 record 包自己的文案逐字不变（§0 第 1 条允许的两类变化除外）。

## 7. 测试与验证

构建由用户运行（§0 第 6 条）。涉及的 session 由扫描产生：在 stock 副本上对 `src/HOL` 与 `src/Benchmarks`（排除
`*.unicode.thy`，刻意排除 `src/Doc`）`/usr/bin/grep -rlE '^\s*record\b|Record\.|\\<lparr>'`（`\<lparr>` 命中手工
筛），命中映射到 session，只列在 `sessions` 下的 session 不算构建、单列。结果：`HOL`（`-b`）、`HOL-Algebra`、
`HOL-Examples`、`HOL-ex`、`HOL-Record_Benchmark`、`HOL-SPARK-Examples`（旧 API 的 gate：`spark_open` →
spark_vcs.ML:347，RIPEMD-160 走 `Record.add_record`，唯一 codegen 开着的旧 API 路径）、`HOL-SPARK-Manual`、
`HOL-Statespace`、`HOL-Hoare`、`HOL-Nitpick_Examples`、`HOL-Bali`、`HOL-UNITY`（含 HOL-Auth）、`HOL-Hoare_Parallel`、
`HOL-Quickcheck_Examples`、`HOL-Imperative_HOL`、`HOL-Unix`、`HOL-NanoJava`、`HOL-Isar_Examples`、`HOL-SMT_Examples`、
`HOL-Datatype_Examples`、`HOL-Codegenerator_Test`、`HOL-Metis_Examples`、`HOL-Predicate_Compile_Examples`
（Examples.thy:248-263 是发行版唯一对 record 的 `code_pred`/`values`）、`HOL-Number_Theory`、`HOL-Decision_Procs`；
light 的 `contrib/light_locale/tests/ROOT` 五个 session；以及本项目的 `Localized_Record_Golden`、
`Localized_Record_Golden_Messages`（`threads = 1`，§7.1 的消息行）、`Localized_Record_Theory_Test`（只 import `Main`，
§7.2，可在 stock 副本上构建）、`Localized_Record_Test`、`Localized_Record_Light_Test`（`imports Light_Locale`）。§7.3、
§7.4 各自开自己的 session 构建。全部预期**已由用户签字**（§0 第 7 条；2026-10-18 晚，签字表 `REV9_SIGNOFF_TABLE.md`：
第一类 7 条已接受的差异仍接受、第 8-12 条逐条接受、其余批量签；表头列出的不签行——6e-iv、P11 第 (3) 半、7c/7d 与
7f/7h 的孪生列、8b/18e 的孪生列——除外）；签字形式由作者定（用户 2026-10-18 委托）：
只把"与 `datatype` 不同"的行与评审新增的行列成表（场景、观测量、预期、依据决定、孪生）逐行过，其余"与孪生相同"的行
一句批量签；签字之后预期**冻结**，再改任何一行都重新请示，不得在改计划时顺手改成实测结果。每行注明 `datatype` 孪生或
无孪生的理由（Spec_Rules 的孪生是同块 `datatype` 的选择子行，ctr_sugar.ML:1117-1120；"孪生是 theory 层 record"也算
理由；决定 22 的父行没有 datatype 对应，孪生是写 record 名的同一行）。

### 7.1 golden（里程碑 0，用户在 stock 副本上构建 `Localized_Record_Golden` 录制；在共享树上比）

只 dump record 自己造的实体，不 dump 整个 theory；只用公开读取函数；以 `ML_file` 载入 light 的 golden.ML，复用
`Golden.recording`/`Golden.check`/`Golden.thms_dump`。针对 `HOL-Algebra`（`partial_object`/`monoid`/`ring`，带
`\<index>` 字段）、`HOL/Examples/Records.thy`（含 300 字段的 ML `add_record`、codegen 关闭的 record）、
`Record_Benchmark`，以及一个最小 theory：普通 mixfix 字段、`\<index>` 字段、子 record、17 字段、带 sort 约束的参数、
`(overloaded)`、缩写作字段类型、实例化的父、无字段使用的参数（`record ('a, 'b) ph = w :: 'b`）、`setup` 里在
`Sign.add_path`/`Sign.mandatory_path`/`Sign.concealed` 下（各随 `restore_naming`）codegen 开着的 `Record.add_record`：

- **定理摘要**（`thms_dump` 加列）：`ML_Syntax.print_term (Thm.prop_of th)` 的 SHA1、`Thm.nprems_of`、**按实际顺序**
  的 `Thm.get_tags`、`Thm.derivation_name`（只核名字与下标；代码证书定理不记此列）、`Global_Theory.lookup_thm` 给出的
  事实名或 NONE（对 info 的每条定理与 Ctr_Sugar 的 exhaust/injects 也记，rev4-C3）、concealed 标记。**不记 serial
  的值**，只记 record 造的条目之间的序关系（rev4-C3、rev6-C7）。
- **事实表**：`Facts.dest_static true` 带 record 前缀的全部事实，每条 `thms_dump`。私有表（`Record.Data`、
  `Iso_Tuple_Thms`）不直接 dump，经读取函数与行为覆盖（rev3-C24）。
- **登记**：每个 record 的 `Raw_Simplifier.dest_simps (simpset_of ctxt)` 中条目的 name hint；`Classical.dest_decls`
  过滤到 record 的定理；`Induct.lookup_casesT`/`lookup_inductT` 对 record 名与 `_scheme` 名；`find_casesT`/
  `find_inductT` 对 record 类型与 scheme 类型，按序；`Induct.dest_rules` 的内容顺序与各键的条目数。
- **名字空间**：一个 dumper 跑常量、类型、事实三个空间，对 record 造的每个实体（含 typedef、plugin、`add_code` 的
  实例常量与事实、`_Tuple_Iso`）记全名、`Name_Space.the_entry` 的 concealed/suppress/theory_long_name、`extern` 与
  `extern_shortest`、每个点后缀的 `intern` 结果；record 造的条目按 group 的划分（每组以首现条目的序号表示）与按
  serial 的先后（只记序关系）。
- **公理与 `Defs`**：`Theory.all_axioms_of` 带 record 前缀的条目；`Defs.dest_constdefs`。
- **`Record.get_info`**：每个 record 的 `info`，类型经 `ML_Syntax.print_typ`（不用 `Syntax.string_of_typ`，打印器自己
  是被测对象，rev3-C4）、定理经 `thms_dump`，并对六个
  attributed 字段核 `Thm.eq_thm_strict`、`Thm.derivation_id` 等于 `Global_Theory.get_thms` 同名事实（stock 六条皆
  同一节点）；`get_parent`（含 args 与 sort）、`get_extension`、`get_extT_fields`/`get_recT_fields`、`get_extinjects`、
  `get_simpset`。
- **语法表**：`mixfix_probe.ML`（`ai-artifacts/probes/`，`out_dir` 作参数、注明树）的 `const_lines` 对每个 record
  常量（plain 与 `\<^indexed>` 两键的 parse/print 规则）移入 golden dumper。
- **代码**：`Code.get_cert` 对每个 record 常量、`Code.get_type` 的构造子集、`equal`/`random`/`full_exhaustive`/
  `typerep`/`term_of` 实例的常量与事实全名。
- **`Spec_Rules.retrieve_global`** 对 `sel_convs' @ upd_convs' @ derived_defs'` 每个头的条目列（顺序、命题）与
  `Spec_Rules.dest_theory`；**`Ctr_Sugar.ctr_sugar_of_global`** 的 record 条目（`T`、`ctrs`、`exhaust`、`injects`、
  `sel_thmss`、`kind` 六个非 dummy 字段）；**`Typedef.get_info_global`** 的五个字段与条目数；常量的类型与 typargs、
  类型声明与缩写右边（theory export 的 `export_theory.ML` 不认 Ctr_Sugar（:123-124 只导出 datatype 的 Ctr_Sugar 条目）、
  record 条目的序号不稳定（:186-188 按 serial 排），故改为 ML 内列，rev6-C7）。
- **打印**：一组 record 项与类型的 `string_of_term`/`string_of_typ`（两种 print mode、两种配置），含 `⦇y = 1, x = 2⦈`
  与单字段项、限定字段名的读与印。
- **`thm_deps`**：六条事实；子 record 的 `induct_scheme`；一条由 `Record.split_simp_tac` 关掉的 lemma、一条由
  simproc 关掉的 lemma、一条 `fun` 用 record 模式、一条对选择子与更新求值的 code_simp 证明的依赖名列；
  `p.select_convs` 作对照。
- **消息**（单独的 session `Localized_Record_Golden_Messages`，`options [threads = 1]`——`parallel_proofs = 0` 是
  进程级 ref、`Par_List` 照样 fork）：成功 record 命令的完整消息（捕获 warning/tracing/writeln/legacy，output.ML:43-49，
  捕获装在消息 session 自己的 theory 里——进程启动会重装每个 `Private_Output` 函数，isabelle_process.ML:125-140；
  `record_timing` 关与开各一行、开时只留标签行）；`declare [[simp_trace]]` 下的输出（rev6-C1 的基线）。变异检查
  （测试本身对错误实现，按仓库规则）：代码变体——把关闭挪回 `map_contexts` 外面——由用户在共享树上在 §8 第 1 步消息行
  通过之后多构建一次 HOL，此行必须变红（预计每条 simps 规则与 `ext_inject` 各多一行 `[0]Adding rewrite rule`）；
  变体临时顶替共享 HOL heap，下一次正常构建前把源码改回。stock 上用 `local_setup` 在 theory 内模拟两种包法只作正对照
  （探针 (y)）。这些行在 light 的捕获重构落地后录（§8 第 1 步前置；若 `isabelle build_log -v -T` 已列出 tracing 消息
  则不需 light 改捕获，探针 (u) 核）；其余行现在录。
- **父 record 的 fixture**（头脑风暴 forms table 的 SETUP），三份 theory；下文与 §7.3 里的 `T` 指**定义该实体的
  theory**——对 `p`、`q1` 是 theory 层 fixture，对 `l0.r`、`l.lp` 是各自的块 fixture，对某一行自己定义的 record 是那一行
  的测试叶（如 6e 的 `T.l.d`）：
  (1) theory 层 fixture `Parent_Forms_Fixture.thy`（session `Localized_Record_Theory_Test`，只 import `Main`，不含任何块，
  stock 也必须接受；§7.2 与探针 P1-P8 用）：`record p0 = u :: nat`；`record 'a p = x :: 'a`；`record ('a, 'b) c = "'a p" +
  z :: 'b`；`record ('a, 'b) ph = w :: 'b`（`'a` 无字段使用）；`record ('a::linorder) s = v :: 'a`；`typedecl t`（无
  `linorder` 实例）；`datatype 'a foo_ext = F 'a`。synonym：`n = nat`；`q1 = "nat p"`；`q4 = q1`；`'b q2 = "'b p"`；
  `('u, 'v) q3 = "('v, 'u) c"`；`'a tv = 'a`；`'x qd = "nat p"`；`'x q8 = "'x s"`；`'a q9 = "nat p"`；`qn = "nat list"`；
  `qph = "(nat, bool) ph"`；`bad = "t s"`；`'z qs = "(nat, 'z) p_scheme"`；`qsyn = "letbinds p"`（语法类型的 synonym）。
  (2) 块 fixture（session `Localized_Record_Test`，里程碑 2；第 6b、6c 行用）：`locale l0 = fixes k :: nat begin record 'a r
  = y :: 'a  type_synonym qa = "nat r" end`（无隐藏参数，`r` 是 `T.l0.r` 的 type_alias）；`interpretation I0: l0 5`。
  (3) 里程碑 4 的 fixture（session `Localized_Record_Test`，里程碑 4；第 6e 行与探针 P9-P11 用；它 import (1)——决定 1 给
  `Localized_Record_Test` 加 `sessions Localized_Record_Theory_Test`）：`locale l = fixes f :: "'a ⇒ 'a" begin record lp =
  g :: "'a ⇒ 'a"  record 'b lpb = gb :: "'a ⇒ 'a"  record 'b lpq = gq :: "'a ⇒ 'a"  h :: 'b  type_synonym ql = "'a list"
  end`（`lp` 有隐藏参数 `'a`，全局 `T.l.lp`，块内局部缩写 `local.lp = ('a, unit) T.l.lp.lp_ext`；`lpb` 的 `'b` 无字段
  使用；`lpq` 两个参数都用）；`interpretation I: l "id :: nat ⇒ nat"`（闭合像，全局缩写 `T.I.lp = (nat, unit)
  T.l.lp.lp_ext`）。规则：同一块里的 record 不共用字段名——record.ML:693-705 按 intern 后的第一个字段取扩展，重名只在
  测遮蔽的行里出现；块内 record 叫 `lp` 而不叫 `p`，为了短名不与 `T.p` 相争。无限定词与开放的 interpretation 不进
  fixture，各在第 6e 行自己的叶里做（6e-ii、6e-iii）。每个子 record 是 `record d = <父> + y :: nat`，除非该行另有
  写法。读取之后抛的每个错误都带第二行 `Failed to define record "d"`。
- **父 record 的行**（决定 22；接受行经 `Record.get_info` 的 parent、args、sort、`get_parent`、`get_recT_fields`
  核）：`"(nat, bool) ph"`（父为 `([nat, bool], T.ph)`，展开里没有 `nat` 的痕迹——显示为什么头是 record 名时保留写的
  参数）；`record 'c d = "('c::order, nat) ph" + y :: 'c`（`'c` 经 `declare_typ` 得 sort `order`）；`"n p"`
  （`n = nat`，参数里的缩写）；现有的子 record 与实例化父的行。拒绝行（每条消息逐行）：`n`、`nat`、`"nat list"`、
  `"nat ⇒ nat"`、`"nat p list"`、`qn`（`= "nat list"`）、`"nat tv"`、`"('a, 'z) p_scheme"`、`"(nat, bool) p_scheme"`、
  `"'z qs"`、`"(nat, bool) p_ext"`、`"⦇x :: nat, … :: 'z⦈"`、`"nat p foo_ext"`（`datatype 'a foo_ext = F 'a`）、`qph`、
  `logic`、`"logic q9"`（三行文案；若解析器用 `mode_syntax` 证书化此行变红）、`qsyn`（`= "letbinds p"`）、`"t s"`、缺
  参数的 `p`、`"'a"`、`"?'x p"`；加现有的未知父、坏父规格、父 arity 行。预期文案（forms table 第 9-20 行，探针 P3 定稿）：
  `n`/`nat`/`"nat list"`/`"nat ⇒ nat"`/`"nat p list"`/`qn`/`"nat tv"` → `Unknown parent record "T.n"`/`"Nat.nat"`/
  `"List.list"`/`"fun"`/`"List.list"`/`"T.qn"`/`"T.tv"`；两种 `p_scheme` 与 `"'z qs"` → `"T.p_scheme"`/`"T.qs"`；
  `"(nat, bool) p_ext"` 与 `"⦇x :: nat, … :: 'z⦈"` → `"T.p.p_ext"`；`"nat p foo_ext"` → `"T.foo_ext"`；`qph` → `"T.qph"`；
  `logic` → `"logic"`；`"logic q9"` → `Illegal occurrence of syntactic type: "logic"` 加 `The error(s) above occurred in
  parent record specification` 加第二行；`qsyn` → `"T.qsyn"`；`"t s"` → `Ill-sorted instantiation of 'a in parent record
  "T.s"`；缺参数的 `p` → `Bad number of arguments for type constructor: "T.p"`（一行）；`"'a"` → `Bad parent record
  specification: 'a`；`"?'x p"` → `Illegal schematic type variable: ?'x`。哪种错误实现会让哪行变红（变异映射）：默认模式
  重读→`"logic q9"`、`"(nat, bool) ph"`（丢 `nat`）；`mode_syntax` 证书化→`"logic q9"`、`qsyn`；`Sign.typ_match` 代
  `raw_match`→`"t q8"`（文案变 Unknown）；不先判头是否 record 名→`"(nat, bool) ph"`。
- **报错与文案**：theory 层 `record p = make :: nat`、`record p = x :: nat  x_update :: nat`、`record p = x :: nat
  x :: nat`、`record p = more :: nat`、`record 'a p = x :: 'b`（`Extra free type variable(s)`）、重复 record、未知父、
  坏父规格、未定义字段类型、未定义 sort、父 arity 错、ML API 下 TVar 字段类型的完整输出。stock 接受的怪名字作基线：
  `record p = a__ :: nat` 与一个叫 `p_ext_Tuple_Iso` 的字段（名字与内部常量撞）。`private record`/`qualified record`
  的文案移到 stock 探针（§8 探针 (ab)，§7.3 第 16 行）。
- **性能基线**另见 §7.5。

golden 在 stock 副本上录；在 light 落地之后、第一次改 `record.ML` 之前，用户在共享树上跑一次对照比较，三份清单文件的
**内容** sha256 与 HOL heap 的 `isabelle_sources` digest 记进 `tests/golden/CONTROL`；对照比较有任何差异即停下里程碑 1
交用户（共享树无法重录，golden.ML:22）。

### 7.2 theory 层回归（里程碑 1 的 gate，并在每个改了 record.ML、typedef.ML、ctr_sugar.ML 的里程碑末重跑）

§7 扫描出的发行版 session、light 的五个 session（其 golden 对 HOL-Algebra 的 record 事实保持字节相同）、
`Localized_Record_Golden`、`Localized_Record_Golden_Messages` 与 `Localized_Record_Theory_Test` 全部构建通过
（`HOL-Record_Benchmark` 在 src/Benchmarks、不在 ROOTS 里：构建它、载入 Record_Benchmark 的 golden 与 §7.5 都要加
`-d '~~/src/Benchmarks'`，预测）；§7.1 全部 golden 字节相同；签名检查按
`signature_additions.txt`（工具按迁移方案 §5）；性能按 §7.5。**`Localized_Record_Theory_Test`**（`tests/Theory`，只 import
`Main`，决定 22 与决定 11 的 gate；一个 theory 里第一条失败的命令就中止整个 theory，所以每个要单独看失败的形式各占
一个叶子，session 把全部失败一起报，thy_info.ML:252-287）：fixture 叶 `Parent_Forms_Fixture.thy`（§7.1 的 theory 层
fixture，不含任何块；stock 也必须接受）；每个新接受的父形式一个叶（forms table 第 21-29 行：`q1`、`q4`、`"bool q2"`、`"(bool, nat) q3"`
（得 `([nat, bool], T.c)`，按 `c` 声明的顺序）、`"nat p tv"`、`"'x qd"`、`"nat q8"`、`"(nat, unit) p_scheme"`、
`"(nat, (bool, unit) c_ext) p_scheme"`、`"(nat, unit) p_ext"`、`"⦇x :: nat⦈"`、`"(| x :: nat |)"`、`"⦇x :: nat, z :: bool⦈"`、
`"⦇x :: nat, … :: unit⦈"`），各定义一个子 record 与一个按 record 名写全参数的孪生，断言 `Record.get_info` 的 parent
相等（名字按孪生）、两者 record 类型的 `get_recT_fields` 相等、`print_record` 的父行相等、args 与 sort 相同；含
`declare_typ` 行（`record 'c d = "('c::order) qd" + y :: 'c` 给 `'c::order`，与孪生 `record ('c::order) d' = "nat p" + y
:: 'c` 同）；文案变化类各一个叶（forms table 第 30-35 行：`"t q8"` 与 `bad` 报 `Ill-sorted instantiation of 'a in parent
record "T.s"`，孪生 `"t s"`；父为 synonym 加重复字段、`more` 字段、多余类型变量、重复 record 名、`definition` 内错各一），
经 `Outer_Syntax.parse_text` 加 `Toplevel.command_errors` 读，去 markup 后与孪生文案相同；typed API 行放只在 port 上跑
的 `Parent_Forms_Typed_API.thy`：`setup` 里 `Record.add_record … (SOME ([], "T.q1"))` 与 `local_setup` 里
`local_add_record` 仍报 `Unknown parent record "T.q1"`。变异检查对测试自身（stock 就是去掉解析器的实现）：用户用
`contrib/light_locale/tools/stock-isabelle` 在 stock 副本上构建本 session（排除 typed API 叶）——fixture 叶通过，每个
正叶各自以 `Unknown parent record "Parent_Forms_Fixture.<head>"` 失败，每个文案变化叶各自在断言处失败。可选的
私有树变体（头脑风暴 T3）：若用户愿意多建一次，把解析器换成"默认模式重读"或"`mode_syntax` 证书化"的错误实现，第 19 行
`"logic q9"` 与第 20 行 `qsyn` 必须变红。决定 11 的一行：theory 层 `declare [[typedef_overloaded]]` 后不带 `(overloaded)`
的 `record 'a::zero r = f :: "'a nz"` 成功（stock 同）。块内 record 向 theory 层 registration 的传播见 §7.3 第 13b 行
（`Groups.monoid` 里的 300 字段 record），它属于 `Localized_Record_Test`，不在本 session。

### 7.3 块内行为（里程碑 2 的 gate）

测试拆成 leaf theory，每个改变持久 theory 状态的场景一个（light 的 ROOT 规则）；负行统一经 `Outer_Syntax.parse_text`
加 `Toplevel.command_errors` 读错误；每行写明比较的观测量；观测量写成一个共用的 ML helper（正行与变异 leaf 共用）；
孪生：有 `datatype` 孪生的注明，否则一句理由。

1. `locale l = fixes k :: nat begin record 'a p = x :: 'a  y :: nat … end`，块内：`term "⦇x = (1::nat), y = 2⦈"`
   并打印回 record 语法；`term "p.x"`；`typ "nat p"`；`typ "⦇x :: nat, y :: nat⦈"`；`print_record "nat p"`；
   `lemma "x (r⦇x := a⦈) = a" by simp`（simproc；无孪生，datatype 无更新）；`lemma "x ⦇x = a, y = b⦈ = a" by simp`
   （`p.simps`，孪生同）；iff 引理 `⦇x = a, y = b⦈ = ⦇x = c, y = d⦈ ⟹ a = c` by blast（孪生 `d.inject`）；`proof
   (cases r) case (fields a b)`、`proof (induct r)`，对 `('a, 'z) p_scheme` 的 `case (fields a b m)`（无孪生：datatype
   无 scheme）；`hd (find_casesT/find_inductT)` 对 recT 与 scheme 类型与 `Record.the_info` 的 `#cases`/`#induct` 同形
   （孪生 `d.exhaust`）；`Thm.get_tags` 按实际顺序对块内的 `p.cases`、`p.cases_scheme`、`p.induct`、`p.induct_scheme`
   等于 theory 层孪生 record 的（预计 `[name, consumes "0", case_names "fields"]`，决定 17 的手写复述）；
   `definition q where "q = ⦇x = k, y = 0⦈"`；一个带 mixfix 的字段（孪生 `datatype … (infixl)`）；
   `fun f where f ⦇x = a, y = b⦈ = a`（孪生同）；`value "x ⦇x = 1, y = 2⦈"`（孪生无代码）；事实短名 `thm select_convs
   p.select_convs ext_inject p_ext_def p_ext.Rep_p_ext_inject p.make_def p.fields_def p.extend_def p.truncate_def p.x_def
   p.x_update_def p.more_def`（决定 20；def 事实 `is_concealed` 为真；无孪生：BNF 的构造子 def 无名）与名字空间 dumper
   对 theory 层孪生 record 的一一映射；负行 `thm l.l.p.simps` 报 Unknown fact；`Spec_Rules.retrieve @{context} (Const
   (\<^const_name>‹x›, dummyT))` 对 `x`、`x_update`、`make` 各恰一条等式条目（孪生 `d.sel`）；`ML_val` 对 `p_ext` 名：`length (Typedef.get_info @{context} T) =
   1`、`is_some (Ctr_Sugar.ctr_sugar_of @{context} T)` 且条目与 theory 层孪生 record 的 `ML_Syntax.print_term` 相同
   （TFree 形式，决定 15）；`copy_bnf ('a, 'z) p_ext` 成功（今天抛 `Empty`；无孪生）；`lemma "x r = y r" nitpick [expect
   = genuine] oops`（孪生同）；同块一个 17 字段 record 及其 simp/simproc/cases 与 `Typedef.get_info` 对 `p_inner1` 为 1；
   `Consts.the_abbreviation` 对每个 record 常量不存在；块内父解析（决定 22）：`record d1 = "nat p" + z :: bool`、
   `type_synonym qa = "nat p"` 后 `record d2 = qa + z :: bool`，两者 `Record.get_parent` 相同（孪生：theory 层 record）。
   1b（单独 leaf）：块内 `declare p.simps [simp del]`：裸 simp 失败、`simp add: p.simps` 成功；再定义一个 record 后
   与重开后仍是删除状态（del note 在 add 之后重放；孪生 `declare d.sel [simp del]`）。1c（单独 leaf，R6-C16 核实
   报告探针 4）：块内 `declare p.cases [cases del]` 后 `print_induct_rules` 不再列它、`proof (cases r)` 退到
   `p.cases_scheme`（按命题删，`del_att`）；孪生 `declare d.exhaust [cases del]`。1d：块内重开（`context l begin`）与
   theory 上的 `context begin` 里 `term "⦇x = 1, y = 2⦈"`/`⦇l.x = 1, y = 2⦈` 的打印同形（决定 3 辩论的改动 [10]）。
2. `end` 之后：`term "⦇l.x = (1::nat), y = 2⦈"` 读回并打印同形；`typ "nat l.p"`；`thm l.p.simps l.simps` 无
   attribute；`lemma "l.x (r⦇l.x := a⦈) = a" by simp` 与 `lemma "r⦇l.x := a, l.x := b⦈ = r⦇l.x := b⦈" by simp`
   **成功**（simproc，无孪生）；`lemma "l.x ⦇l.x = a, y = b⦈ = a"`：`by simp` 失败、`by (simp add: l.p.simps)` 成功
   （孪生同）；iff 引理裸 `blast` 失败、`blast dest: l.p.iffs[THEN iffD1]` 与 `auto iff: l.p.iffs` 成功、`blast dest:
   l.p.iffs` 报 `Ill-formed destruction rule`（孪生 `l.d.inject`）；`value` 成功；`proof (cases r) case (fields a b)`
   成功、`induct r`/`case_tac r`/`induct_tac r` 用 record 的规则（决定 17；孪生 `cases t` 失败 `Failed to apply proof
   method`、`induct t` 报 `Unable to figure out induct rule`）；`take 3 (map Thm.prop_of (Induct.find_casesT @{context}
   @{typ "nat l.p"}))` 按 `aconv` 等于 `l.p.cases`、`l.p.cases_scheme`、`l.p.p_ext.Abs_p_ext_cases` 的命题，`drop 3`
   等于 `find_casesT` 对 `'x` 的；scheme 类型同法；`Induct.dest_rules` 中 `Thy.l.p`、`Thy.l.p_scheme` 各一条，且**没有**
   带前提的 record 规则（rev6-C16）；`fun g where g ⦇l.x = a, y = b⦈ = a` 成功（孪生同）；`thm l.p.select_convs
   l.select_convs l.Rep_p_ext_inject`，负行 `thm p.select_convs` 报 Unknown fact；打印：`term "l.x r"` 印 `l.x r`；
   父解析：`record c1 = "nat l.p" + w :: nat`、`type_synonym qb = "nat l.p"` 后 `record c2 = qb + w :: nat` 同父；
   `definition v :: "nat l.p" where "v = ⦇l.x = 1, y = 2⦈"` 后 `value v`（命名的 value 项）；另一个 locale `m` 里同名
   record `p` 之后 `l.p`/`m.p` 两套名字互不遮蔽、`thm l.p.simps m.p.simps` 各取各的；全名、`intern`/`extern` 与 §4
   逐项相同（名字空间 dumper）。
   2b（变异检查，表格：目标行 × 观测 context → 重施位置、leaf、取反后的预期）：观测量——`Thm.nprems_of (hd
   (find_inductT …)) = 1` 且 `Exported_Premises.count_of = 0`、`induct_tac r` 不留 `0 < ?n`、`proof (induct r) case
   (fields a)` 成功、`cases` 同法、对 record 键与 `nat` 键的整张 `find_casesT`/`find_inductT` 列表里没有带多余前提的
   record 条目；对 `nat` 键只查 `find_casesT`（induct 表按结论归档，`nat` 下不会有 record 条目，induct.ML:127、:230）。
   变异表（变体 × 观测 context → 重施位置、leaf、取反后的预期；全部预测）：

   | 变体 | 观测 context | 取反后的预期 |
   | --- | --- | --- |
   | M1：块内 notes 换回 stock 列表（把四份条件副本连 stock 的 attribute 按 stock 顺序登记、使之最新） | 嵌套 `assumes` 之后的外层（4b 叶）、重开块、之后的 interpretation、7b、8b、light 的 theory 副本、record 之前已有的 registration、7k | 头的 `nprems_of` 为 2、导出前提留作子目标、无 tag 副本上 `Too many parameters for case`，带 K tag 的副本上 light 的 rule_cases 跳过 K 条前提、case 对齐而证明在 `qed` 失败；7h（第一前提无 Var）处重施时直接抛 THM |
   | M2：立即施加缺失——单独的 4b 形叶（`locale l4 = fixes k :: nat`；`interpretation I: l4 5`；`context l4 begin context fixes n :: nat assumes "0 < n" begin record p4 = z :: nat`），record 之后紧接 `local_setup ‹fn lthy => Local_Theory.map_contexts (fn _ => fold (fn (th, att) => #2 o Thm.proof_attributes [att] th) (map (Proof_Context.get_thm lthy) ["p4.cases", "p4.cases_scheme", "p4.induct", "p4.induct_scheme"] ~~ [Induct.cases_del, Induct.cases_del, Induct.induct_del, Induct.induct_del])) lthy›` | 定义层与外层——内层 `end` 之后的外层就是第 0 层（local_theory.ML:167、:452-456） | `Failed to apply initial proof method`（proof.ML:938；`case_split` 退路，induct.ML:516）、`Unable to figure out induct rule` |
   | 3E 格（重开、interpretation、G、导入格） | 从 theory 重建的 context | M2 不影响（模拟只改当时打开的层，不存 note、不写 theory）；只有 theory 层 `[cases del]` 才能让它们变红——第 5 行的 `[cases del]` 行就是这个格的对照 |

   M2 不用 `declare … [cases del]` 模拟的理由：heavy locale 或 class 里 `Locale.add_facts` 会把这条 del note 存下，在重开、
   interpretation、G 与导入它的 locale 里重放（locale.ML:666-683、:574-586；与第 1b 行同一机制），3E 格会跟着变红；
   嵌套 `assumes` 叶里到达第 0 层的那份副本被导出成 `0 < ?n ⟹ …`（generic_target.ML:447-449），`del_att` 按命题匹配，
   删不掉无条件规则，外层格反而保持绿；theory 上的 unnamed context 里 `theory_target_notes` 保留 attribute
   （generic_target.ML:407-408），del 会写进 theory。
   这检查的是观测量能区分正误，不是代码本身——ELSE 分支是私有的、在 heap 里，重载 record.ML 撞重复命令检查，改名
   副本是 §10 否决的 rev3-C25；M1 的代码变体由用户用"ELSE notes 换回 stock 列表"的代码构建一次（核实报告探针 3），
   各格应变红。Spec_Rules 的两种写入顺序同法（第 5 行与第 20 行的头）。第 8、9 行作对照（预计绿）。
3. `context l begin … end` 重开：短名（含事实别名、def 事实）、simp、simproc（`lemma "x (r⦇x := a⦈) = a" by simp`）、
   cases、`fun`、`copy_bnf` 恢复；
   `Induct.dest_rules` 中 `Thy.l.p` 条目数 1；重建的 context 从 theory 取 3E 的无条件规则，`hd find_casesT` 是它
   （3E 格；孪生 `datatype`）。
4. `interpretation I: l 5`：`thm I.p.simps I.simps`、`I.x`、`I.p.x`、`typ "nat I.p"`、`thm I.p.select_convs I.p.make_def`
   （同一对象）；theory 层 `term "l.x r"` 印 `I.x r`、`⦇I.x = …⦈` 并读回（孪生：无参数 locale 的 definition、
   `type_synonym`）；interpretation 实例的 `[simp]`/`[iff]` 在 theory 层生效；`cases r` 用的规则与匿名规则同命题、
   `Induct.dest_rules` 中条目数 1；`record c3 = "nat I.p" + w :: nat` 与 `"nat l.p"` 同父（决定 22；type_alias、stock
   路径，同 6b；孪生 theory 层）；接着 `interpretation J: l 6`：无错、无重复警告（light 的 `Test_Support.with_warnings`
   捕获）、`thm J.p.simps`、J 之后 `value` 不变、代码证书不变、`Induct.dest_rules` 的 `#type_cases` 里 `Thy.l.p` 的条目
   数仍 1（父解析头脑风暴综合给的计数法）、
   Spec_Rules 行按 §5.8 (6)；同块第二个 record `big`（300 字段）的 `I.big.simps` 可用；在 record 之前做的 interpretation
   之后 Induct 存的是匿名规则（按命题比较）。
   4b（单独 leaf）：`locale l4 = fixes k :: nat`；`interpretation I: l4 5`；`context l4 begin context fixes n :: nat
   assumes "0 < n" begin record p4 = z :: nat end … end`；观测点：外层、`end` 后 theory 层、`context l4 begin` 后、
   之后的 `interpretation J: l4 6` 后、theory 上 `context fixes c assumes "0 < c"` 里的 `global_interpretation G: l4 7`
   后；观测量对 recT 与 rec_schemeT：`Thm.nprems_of (hd find_inductT/find_casesT) = 1`、`Exported_Premises.count_of = 0`、
   `proof (induct r) case (fields a)`、`induct_tac r` 不留 `0 < ?n`、`nat` 键下没有 record 条目、theory 层 `fun` 用 `p4`
   模式成功；Spec_Rules 头按 §5.8 (15)/(19) 的免检格；哪个格测什么：外层 = `map_contexts` 步；`end` 后 theory 层、重开、
   之后的 interpretation、G、record 之前已有的 registration 的 theory 层与导入格 = 3E 的 theory 写；孪生：`datatype
   (plugins del: code)` 与 `typedef`（探针 (m)；普通 `datatype` 崩在 `dest_equals`）。
5. `locale la = fixes k :: nat assumes "k > 0" begin record 'a p = x :: 'a  y :: nat … end`（另一变体 `locale la0 = fixes
   k :: nat`，没有 `assumes`，单独 leaf）：theory 层 `la.p.simps` 的 `Thm.nprems_of` 比 stock 多 1；块内 simp 正常；`end`
   后 theory 层 `record 'a cq = "'a la.p" + w :: nat` 成功（孪生 `primrec` 失败），且 `Ctr_Sugar.ctr_sugar_of_global thy`
   对 `cq` 的扩展类型有条目、`Thm.nprems_of (#exhaust …)` 为 1、theory 层 `fun h :: "nat la.cq ⇒ nat" where h ⦇la.x = a,
   y = b, w = c⦈ = c` 成功（形状同 theory 层孪生）；`Record.get_info thy "…la.p"` 六条定理 `nprems_of` 与 stock theory 层
   相同（`simps`/`iffs` 0、四条规则 1）、`hyps_of` 空、tag 按字段：四条 `[name, consumes, case_names]`、`simps`/`iffs`
   `[name]`；theory 层 `fun f :: "nat la.p ⇒ nat" where f ⦇la.x = a, y = b⦈ = a` 成功、`Thm.nprems_of (#exhaust (the
   (Ctr_Sugar.ctr_sugar_of_global thy T)))` 为 1（决定 15；孪生 `datatype` 预计失败到 interpretation）；`cases r`
   用无条件规则（`Thm.nprems_of (hd …) = 1`）；`declare la.p.cases [cases del]` 后 `cases r` 仍用匿名规则，再以无条件
   命题写 lemma 并 `[cases del]` 后退到 `la.p.cases_scheme`（§5.8 (4)），随后重开 `context la begin` 与
   `interpretation I: la 5` 之后仍保持删除（不再加回；孪生：theory 层 record 的 `[cases del]`）；`la0` 变体直接
   `declare la0.p.cases [cases del]` 删得掉且同样保持；`declare I.p.cases [cases del]` 同法；删后以
   `declare la0.p.cases [case_names fields, cases type: la0.p]` 加回、`case (fields a b)` 可用（`type:` 收一个类型名，
   induct.ML:375、args.ML:170-172；它是 `cases r type: la0.p` 查表的键，induct.ML:285、:905-910）；interpretation 之前
   与之后各观测一遍（计数：`Induct.dest_rules` 的 `#type_cases` 里 `Thy.la.p` 的条目数，`interpretation I: la 5` 之后 1、
   `interpretation J: la 2` 之后 1）；`simp add: la.p.simps` 失败、`simp add: la.p.select_convs` 成功；
   `Spec_Rules.retrieve_global` 对 `la.x` 两条、头一条无条件（孪生 `d.sel`）；export `spec_rules` 行数；`copy_bnf`、
   `nitpick` 行同第 1 行（E）。
   **5b**（用户自己登记的规则不被压下，rev7-C2 的另一面；单独 leaf，与第 5 行、6d 行查同一机制——`Item_Net.update` =
   `cons` ∘ `remove`，item_net.ML:78）：`locale l5 = fixes k :: nat begin record 'a p = x :: 'a  y :: nat end`；theory 层
   `lemma my_cases [case_names fields, cases type: l5.p]: "(⋀b a. r = ⦇l5.x = a, y = b⦈ ⟹ P) ⟹ P"`（字段顺序故意
   颠倒）；观测点：lemma 之后；`context l5 begin` 里；在那里再 `record q = z :: nat` 之后与它 `end` 之后；`interpretation
   I: l5 5` 之后；`lemma (in l5)` 里；观测量：`Thm.prop_of (hd (Induct.find_casesT @{context} @{typ "nat l5.p"}))`
   aconv `Thm.prop_of @{thm my_cases}`，且 `proof (cases r) case (fields b a)` 给出 `r = ⦇l5.x = a, y = b⦈`（只看 `case
   (fields b a)` 成功分不出规则）；预期全绿；孪生 theory 层 record；变异：6d 的构造——`local_setup` 一条忽略 morphism、
   重施本 record 自己原始 `cases` 规则的存下 declaration，重开格与 interpretation 格必须变成 `r = ⦇l5.x = b, y = a⦈`。
   预期进批量签字。
6. 父子：块内 `record 'a cp = "'a p" + z :: bool`；块外 `record 'a cq = "'a l.p" + w :: nat`，且
   `Ctr_Sugar.ctr_sugar_of_global thy` 对 `cq` 的扩展类型有条目、`Thm.nprems_of (#exhaust …)` 为 1、theory 层 `fun h ::
   "nat l.cq ⇒ nat" where h ⦇l.x = a, y = b, w = c⦈ = c` 成功（形状同 theory 层孪生）；theory 层
   `record par = a :: nat` 后块内 `record ch = par + b :: nat`，`end` 后 `proof (cases r) case (fields a b)` 对
   `r :: l.ch` 得到 `a`、`b`（今天静默得父规则；无孪生：决定 22 与父子关系没有 datatype 对应，孪生是 theory 层同样
   写法的 record）；theory 层 `fun` 对 `ch` 模式与 theory 层孪生相同（探针 (l) 的 stock 结果）。6b（块内形式，决定 22；
   用 §7.1 的块 fixture `l0`/`r`/`qa`/`I0`）：在 `l0` 里 `"nat r"` 与块内 `qa` 作父；`end` 后 `"nat l0.r"`；
   `interpretation I0: l0 5` 后 `"nat I0.r"`（type_alias 的头是 record 名，stock 路径）。6c（负行，里程碑 2，只这两条）：
   `"(nat, bool) r_scheme"` 报 `Unknown parent record "T.l0.r_scheme"`、`"nat list"` 报 `Unknown parent record
   "List.list"`；theory 上 unnamed context 里 `local.r` 的通过条件在 6e-v（里程碑 4）。
   **6d**（rev7-C2；单独 leaf）：子在父块外。`locale l6 = fixes k :: nat begin record p6 = x :: nat end`，theory 层
   `record c6 = "l6.p6" + y :: nat`；bundle 变体 `bundle b6 begin record pb = z :: nat end`、`record cb = pb + w :: nat`、
   `unbundle b6`；观测点：`context l6 begin` 之后、`interpretation I6: l6 5` 之后、`locale m6 = l6 begin` 内、`unbundle`
   之后，另加 class `d = c + …` 与 `sublocale` 变体；观测量：`Thm.prop_of (hd (Induct.find_casesT @{context} @{typ c6}))`
   aconv `c6.cases`、`find_inductT` aconv `c6.induct`、`proof (cases r) case (fields a b)` 得 `r = ⦇l6.x = a, y = b⦈`、
   `case_tac`/`induct_tac` 同；预期全绿；孪生 theory 层 `par6`/`ch6`；变异：`local_setup` 重加一条忽略 morphism、
   重施父原始规则的存下 declaration，各格必须变红（探针 (aa) 在 stock 上的复现是负对照）。
   **6e**（里程碑 4；用 §7.1 的里程碑 4 fixture `l`/`lp`/`lpb`/`lpq`/`ql`/`I`，分几个叶；每个"在 `context l begin` 里定义
   record 又在同块按短名使用它"的正项都写明在无限定词 interpretation 之前还是之后——除 6e-iv 外都在之前）：
   6e-i（导入 fixture 的叶，没有无限定词 interpretation）——`context l begin` 里 `record d = lp + y :: nat` 的 `#args`
   （经 `Record.get_info "T.l.d"`）含隐藏参数 `'a`，名字与 sort 就是块里的（隐藏项等于 `("'a", 块的 sort)`）、
   `Record.get_parent` 为 `SOME ([TFree 'a], "T.l.lp")`、`term "⦇g = f, y = 0⦈ :: d"` 类型检查通过；孙 record；`record
   (in l) c = lp + …`；`record 'a c2 = lp + z :: 'a`（声明的 `'a` 是块固定变量）：`#args` 与父参数带同一个新鲜名、没有
   隐藏参数；theory 层 `"I.lp"` 与 `"nat l.lp"` 同父（`([nat], T.l.lp)`）；`lpq` 的全局参数表 `('b, 'a)`（观测量
   `Record.get_info` 的 `#args`）：块外 `(bool, nat) l.lpq` 接受且字段类型 `h :: bool`、`gq :: nat ⇒ nat`；`('b, nat, 'z)
   l.lpq_scheme` 接受且 `h :: 'b`、`gq :: nat ⇒ nat`（只凭接受分不出两种顺序：Pure 只查参数个数，type.ML:286）；
   `interpretation J: l Suc` 后 `bool J.lpq` 印 `(bool, nat) l.lpq`；`print_record` 的头；同块子 `('b, 'c) lpc = "'b lpq"
   + k :: 'c` 的全局参数表 `('b, 'c, 'a)`，块外 `(bool, int, nat) l.lpc` 且 `h :: bool`、`k :: int`、`gq :: nat ⇒ nat`；
   同块 `type_synonym qla = "'a p"`（forms 第 43 行）后 `record d3 = qla + y :: nat` 与同块孪生 `"'a p"` 同父；class/
   instantiation/light/experiment 变体；决定 19 写入顺序的正项：块内 `lp` 解析为 `local.lp`、`definition fd :: "lp ⇒ nat"
   where "fd r = 0"` 可用（`l` 固定了 `f`，写 `definition f` 会报 `Duplicate fixed variable(s)`，决定 13、第 14 行）；
   交换两条缩写写入顺序的变异在这里预计仍绿（作对照），变红的格在 6e-v。
   6e-ii（无限定词 interpretation 叶，导入 fixture）：实例用 `interpretation l "λx::nat. x"`——fixture 的 `I`（实例
   `id :: nat ⇒ nat`）在 `Pattern.matchess` 下不匹配它（stock locale.ML:303-304、:616-624），不会被静默跳过，且仍给
   `'a := nat`；按顺序核：(a) interpretation 之前 theory 层 `typ lp` 报 `Undefined type name: "lp"`（正对照）；(b) 之后
   theory 层 `record d = lp + y :: nat` 父为 `([nat], T.l.lp)`（全局缩写 `<leaf>.lp`，`<leaf>` 是这个叶的 theory 名）；
   (c) 只记录：重开 `context l begin` 里 `lp` 读成什么（P11 第 (2) 半）。
   6e-iii（开放 interpretation）：`interpretation K: l id` 后 `typ "K.lp"` 报 `Undefined type name: "K.lp"`（forms 第 41
   行；提供方决定 2）。
   6e-iv（先解释后定义；只记录，预期值等用户裁，§5.8 (22) (b)）：无限定词 interpretation 在先的叶里 `context l begin
   record lp2 = g :: "'a ⇒ 'a"  record d2 = lp2 + y :: nat end`，记第二条命令里 `lp2` 的读法与 `d2` 的父（源码预测
   `([nat], T.l.lp2)`、无隐藏 `'a`）；再加非强制前缀的变体 `interpretation i?: l "λx::nat. x"`（提供方决定 5 第三点
   预测短名读成 `T.i.lp2`）。
   6e-v（theory naming 的两个叶 = P11 第 (1) 半，各自一个 theory）：theory 上 `context fixes x :: 'a begin record r = y ::
   'a  record d = r + z :: nat end`——`r` 读成 `local.r`、`d` 的父等于孪生 `"'a T.r"`、`end` 后 `"nat r"` 读成 `T.r`；
   `instantiation list :: (type) c begin record lp = …` 用 `'a` 得隐藏参数、块内写 `lp`（forms 第 36 行）；两叶各带决定
   19 写入顺序的变异：交换两条缩写的写入顺序后，`definition f :: "r ⇒ nat"` 必须报 `Bad number of arguments for type
   constructor: "<thy>.r"`（instantiation 叶同，`"<thy>.<record 名>"`）。
   负行——`"nat lpb"` 报 `Unknown parent record "local.lpb"`、绕法 `"(nat, 'a) l.lpb"` 成功（forms 第 42 行的拒绝；该行
   写的绕法 `"('a, nat) l.lpb"` 是隐藏参数在前时的写法，已被用户的在后裁定取代，forms table 此后只作历史记录）；`ql`
   作父报 `Unknown parent record "local.ql"`（第 44 行）。规则：同一个导入闭包里不重复 fixture 用过的前缀（`I0`、`I`），
   也不用更早的 registration 会匹配的实例去解释 `l`（会被静默跳过）；这里的实例与头脑风暴 forms 第 38-39 行的
   `id :: nat ⇒ nat` 不同。孪生：无隐藏参数、按名写的同样 record。这些预期进批量签字。
7. 嵌套 `context fixes z :: nat begin record … end`（theory 上的 unnamed context）：名字无前缀、`[simp]`/`[iff]` 全局、
   `value` 成功、`Induct.dest_rules` 中条目数 1（孪生 `datatype`）。7b `context fixes n :: nat assumes "0 < n" begin
   record q = y :: nat end`：`q.simps` theory 副本条件形式；simproc（`lemma "q.y (r⦇q.y := a⦈) = a" by simp`、`lemma
   "r⦇q.y := a, q.y := b⦈ = r⦇q.y := b⦈" by simp`）与 `value` 可用（孪生：普通 `datatype` 崩在 code
   插件的 `dest_equals`（`TERM`）；`datatype (plugins del: code)` 预计通过，但其 BNF typedef 的 `Abs_cases` 与 `exhaust`
   的条件副本归到 `nat` 下，探针 (e)）；`cases r`/`induct r` 对 `r :: q` 用无条件规则、case 名 `fields` 正确；theory 层
   `fun` 用 `q` 模式成功；级别 2 里 `export_code`、`quickcheck` 可用；`find_casesT @{typ nat}` 的头与块前一致（按
   `eq_thm_prop`；预计 `Nat.nat_exhaust`），`lemma "m = 0 ∨ (∃k. m = Suc k)" for m :: nat by (cases m) auto` 成功、
   `proof (cases m) case 0` 成功（rev6-C16：record 列普通 gate 行）。7c-7d：同 7b 的 `typedef` 与 `datatype (plugins
   del: code)` 孪生列，前置：light 窄变体落地；变体落地后的 gate 值：`nat` 键的头回到 `Nat.nat_exhaust`、条件副本带 K
   tag。7e `locale l3 = fixes k :: nat begin context assumes "1 < k" begin record p3 = z :: nat end …`：record 命令成功
   （rev6-C16）；外层 `proof (induct r) case (fields a)` 无多余子目标（`map_contexts` 格）；`end` 后 theory 层、重开后同
   （3E 格）；孪生 `typedef`/`datatype (plugins del: code)` 的命令预计抛 THM（窄变体前；变体后的值取决于 light 对外层
   `standard_notes` 副本的回答——`Locale.add_facts` 存进 target context 的记录副本，light 的第一项已覆盖，决定 21 D3
   (c)）。7f `interpretation I: l3 5` 成功
   （record 列）；nat 的观测用 4b 的 `fixes n :: nat assumes "0 < n"` 变体；孪生列待 light 回答 (iii)。7g 封闭的 class
   例：`class c7 = fixes cc :: 'a begin context assumes "cc = cc" begin record p7 = z :: nat end … end`，用 4b 的整表
   观测量，在 class 层、`end` 后 theory 层（3E 格）与重开后各观测一次；孪生预计 THM（7c-7j 前置）；探针 (m) 加封闭变体。
   7h record 之前做的 interpretation（闭命题 `assumes "1 < k"`，k 实例化为 5）：record 命令成功；孪生预计 THM（窄变体
   前；孪生列另待 light 对 (iii) 的正式确认，同 7f）。7i `context fixes n :: nat begin context assumes "0 < n" begin
   record q7 = z :: nat end … end`（theory 上双层嵌套）：外层与 theory 层观测，theory 层 `fun` 用 `q7` 模式成功；孪生
   探针 (w)（窄变体前预计 THM；变体后的值取决于 light 对外层 `standard_notes` 副本与 theory 副本落点的回答；7i 没有
   registration，不涉 (iii)）。7j theory 上 `context assumes "finite (UNIV
   :: bool set)"`（闭命题）：record 成功；孪生预计 THM（探针 (n)）。7k（两个写者一起）：record 之前在 theory 上
   `context fixes c assumes "0 < c"` 里做过 `global_interpretation`，之后定义 record、再 `cases r`；预期 `nprems_of` 1、
   `cases` 成功、每键一条、`nat` 键干净；孪生列在 7c-7j 的前置下。
8. `instantiation nat :: c begin record … end`：同 theory 层外加别名；名字空间 dumper 与 theory 层孪生、同块
   `datatype` 孪生相同；`Induct.dest_rules` 条目数 1（无孪生：datatype 在 instantiation 里的条目数另计）；父行 `"nat p"`
   与块内 synonym `qa`，与按 record 名写的孪生比 `Record.get_parent`；级别 2 的 `export_code`、`quickcheck`；§5.8 (24)
   (ii) 的观测：一个叫 `cc_nat` 的字段仍是普通字段、`instance` 仍要求定义 `cc`。8b：`instantiation nat :: c begin context
   fixes n :: nat assumes "0 < n" begin record p8 … end … end`，theory 层 `hd find_inductT` 无条件、`nat` 键干净（孪生
   `datatype (plugins del: code)`，孪生列标 D3：窄变体须覆盖非 `Named_Target` 的 target）。8c（§5.8 (17)，单独 leaf）：
   装置 `typedef t = "UNIV :: nat set" by simp` 加 `code_datatype Abs_t`（给出 typerep、term_of 与代码，不给
   random/full_exhaustive 实例）；`instantiation t :: random` 里先 `record p1 = f1 :: t  g1 :: nat`，再 `instance ..`
   （可执行的 `random_t`），再 `record p2 …`，`end` 后 theory 层 `record p3 …`；`Sorts.has_instance (Sign.classes_of
   thy) <ext 名> @{sort random}` 预计 `p1` 假、`p2`、`p3` 真；`quickcheck [random]` 对 `p3` 可跑、对 `p1` 报无生成器；
   第二个类型上 `full_exhaustive` 同法（`code_datatype` 供 term_of，code_evaluation.ML:126-128）；没有 `t` 类型字段时
   不出现此缺口；`datatype` 孪生只作信息。
9. `class c = fixes cc :: 'a begin record 'b p = … end`：成功且 `value` 可用（孪生 `datatype` 失败）；`end` 后预期
   （§5.5，预测）：`c_class.p.simps` 在 `dest_simps`、theory 层 simp 引理成功、cases 条目一条且命题为原始规则、短名
   `p.select_convs`/`x` 解析（theory 层检查无孪生）；父行 `"nat c.p"` 与 `"nat p"`；class `end` 后 `typ "nat p2"` 可读
   （孪生 `record 'b p2 = h :: 'b`）；§5.8 (24) (i) 的观测：`c.x` 的类型不带 `'a::c` 约束、同块 `definition f :: "'a
   ⇒ 'a" where "f x = cc"` 的 `c.f` 带；负行 `record 'a bad = x :: 'a`（里程碑 4 前 §6 两行；里程碑 4 起转正：`'a` 是
   声明参数、按决定 19 (a) 在背景换新鲜名，`Record.get_info "T.c.bad"` 的 `#args` 恰一项、sort 是块里读到的 sort——
   class 块里预测为 base sort（record.ML:2370-2375、class.ML:339-341），探针 P9 核）；不声明的变体 `record bad2 = bu ::
   'a`（里程碑 4 前 stock 的 `Extra free type variable(s)`；里程碑 4 起 `'a` 作隐藏参数、带 base sort，`nat c.bad2` 对
   非实例也接受，预测）；9b `class c9b = fixes cc :: 'a begin context fixes n :: nat assumes "0 < n" begin
   record p9 = z :: nat end … end`：4b 的整表观测量对 recT、rec_schemeT 与 `nat` 键，加 `proof (cases r)`（孪生探针 (m)
   的 `datatype (plugins del: code)`）；9c `class c9 = fixes cc :: 'a assumes "cc = cc" begin record 'b p9 = x :: 'b
   end`：第 9 行的预期加第 5 行的 `get_info` 检查（无孪生：`datatype` 在 class 里失败，§5.5）。
10. `locale lf = fixes f :: "'a ⇒ 'a" begin record 'a bad = …` 报 §6 两行；`record 'b ok = …` 成功；字段类型变体
    `record ok2 = g :: "'a ⇒ 'a"` 报 `Extra free type variable(s)`（里程碑 4 前）；`instantiation` arity 变量的
    负行；`locale l0 begin definition f :: "'a ⇒ 'a" where … record 'a p … end` 成功；纯类型 locale 的负行；
    `locale lz = fixes g :: "'z ⇒ 'z" begin record 'a p = x :: 'a  y :: nat end` 成功（决定 9 的 `zeta`），其 `typ`、
    `print_record`、simproc 行；各带 `datatype` 孪生（`datatype` 对不声明直接用的变量报 `Extra type variables on
    right-hand side`，bnf_fp_def_sugar.ML:2335-2338，对声明为参数的报 :2309 的 `Locally fixed type argument`）。里程碑 4
    起第 9、10 行的负行改正行：`record d = p + k :: nat` 得隐藏参数；`term "r :: p"` 的打印（§5.8 (20)，孪生无隐藏参数
    的 record 印 `p`）；例外行：theory 层 `record ('a, 'b) ph = w :: 'b`，块内 `record d = "('a, nat) ph" + y :: nat`
    报 `Extra free type variable(s) 'a`（孪生 (i) theory 层同命令同文案；(ii) 同块 `"(nat, 'a) ph"` 成功、得隐藏 `'a`）；
    嵌套层子行：`context fixes y :: 'd begin record r2 = w :: 'd end` 后外层 `r2` 报 `Undefined type name`、`nat l.r2`
    可读（§5.8 (25)；孪生 `record 'd r2 = w :: 'd`）；`locale m = l1 + l2` 两边各有带隐藏参数、内容不同的 `p`
    （`locale l1 = fixes x :: "'a::order"` 里 `record p = g :: "'a ⇒ 'a"`，`locale l2 = fixes u :: 'b` 里 `record p = h ::
    "'b option"`）：预期三行——提供方 §6 第 2 条 `Type abbreviation "p" is already defined as "…" and cannot also be
    defined as "…".`、`Rename it or import it with a qualifier.`，再接 `The above error(s) occurred while activating facts
    of locale instance …`（stock locale.ML:529）；两个展开式属于不同的全局 record 类型、内容必不同，印出的具体形式由
    探针钉住；`p` 先于 `p_scheme` 登记，所以报的是 `p`；随 local_type_abbrev 决定 5/17/20 与其 §5 第 8 行（§5.8 (21)）；
    孪生无隐藏参数时成功。10b（第二次无限定词 interpretation）：`interpretation l Suc`（`'a := nat`）之后
    `interpretation l "λx::bool. x"`——先报提供方 §6 第 2 条加 activation 行（其 §5 第 8f 行）；之后再做一次 `nat` 实例
    `interpretation l "λx::nat. x"`——副本内容相同、提供方决定 20 接受，剩下 stock 自己的 `Duplicate fact declaration`
    （全局事实严格，global_theory.ML:300；预测）。父解析与 `lpb`/`I.lp` 各行移到 6e。
11. 旧 API：`ML ‹Record.add_record {overloaded = false} … thy›` 在 `setup` 里仍可用（理由：孪生是 theory 层 record）；
    `Record.get_info thy`、`Record.get_recT_fields thy` 对块内 record（经 `l.p`）给出结果。
12. `(overloaded)`：装置 `typedef (overloaded) 'a::zero nz = …`；`record (overloaded) 'a::zero r = f :: "'a nz"` 块内
    成功；负孪生：不带 `(overloaded)` 报 typedef 的 open-dependencies 错接 record 包装，与同块裸 `typedef` 对照；决定 11
    的行：块内 `declare [[typedef_overloaded]]` 之后不带 `(overloaded)` 的 `record 'a::zero r2 = f :: "'a nz"` 成功
    （孪生：同块裸 `typedef` 带开关、theory 层同写法的 record）。
13. 同一 locale 两个 record 后 `interpretation`：无 `Duplicate fact declaration`（决定 14；孪生 `datatype`）。13b：
    `context monoid begin` 里一个 300 字段 record，在 `Locale.registrations_of` 给出的每个 theory 层 registration 前缀
    （Main 下 `add`、`mult`、`inf_top`、`sup_bot`、`or`、`xor`、`and`）下 `<前缀>.p.select_convs` 可解析、规则同命题；
    重开与再做一次 interpretation 无错、无重复警告；孪生 §7.5 (1) 的 300 字段 theory 层 record；§7.2 指向它；§7.5 的
    (2)、(4)、(5) 含向这些 registration 的传播，比值不是纯块内开销。
14. 同名块参数：`locale lx = fixes x :: nat begin record p = x :: nat`、`fixes make` 各一行，第一行与同块
    `definition x …`、`datatype` 的报错同文（去 markup 比较）、第二行是包装（决定 13、§6）；theory 上 unnamed context
    的变体。
15. **合并方向**（§3.10、§3.11 的"保留 context 条目"）：`locale lb = fixes k :: nat assumes "0 < k" begin` 先
    `typedef t`、`datatype d`，再 `record p`。record 之前（正对照）：块内 `d` 的 exhaust `nprems_of` 1、`Rep_t_inject`
    0，theory 侧 2、1——两侧不同才能判别；record 之后四值不变、`Typedef.get_info` 对 `t` 长度 1、块内 `fun h where
    h (D n) = n` 成功。孪生：以 `datatype e` 代 record。无 light 孪生（light 里程碑 3 的读者会遮住反向合并）。无
    变异检查（hunk 在 heap 里、Data 未导出）。
16. `private record`、`qualified record`、`record (in l)`、`record (in -)`：在 theory 上的 unnamed context 与
    `experiment` 里与 `private datatype`、`private definition`、`definition (in -)` 等对照可达性（含实例与 typedef 名）；
    theory 层与 `locale l begin` 里 `private record` 的负行（`Missing local scope`，文案由探针 (ab) 在 stock 上定）；
    嵌套块里 `record (in -)` 的负行（级别 2 不可重初始化）。
17. `code_pred` 对返回块内 record 的谓词：与 theory 层孪生 record **相同**（条目同形）；`inductive Pr :: "p ⇒ bool"
    where "Pr ⦇x = 0, y = 0⦈"` 后 `code_pred Pr .` 在块内与 theory 层同报 "Not a datatype constructor"（预测，探针 (v)；
    若块内越过编译抛 THM 即为倒退）。
18. `bundle b begin record … end`（18a）、`open_bundle`（18b）、18c 一个调 `Local_Theory.define` 的替身插件（第 25 行的
    测试插件加一条 `define`）下的 bundle（**预计 record 成功**，插件常量 `Thy.p.c` 在 theory 层，rev6-C6）：按 §5.7 的表
    逐格核；`unbundle` 在 theory 层与另一个 locale 内各一次；变异：块内 notes 的 tag-only 列表换成 `Thm.rule_attribute`
    版，预期到 `unbundle` 时失败（决定 17）；孪生 `datatype` 报 `Not possible in bundle target`、裸 `typedef` 成功、
    mixfix 行孪生 `bundle b2 begin notation f … end`。18d `overloading` 块：`consts c0 :: "'a ⇒ nat"`，`overloading c0_nat
    ≡ "c0 :: nat ⇒ nat" begin record p = c0_nat :: nat … definition c0_nat where "c0_nat n = n" end`——装置必须在块内
    定义重载常量，否则 `end` 报 `Missing definition(s) for parameter(s) "c0"`（overloading.ML:183-190）；观测同 §5.4；
    §5.8 (24)(ii) 的 overloading 半的观测：字段 `c0_nat` 仍是普通选择子、`definition c0_nat` 仍被要求（孪生：同块
    `datatype d = D nat`，只作信息）。18e `overloading` 里嵌套 `context fixes n :: nat assumes "0 < n" begin record p18 =
    z :: nat end`：用 8b 的观测量（theory 层 `hd find_inductT` 无条件、`nat` 键干净），核决定 21 里"`instantiation`/
    `overloading` 内的嵌套层同样分属 (i)/(ii)"那一句；孪生 `datatype (plugins del: code)`，孪生列标 D3。`experiment
    begin record … end`：块内
    观测同 §5.2（含父行 `"nat p"`），`Induct.dest_rules` 多一条匿名条目（无 theory 层 `fun` 行：名字 concealed 且私有）。
19. 单独 leaf：locale 里 `declare [[record_codegen = false]]` 后 record 无代码证书，同一 theory 里之后 theory 层的 record
    代码完整（决定 5；理由：孪生 theory 层）。
20. **四表规则的机械核查**：context 集合——定义层；内层 `end` 之后的每个外层；`end` 之后的 theory 层；重开的块；
    一次与两次 interpretation 之后；可重初始化处的 `lemma (in -)`；导入的 theory（含 diamond：A；B、C 各导入 A 并加
    不同内容——否则合并走 `pointer_eq` 捷径；D 导入 B、C；D′ 导入 C、B）；bundle、`open_bundle`、`context -`。不依赖
    名字的比较：`length (Typedef.get_info ctxt T)`（record 造的每个类型）；`hd (find_casesT/find_inductT ctxt T)` 与
    `Record.the_info` 的 `#cases`/`#induct` 按 `same_shape`（命题 aconv 且前提数相同），对 `recT` 与 `rec_schemeT`；
    Ctr_Sugar exhaust 的 `nprems_of`；每选择子 `Spec_Rules.retrieve` 头条的 `nprems_of`——以 theory 层孪生 record 的值为
    预期；免检格按 §5.8 的编号逐格写（context、表、`recT`/`rec_schemeT`、预期值）：(2) `context -` 块内的
    `Spec_Rules.retrieve` 为空；(15) 嵌套 `assumes` 层的外层 Spec_Rules 头 `nprems_of` 1、重开块的头条件行在前；(19)
    带 `assumes` 的 unnamed context 里 `global_interpretation` 之后 theory 头 `nprems_of` 1；导入格要写明装置（导入
    theory 无 interpretation 时 stock 头 `nprems` 0）；(3)、(13) 在此无格。
21. 事实别名：21a heavy locale 无 registration——theory 层 `thm p.select_convs`、`thm p.make_def` 报 Unknown fact（孪生
    `datatype` 的 `thm d.sel`）；21b class——`p.select_convs` 与 `c_class.p.select_convs` 可解析（无孪生：`datatype` 在
    class 里失败）；21c interpretation——只有 `I.p.select_convs` 可解析（孪生 `I.d.sel`）；21d light——重开块后短名可用
    （孪生 light 块里的 `datatype`）。
22. `context - begin record p = x :: nat  y :: nat … end`（单独 leaf）：块内 `Typedef.get_info` 长度 1、`ctr_sugar_of`
    条目等于 `ctr_sugar_of_global`、`x ⦇x = a, y = b⦈ = a` by simp、`proof (cases r) case (fields a b)`、`fun g` 用
    record 模式、`Spec_Rules.retrieve` 为空（§5.8 (2)）；`end` 后 Spec_Rules 头等于孪生。stock 对照报 `Bad context for
    command`；孪生：`context -` 里的 `datatype`。判别 leaf（代替做不到的换实现）：`context -` 里 `local_setup
    ‹Local_Theory.background_theory (Record.add_record …)›`，预期 simp、`cases` 失败、`Typedef.get_info` 为空。
23. `local.foo` 打印（§5.8 (14)）：theory 上的 unnamed context 里 `lemma foo: True ..` 然后 record，`Facts.extern` 对
    `foo` 前后（预计 `foo` → `local.foo`）；locale 里不变；class 变体、无限定词 interpretation 变体、本 record 的
    `p.simps` 变体；两个 record 的变体；孪生 `named_theorems`。
24. import 行：复用第 20 行的 diamond，导入含块内 record 的 theory 后 cases、induct、`fun`、simproc、四表、`dest_rules`
    按键的计数，预期"与同样导入的 theory 层孪生相同"、每键 1；父行：导入 theory 里 `"nat l.p"`、导入 theory 自己的
    synonym、`"nat I.p"` 各一；含之后登记的插件（第 25 行）。
25. 测试专用插件（`Plugin_Name.declare_setup` 加 `Ctr_Sugar.ctr_sugar_interpretation`），两份日志：一份 Theory_Data
    记类型名与 naming 前缀（块内立刻可见，local_theory.ML:217-221）、一份经 declaration 写的 Generic_Data 集合（定义块内
    不可见，`end` 后、重开、interpretation 后、导入 theory 里可见——§5.8 (13) 的测试）；两份日志只滤 record 扩展类型名
    （后登记的 interpretation 也会跑遍已有 datatype，plugin.ML:160-169）；预期前缀是定义处的 naming（`Thy.l.p`）、每
    record 跑一次；在 theory 层、`context -`、locale、class、bundle 各跑一次并配 theory 层孪生。
26. 畸形的字段 mixfix：theory 层与块内各一行写不合法的 mixfix（如 binder 形式），报错文案与 stock 的 theory 层相同
    （探针 (c) 在 stock 上定文案；决定 16 (i) 的残余）；块内 `const_lines`（语法表探针）与 theory 层孪生逐条相同。
27. （可选）TAT 的 Record node 以 synonym `q1` 作父走 `add_record_cmd`，得到与命令相同的结果（决定 6；头脑风暴 T7）。

### 7.4 light 块（里程碑 3 的 gate）

`tests/Light/Record_Light.thy`，`imports Light_Locale`。`light_locale LF = fixes S :: "nat set" assumes "finite S"
begin record 'a p = x :: 'a  y :: nat end`——块内第 1 行全部（含事实别名、`Typedef.get_info` 为 1、Ctr_Sugar 条目同
theory 层、Spec_Rules 条目数 1、块内 `p.cases` 等的 `Thm.get_tags` 等于孪生——无 K tag，shared generic_target.ML:472）；
`LF.p.simps` 带 `LF ?S ⟹`、`exported_premises` tag 为 1、`[simp]` 保留；`end` 后 `LF.p.cases` 等带 `consumes "1"` 与
`exported_premises` tag（shared attrib.ML:362-371、rule_cases.ML:216-218）；`Record.get_info` 的定理 `nprems_of` 与
stock 相同、hyps 空；`end` 后 theory 层 simproc（`lemma "LF.x (r⦇LF.x := a⦈) = a" by simp` 与 `lemma "r⦇LF.x := a,
LF.x := b⦈ = r⦇LF.x := b⦈" by simp`）、`value`、`fun`、子 record 成功，`length (Spec_Rules.retrieve_global …)`
对每个选择子为 1 且头 `nprems_of` 0（light 副本与 stock 条目合并，§5.8 (6)）；`Induct.find_casesT` 对 record 类型的头是
无 tag 的无条件规则（`nprems_of` 1）、`cases r` 不链 `LF_axioms` 给出 `fields`、`using LF_axioms proof (cases r)` 成功
且 `LF S` 为未用前提、`rule: LF.p.cases` 链 `LF_axioms` 到 K tag 副本（孪生：light 的 datatype 裸 `cases t` 错位、
`using LF_axioms` 成功）；父行：块内 `"nat p"`、重开块、`interpretation I: LF {1}` 后 `"nat I.p"`、`lemma (in LF)` 里
（`p.simps` Unknown、`LF.p.simps` 可用）；`interpretation I: LF {1}`：`thm I.p.select_convs` 等于 `LF.p.select_convs`、
`term I.x`、`typ "nat I.p"`、`thm I.p.simps` 报 Unknown fact（孪生 light datatype）；重开块（无 solver）：别名、字段
mixfix、simproc（同样两条引理，写 `x`）、`fun` 用 record 模式、`cases r` 经 theory 的无条件规则、`thm p.simps` 报 Unknown fact、`thm LF.p.simps`
可用（孪生：同块 `datatype d` 重开后 `d.simps` Unknown、`LF.d.simps` 可用）；重开块（有 solver，light 里程碑 3 后）：
`LF ?S` 形式的 simps 可 simp；无谓词的 `light_locale LG = fixes S :: "nat set" begin record 'a p = x :: 'a  y :: nat`
处处无条件、`Induct.dest_rules` 条目数 1；嵌套层：`light_locale LN = fixes S :: "nat set" assumes "finite S" begin
context fixes n :: nat assumes "0 < n" begin record pn = z :: nat end … end`，theory 层对 recT、rec_schemeT 与 `nat` 键
的整张 `find_casesT`/`find_inductT` 列表：头无条件、`Exported_Premises.count_of = 0`、`nat` 键干净（孪生 light
datatype）。

### 7.5 性能（复审 D4，作者自决，用户委托 2026-10-15）

探针用 `isabelle ML_process -l HOL -o threads=1`（gcthreads 随之为 1），在主线程直接调被测代码，`Timing` 取 elapsed
与 CPU，至少 3 次取最小，**只 gate elapsed**；多线程下的延迟只作信息（`Goal.prove_sorry` 在 `Future.proofs_enabled 1`
下 fork、record.ML:2146-2150 在 `Par_List` 里跑，否则大半证明工作逃出计时；§11 的 66.7 s 很可能就是这样量的）。
(1) 300 个 `nat` 字段的 `Record.add_record`，codegen 开——theory 层开销（含三个背景步各两次 transfer、每次作用于
level+1 个 context，六个 attribute 的 `map_contexts`）；(1b) theory 层连续 100 个小 record；(2) `Groups.monoid` 里一个
300 字段 record（含向 theory 层 registration 的传播，第 13b 行）；(3) 一个 locale 里连续 100 个小 record；(4) 别名
上界：`Groups.monoid` 里决定 13 的别名清单实际长度（按读源码 631，含内层 `Rep`/`Abs` 则 673），加 `context monoid begin
end` 与一次 `interpretation`，各带与不带别名；(5) 决定 20 的各部分分别计时：两次事实名字空间扫描、`transfer_facts`、
别名 declaration，在 `Groups.monoid` 的 lthy 上，HOL 与 HOL-Analysis 下各一次；(6) 带父的子 record：父写 record 名
（相对 stock 多一次 `get_info` 的 `Symtab` 查找）、父写 synonym（stock 没有基线——它拒绝；多付一次 `cert_typ` 加对
record 表按表的键序的线性扫描，首个匹配即停、失败时扫完，每个被访问的 record 付 `get_parent_info`、`mk_recordT`、
`raw_match`，随 record 数线性增长，预测、只作信息；若可观，先比较 `fst (#extension info)` 与 `last_extT` 再建模式），
加 HOL-Algebra 与 Record_Benchmark 的子 record 各计一次。**gate**：(1)、(1b) 相对基线增幅 ≤ 10%（阈值已批 2026-10-13）；
(2)、(3) 记为相对 theory 层孪生 (1)、(1b) 的比值，不 gate；(4)、(5) 是 §10 "合并别名 declaration"条目的比较基准，10%
为重提触发线；(6) 信息；`Record_Benchmark` 的 "Finished" 行作信息（rev3-C27）。基线连同三份清单文件的**内容** sha256
与 HOL heap 的 `isabelle_sources` digest 写进 `tests/golden/perf_baseline.txt`，在 light 落地后的共享树上、第一次改
`record.ML` 之前由 agent 取。digest 变了**或**增幅超过 10% 时都不自动判定：报两个数字由用户选——接受，或用户构建一份
只差 stock `record.ML` 的副本、在同一时间窗里交替重测（rev4-C28）。AFP 的旧 API 调用者不进 gate。

## 8. 实施步骤

每步以"涉及 session 构建通过且本步 gate 全过"为完成门槛；里程碑 N 即本节第 N 步；里程碑 1 之后任何改了 record.ML、
typedef.ML、ctr_sugar.ML 的里程碑，在其最终代码上重跑全部 §7.2，改了 record.ML 的还重跑 §7.3 与 §7.4。每条探针标
**[树；里程碑；消费者]**：树是 stock（`contrib/light_locale/tools/stock-isabelle` 在 stock 副本上跑）或 shared（共享树，
记 light 的 commit；light 的里程碑写在树字段里）；里程碑字段是本项目的步骤号；消费者是它要定下的计划条目。stock 副本
的行号规则：计划引用的 record.ML 行号都是 stock 副本的（rev3-C40）。

0. **准备**（Isabelle 可用后——由用户通知；Opus agent 用 `isabelle ML_process -l HOL` 跑探针、不构建、不启动 REPL）：
   (a0) [stock; 0; §10 的 `define` 路线条目、决定 3] 决定 3 改版的实证依据（决定 3 辩论的裁判要求、用户 2026-10-13 批，
   rev 4 改写时误删）：在 `locale l = fixes k :: nat` 的嵌套 scope 里 `Local_Theory.define` 一个右边 `x + 1`、对闭合的
   `d` 的常量 `c`，核 `Consts.the_abbreviation` 命中（走的是缩写分支）、`Thy.l.c 3` 的打印坏掉、`interpretation I: l 5`
   之后 `Scratch.I.c` 的形状；theory 层孪生；预期不符即停下报用户。
   (a) [stock; 0; 决定 3 的 rev3-C2] `locale la = fixes k :: nat assumes "0 < k"` 里 `Typedef.add_typedef lthy`，记
   `Rep_inject` 的 `Thm.hyps_of` 与导出后的形状。
   (b) [stock 半：HOL-Algebra、Records.thy、Benchmark 的全部 record 事实与 `get_info` 定理，查 `Goal.norm_result` 是否改变
   `ML_Syntax.print_term (Thm.full_prop_of th)`（预期只有 `fold_congs`/`unfold_congs`）；shared 半：standard、interpretation、
   class 三种 morphism 保持命题 aconv（§5.8 (6) 的 Spec_Rules 实例行合并、§5.6 的 light theory 副本；决定 17 不再消费
   它——不存 declaration 就没有重放的 morphism）；0；§5.1、§5.8 (6)]。
   (c) [stock; 0; 决定 16 (i)、第 26 行] 跑 `probes/mixfix_probe.ML`（改为收 `out_dir` 参数、注明树），`r2_two_phase =
   r1`；对照预期：`r1_again`、`r1_nopos`、`r2_interleaved` 都等于 `r1`，`r2_batched` 可以不同（批量 `notation` 的次序），
   binder 形式在各条路线都失败；再记畸形字段 mixfix 在 stock theory 层的报错文案。
   (d) [stock; 0; 决定 17] 决定 17 复现：theory 层 `record p = x :: nat` 后 `declare p.cases [cases del] p.cases_scheme
   [cases del] p.induct [induct del] p.induct_scheme [induct del]`，核 `find_casesT` 只剩 `Abs_p_ext_cases`、`apply (cases
   r)` 的 Abs 目标、`Undefined case: "fields"`；再删 typedef 的两条，核响亮失败；子 record 残余（`par`/`ch`）；`datatype`
   孪生在 `locale m = fixes k :: nat assumes "0 < k"` 里 `end` 后 `cases t` 的失败文案。
   (e) [stock；shared 在里程碑 1 开始时重跑（决定 21 的应急）、light 窄变体那一步之后再跑一次作验收；0/1；决定 21、
   §5.3、第 7b/7c/7d 行] `context fixes n :: nat
   assumes "0 < n" begin typedef t = "UNIV :: nat set" by simp end` 后 `find_casesT nat` 的头（是否 `Nat.nat_exhaust`、
   与 `nat.exhaust` 是否 `eq_thm_prop`）与 `proof (cases m)` 的选择；同一块里 `datatype (plugins del: code)` 能否通过
   （预计通过、`nat` 下多一条条件副本）；`locale l = fixes k :: nat begin context assumes "1 < k" begin typedef … end
   end` 预期 THM。
   (f) [stock; 0; 决定 15] `locale m = fixes k :: nat assumes "0 < k" begin datatype d = D nat end` 后 theory 层 `fun g
   where g (D n) = n`，与 theory 上 `context fixes n assumes "0 < n" begin datatype d2 = D2 nat end`（第二变体用 `plugins
   del: code`）——只断言"失败"（Bind 或完备性失败）。
   (g) [stock; 0; 决定 15、第 1 行] `datatype 'a dt = DC 'a` 与 `record 'a rc = fld :: 'a` 的 `ctr_sugar_of` 条目 `T` 的
   形式（TFree）。
   (h) [stock; 0; 决定 9] `locale l0 begin definition f :: "'a ⇒ 'a" where "f x = x" datatype 'a t = C 'a end` 成功。
   (i) [stock; 0; §5.5、决定 20] `class c = fixes cc :: 'a begin lemma foo [cases type: nat]: … lemma bar [simp]: …
   local_setup ‹一条事实别名 declaration› end` 后 theory 层 `find_casesT nat` 的头（预期 `foo` 经自我 registration 的
   实例副本；locale 孪生里 theory 层仍是 `nat.exhaust`）、`dest_simps`、别名是否可达。
   (j) [stock; 0; 决定 17] 前半：theory 上 `context fixes m begin context fixes n :: nat assumes "0 < n" begin typedef …
   （或 lemma foo [cases type: T, induct type: T]）end` 核外层只有条件副本（不用 datatype：code 插件的 declaration 先在
   `dest_equals` 崩）；后半（rev7-C2 之后）：locale 里用 `local_setup` 模拟"3E 写 theory 加一次 `map_contexts`"，核
   当前层与外层立刻有规则、重开、interpretation、class 变体、`global_interpretation` 变体后规则来自 theory 且是头。
   (k) [stock 加 `-d $AFP`；0；决定 15] 载 Constructor_Funs、Lazy_Case，`locale l`、`locale la … assumes` 里的 datatype，
   再 `context l begin end`、`interpretation I: l 5`、class 块、已有 interpretation 的 locale——预期 DUP（待确认）、带
   assumes 时 unfold 规则 theory 副本 `nprems_of` 1。
   (l) [stock; 0; 第 6 行] `fun` 对子 record 模式（`record par`、`record ch = par + b`、`fun g :: "ch ⇒ nat"`）。
   (m) [stock; 0; 第 4b/9b/7g 行] `datatype` 孪生在 class 内与已有 interpretation 的 locale 内的嵌套 `fixes n :: nat
   assumes "0 < n"` 块：普通 `datatype` 预计崩在 code 插件的 `dest_equals`（declaration 施到已有 registration，
   ctr_sugar.ML:1126-1131、locale.ML:666-689），`datatype (plugins del: code)` 预计通过、条件副本归 `nat`（决定 21 (i)）；
   封闭变体（`context assumes "cc = cc"`）预计 THM。
   (n) [stock; 0; 第 7j 行] theory 上 `context assumes "finite (UNIV :: bool set)"` 里的 datatype（预计 THM：BNF typedef
   的 `Abs_cases` attribute 先触发）。
   (o) [stock; 0; §5.8 (14)、第 23 行] `context begin lemma foo: True .. named_theorems bar end` 前后 `Facts.extern` 对
   `local.foo`（预计 `foo` → `local.foo`），locale 里不变；class 变体、无限定词 interpretation 变体。
   (p) [stock; 0; 决定 4] tag 顺序：theory 层 record 的 info 规则（预计 `[name, consumes, case_names]`）与 Induct 表头
   （预计 `[consumes, case_names, name]`），不排序打印。
   (q) [shared，light 窄变体那一步之后；实际跑在里程碑 1 或 2——它只是 7c-7j 孪生列的前置，不挡 record 自己的行；决定 21
   (iii) 的 typedef/datatype 孪生] 给定理打 `exported_premises 1`，
   `Thm.instantiate_frees` 非空实例化后 tag 是否还在（light 2026-10-18 已答：经登记/激活 morphism 以 K + d 存活，待实测）。
   (r) [stock; 0; §7.5] 300 字段 `Record.add_record` 在 `threads=1` 与默认线程（`threads=0`，记 `Multithreading.max_threads
   ()`）下的 elapsed 之差；`transfer_facts`、两次事实名字空间扫描、别名 declaration 在 HOL 与 HOL-Analysis 下各自计时。
   (s) [stock; 0; §5.7、第 18 行] `bundle b begin … end` 里用 `local_setup` 跑 `background_theory_result` 加 `map_contexts`、
   `transfer_facts`、`Typedecl.abbrev`、`const_alias`/`type_alias`/`notation`、`Local_Theory.notes [simp]`、
   `Spec_Rules.add`，核不报错、`end` 后命名事实 Unknown、`unbundle` 后 attribute 与别名生效；`datatype`、`typedef` 孪生。
   (t) [stock; 0; §5.8 (19)、第 4b 行的 G 格] 在 stock 上用 `local_setup`（`Spec_Rules.add` 加一条忽略 morphism 的
   declaration）模拟：带 assumes 的 heavy locale，然后在 theory 上 `context fixes c assumes …` 里 `global_interpretation`，
   记 record 类型与 `c` 类型下 `find_casesT` 的头（预期：record 类型下是无条件的原始规则；`c` 类型下按 `eq_thm_prop`
   不变）、每选择子 Spec_Rules 的头（预计条件）。
   (u) [—; 0; 决定 1] 建 repo 骨架，`tools/signature_additions.txt`（改动文件清单与 patch 生成随迁移方案 §5，待其批准）；
   用户在 stock 副本上构建 `Localized_Record_Golden` 录 §7.1 golden 与 METADATA（消息行待捕获通道落地后补录，见第 1
   步）；核 session 接受 `ML_file` 指向 `contrib/light_locale/tests/Golden/golden.ML`；核 `isabelle build_log -v -T` 是否
   列出 tracing 消息（若是，消息 golden 不需 light 改捕获）。
   (v) [stock; 0; 第 17 行] theory 层 record 模式的 `code_pred`（精确文案；`inductive Pr :: "p ⇒ bool" where "Pr ⦇x = 0,
   y = 0⦈"` 后 `code_pred Pr .`）。
   (w) [stock; 0; 第 7i 行] `context fixes n begin context assumes "0 < n"` 里的 typedef（预计 THM）。
   (x) [stock，可选；0；§5.8 (11)、第 5 行] assumes 块里的 `copy_bnf … via` 与 `nitpick`；theory 层 `copy_bnf`/`nitpick`
   孪生、普通 locale 里的 `via` 形式、`Sorts.has_instance` 对 typerep 作对照。
   (y) [stock 对照 + shared golden 行；0/1；rev6-C1、§7.1 消息行] 开捕获、`threads = 1`，`declare [[simp_trace]]` 后
   theory 层 `record p = x :: nat  y :: nat`；stock 上用 `local_setup` 跑两次 `map_contexts`（守卫在函数体内 / 只包在
   lthy 外）数 "Adding rewrite rule" 行作正对照：前者不多打，后者每条 simps 规则多一行 `[0]`、`ext_inject` 多一行；
   真正的变异检查是 §7.1 说的代码变体构建。
   (z) [stock; 0; rev6-C16、决定 3/17] 构造函数核：`locale l = fixes k :: nat begin` 里 `local_setup` 用 `Local_Theory.notes`
   登记一条 cases 规则，attribute 为 `[Attrib.internal ⌂ (K (Rule_Cases.case_names ["fields"])), Attrib.internal ⌂ (K
   (Thm.rule_attribute [] (K (Rule_Cases.default_consumes 0))))]`，预期 "Mixed dynamic attribute followed by static rule"；
   换 `Thm.mixed_attribute (apsnd (Rule_Cases.default_consumes 0))` 预期成功且 `Thm.get_tags` 与 stock 列表版相同，在
   块内副本、嵌套 assumes 后的外层副本、theory 上 `context fixes n :: nat assumes "0 < n"` 里的 theory 副本
   （`theory_target_notes` 保留 attribute；heavy locale 的 theory 副本被剥掉 attribute，不能用）、interpretation 副本、
   `unbundle` 副本上各核一次；[shared; 3; §7.4] light 的 theory 副本 `consumes "1"`、块内副本 `consumes "0"`。
   (aa) [stock; 0; 决定 17、第 6d 行的负对照] 在 stock 上复现 rev7-C2 的机制：theory 层 `record par = x :: nat`；一个
   locale 的 `declaration` 忽略 morphism、重施 `Induct.cases_type` 于 `par.cases_scheme`；`record ch = par + y :: nat`；
   `interpretation I: l 5`；预期 `hd (Induct.find_casesT @{context} @{typ ch})` 是 `par.cases_scheme`、`proof (cases r)`
   对 `r :: ch` 给 `fields a more`。
   (ab) [stock; 0; §5.1、第 16 行] theory 层 `private record p = x :: nat` 与 `qualified record …` 的 stock 外层语法
   报错原文（预计 `Parse.!!!` 在 `private` 处失败，outer_syntax.ML:239-241）。
   **决定 22 的探针**（P1-P7 [stock; 0]；P8 [stock 与 shared; 0/1]；P9-P11 [shared; 4]；P1-P8 用 §7.1 的 theory 层
   fixture `Parent_Forms_Fixture`，P9-P11 用里程碑 4 的 fixture；消费者 §3.7、§5.1、第 6b/6c/6e 行、
   `Localized_Record_Theory_Test`）：
   P1 `type_synonym q1 = "nat p"` 后 `Type.lookup_type (Proof_Context.tsig_of @{context}) "T.q1"` 是 `Abbreviation ([],
   (nat, unit) T.p.p_ext, false)`——缩写存展开形式；P2 `record ('a,'b) ph = w :: 'b` 被接受，`record d = "(nat, bool) ph" +
   y :: nat` 的 `Record.get_parent` 是 `SOME ([nat, bool], "T.ph")`，`record 'c d2 = "('c::order, nat) ph" + y :: 'c` 的 `'c`
   带 sort order；P3 记录 §7.1 全部拒绝行的精确文案（含引号里的全名 `"fun"`、`"logic"`、`"T.p.p_ext"` 与 `"logic q9"`
   的三行）；P4 `read_typ_abbrev` 对 `q1`、`⦇x :: nat⦈`、`(nat, unit) p_scheme`、`logic`、`"logic q9"` 的返回值（预期
   `Type ("T.q1", [])`、`Type ("T.p.p_ext", [nat, unit])`、`Type ("T.p_scheme", [nat, unit])`、`Type ("logic", [])`、
   `Type ("T.q9", [Type ("logic", [])])`），`Proof_Context.cert_typ` 对 `"logic q9"`、`qsyn` 抛错；P5 `type_synonym bad = "t s"`、`'x q8 = "'x s"` 被接受（不查
   sort），`qsyn = "letbinds p"` 接受且 `syntactic = true`；P6 用导出的 `Record.get_info`/`get_hierarchy` 在 ML 块里原型
   `record_of_type`，对 forms table 的每个 theory 层行比对预测；P7 `print_record q1` 可用（:2417-2421 默认模式读——record
   已按展开类型识别自己的先例）；P8 决定 7 的先例：`term "⦇T.x = 1, bogus = 2⦈"` 两树文案；P9 locale、class、instantiation、
   light 块里 `read_typ_abbrev` 对 `lp` 给 `Type ("local.lp", [])`，`cert_typ` 展开为 `('a, unit) T.l.lp.lp_ext`，`'a` 存的
   sort 等于块里读到的 sort；P10 两半：闭合半用 fixture 自己的 `interpretation I: l "id :: nat ⇒ nat"`，`T.I.lp` 存在
   （右边 `(nat, unit) T.l.lp.lp_ext`）；开放半在导入 fixture 的叶里 `interpretation K: l id`，不造 `K.lp`、`K.lp` 报
   `Undefined type name: "K.lp"`；P11 三半：(1) theory naming 半是**通过条件**——theory 上 `context fixes x :: 'a begin
   record r = y :: 'a  record d = r + z :: nat end` 里 `Proof_Context.read_typ_abbrev ctxt "r"` 为 `Type ("local.r", [])`、
   `d` 的父等于孪生 `"'a T.r"`、`end` 后 `"nat r"` 读为 `T.r`；`instantiation list :: (type) c begin` 里同（两者各占
   一个 theory，与第 6e 行的叶分开——6e 的无限定词 interpretation 会造出 `lp`，这里会造出 `r`/`d`）；决定 19 写入顺序的
   变异放在这两个叶：交换两条缩写的写入顺序，unnamed context 叶里 `definition f :: "r ⇒ nat"` 预期报 `Bad number of
   arguments for type constructor: "<thy>.r"`，instantiation 叶同（`"<thy>.<record 名>"`）；(2) 重开半只记录——`lp` 已
   在 `l` 里定义，之后无限定词 `interpretation l "λx::nat. x"`，再重开 `context l begin`，`lp` 读成 `local.lp`（源码
   预测：重放的局部副本赢，提供方决定 5"相反的顺序不遮蔽"）还是 `T.lp`——若全局赢，报用户与提供方（§5.8 (22) (a)）；
   (3) 先解释后定义半只记录、预期值等用户裁——无限定词 interpretation 在先，`context l begin record lp2 = g :: "'a ⇒ 'a"
   record d2 = lp2 + y :: nat end`，记第二条命令里 `lp2` 读成什么、`d2` 的父是什么（源码预测 `T.lp2`、`([nat], T.l.lp2)`、
   无隐藏 `'a`，§5.8 (22) (b)）。
   **刻意不跑的裁判探针**：`unused_thms`（record 的事实 kind 为 `""`，它只看 `theorem`）；`Thm.derivation_name` 对代码证书
   定理的列（恒为空）；对 record 行为的 light 孪生（light 里程碑 3 的读者会遮住合并方向，第 15 行已说明）；
   `Ctr_Sugar.dest_ctr` 对 `⦇fld = 1⦈`、`text ‹@{datatype rc_ext}›`、`time_fun` 对 record 构造子（只服务于 §10 被否的
   TVar 形式退路）。
1. **移植**（§3 全部）。**前置条件**：用户 2026-10-18："建议把所有问题都敲定后再开工，而且我们必须等 light locale 全部
   完成后再开工"——头部"待用户"列表全部定下；light 三个里程碑完成并提交；补丁系统迁移落地、本项目的分支建在
   `local_type_abbrev` 之上（§0 第 5 条），且 local_type_abbrev 带 `Typedecl.fixed_names` 导出的修订已 merge 进来
   （决定 9）；用户在共享树上跑 §7.1
   的对照比较（CONTROL 记清单文件内容 digest 加 HOL heap 的 `isabelle_sources` digest；任何差异停下报用户——共享树不能
   重录；之后的 golden 失配按 CONTROL 归因：digest 未变的失配归本项目，变了的先与 light 联合分辨，rev4-C27）并由 agent
   取 §7.5 基线；消息捕获通道落地后补录 §7.1 消息行（record_timing 关、开、`declare [[simp_trace]]` 三行）；决定 21 的
   窄变体只是 typedef/datatype 孪生行（7c-7j 的孪生列）的前置，record 自己的行不等它（rev6-C16）；探针 (q) 随之同属
   孪生前置；里程碑 1 开始时在共享树重跑探针 (e)，缺则报用户（决定 21 的应急）；碰共享树前通知 light。`record.ML`
   是一个编译单元，§3 的顺序是写作顺序不是检查顺序。改动只有重建 HOL heap 才生效：`ML_process` 从不构建、只查已有
   heap（ml_process.scala:170-176）；Isa-REPL 启动会重建**共享的** HOL heap（repl_tool.scala:103-112），编不过的
   `record.ML` 会让树上所有 agent 失去 HOL——agent 重启 REPL 前逐次请示（§0 第 6 条）。开发循环：改 → 用户跑 `-b HOL`
   → agent 用 `ML_process` 跑最小 theory 对 golden 与 §7.3 的行。先过最小 theory，再上 HOL-Algebra 与全部 session
   （§7.2）。rev6-C1 的变异检查在本步消息行通过之后：用户用守卫放在 lthy 外的代码变体多构建一次 HOL，消息行必须变红，
   然后改回（§7.1）。决定 22 的解析器在本步（theory 层的 synonym 立刻可用；`Localized_Record_Theory_Test` 是本步 gate
   的一部分，stock 上的变异跑由用户用 `stock-isabelle` 构建）；决定 11 的 `typedef_overloaded` 读取也在本步。补丁落地后
   把最终导出的名字与签名发 TAT record 会话（决定 6）。
2. **块内行为**：§7.3 的 leaf theory（第 7c-7j 行的孪生列以窄变体落地为前置）；§5.5 第 9 行、§5.8 的 E 项实测写回。
3. **light 块与补丁**：§7.4；本项目的发布 tag 与 `patches/Isabelle2025-2/` 下的 patch 文件按迁移方案 §5 生成（基发布
   tag 与本项目发布 tag 之间的 diff，按文件拆开；往返一致由构造保证；细节待迁移方案批准后写入）；签名检查按
   `signature_additions.txt`；light 里程碑 3 的 hunk 定形后两边重核 typedef.ML、ctr_sugar.ML。
4. **块固定的类型变量**（决定 19，含决定 22 的块内形式）：前置：`contrib/local_type_abbrev` 里程碑 1-3 提交并经分支链
   merge 进本项目的分支（§0 第 5 条）；它承诺三文件补丁出来时通知本项目。
   删 `err_fixed_params`；`err_extra_frees` 对隐藏参数放行（隐藏参数按 record 类型算：字段类型加解析出的父的实例化扩展
   类型，只落在父的无字段使用参数位置的块固定变量仍报 `Extra free type variable(s)`）；参数顺序与 sort（决定 19 (b)：
   声明参数在前、隐藏参数按块里的名字在后、`'z` 最后；隐藏参数带块里的 sort）；只给用户声明为 record 参数的块固定变量
   换新鲜名（字段类型与父参数里一次代换），隐藏参数保持块里的名字与 sort（决定 19 (a)，用户 2026-10-18）；背景的
   全局缩写与 `make_info` 的参数表出自同一份参数列表；target 步 1 有隐藏参数时先在背景加全局 `Sign.add_type_abbrev`
   再 `Typedecl.abbrev` 分流到局部缩写（顺序不能反；只在 theory naming 的 target 里有后果，决定 19）；§6 决定 9 的文案
   退役；§7.3 第 9、10 行的负行改正行、第 6e 行全部（用 §7.1 的里程碑 4 fixture）；核局部条目全名 `local.lp` 与闭合像
   `I.lp` 的可用性（开放 interpretation `K: l id` 不造 `K.lp`，写实例类型或 `"'b l.lp"`）；第 6e 行里"无限定词
   interpretation 在先"的记录行，预期值等用户裁（§5.8 (22)）。`contrib/local_datatype` 落地后决定 2(b) 的第三条有利
   偏离改为已消失。

## 9. 分发

本期不做，另立计划。方向按迁移方案（`ai-artifacts/ISABELLE_GIT_MIGRATION_PLAN.md`，待批）：发布 tag 之间生成的
`patches/Isabelle2025-2/` 补丁文件是分发单位，conda 包在 post-link 应用、pre-unlink 撤销；本项目的包依赖链上前一个包
（`contrib/local_type_abbrev` 的包，它又依赖 light locale 的包）；`contrib/local_datatype` 的包依赖本项目的包。

## 10. 已否决的提议（不再重提）

- **最小补丁路线**（作者 2026-10-11 提议，用户同日否决："我认为需要走正经移植，要走最正确最优雅的哪怕是困难的路"）：
  把 `record` 注册成 `Toplevel.local_theory`，块里把 stock 的 `add_record_cmd` 包进 `Local_Theory.raw_theory`（名字
  不带 locale 限定），再用 `Local_Theory.map_contexts` 把 simps/iffs/cases 自动重施到打开的各层；连带的论点"locale
  限定词对 record 在语义上没有用处"也未被采纳（决定 2(b)，用户 2026-10-13 确认名字跟着 target）。
- **把整个 `Record.add_record` 包进 `Local_Theory.background_theory`、不加别名**（2026-10-11 探针）：record 语法当场坏。
- **把 `record.ML` 加进 light locale 补丁集**（用户 2026-10-12 否决）。
- **改旧 ML API 的名字或类型**（用户 2026-10-12 否决）。
- **`split_args` 认点号的后缀测试**（用户 2026-10-12 否决）。
- **代码生成在 `class` 块里加守卫、或人为让 record 在 class/bundle 块里像 datatype 一样失败**（用户 2026-10-11 否决
  守卫；决定 2 不加任何 target 专用失败）。
- **常量经 `Local_Theory.define`**（rev 1；辩论 `wf_e5c880df-0b6`，用户 2026-10-13 批其 12 条改动）：导出后
  `const_decl` 走 abbreviation 分支，record 打印全坏；λ 右边则改五条公理。第一个理由只按源码核过，实证是 §8 探针
  (a0)。连带否决：每常量一个 nested scope 的 `define` 写法；`define` 给封闭常量、背景路线给五个应用形式常量的混合
  （仍要整套背景机器、一个 record 两种 foundation、保留 `const_decl` 依赖与 nested scope、记号本来就由 `notation`
  放置，一无所得）。性能不是否决 `define` 的理由（§11 2026-10-12 的数字）。
- **用 `Local_Theory.declaration` 安装打印翻译**（作者 2026-10-12，决定 8）：declaration 只在作用到 theory 时有效，
  块内不多给任何东西，还往 locale 里存一个无用的 proof 侧空操作。
- **字段 mixfix 一律经 `notation`、theory 层也不传 `field_syntax`**（作者 2026-10-13 的选项 (b)，用户先批后换
  "4. 好"选 (a)）：theory 层字节会变（`notation` 的产生式顺序与 stock 声明时不同）。**为 `setup`/ML API 调用者预校验
  mixfix**（rev3-C44）：stock 不做，做了就是新行为。
- **在块的 lthy 里建逻辑内容**（rev 2/3；评审 `wf_c4edfeb3-0ed` 四条 blocker）：见决定 3。**record 的 typedef 经 target
  （BNF 式 `begin_nested`）**（2026-10-14/15 两次重审）：决定 2(a) 只能靠 golden；`assumes` 下 typedef 的 info 与事实变条件、
  Iso_Tuple 证明吃到带 hyps 的定理；子 record 的决定 17 情形不修；约 80-120 行。
- **六条事实带名字在每个 target 全局登记并用别名**（"放宽决定 2(b)"，评审报告称 R2 relaxation；用户 2026-10-14
  否决）：locale 里 record 的 simp/iff 规则 `end` 后全 theory 生效且不能在 locale 内 `declare [simp del]`、theory 事实
  无条件、interpretation 得别名。
- **早改名或读回法填 `info`**（2026-10-14 头脑风暴 `wf_79f85875-b05`）：早改名改变全局 simpset 里对象的 derivation，
  破坏决定 2(a)；读回法靠未验证的等价断言。同一次头脑风暴的其余被否设计：延迟列表编码（把 attribute 列表延后到块外
  施加——块内就没有 `[simp]`）；用 `Thm.map_tags` 整份拷贝 tag（拷进不该有的 tag）；块内 info 不打 tag（用户 2026-10-14
  的决定 2 选项 (ii)，用户"全部按你的建议来"选了打 tag）；从 `Local_Theory.notes` 的返回值取 info（返回的是经 morphism
  的块内副本，TFree 变 TVar）；stock 全局登记加同名的 target notes（`Duplicate fact declaration`）；stock 全局登记加
  无名 notes 或非 pervasive declaration（`Ignoring duplicate rewrite rule` 警告）；读已登记的事实来选 info（依赖名字空间
  状态）；在一次性 context 或 theory 里求值 attribute（对象不在正式 theory 里）。`context -` 缺口（§5.8 (2)）的被否修法：
  命令结束时退出 theory target 再重新 init（丢掉块的 includes 与状态）；拒绝在 `context -` 里用 record（分不出来）——
  用户 2026-10-14 接受缺口为已知限制。
- **`Thm.name_derivation` 改名原始证明结果**（rev 4 决定 18）：造未登记的新节点，thm_deps 改变。
- **按"intern 当时能否解析"决定加不加别名**（辩论裁定）：随行为变的条件。
- **用 `Attrib.case_names` 源形式**：多加 `cases_hyp_names` tag。
- **Spec_Rules 的 stock 条目写在 target 副本之前**（辩论 Q4 的一半；另一半——Induct 的写入顺序——随 rev6-C16 与
  rev7-C2 失去对象）：class 自我 registration、已有 interpretation、theory 上 `assumes` 块、`instantiation` 内嵌套
  `assumes`、light 的 K 副本会把条件副本压在 stock 条目之上；所以 stock 条目后写（决定 15）。
- **存下并重放的 declaration 写 Induct**（决定 17 的 rev 5-7 形状；D6 第 1 条用户 2026-10-15 批，2026-10-17 随 rev7-C2
  否决）：rev6-C16 之后重放不再增加覆盖，而每次重放把父 record 的 `cases_scheme` 顶到 theory 层子 record 自己的规则
  之上，`cases r` 静默选错；同时带来 theory 层 `[cases del]` 被加回、用户自己的规则被压下两处差别。D6 原文设想的
  `pervasive = true`、取代 3E 的写、只剩一个写者的变体（作者 2026-10-15 提案文字）rev 6 起就没有采用（3E 的 theory 写是
  `Thm.theory_attributes` 自带的，bundle 的 declaration 从不写 theory，bundle.ML:258-262），rev 8 一并作废。现行做法
  （3E 之后一次 `map_contexts`）正是放置原则头脑风暴（`wf_50483b4f-eab`）设计 3 中"把原始规则 `map_contexts` 进每一
  层"的那一半——2026-10-15 的 §10 曾以"重开时 locale 的条件 note 又成最新"为由否决它，该理由随 rev6-C16 消失。
- **块内四条 cases/induct 的 tag-only attribute 用 `Thm.rule_attribute`**（rev6-C16 核实）：排在 `case_names` 之后被
  `Attrib.partial_evaluation` 拒绝（"Mixed dynamic attribute followed by static rule"）；挪到前面则 tag 被烘进存下的定理、
  导出与实例化的副本丢 tag。用 `Thm.mixed_attribute (apsnd (Rule_Cases.default_consumes 0))`。
- **保持决定 15 的"Ctr_Sugar 经 target"**（辩论 Q5 的选项 c）：theory 上 `assumes` 块永不可修、子 record、diamond import。
- **用 `register_ctr_sugar_raw` 覆盖 Ctr_Sugar 的 theory 条目**（放置原则头脑风暴的 5(a)；"背景步 4"是那次头脑风暴
  的旧编号，对应现在的 3E 之后）：保证只因最后一次写、嵌套 `assumes` 的 declaration 重放时覆盖回去。
- **schematic（TVar）形式的 Ctr_Sugar 条目**（rev3-C7）：`dest_ctr` 会把每个 record 都认成构造子、`split_asm` 暴露；
  本计划的条目是 TFree 形式（决定 15；核实 `reviews/2026-10-15-ctr-sugar-tvar-form.md`）。
- **`bottom_locale_of` 白名单与全名比较的测试**（rev3-C11）：按全名判断"在哪个 locale"会在嵌套与导入时有害地失败。
- **theory 数据里可替换的 morphism 钩子**（rev 1 决定 10 的可选项；rev3-C36）：rev 3 的裁判否决了这个形状，三条理由：
  theory 数据里一个函数值的槽没有合理的 merge（Pure 存函数的先例是带 stamp 的列表，`Foundation_Interpretations`，
  generic_target.ML:169-177）；它许诺的够不着——`sel_upd` 的 simpset/defset 是 simpset 不是定理表、`Iso_Tuple_Thms`
  由 `iso_tuple_intros_tac` 直接读；与 light 决定 20(a) 对 Typedef/Ctr_Sugar/BNF 就地打读者补丁的做法相悖，又是一个
  树内无人使用的扩展点、有损 §0 第 3 条的上游目的。作者当时承认形状错；决定 3 改为背景构造后数据本就无条件，钩子
  失去对象。用户 2026-10-13 的"先记下来然后搁置"引的是同一条消息里工具层那一段（`check_stock_diff.sh`，决定 10），
  钩子那一段作者标"可选、留到里程碑 3 再定"，用户没有单独表态；light 施工完成后若有需要可重提，不是永久否决。
- **把 record 的语义、已知差异、测试条目写进 light 的计划**（rev 1 决定 10 的同步清单；用户 2026-10-13 撤回：record
  不需要 light 改代码就不要求 light 改计划，新增测试是本项目自己的事）。
- **record 侧的回折打印**（rev6-C3 的裁判与作者建议：在 record 自己的打印翻译里对局部条目回折；用户 2026-10-15
  否决，改进若做归 local_type_abbrev 在类型层统一做）。
- **rev 3/4 评审里被弃的测试与指标提案**（rev3 C29、C33、C42 (a)(d)、C17 (c)；rev4 C27 (b)(c)、C5；rev3-C24 的两个
  子项——直接 dump `Iso_Tuple_Thms` 私有表、按 AFP 插件名列 golden；rev3-C27 的三个子项——stock 副本上的性能基线、三次
  构建取最小、locale/theory 比值作 gate 行；rev4-C28 的"占总构建时间比例"gate）：各因重复、不可测或被 rev5-C35/D4 的
  做法取代而弃；这几条意见的其余部分已采纳——§7.1 的 Sign-path golden 与后代 session 的构建由 rev5-C35 与 D4 重新纳入，
  私有表经读取函数与行为覆盖，比值回到 §7.5 作不 gate 的 (2)、(3) 项。
- **Ctr_Sugar 插件在块的 lthy 上跑（`interpret_ctr_sugar`）**（rev 5；rev5-C6）：Constructor_Funs 的 `update_new`
  declaration 重放时预计抛 DUP，class 块里命令自身崩；HOL 无插件、无测试可触。
- **给 Pure 的 spec_rules.ML 加 Context.generic 写入口或整表 transfer**：Item_Net 并集会把块内定义的导出规格带进
  context 成为最新；只写 theory 则块内读者丢条目。**用自定 operations 的一次性 `Local_Theory.init` 只写一个 context 的
  Spec_Rules**：依赖 Local_Theory 内部。
- **导出原始的 `Typedef.put_info`**（而非 `transfer_info`）：record.ML 要自己算 `p_ext`、`p_inner<i>` 的名字、靠键是新的
  避免 `cons_list` 重复；设计 3 的另一半——带守卫的 `ext_def` 遍历——同样会把用户字段类型里的构造子一起收进来。**declaration 式
  写 typedef info**：locale 里同时写带条件的 theory 副本，覆盖 stock 条目。让 typedef info 在块内可见的其他被否路线
  （`reviews/2026-10-14-reexam-sec5_2c.md`）：`Typedef.interpretation`（在每个 typedef 自己的新 target 里跑、对所有
  typedef 生效）；`transform_info`（纯函数，不写 context）；重跑 `add_typedef`（类型声明两次）；`Context.>>`（作用在
  ML 编译期 context）；重新初始化块（target 专用、嵌套层与 theory 上的 unnamed context 做不到）；拷贝私有槽（私有）。由 light 的 typedef.ML
  补丁带 `transfer_info`（record.ML 会依赖 light 补丁、违 §0 第 3 条，且要等 light 里程碑 3）与把 typedef.ML:69 的
  merge 提升（hunk 落进 light :72-74 的上下文，`patch -F0` 往返失败）——用户 2026-10-15"建议 record 自有 / 赞同"。
  块内可见 typedef info 的唯一入口因此是 typedef.ML 的 `transfer_info`（§0 第 4 条、§3.10）。
- **Pure 层整体刷新打开 context 的 Generic_Data**：撤销块内 `[simp del]`、把 light 的条件副本带进块、让 typedef 的 Abs
  规则压过 record 的；改变所有包的 `background_theory` 语义。**让 `Named_Target.theory_map_result` 的声明传给外层 lthy**：
  named_target.ML 的有状态侧通道，只修 typedef info。**改 Induct 的归档键**：决定 17 不是归档问题；record 以缩写名登记；
  induct.ML 归 light。
- **用 `Facts.dest_static` 扫新事实**：`fold_static` 强制并整合整张表里每条未完成的 lazy 事实、跳过动态事实
  （facts.ML:222-239；concealed 在 `verbose = true` 下其实保留，不是理由）；**把 `transfer_facts` 放进
  `background_step`**：theory 层每个 record 三次整表合并、且需第三处 `theory_level`；**把 `local.foo` 的打印改掉**：
  要换别名机制，重开 D6 第 2 条（§5.8 (14)）。
- **决定 22 的被否方案**（头脑风暴 `wf_0caab246-07c`）：用默认模式**重读**父类型（丢"无字段使用的参数"的实参、报错改名
  展开后的头、`logic` 过早失败、丢 `declare_typ` 的 sort）；**顺着缩写名逐层追**（Pure 存的右边已展开，第一步就落到扩展
  类型）；**解析放进共享内部 `local_add_record`**（改旧 typed API 语义、破坏 Optics 的 `alphabet`）；**不先判头是否 record
  名、一律匹配**（决定 2(a) 变成要靠三个条件的证明）；**用 `mode_syntax` 证书化**（会新接受 `"logic q9"`、改 `qsyn` 的文案）；
  **`Sign.typ_match`**（ill-sorted 的 synonym 得到误导的 Unknown、sort 检查跑两遍）；**用 record 自己的类型缩写当匹配
  模式**（多一层对缩写表的依赖；从 record 表现算的 `mk_recordT` 与建子 record 用的是同一函数，按构造一致）；
  **`gen_local_add_record prep_parent` 的放置**
  （多一个入口、理由——schematic 守卫——不成立）；**失败后用原写法重跑整条命令以保文案**（整条命令包 ERROR、双倍工作、
  重复警告、错误诊断——决定 22 用户决定 2 (b)）；**typ 版 typed API**（重复 `add_record`、表达不了无字段使用的参数）；
  **缩写名→record 的 record 侧表**（target 相关、改数据段、漏掉后来的 interpretation 与 synonym）；**请 Pure 或
  local_type_abbrev 存未展开右边**（record.ML 之外、无强理由、用户 synonym 本来就展开）；**现在导出 `resolve_parent`**
  （要批名字、无人需要；用户 2026-10-17："我们不管"）；**再加一条"头必须是类型缩写"的判断**来挡住 `p_ext`、`⦇x ::
  nat⦈` 作父（挡不住 `p_scheme`，除非再靠 `_scheme` 命名惯例；用户 2026-10-17 接受一条规则、无例外）；**给无字段
  使用的参数补值以支持 `qph` 作父**（填 `unit` 是对父信息说谎、填新鲜类型变量平添参数；用户 2026-10-17 曾说"能支持
  也是很好的"，作者裁定不支持，用户 2026-10-18 确认）。
- **重命名的开发副本包**（rev3-C25）：分叉的命令与语法，核不了 theory 层同一性。

**延后（不是否决）**：合并成一条的别名 declaration——§7.5 第 (4)、(5) 项显示差距 ≥ 10% 时再议。

**退路（不是否决）**：(i) 决定 20 的别名集合按 stock binding 手写清单、全名读返回对象的 name hint；(ii) 删 typedef 的
`Abs_*_cases`/`induct` 登记以修决定 17（辩论 Q3 的选项 B）——若用户撤回决定 17 才用，且裁判给了两个条件：经
`Typedef.get_info_global` 的 `#Abs_cases`/`#Abs_induct` 找规则而不按登记名找，找不到（NONE）时响亮报错而不是静默
跳过；它的缺点：响亮失败仍是缺陷、碰不到子 record、theory 上带 `assumes` 的 unnamed context 里 `induct r` 永远错配、
靠 typedef 命名惯例。

## 11. 证据与历史

日期约定：全文用用户的本地日期（UTC+8）；转录里的时间戳是 UTC，本地 08:00 之前的 UTC 时间属前一天 UTC、同一天本地。
rev 7 把几处裁定写成 2026-10-16 是会话日期提示停在 10-16 所致，rev 8 按转录改正。

评审与头脑风暴记录（各轮的质疑原文、辩护与反驳在同名 JSON 里）：

| 编号前缀 / 名称 | workflow | 记录 |
| --- | --- | --- |
| 决定 3 辩论 | `wf_e5c880df-0b6` | 会话 workflows 目录 |
| rev3-C* | `wf_c4edfeb3-0ed` | 同上 |
| rev4-C* | `wf_602fd792-fc7` | 同上 |
| 六条事实头脑风暴 | `wf_79f85875-b05` | 同上 |
| 放置原则头脑风暴 | `wf_50483b4f-eab` | `reviews/2026-10-15-brainstorm-*.json` |
| Q3/Q4/Q5 辩论 | `wf_7013bfb2-e81` | `reviews/2026-10-15-debate-q3-q4-q5*.{md,json}` |
| rev5-C* | `wf_18116d0a-779` | `reviews/2026-10-15-rev5-review.json` |
| rev6-C* | `wf_935c4c96-b23` | `reviews/2026-10-15-rev6-check.json` |
| 父解析头脑风暴 | `wf_0caab246-07c` | `reviews/2026-10-15-parent-resolution-brainstorm.json` |
| rev7-C* | `wf_1706a31f-824` | `reviews/2026-10-17-rev7-check.json` |
| 考古 M* | `wf_ad866c4c-eda` | `reviews/2026-10-17-rev7-archaeology.json` |
| rev7-C2 核实 | 单个 agent | `reviews/2026-10-17-r7c2-cost-verification.md` |
| 隐藏参数顺序辩论 | `wf_ed1080ae-844` | `reviews/2026-10-17-hidden-param-order-debate.json` |
| rev8-C*、J-1 | `wf_9aee7e55-2af` | `reviews/2026-10-18-rev8-check.json`、裁决正文 `reviews/2026-10-18-rev8-check-verdict.md` |
| 重审与核实 | — | `reviews/2026-10-14-reexam-decision17.md`、`2026-10-14-reexam-sec5_2c.md`、`2026-10-15-ctr-sugar-tvar-form.md`、`2026-10-15-r6c16-verification.md` |

- 2026-10-10：TAT 的 `Record` node class 设计中发现 `record` 在 locale 里报 `Bad context for command "record"`
  （record.ML:2427-2432 `Toplevel.theory`；toplevel.ML:429-436）。
- 2026-10-11：四个 Opus agent 的研究（record 包解剖、局部化模式、light 约束、语法层）；作者提议最小补丁路线（§10
  第一条），用户否决并定下标准："我认为需要走正经移植，要走最正确最优雅的哪怕是困难的路"。探针 `syn_names` 同日跑。
- 2026-10-12：用户决定独立 repo、旧 API 不改、`split_args` 保持原本行为、新接口命名；"现在 isabelle 不可用。可用后
  我会给你通知"；repo 归属（submodule、提交时机）首次提出，2026-10-18 定。rev 1 决定 3 的性能实测，分两栏读：theory 层
  600 常量 stock 0.74 s；新 locale 里 `Main.monoid` 一个 scope 的 `define` 11.2 s（单 scope 二次方增长；每常量一个 scope
  的 `define` 在那里没量）、51 s（更大规模）、每常量一个 scope 2.2 s；"背景声明+定义+别名+note 1.8 s"是**逐常量、未批量**
  的形式，不是采纳的形状；300 字段整条 66.7 s——多线程下很可能漏掉 fork 的证明（§7.5）。性能不是否决 `define` 的理由。
- 2026-10-13：决定 3 的 7-agent 辩论 `wf_e5c880df-0b6`，常量走 background theory；用户批其 12 条改动，其中两条"要提给
  用户的偏离"（class 块里无 class 操作、instantiation 参数不被认领）当时被作者以旧决定 5 为由搁下，2026-10-17 补提、用户
  接受（§5.8 (24)）；rev 3 的 54-agent 评审（44 条质疑，4 blocker rev3-C1 至 C4）；四个 Opus agent 核选项代价
  （Generic_Data 不可见、`cases r`、`info` 存 `note_thmss` 返回值）；用户批准 rev 4 的形状、决定 1 修订、决定 2 形状、
  §7.5 阈值（当时编号 §7.2）、子选择 1-5 与 7（第 6 项是提问，非批准；作者对子选择 6 的解释当时有误、后更正）。用户
  裁定 rev 1 决定 10 越界（"既然不需要改代码，你为何需要改其计划呢？如果是新增测试的话，也应该是你来做啊"），对
  light 只剩工具层一项（light 的 `check_stock_diff.sh` 要接受依赖项目登记的文件）、"现在先记下来然后搁置"（14:49）；
  同一条作者消息里另有一项标"可选、留到里程碑 3 再定"的 theory 数据 morphism 钩子（rev3-C36），用户没有单独表态
  （§10）；用户"你应该用 Opus 跑！已有的继续复用"。rev 4 的 36-agent 聚焦复审（rev4-C1 至 C29：决定 18 的推翻、C6 的 `[cases
  type]` 坑、C7 决定 2(b) 的措辞、C9 时序；23 条 author 修法进 rev 5）。
- 2026-10-14：六条事实的头脑风暴 `wf_79f85875-b05`（4 设计 + 4 批评 + 综合）与读回法的核实；用户批准五项（含 info 的
  name hint："赞同打上"）、串行、§6 规则；用户同时说"我们还是要努力减少差异和代价的"（2026-10-18 裁定先不写成常设
  规则，记在此作背景）；用户定下 §0 第 8 条的判定标准；用户批决定 19 的方向与"声明为参数的块固定变量保持为参数、
  不声明直接用的成为隐藏参数"。作者承诺不再用 R1/R2 标签
  （术语表）。决定 17 与 §5.2(c) 的重审报告（`reviews/2026-10-14-reexam-*.md`；报告中的 "rev 5" 指 2026-10-14 的草稿，
  `Rule_Cases.save` 随它而来）。rev4-C6 交 light；用户在 light 会话 2026-10-14 17:47 本地接受窄变体（记在主仓库
  `ai-artifacts/LIGHT_LOCALE_HANDOFF.md` 条目"`record` 会话的请求与裁决（2026-10-15）"；仓库根目录同名文件是另一个更早
  的文件）。放置原则的头脑风暴 `wf_50483b4f-eab` 在本日跑（文件名按归档日期 10-15）。一条在后来被回退的分支上提出的
  要求——TAT 的 Record/Datatype node 遇块固定类型变量时给清晰指引（考古 M08；作者当时更正了用户建议的补救：把块固定的
  `'a` 声明为参数同样被拒，正确指引是改用块里没有固定的新鲜变量并声明、或在使用处实例化；过渡期 TAT agent 读到的是
  Isabelle 自己的两行文案，决定 19 与 `contrib/local_datatype` 落地后该错误消失）——2026-10-18 用户撤回（"不要指引。
  等计划完成就好"）。
- 2026-10-15：三项的对抗辩论 `wf_7013bfb2-e81`：Q3 采纳匿名登记（选项 B refuted、C holds_with_repairs）、Q4 之后、Q5
  分治——三项用户委托、作者裁定；用户对决定 17 的原话："第 3 项的那个否决点 / 我没有否决意见"（12:57；结清 Q3 裁判的条件 2：
  否决"放宽决定 2(b)"的理由不覆盖匿名 Induct 登记；"Q3 未委托"的说法来自一次丢了指代的转述，以此为准）；Ctr_Sugar
  条目 TVar 形式的核实；用户批准 §0 第 4 条两次放宽、决定 20、命名例外授权、`Ctr_Sugar.transfer_ctr_sugars` 的名字；
  light 确认两条共享假定并**建议**本项目的函数不与 ctr_sugar.ML:185-193、:221-231 相邻（例如结构末尾）。探针文件归档
  `ai-artifacts/probes/`（不提交）。rev 5 的 82-agent 聚焦复审（rev5-C1 至 C36：blocker C1 嵌套 `assumes` 层的外层与
  重放；C6 插件崩；C5 tag 顺序；C9/C10 别名集合；C13/C27 单一阶段函数；C24 性能指标；C36 决定 19 的提供方；rev 5 里
  §5.8 的依据 C 来自合并者对委托范围的理解）。用户处置：D1 作者裁定（插件回 theory 侧）；D2、D3 等 light 施工完成后
  再议；D4、D5 作者自决（D5 以不改变设计为限）；作者在 D6 未答时就写了 rev 6，用户纠正（"你为什么现在就写 rev 6 了？
  D6 我回答了吗？"），作者从零重讲后用户答 "批准第 1, 2 条 / D6 已知晓，请你继续"（16:18；编号按作者 16:17 的提案
  消息；第 1 条 = 决定 17 的 declaration
  扩展，其提案原文设想 `pervasive = true`、单一写者，rev 6 实际写成 `pervasive = false`、两个写者而未报告，rev 8 随
  rev7-C2 整条作废；第 2 条 = concealed def 事实的别名；其余五条知晓：rev5-C16 bundle、C30 `local.foo`、C31
  interpretation 打印、C32 Spec_Rules 行、C33 light interpretation）。rev 6 的 38-agent 短核查（rev6-C1 至 C16：blocker
  C1 simp_trace 包装位置；C2 declaration 的存放按 target；C5 quickcheck 实例；C6 bundle 表与第 18c/25 行；C7 消息 golden
  通道；C8/C9 变异检查与观测量；C12 `name_thm` 写法；C13 `Facts.dest_static` 的理由；C16 tag-only attribute 的提问）。
  用量恢复后以 `resumeFromRunId` 续跑完成。当晚：rev6-C16 由一个 Opus agent 核实（裁判写的 `Thm.rule_attribute` 在
  `Attrib.partial_evaluation` 下报错，改用 `Thm.mixed_attribute (apsnd (Rule_Cases.default_consumes 0))` 后六项全部成立；
  作者披露 §5.8 (4) 的两处差别后用户"确认接受 R6-C16"，20:12）；rev6-C5 用户接受为已知差异（只针对 `instantiation`，
  19:40）；rev6-C3：(a) 打印差异接受、改进归 local_type_abbrev 统一回折；(b) 由 local_type_abbrev 计划 rev 2 的决定
  5/17 决定；(c) 由决定 22 取代（20:47-21:20）。
- 2026-10-17 上午：父 record 解析的头脑风暴 `wf_0caab246-07c`（9 agent）：用户接受规则与新接受输入、文案变化类、决定 19
  的改措辞、残余（09:28-09:38）；落里程碑 1 由作者自决；解析函数不导出、AFP 的三个 `read_parent` 拷贝"我们不管"。用户
  同时裁定：TAT 的所有 type node 要在自己的 evaluation 里拒绝未使用的类型参数、文案统一，"如果相关 agents 还活着请通知，
  否则之后需要你去实现这个检查与报错"（已通知 TAT record、datatype、quotient type、mlml-98；e0c78c 是 AoA 会话、已拒；
  当时没有 typedef 会话）。rev 7 分两段写成（§0-§7.5 与 §8-§11），决策交接记录在 `REV7_HANDOFF.md`。
- 2026-10-17 中午至晚：rev 7 的 38-agent 短核查（rev7-C1 至 C16：C2 重放把父规则顶到子 record 之上；C8 里程碑 1 的
  gate 没有 session；C1 两条知晓被写成已知悉；C3 两条缩写的写入顺序；C4 隐藏参数顺序；C5/C7 第 4、18c 行会跑红；C6
  孪生的 THM 预测；C9 两个新机制缺变红检查；C10-C16 措辞与日期）；98-agent 决策考古（1915 条条目、54 条成立：丢掉的
  常设规则、被写成已定的未决事项、未报告的实现偏离、被反写或删掉的已接受修法、§10 漏项、掉落的跨项目承诺）。用户当日
  下午裁定（转录 06:44-08:00 UTC，本地 14:44-16:00）：rev6-C6 (i) 接受为合理行为；rev6-C14 委托作者修、不动设计；
  rev7-C2 经一个 Opus agent 核实"代价只是计划文字"后支持删重放；rev7-C8 委托作者（"与测试相关且不改变设计的可以请你
  自决"，作常设授权）；隐藏参数之间按名字排（在前还是在后交 Opus 辩论 `wf_ed1080ae-844`，用户直觉在后）；两条给
  local_type_abbrev 的通知批准、发出、被采纳；TAT 文案"转"（16:00）——此时 TAT record 会话已改用用户在 quotient type
  会话定的句子 `The field `type_parameters[1]` declares `'b`, which is not used.`（`InvalidField`、gen 时、COMMON.md §4
  a328367）并在 std/common.py 实现共享 helper `check_type_parameters_used`、Record 已接入（只经父用到的参数算用到），
  兜底义务落实；Datatype 的接入归 quotient type 会话（它持有 datatype.py 的 hunk）、Typedef 的归 QuotientType 的实施步；
  TAT 文案与分析按"转"转给 mlml-98 与 datatype 会话。辩论当晚撞 Opus 周配额、六个 agent 全部失败，次日恢复。
- 2026-10-18 上午至午后（转录 02:34-06:58 UTC，本地 10:34-14:58）：用户"1. 恢复辩论"，以 `resumeFromRunId` 复用已完成
  的 agent 续跑；裁判倾向在前、优势不大，用户"那么建议在后 / 确认按名字排用块里的名字"（11:50）；class 块两条偏离接受
  （11:58；10-17 提出）；块内 `declare [[typedef_overloaded]]` 照 `record_codegen` 的做法在 target 侧读一次传入，并要求
  datatype 也做块固定类型变量扩展、同样改系统代码（12:19；datatype 会话受命立项 `contrib/local_datatype`，计划 rev 1）；
  "record 接受块固定的类型变量（两种用法）、datatype 拒绝"列为决定 2(b) 的第三条有利偏离（插队消息）；无字段使用的
  参数经 synonym 作父确认不支持；§0 第 7 条的授权边界新写法；"努力减少差异和代价"先不写成常设规则（12:28）；知晓类
  事项可先写入正文标"待用户知晓"（12:29）；REPL 重启逐次批准（12:34）；repo 挂 submodule、分支 `main`、首次提交等
  短核查后由用户说"提交"；§7 签字形式由作者定（12:42）；TAT 节点指引不要（"不要指引。等计划完成就好"，14:58）；记忆
  文件改写批准。用户在 datatype 会话裁 phantom type 一律拒绝（10:25 本地）。用户提议 TAT 全局 `declare
  [[typedef_overloaded]]`、作者分析转 mlml-98 与 TAT record（由用户在 TAT 会话定），TAT 侧回报已采纳（TAT_Std.thy
  开头统一 declare、删各 type node 自己的 overloaded 判断）。light 通报（见决定 21）：窄变体保留为里程碑 3 第一项之后
  的单独一步、D3 四问的现答、窄变体批准时间为 2026-10-14。rev 8 写成，`REV8_CHECKLIST.md` 是它的逐条改动清单。
- 2026-10-18 午后至晚：rev 8 的 38-agent 短核查 `wf_9aee7e55-2af`（rev8-C1 至 C16 与裁判加项 J-1：C1 §7.1 的 fixture
  要拆成 theory 层、块、里程碑 4 三份；C2 隐藏参数在全局 record 里保留块里的名字还是换名——计划两处说法矛盾；C3 第 2b
  行的 M2 模拟改用 `local_setup` 版 `[cases del]`；C4 决定 19 写入顺序只在 theory naming 的 target 里可观察；C5 第 6e
  行的 interpretation 实例会被 fixture 里已有的 registration 匹配而静默跳过；C6 `definition f` 撞 locale 参数、fixture
  字段重名；C7 无限定词 interpretation 在先时的短名遮蔽让子 record 静默得到闭合父；C8 §5.8 (21) 的文案随提供方 rev 4；
  C10 新增第 5b 行；C11 §7.2 清单缺消息 session；C12 决定 21 引文不是 light 的原话；C13 §5.8 (3)/(17)/(24) 的范围；C14
  两段代码片段的未定义名；C15/C16 日期与措辞）；裁定里程碑 1 相关修法后即可开工里程碑 1——用户 compact 之后推翻（下条）。
  datatype 会话转来两条待用户裁的发现（`Typedecl.fixed_names`；typedef 的 `type_alias` 重放），记头部。compact 之后
  用户裁定：R8-C2 选 (a)（隐藏参数保留块里的名字与 sort）；R8-C7 等 local_type_abbrev 自己的探针（其 §7.1 第 1 项）
  结果再裁；R8-C13 的 overloading 半作者从零讲过后"知晓"；**"建议把所有问题都敲定后再开工，而且我们必须等 light locale
  全部完成后再开工"**——里程碑 1 也等全部未决项定下、light 施工全部完成。rev 9 写成（本文件）：按裁决正文的 17 组修法
  手改；R7-C11 第 5 项把 `overloading` 误加进 §5.8 (17) 的范围句，rev 9 删（`overloading` 块不加 arity，
  overloading.ML:193-215）；决定 19 (a) 的换名范围收窄到声明为参数的块固定变量，偏离 Q5 裁判条件 [7] 的字面（决定 15）。
  rev 9 写成后通知 datatype 会话（只告知，无请求）；它回复：datatype 结构上只能给隐藏参数换新鲜名（BNF 在块的 lthy 里
  构造），与 record 的差别只是 theory 层事实陈述里的类型变量名（`?'a` 对 `?'b`），记入它的计划作已知差异；R8-C7 对应它
  决定 8 的例外、同一前置条件；它的里程碑 1 只等用户放行、里程碑 2 等 local_type_abbrev 按两条发现修订。它随后转述
  两条用户在它那边的裁定（git 分支链、`Typedecl.fixed_names` 导出），用户随即在本会话确认："都确认"——§0 第 5 条改为
  分支链（本项目基于 `local_type_abbrev`、`local_datatype` 在后）、D2 与决定 10 的工具层拟议作废、决定 9 的定义改为
  引用 `Typedecl.fixed_names`、里程碑 1 多一条对 local_type_abbrev 修订的依赖；迁移方案（rev 2）本身待批，§8 第 3 步、
  §9、决定 1 的 `tools/` 的细节等它批准后写。签字表：用户确认第一类 7 条已接受的差异仍接受，第 8-12 条逐条接受（第 12
  条即 §5.8 (18) 第二部分的知晓），其余"都接受"——§7 预期冻结。
