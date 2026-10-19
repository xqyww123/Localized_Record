# §7 预期的批量签字表（rev 9，2026-10-18）

> **签字状态（2026-10-18 晚）**：用户已签。作者先把"需要注意的"列成 12 条（第一类：7 条已接受过的已知差异，这次以测试行再
> 出现；第二类：里程碑 4 新写的预期 4 条；第三类：§5.8 (18) 第二部分的知晓 1 条），用户"确认"第一类、逐条"接受"第 8-12 条
> （第 8、9、11 条经作者举例讲解后），其余行"都接受"。§7 的预期自此**冻结**；表头列出的不签行除外。

依据 `LOCALIZED_RECORD_PLAN.md` rev 9 §7 与 §0 第 7 条（测试里的预期行为要用户批准）。签字形式由作者定（用户 2026-10-18
委托）：只列**与 `datatype` 孪生不同**的行与**评审新增**的行；其余"与孪生相同"的行一句批量签。签字之后预期**冻结**，再改
任何一行都重新请示，不得在改计划时顺手改成实测结果。

**不在本表、不签**（预期值尚未定）：第 6e-iv 行与探针 P11 第 (3) 半（先解释后定义的短名；等 local_type_abbrev §7.1 第 1 项
的探针结果后用户裁，§5.8 (22) (b)）；第 7c、7d 行与 7f、7h 的孪生列（等 light 窄变体那一步与 light 对 D3 (iii) 的正式确认）；
第 8b、18e 的孪生列（标 D3）。"预测"指按源码预测、未跑过探针；失败即缺陷，不是签了就算对。

每行：行号 | 场景 | 观测量 | 预期 | 依据 | 孪生或无孪生的理由。

## A. §7.3 块内行为（里程碑 2 的 gate；6e 为里程碑 4）

