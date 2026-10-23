# 例子：线索来问工作坊的价格（Lead_T04）

Lead_T04 是我们团队自己编的测试线索，不是真实客户。我隐去了客户名和材料名（用 `[…]` 表示），其他记录没有改。下面的输出摘自 2026 年 10 月 19 日每周简报和每日提醒在测试数据上的实际运行结果，德语原文后面附了我的中文翻译。整理作品集时没有重新运行。

## 输入

线索档案：

| 字段 | 内容 |
|---|---|
| lead_id | Lead_T04（编的） |
| 职位 | Owner，企业主 |
| 公司 | Company_T4 |
| 负责顾问 | Consultant_A |
| 语言和称呼 | 德语，Sie |
| 来源 | 2026 年 9 月下载了自测问卷 `[问卷名已隐去]` |
| 状态 | 线索，还没有商机 |

互动记录（数据截至 2026-10-14，运行日期是 10-19）：

| 日期 | 类型 | 谁联系谁 | 内容 | 结果 |
|---|---|---|---|---|
| 15.09.2026 | 自测问卷 | 线索联系客户 | 下载了问卷，主题是管理者的心理负担和责任 | 完成 |
| 16.09.2026 | 第一封邮件 | 客户联系线索 | 讲为什么做这份问卷，问了一个开放问题 | 没回 |
| 22.09.2026 | 跟进 | 客户联系线索 | 换了一个角度：把“一起想”这件事也交给团队 | 没回 |
| 02.10.2026 | 跟进 | 客户联系线索 | 分享了一个实用的思路 | 回复了 |
| 13.10.2026 | 回复 | 线索联系客户 | „Spannend. Was würde ein halbtägiger Workshop für mein Führungsteam (6 Personen) ungefähr kosten?“ | 问价格 |

另外还用到了三份知识库文件，参考日期是 2026-10-19。

## 它是怎么判断的

这一段是我按 Skills 的规则解释结论是怎么来的。运行时的中间分析没有保存全文，以下一节的实际输出为准。

1. lead-analysis：线索 13 号主动来问价格，兴趣很明确，处在评估阶段，主题是领导力。客户的痛点还看不出来，下载的问卷主题不能直接当成痛点。13 号之后没有任何顾问回复的记录。
2. next-action：命中“线索回复后，一个工作日内要回应”这条规则，目标日期是 14 号，已经过了。但数据只到 14 号，看不出顾问到底回没回，所以状态是“过期，未确认，先核实”。
3. pipeline-triage：优先级 A。
4. content-matching：现在要做的是确认或回复询价，不该附推广材料。材料库里有一份带价格的方案模板，形式上标的是可发送，但条目里写明它是内部报价用的，所以只放进“内部参考”，并注明不能外发。没有能对外发的工作坊介绍，所以记一条内容需求，结果为 none。
5. followup-email：规则要求草稿里不写金额，也不做承诺。草稿放在折叠的标签页里，这次的截图没有保存全文。

## 实际输出

每周简报里的卡片（原文）：

> Lead_T04 · Consultant_A · Priorität A · Überfällig: unbestätigt · warm
> Evaluation · Lead fragte am 13.10. nach den Kosten eines halbtägigen Workshops für 6 Führungskräfte · keine `[客户]`-Antwort protokolliert
> Zieldatum 14.10.2026 · `[客户]`-gestützte Regel (Antwort innerhalb 1 Arbeitstag, K2 Regel 1). Zieldatum verstrichen.
> Erst prüfen: Wurde die Preisanfrage vom 13.10. beantwortet? Falls nicht, jetzt ohne Betrag antworten; der Betrag wird mit `[客户]` geklärt und ein kurzes Klärungsgespräch vorgeschlagen.
> Danach (bedingt, nicht gezählt): Nach der Antwort: Klärungsgespräch, dann Angebot nur mit `[客户]`-freigegebenem Preis.

中文意思：

- 优先级 A，过了期限但未确认，暖线索。
- 线索 13 号问了 6 人管理团队半天工作坊的价格，记录里没有公司的回复。
- 依据是规则 1：一个工作日内回复，目标日期 14 号已经过了。
- 先确认 13 号的询价有没有回过。如果没有，现在回，但不写金额。金额由顾问和公司商量，再约一次简短的电话。
- 之后的步骤只作为备注，不算进当前待办：通话之后，再给一份价格经过公司批准的方案。

同一天的每日提醒（原文）：

> Prüfen, ob die Preisanfrage vom 13.10. schon beantwortet wurde; falls nicht, Antwort vorbereiten. Den Preis klärt der Berater mit `[客户]`, nicht der Assistent.

意思是：先确认询价有没有回；没回的话准备回复。价格由顾问和公司确定，不由助手给出。

周报里记下的内容需求（原文）：

| lead_ref | stage | main_topic | pain_point | matched_ids | result | gap_note |
|---|---|---|---|---|---|---|
| Lead_T04 | Evaluation | Leadership & Self-Leadership | (empty) | — | none | No sendable workshop description or format overview for a lead asking about a half-day leadership-team workshop and its cost. |

周报的“数据缺口和材料冲突”一节里也提到了那份方案模板：它在材料库里标的是可发送，但条目写明用于内部报价、含费用信息，所以只作为内部参考，材料库里的状态没有改。

## 我想用这个例子说明的

价格这种事，助手不替人做决定。数据有延迟时，它先让人核实，不会默认顾问没回。形式上能发的材料，如果其实是内部用的，它也不会推给客户。没有合适的材料时，它会记下来，月底汇总，客户就知道该补什么内容。还有，同一个线索在日报和周报里得到的结论是一样的。