| 行 | 场景 | 观测量 | 预期 | 依据 | 孪生 / 理由 |
| --- | --- | --- | --- | --- | --- |
| 1 | `locale l = fixes k :: nat begin record 'a p = x :: 'a  y :: nat … end`，块内 | `lemma "x (r⦇x := a⦈) = a" by simp`（simproc） | 成功 | 决定 3、4（数据表全局） | 无孪生：datatype 无更新 |
| 1 | 同上 | `proof (cases r) case (fields a b)`、`proof (induct r)`，对 `('a, 'z) p_scheme` 的 `case (fields a b m)` | 成功 | 决定 17 | 无孪生：datatype 无 scheme |
| 1 | 同上 | `Thm.get_tags` 对块内 `p.cases`、`p.cases_scheme`、`p.induct`、`p.induct_scheme` | `[name, consumes "0", case_names "fields"]`，等于 theory 层孪生 record 的 | 决定 17（`consumes 0` 是手写复述） | 孪生：theory 层 record |
| 1 | 同上 | 事实短名 `select_convs`、`p.select_convs`、`ext_inject`、`p_ext_def`、`p_ext.Rep_p_ext_inject`、`p.make_def` 等（def 事实 `is_concealed` 为真）；名字空间 dumper 与 theory 层孪生一一映射；负行 `thm l.l.p.simps` 报 Unknown fact | 可解析 / 映射成立 / Unknown fact | 决定 20、14 | 无孪生：BNF 的构造子 def 无名 |
| 1 | 同上 | `Spec_Rules.retrieve` 对 `x`、`x_update`、`make` | 各恰一条等式条目 | 决定 15 | 孪生 `d.sel` |
| 1 | 同上 | `length (Typedef.get_info @{context} T) = 1`；`Ctr_Sugar.ctr_sugar_of` 条目与 theory 层孪生 record 的 `ML_Syntax.print_term` 相同（TFree 形式） | 成立 | 决定 15、§3.10、§3.11 | 孪生：theory 层 record |
| 1 | 同上 | `copy_bnf ('a, 'z) p_ext`；`lemma "x r = y r" nitpick [expect = genuine] oops` | 成功 / genuine（E） | §5.8 (11) | 无孪生 / 孪生同 |
| 1 | 同上，17 字段 record | simp、simproc、cases；`Typedef.get_info` 对 `p_inner1` | 成功；长度 1 | §3.10 | 孪生：theory 层 record |
| 1 | 同上 | `Consts.the_abbreviation` 对每个 record 常量 | 不存在 | 决定 3（不经 `define`） | 孪生：theory 层 record |
| 1 | 同上，块内父解析 | `record d1 = "nat p" + z :: bool` 与 `type_synonym qa = "nat p"` 后 `record d2 = qa + z :: bool` 的 `Record.get_parent` | 相同 | 决定 22 | 孪生：theory 层 record |
| 1b | 块内 `declare p.simps [simp del]` | 裸 simp / `simp add: p.simps`；再定义一个 record 后与重开后 | 失败 / 成功；仍是删除状态 | 决定 2(b) | 孪生 `declare d.sel [simp del]` |
| 1c | 块内 `declare p.cases [cases del]` | `print_induct_rules`；`proof (cases r)` | 不再列它；退到 `p.cases_scheme` | 决定 17（`del_att` 按命题） | 孪生 `declare d.exhaust [cases del]` |
| 1d | 块内重开与 theory 上 `context begin` 里 `term "⦇x = 1, y = 2⦈"` / `⦇l.x = 1, y = 2⦈` | 打印 | 同形 | 决定 3 辩论改动 [10] | 无孪生（打印翻译是 record 的） |
| 2 | `end` 之后 theory 层 | `lemma "l.x (r⦇l.x := a⦈) = a" by simp`、`lemma "r⦇l.x := a, l.x := b⦈ = r⦇l.x := b⦈" by simp` | **成功** | 决定 3、4 | 无孪生：datatype 无更新 |
| 2 | 同上 | `lemma "l.x ⦇l.x = a, y = b⦈ = a"`：`by simp` / `by (simp add: l.p.simps)` | 失败 / 成功 | 决定 2(b) | 孪生同 |
| 2 | 同上 | iff 引理裸 `blast` / `blast dest: l.p.iffs[THEN iffD1]` 与 `auto iff: l.p.iffs` / `blast dest: l.p.iffs` | 失败 / 成功 / `Ill-formed destruction rule` | 决定 2(b) | 孪生 `l.d.inject` |
| 2 | 同上 | `proof (cases r) case (fields a b)`、`induct r`、`case_tac r`、`induct_tac r` | 成功、用 record 的规则 | 决定 17 | 孪生 `cases t` 失败 `Failed to apply proof method`、`induct t` 报 `Unable to figure out induct rule` |
| 2 | 同上 | `take 3 (map Thm.prop_of (Induct.find_casesT @{context} @{typ "nat l.p"}))` | aconv `l.p.cases`、`l.p.cases_scheme`、`l.p.p_ext.Abs_p_ext_cases` 的命题；`drop 3` 等于对 `'x` 的；scheme 类型同法；`Induct.dest_rules` 中 `Thy.l.p`、`Thy.l.p_scheme` 各一条且无带前提的 record 规则 | 成立 | 决定 17、rev6-C16 | 无孪生（theory 层检查） |
| 2 | 同上 | `fun g where g ⦇l.x = a, y = b⦈ = a` | 成功 | 决定 15 | 孪生同 |
| 2 | 同上 | `thm l.p.select_convs l.select_convs l.Rep_p_ext_inject`；负行 `thm p.select_convs` | 可解析；Unknown fact | 决定 20 | 无孪生 |
| 2 | 同上，父解析 | `record c1 = "nat l.p" + w :: nat` 与 `type_synonym qb = "nat l.p"` 后 `record c2 = qb + w :: nat` | 同父 | 决定 22 | 孪生：写 record 名的同一行 |
| 2 | 同上 | `definition v :: "nat l.p" where …` 后 `value v`；另一个 locale `m` 里同名 `p` 后 `thm l.p.simps m.p.simps` 各取各的；全名、`intern`/`extern` 与 §4 逐项相同 | 成立 | 决定 14、§4 | 孪生：theory 层 record / 无 |
| 2b | 变异检查表（M1 块内 notes 换回 stock 列表；M2 单独 4b 形叶 + `local_setup` 版 `[cases del]`/`[induct del]`；3E 格） | 各格的 `nprems_of`、`count_of`、`induct_tac` 残留、`case (fields a)` | 按表：M1 各格变红（`nprems_of` 2、`Too many parameters for case`、7h 处 THM）；M2 只定义层与外层变红（`Failed to apply initial proof method`、`Unable to figure out induct rule`）；3E 格不受 M2 影响 | 决定 17、rev7-C9、R8-C3 | 评审新增（全部预测） |
| 3 | `context l begin … end` 重开 | 短名（含事实别名、def 事实）、simp、simproc、cases、`fun`、`copy_bnf`；`Induct.dest_rules` 中 `Thy.l.p` 条目数；`hd find_casesT` | 恢复；1；3E 的无条件规则 | 决定 17、20 | 孪生 `datatype` |
| 4 | `interpretation I: l 5` | `thm I.p.simps I.simps`、`I.x`、`I.p.x`、`typ "nat I.p"`、`thm I.p.select_convs I.p.make_def`（同一对象）；theory 层 `term "l.x r"` 印 `I.x r`、`⦇I.x = …⦈` 并读回；实例的 `[simp]`/`[iff]` 在 theory 层生效 | 成立 | 决定 20、7、§5.8 (16) | 孪生：无参数 locale 的 definition、`type_synonym` |
| 4 | 同上 | `cases r` 用的规则与匿名规则同命题；`Induct.dest_rules` 的 `#type_cases` 里 `Thy.l.p` 条目数；`record c3 = "nat I.p" + w :: nat` 与 `"nat l.p"` 同父 | 同命题；1；同父 | 决定 17、22 | 无孪生 / 孪生 theory 层 |
| 4 | 接着 `interpretation J: l 6` | 无错、无重复警告；`thm J.p.simps`；`value` 与代码证书不变；条目数仍 1；Spec_Rules 行按 §5.8 (6)；同块 300 字段 `big` 的 `I.big.simps` 可用；record 之前做的 interpretation 之后 Induct 存的是匿名规则（按命题比较） | 成立 | 决定 14、15、17 | 评审新增 |
| 4b | `locale l4 = fixes k :: nat`；`interpretation I: l4 5`；`context l4 begin context fixes n :: nat assumes "0 < n" begin record p4 = z :: nat end … end` | 外层、`end` 后 theory 层、重开后、之后的 `interpretation J: l4 6` 后、theory 上 `context fixes c assumes "0 < c"` 里的 `global_interpretation G: l4 7` 后：对 recT 与 rec_schemeT 的 `Thm.nprems_of (hd find_inductT/find_casesT) = 1`、`Exported_Premises.count_of = 0`、`proof (induct r) case (fields a)`、`induct_tac r` 不留 `0 < ?n`、`nat` 键下没有 record 条目、theory 层 `fun` 用 `p4` 模式成功；Spec_Rules 头按 §5.8 (15)/(19) 的免检格 | 全绿 | 决定 17、rev6-C16、决定 15 | 孪生 `datatype (plugins del: code)` 与 `typedef`（探针 (m)）；评审新增 |
| 5 | `locale la = fixes k :: nat assumes "k > 0" begin record 'a p = x :: 'a  y :: nat … end` | theory 层 `la.p.simps` 的 `nprems_of` 比 stock 多 1；块内 simp 正常 | 成立 | 决定 2(b) | 孪生同 |
| 5 | 同上，`end` 后 theory 层 | `record 'a cq = "'a la.p" + w :: nat`；`Ctr_Sugar.ctr_sugar_of_global` 对 `cq` 的扩展类型有条目、`#exhaust` 的 `nprems_of` 1；`fun h :: "nat la.cq ⇒ nat" where h ⦇la.x = a, y = b, w = c⦈ = c` | 成功 | 决定 22、15 | 孪生 `primrec` 失败 / 形状同 theory 层孪生（R8-C11 新增） |
| 5 | 同上 | `Record.get_info thy "…la.p"` 六条定理：`nprems_of` 与 stock theory 层相同（`simps`/`iffs` 0、四条规则 1）、`hyps_of` 空、tag `[name, consumes, case_names]` / `[name]` | 成立 | 决定 4 | 无孪生（info 是 record 的） |
| 5 | 同上 | theory 层 `fun f :: "nat la.p ⇒ nat" where f ⦇la.x = a, y = b⦈ = a`；`Thm.nprems_of (#exhaust (the (Ctr_Sugar.ctr_sugar_of_global thy T)))` | 成功；1 | 决定 15 | 孪生 `datatype` 预计失败到 interpretation |
| 5 | 同上 | `cases r` 用无条件规则（`nprems_of (hd …) = 1`）；`declare la.p.cases [cases del]` 后 `cases r` 仍用匿名规则；再以无条件命题写 lemma 并 `[cases del]` 后退到 `la.p.cases_scheme`；重开与 `interpretation I: la 5` 之后仍保持删除 | 成立 | 决定 17、§5.8 (4) | 孪生：theory 层 record 的 `[cases del]` |
| 5 | `locale la0 = fixes k :: nat`（无 `assumes`，单独 leaf） | 直接 `declare la0.p.cases [cases del]` 删得掉且保持；`declare I.p.cases [cases del]` 同法；删后 `declare la0.p.cases [case_names fields, cases type: la0.p]` 加回、`case (fields a b)` 可用；`Induct.dest_rules` 的 `#type_cases` 里 `Thy.la.p` 条目数在 `interpretation I: la 5`、`J: la 2` 之后各为 1 | 成立 | 决定 17、§5.8 (4) | 孪生：theory 层 record |
| 5 | 同上 | `simp add: la.p.simps` / `simp add: la.p.select_convs`；`Spec_Rules.retrieve_global` 对 `la.x` | 失败 / 成功；两条、头一条无条件 | 决定 2(b)、15 | 孪生 `d.sel` |
| 5b | `locale l5 = fixes k :: nat begin record 'a p = x :: 'a  y :: nat end`；theory 层 `lemma my_cases [case_names fields, cases type: l5.p]: "(⋀b a. r = ⦇l5.x = a, y = b⦈ ⟹ P) ⟹ P"` | lemma 之后、`context l5 begin` 里、那里再 `record q` 之后与 `end` 之后、`interpretation I: l5 5` 之后、`lemma (in l5)` 里：`Thm.prop_of (hd (Induct.find_casesT @{context} @{typ "nat l5.p"}))` aconv `my_cases`，且 `proof (cases r) case (fields b a)` 给 `r = ⦇l5.x = a, y = b⦈` | 全绿 | 决定 17（不重放）、`Item_Net.update` = `cons` ∘ `remove` | 孪生 theory 层 record；变异：6d 的构造，重开格与 interpretation 格变成 `r = ⦇l5.x = b, y = a⦈`；R8-C10 新增 |
| 6 | 父子：块内 `record 'a cp = "'a p" + z :: bool`；块外 `record 'a cq = "'a l.p" + w :: nat`（加 Ctr_Sugar 条目、`nprems_of` 1、theory 层 `fun h`）；theory 层 `record par` 后块内 `record ch = par + b :: nat`，`end` 后 `proof (cases r) case (fields a b)` 对 `r :: l.ch` | 得到 `a`、`b`；theory 层 `fun` 对 `ch` 模式与孪生相同 | 决定 22、17、15 | 无 datatype 对应；孪生是 theory 层同样写法的 record |
| 6b | 块 fixture `l0`：`"nat r"` 与块内 `qa` 作父；`end` 后 `"nat l0.r"`；`interpretation I0: l0 5` 后 `"nat I0.r"` | 接受、同父 | 决定 22 | 孪生：写 record 名 |
| 6c | 负行 | `"(nat, bool) r_scheme"` 报 `Unknown parent record "T.l0.r_scheme"`；`"nat list"` 报 `Unknown parent record "List.list"` | 文案如左 | 决定 22 | 孪生：stock 的 `Unknown parent record` |
| 6d | 子在父块外：`locale l6 … record p6` 后 theory 层 `record c6 = "l6.p6" + y :: nat`；bundle 变体 `pb`/`cb`/`unbundle b6`；观测点 `context l6 begin`、`interpretation I6: l6 5`、`locale m6 = l6 begin`、`unbundle` 之后、class `d = c + …`、`sublocale` 变体 | `hd (Induct.find_casesT @{context} @{typ c6})` aconv `c6.cases`、`find_inductT` aconv `c6.induct`、`proof (cases r) case (fields a b)` 得 `r = ⦇l6.x = a, y = b⦈`、`case_tac`/`induct_tac` 同 | 全绿 | 决定 17（rev7-C2） | 孪生 theory 层 `par6`/`ch6`；变异：重加忽略 morphism 的存下 declaration，各格必须变红；评审新增 |
| 6e-i | 里程碑 4 fixture `l`/`lp`/`lpb`/`lpq`/`ql`/`I`，导入它的叶（无无限定词 interpretation） | `context l begin record d = lp + y :: nat`：`#args` 含隐藏 `'a`、隐藏项 = `("'a", 块的 sort)`、`get_parent = SOME ([TFree 'a], "T.l.lp")`、`term "⦇g = f, y = 0⦈ :: d"` 类型检查；孙 record；`record (in l) c = lp + …`；`record 'a c2 = lp + z :: 'a` 的 `#args` 与父参数同一个新鲜名、无隐藏参数；theory 层 `"I.lp"` 与 `"nat l.lp"` 同父 `([nat], T.l.lp)` | 成立 | 决定 19 (a)(b)、22 | 孪生：无隐藏参数、按名写的同样 record |
| 6e-i | 同上 | `lpq` 的 `#args` 为 `('b, 'a)`；块外 `(bool, nat) l.lpq` 接受且 `h :: bool`、`gq :: nat ⇒ nat`；`('b, nat, 'z) l.lpq_scheme` 接受且 `h :: 'b`、`gq :: nat ⇒ nat`；`interpretation J: l Suc` 后 `bool J.lpq` 印 `(bool, nat) l.lpq`；`print_record` 的头；同块子 `('b, 'c) lpc = "'b lpq" + k :: 'c` 的 `#args` 为 `('b, 'c, 'a)`，块外 `(bool, int, nat) l.lpc` 且 `h :: bool`、`k :: int`、`gq :: nat ⇒ nat` | 成立 | 决定 19（顺序：声明在前、隐藏按块里的名字在后、`'z` 最后） | 同上 |
| 6e-i | 同上 | 同块 `type_synonym qla = "'a p"` 后 `record d3 = qla + y :: nat` 与同块孪生 `"'a p"` 同父；class/instantiation/light/experiment 变体；块内 `lp` 解析为 `local.lp`、`definition fd :: "lp ⇒ nat" where "fd r = 0"` 可用；交换两条缩写写入顺序的变异在这里预计仍绿（对照） | 成立 | 决定 19、22、提供方里程碑 1-3 | 同上 |
| 6e-ii | 无限定词 interpretation 叶：`interpretation l "λx::nat. x"` | (a) 之前 theory 层 `typ lp` 报 `Undefined type name: "lp"`；(b) 之后 theory 层 `record d = lp + y :: nat` 父为 `([nat], T.l.lp)`；(c) 只记录：重开 `context l begin` 里 `lp` 读成什么 | (a)(b) 如左；(c) 不签 | 决定 22、提供方决定 5/8 | 孪生：写 `"nat l.lp"` |
| 6e-iii | `interpretation K: l id`（开放） | `typ "K.lp"` | `Undefined type name: "K.lp"` | 提供方决定 2 | Pure 自己的行为 |
| 6e-v | theory naming 的两个叶（= P11 第 (1) 半）：theory 上 `context fixes x :: 'a begin record r = y :: 'a  record d = r + z :: nat end`；`instantiation list :: (type) c begin record lp = …` | `r` 读成 `local.r`、`d` 的父等于孪生 `"'a T.r"`、`end` 后 `"nat r"` 读成 `T.r`；instantiation 叶里 `'a` 得隐藏参数、块内写 `lp`；变异：交换写入顺序后 `definition f :: "r ⇒ nat"` 报 `Bad number of arguments for type constructor: "<thy>.r"`（instantiation 叶同） | 成立 | 决定 19 写入顺序（R8-C4） | 孪生：写 `"'a T.r"` |
| 6e 负行 | `"nat lpb"`；绕法 `"(nat, 'a) l.lpb"`；`ql` 作父 | `Unknown parent record "local.lpb"`；成功；`Unknown parent record "local.ql"` | 文案如左 | 决定 22 残余（§5.8 (22)） | 孪生：stock 文案形式 |
| 7 | theory 上 `context fixes z :: nat begin record … end` | 名字无前缀、`[simp]`/`[iff]` 全局、`value` 成功、`Induct.dest_rules` 中条目数 1 | 成立 | §5.3 | 孪生 `datatype` |
| 7b | `context fixes n :: nat assumes "0 < n" begin record q = y :: nat end` | `q.simps` theory 副本条件形式；simproc（`q.y (r⦇q.y := a⦈) = a`、`r⦇q.y := a, q.y := b⦈ = r⦇q.y := b⦈` by simp）与 `value` 可用；`cases r`/`induct r` 用无条件规则、case 名 `fields`；theory 层 `fun` 用 `q` 模式；级别 2 的 `export_code`、`quickcheck`；`find_casesT @{typ nat}` 的头与块前一致（预计 `Nat.nat_exhaust`）、`cases m` 两种写法成功 | 成立 | 决定 17、rev6-C16 | 孪生：普通 `datatype` 崩在 `dest_equals`；`(plugins del: code)` 版的条件副本归到 `nat`（探针 (e)，7c/7d 列不签） |
| 7e | `locale l3 = fixes k :: nat begin context assumes "1 < k" begin record p3 = z :: nat end …` | record 命令成功；外层 `proof (induct r) case (fields a)` 无多余子目标；`end` 后 theory 层、重开后同 | 成立 | rev6-C16、决定 17 | 孪生列不签（THM 预测，等窄变体） |
| 7f | `interpretation I: l3 5` | 成功（record 列） | 成立 | 决定 17 | 孪生列不签 |
| 7g | 封闭的 class 例 `class c7 … context assumes "cc = cc" begin record p7 …` | 4b 的整表观测量，在 class 层、`end` 后 theory 层、重开后 | 全绿 | 决定 17 | 孪生列不签 |
| 7h | record 之前做的 interpretation（闭命题 `assumes "1 < k"`，k := 5） | record 命令成功 | 成立 | rev6-C16 | 孪生列不签 |
| 7i | theory 上双层嵌套 `context fixes n :: nat begin context assumes "0 < n" begin record q7 …` | 外层与 theory 层观测；theory 层 `fun` 用 `q7` 模式 | 成立 | 决定 17 | 孪生探针 (w)，不签 |
| 7j | theory 上 `context assumes "finite (UNIV :: bool set)"`（闭命题） | record 成功 | 成立 | rev6-C16 | 孪生列不签 |
| 7k | record 之前在 theory 上 `context fixes c assumes "0 < c"` 里做过 `global_interpretation`，之后定义 record、再 `cases r` | `nprems_of` 1、`cases` 成功、每键一条、`nat` 键干净 | 成立 | 决定 17（两个写者一起） | 孪生列不签 |
| 8 | `instantiation nat :: c begin record … end` | 同 theory 层外加别名；名字空间 dumper 与 theory 层孪生、同块 `datatype` 孪生相同；`Induct.dest_rules` 条目数 1；父行 `"nat p"` 与块内 `qa` 对 `Record.get_parent`；级别 2 的 `export_code`、`quickcheck`；字段 `cc_nat` 仍是普通字段、`instance` 仍要求定义 `cc` | 成立 | §5.4、§5.8 (24)(ii) | 无孪生：datatype 在 instantiation 里的条目数另计；(24)(ii) 用户已接受 |
| 8b | `instantiation nat :: c begin context fixes n :: nat assumes "0 < n" begin record p8 … end … end` | theory 层 `hd find_inductT` 无条件、`nat` 键干净 | 成立 | 决定 17 | 孪生列标 D3，不签 |
| 8c | `typedef t = "UNIV :: nat set"` 加 `code_datatype Abs_t`；`instantiation t :: random` 里 `record p1`（`instance` 前）、`instance ..`、`record p2`，`end` 后 `record p3` | `Sorts.has_instance (Sign.classes_of thy) <ext 名> @{sort random}`：`p1` 假、`p2`、`p3` 真；`quickcheck [random]` 对 `p3` 可跑、对 `p1` 报无生成器；`full_exhaustive` 同法 | 成立 | §5.8 (17)（用户 2026-10-15 接受） | `datatype` 孪生只作信息 |
| 9 | `class c = fixes cc :: 'a begin record 'b p = … end` | 成功且 `value` 可用 | 成立 | 决定 5、§5.5 | 孪生 `datatype` 失败 |
| 9 | 同上，`end` 后 | `c_class.p.simps` 在 `dest_simps`、theory 层 simp 引理成功、cases 条目一条且命题为原始规则、短名 `p.select_convs`/`x` 解析；父行 `"nat c.p"` 与 `"nat p"`；`typ "nat p2"` 可读 | 成立（预测） | §5.5（class 的自我 registration） | theory 层检查无孪生 / 孪生 `record 'b p2 = h :: 'b` |
| 9 | 同上 | `c.x` 的类型不带 `'a::c` 约束；同块 `definition f :: "'a ⇒ 'a" where "f x = cc"` 的 `c.f` 带 | 成立 | §5.8 (24)(i)（用户已接受） | 与 `definition` 的偏离 |
| 9 | 负行 → 正行（里程碑 4） | `record 'a bad = x :: 'a`：里程碑 4 前 §6 两行；里程碑 4 起成功、`#args` 一项、sort 是块里读到的 sort（class 块预测 base sort，P9）；`record bad2 = bu :: 'a`：里程碑 4 前 `Extra free type variable(s)`，起作隐藏参数、`nat c.bad2` 对非实例也接受 | 如左 | 决定 9、19 | 孪生 `datatype` 两种都拒绝（决定 2(b) 第三条有利偏离） |
| 9b | `class c9b = fixes cc :: 'a begin context fixes n :: nat assumes "0 < n" begin record p9 … end … end` | 4b 的整表观测量对 recT、rec_schemeT 与 `nat` 键，加 `proof (cases r)` | 全绿 | 决定 17 | 孪生探针 (m) |
| 9c | `class c9 = fixes cc :: 'a assumes "cc = cc" begin record 'b p9 = x :: 'b end` | 第 9 行的预期加第 5 行的 `get_info` 检查 | 成立 | §5.5 | 无孪生：`datatype` 在 class 里失败 |
| 10 | `locale lf = fixes f :: "'a ⇒ 'a"` 里的负行（`record 'a bad`、`ok2 = g :: "'a ⇒ 'a"`、`instantiation` arity 变量、纯类型 locale）；`locale l0 begin definition f … record 'a p …`；`locale lz = fixes g :: "'z ⇒ 'z" begin record 'a p …` | §6 两行 / `Extra free type variable(s)` / 成功 / 成功（`zeta` 换名） | 如左 | 决定 9 | 各带 `datatype` 孪生（文案不同：`Locally fixed type argument` / `Extra type variables on right-hand side`） |
| 10 | 里程碑 4 起 | `record d = p + k :: nat` 得隐藏参数；`term "r :: p"` 印 `'a l.p`；theory 层 `record ('a, 'b) ph = w :: 'b` 后块内 `record d = "('a, nat) ph" + y :: nat` 报 `Extra free type variable(s) 'a`、`"(nat, 'a) ph"` 成功得隐藏 `'a`；嵌套 `context fixes y :: 'd begin record r2 = w :: 'd end` 后外层 `r2` 报 `Undefined type name`、`nat l.r2` 可读 | 如左 | 决定 19 (b) 例外、§5.8 (20)(25) | 孪生：theory 层同命令 / 无隐藏参数的 record |
| 10 | `locale m = l1 + l2`，两边各有带隐藏参数、内容不同的 `p` | 三行：`Type abbreviation "p" is already defined as "…" and cannot also be defined as "…".`、`Rename it or import it with a qualifier.`、`The above error(s) occurred while activating facts of locale instance …`；报的是 `p` | 如左（展开式由探针钉住） | §5.8 (21)、提供方决定 5/17/20 与其 §6 第 2 条 | 孪生无隐藏参数时成功 |
| 10b | `interpretation l Suc` 之后 `interpretation l "λx::bool. x"`；再 `interpretation l "λx::nat. x"` | 前者：提供方 §6 第 2 条加 activation 行；后者：`Duplicate fact declaration` | 如左（预测） | §5.8 (21)、提供方决定 20、global_theory.ML:300 | 评审新增（R8-C8） |
| 12 | `(overloaded)`：`typedef (overloaded) 'a::zero nz`；`record (overloaded) 'a::zero r = f :: "'a nz"`；不带 `(overloaded)`；`declare [[typedef_overloaded]]` 后不带 `(overloaded)` 的 `r2` | 成功 / typedef 的 open-dependencies 错接 record 包装 / 成功 | 如左 | 决定 11 | 孪生：同块裸 `typedef`、theory 层同写法 |
| 13 | 同一 locale 两个 record 后 `interpretation` | 无 `Duplicate fact declaration` | 成立 | 决定 14 | 孪生 `datatype` |
| 13b | `context monoid begin` 里 300 字段 record | `Locale.registrations_of` 给出的每个 theory 层前缀下 `<前缀>.p.select_convs` 可解析、规则同命题；重开与再 interpretation 无错、无重复警告 | 成立 | 决定 20、14 | 孪生 §7.5 (1) |
| 15 | 合并方向：`locale lb = … assumes "0 < k" begin typedef t; datatype d; record p` | record 之前块内 `d` 的 exhaust `nprems_of` 1、`Rep_t_inject` 0，theory 侧 2、1；record 之后四值不变、`Typedef.get_info` 对 `t` 长度 1、块内 `fun h where h (D n) = n` 成功 | 成立 | §3.10、§3.11（保留 context 条目） | 孪生：以 `datatype e` 代 record |
| 18 | `bundle b begin record … end`（18a）、`open_bundle`（18b）、调 `Local_Theory.define` 的替身插件（18c） | 按 §5.7 的表逐格；`unbundle` 在 theory 层与另一 locale 内各一次；变异：tag-only 列表换 `Thm.rule_attribute` 版到 `unbundle` 时失败 | record **成功**；表如 §5.7 | §5.7（rev5-C16、rev6-C6，作者按授权接受） | 孪生 `datatype` 报 `Not possible in bundle target`、裸 `typedef` 成功、mixfix 行孪生 `bundle b2 begin notation f … end` |
| 18d | `consts c0 :: "'a ⇒ nat"`；`overloading c0_nat ≡ "c0 :: nat ⇒ nat" begin record p = c0_nat :: nat … definition c0_nat where "c0_nat n = n" end` | 观测同 §5.4；字段 `c0_nat` 仍是普通选择子、`definition c0_nat` 仍被要求 | 成立 | §5.8 (24)(ii) overloading 半（用户已知晓） | 孪生同块 `datatype`，只作信息；评审新增 |
| 18e | `overloading` 里嵌套 `context fixes n :: nat assumes "0 < n" begin record p18 … end` | 8b 的观测量 | 成立 | 决定 21（instantiation/overloading 的嵌套层分属 (i)/(ii)） | 孪生列标 D3，不签；评审新增 |
| 18 | `experiment begin record … end` | 块内观测同 §5.2（含父行 `"nat p"`）；`Induct.dest_rules` 多一条匿名条目 | 成立 | §5.7、§5.8 (8) | 无 theory 层 `fun` 行（名字 concealed） |
| 20 | 四表规则的机械核查（定义层、外层、theory 层、重开、一次与两次 interpretation、`lemma (in -)`、diamond 导入、bundle、`open_bundle`、`context -`） | `length (Typedef.get_info ctxt T)`；`hd (find_casesT/find_inductT ctxt T)` 与 `Record.the_info` 的 `#cases`/`#induct` 按 `same_shape`；Ctr_Sugar exhaust 的 `nprems_of`；每选择子 Spec_Rules 头条的 `nprems_of` | 以 theory 层孪生 record 的值为预期；免检格：(2) `context -` 块内 `Spec_Rules.retrieve` 为空；(15) 嵌套 `assumes` 层的外层 Spec_Rules 头 `nprems_of` 1、重开块的头条件行在前；(19) 带 `assumes` 的 unnamed context 里 `global_interpretation` 之后 theory 头 `nprems_of` 1 | §1 放置原则、§5.8 | 孪生 theory 层 record；评审新增 |
| 21 | 事实别名 | 21a heavy locale 无 registration：theory 层 `thm p.select_convs`、`thm p.make_def` 报 Unknown fact；21b class：`p.select_convs` 与 `c_class.p.select_convs` 可解析；21c interpretation：只有 `I.p.select_convs` 可解析；21d light 重开块后短名可用 | 如左 | 决定 20 | 21a 孪生 `thm d.sel`；21b 无孪生；21c 孪生 `I.d.sel`；21d 孪生 light 块里的 datatype |
| 22 | `context - begin record p … end` | 块内 `Typedef.get_info` 长度 1、`ctr_sugar_of` 条目等于 `ctr_sugar_of_global`、simp、`proof (cases r)`、`fun g`、`Spec_Rules.retrieve` 为空；`end` 后 Spec_Rules 头等于孪生；判别 leaf（`local_setup ‹Local_Theory.background_theory (Record.add_record …)›`）simp、`cases` 失败、`Typedef.get_info` 为空 | 如左 | §5.8 (2)（用户 2026-10-14 接受缺口） | stock 对照报 `Bad context for command`；孪生 `context -` 里的 `datatype` |
| 23 | `local.foo` 打印：theory 上 unnamed context 里 `lemma foo: True ..` 然后 record；class 变体、无限定词 interpretation 变体、本 record 的 `p.simps` 变体、两个 record 的变体 | `Facts.extern` 对 `foo` 前后 | `foo` → `local.foo`（预测；若探针 (o) 显示前缀不出现，§5.8 (14) 删） | §5.8 (14)（决定 20 的 `transfer_facts`；rev6-C14 委托作者） | 孪生 `named_theorems` |
| 24 | import 行（复用第 20 行的 diamond） | cases、induct、`fun`、simproc、四表、`dest_rules` 按键的计数；父行 `"nat l.p"`、导入 theory 自己的 synonym、`"nat I.p"` | 与同样导入的 theory 层孪生相同、每键 1 | §1、决定 17、22 | 孪生：同样导入的 theory 层 record |
| 25 | 测试专用插件（两份日志） | Theory_Data 日志块内立刻可见；经 declaration 写的 Generic_Data 集合定义块内不可见、`end` 后/重开/interpretation 后/导入 theory 里可见；前缀是定义处的 naming、每 record 跑一次；theory 层、`context -`、locale、class、bundle 各一次 | 如左 | 决定 15、§5.8 (13) | 配 theory 层孪生 |
| 26 | 畸形的字段 mixfix（binder 形式），theory 层与块内 | 报错文案与 stock theory 层相同（探针 (c) 定文案）；块内 `const_lines` 与 theory 层孪生逐条相同 | 如左 | 决定 16 (i) | 孪生 theory 层 |

## B. §7.4 light 块（里程碑 3 的 gate）

| 行 | 场景 | 观测量 | 预期 | 依据 | 孪生 / 理由 |
| --- | --- | --- | --- | --- | --- |
| L1 | `light_locale LF = fixes S :: "nat set" assumes "finite S" begin record 'a p = x :: 'a  y :: nat end`，块内 | 第 1 行全部；块内 `p.cases` 等的 `Thm.get_tags` 等于孪生——无 K tag | 成立 | 决定 2(b)、17 | 孪生 light datatype |
| L2 | `end` 后 | `LF.p.simps` 带 `LF ?S ⟹`、`exported_premises` 1、`[simp]` 保留；`LF.p.cases` 等带 `consumes "1"` 与 `exported_premises` tag；`Record.get_info` 的定理 `nprems_of` 与 stock 相同、hyps 空 | 成立 | light 决定 9 (i)、决定 4 | 孪生 light datatype |
| L3 | `end` 后 theory 层 | simproc（`LF.x (r⦇LF.x := a⦈) = a`、`r⦇LF.x := a, LF.x := b⦈ = r⦇LF.x := b⦈` by simp）、`value`、`fun`、子 record 成功；`length (Spec_Rules.retrieve_global …)` 对每个选择子 1 且头 `nprems_of` 0 | 成立 | 决定 3、15、§5.8 (6) | 比 light 块里的 `datatype` 强（无孪生） |
| L4 | `end` 后 theory 层 | `Induct.find_casesT` 对 record 类型的头是无 tag 的无条件规则（`nprems_of` 1）、`cases r` 不链 `LF_axioms` 给出 `fields`、`using LF_axioms proof (cases r)` 成功且 `LF S` 为未用前提、`rule: LF.p.cases` 链 `LF_axioms` 到 K tag 副本 | 成立 | 决定 17、§5.6 | 孪生 light datatype：裸 `cases t` 错位、`using LF_axioms` 成功 |
| L5 | 父行 | 块内 `"nat p"`、重开块、`interpretation I: LF {1}` 后 `"nat I.p"`、`lemma (in LF)` 里（`p.simps` Unknown、`LF.p.simps` 可用） | 成立 | 决定 22、§5.8 (18) | 孪生：写 record 名 |
| L6 | `interpretation I: LF {1}` | `thm I.p.select_convs` 等于 `LF.p.select_convs`、`term I.x`、`typ "nat I.p"`、`thm I.p.simps` 报 Unknown fact | 成立 | 决定 20、§5.8 (18) | 孪生 light datatype |
| L7 | 重开块（无 solver） | 别名、字段 mixfix、simproc（同两条引理，写 `x`）、`fun` 用 record 模式、`cases r` 经 theory 的无条件规则、`thm p.simps` 报 Unknown fact、`thm LF.p.simps` 可用 | 成立 | 决定 20、17、§5.8 (18) 第二部分（待用户知晓） | 孪生：同块 `datatype d` 重开后 `d.simps` Unknown、`LF.d.simps` 可用 |
| L8 | 重开块（有 solver，light 里程碑 3 后） | `LF ?S` 形式的 simps 可 simp | 成立 | light 里程碑 3 | 孪生 light datatype |
| L9 | 无谓词的 `light_locale LG` | 处处无条件、`Induct.dest_rules` 条目数 1 | 成立 | 决定 17 | 孪生 light datatype |
| L10 | 嵌套层 `light_locale LN … context fixes n :: nat assumes "0 < n" begin record pn … end … end` | theory 层对 recT、rec_schemeT 与 `nat` 键的整张列表：头无条件、`count_of = 0`、`nat` 键干净 | 成立 | 决定 17、rev6-C16 | 孪生 light datatype |

## C. §7.2 theory 层回归里的新接受输入（`Localized_Record_Theory_Test`，里程碑 1）

| 行 | 场景 | 观测量 | 预期 | 依据 | 孪生 / 理由 |
| --- | --- | --- | --- | --- | --- |
| T1 | 每个新接受的父形式一个叶（forms table 第 21-29 行：`q1`、`q4`、`"bool q2"`、`"(bool, nat) q3"`、`"nat p tv"`、`"'x qd"`、`"nat q8"`、`"(nat, unit) p_scheme"`、`"(nat, (bool, unit) c_ext) p_scheme"`、`"(nat, unit) p_ext"`、`"⦇x :: nat⦈"`、`"(| x :: nat |)"`、`"⦇x :: nat, z :: bool⦈"`、`"⦇x :: nat, … :: unit⦈"`） | 子 record 与按 record 名写全参数的孪生：`Record.get_info` 的 parent 相等（名字按孪生）、`get_recT_fields` 相等、`print_record` 的父行相等、args 与 sort 相同；`declare_typ` 行给 `'c::order` | 相等 | 决定 22（规则与新接受输入用户 2026-10-17 接受） | 孪生：写 record 名的同一行 |
| T2 | 文案变化类各一个叶（forms 第 30-35 行：`"t q8"` 与 `bad` 报 `Ill-sorted instantiation of 'a in parent record "T.s"`；父为 synonym 加重复字段、`more` 字段、多余类型变量、重复 record 名、`definition` 内错） | `Toplevel.command_errors` 去 markup 后与孪生文案相同 | 相同 | 决定 22 文案变化类（用户 2026-10-17 接受） | 孪生 `"t s"` 等 |
| T3 | typed API 叶 `Parent_Forms_Typed_API.thy`（只在 port 上跑） | `Record.add_record … (SOME ([], "T.q1"))` 与 `local_add_record` | 仍报 `Unknown parent record "T.q1"` | 决定 6、22 | 无孪生（typed API 不解析） |
| T4 | 变异（stock 副本上构建本 session，排除 typed API 叶） | fixture 叶通过；每个正叶以 `Unknown parent record "Parent_Forms_Fixture.<head>"` 失败；每个文案变化叶在断言处失败 | 如左 | §7.2 | stock 就是去掉解析器的实现 |
| T5 | 决定 11 的一行：theory 层 `declare [[typedef_overloaded]]` 后不带 `(overloaded)` 的 `record 'a::zero r = f :: "'a nz"` | 成功 | 成立 | 决定 11 | stock 同 |

## D. §7.1 golden 里的父 record 行（文案预期，探针 P3 定稿）

拒绝行的预期文案（forms table 第 9-20 行）：`n`/`nat`/`"nat list"`/`"nat ⇒ nat"`/`"nat p list"`/`qn`/`"nat tv"` →
`Unknown parent record "T.n"`/`"Nat.nat"`/`"List.list"`/`"fun"`/`"List.list"`/`"T.qn"`/`"T.tv"`；两种 `p_scheme` 与 `"'z qs"` →
`"T.p_scheme"`/`"T.qs"`；`"(nat, bool) p_ext"` 与 `"⦇x :: nat, … :: 'z⦈"` → `"T.p.p_ext"`；`"nat p foo_ext"` → `"T.foo_ext"`；
`qph` → `"T.qph"`；`logic` → `"logic"`；`"logic q9"` → `Illegal occurrence of syntactic type: "logic"` 加 `The error(s) above
occurred in parent record specification` 加第二行；`qsyn` → `"T.qsyn"`；`"t s"` → `Ill-sorted instantiation of 'a in parent
record "T.s"`；缺参数的 `p` → `Bad number of arguments for type constructor: "T.p"`（一行）；`"'a"` → `Bad parent record
specification: 'a`；`"?'x p"` → `Illegal schematic type variable: ?'x`。接受行：`"(nat, bool) ph"`（父 `([nat, bool], T.ph)`）、
`record 'c d = "('c::order, nat) ph" + y :: 'c`（`'c::order`）、`"n p"`。每条都带第二行 `Failed to define record "d"`（读取
之后抛的错误）。依据决定 22；孪生是写 record 名的同一行。

## 其余行

§7.3 第 11、14、16、17、19、27 行与 §7.1 的其余 golden 行、§7.2 的发行版 session 构建与 golden 字节相同、§7.5 的 gate，
预期都是"与孪生相同"或"与 stock 字节相同"，一句批量签。
