# 示例：线索输入格式（示例版）

> **示例版，不是真实数据，也不是测试原件。** 展示测试模式下“一个线索一个文件”的格式。真实部署时同样的信息来自 CRM 的只读导出。

```
TEST DATA – simulated CRM record (not real customer data)

Lead_DEMO (synthetic)

Profile
- lead_id: Lead_DEMO
- job_title / role: Head of HR
- organization: Company_DEMO
- lead_owner: Consultant_X
- language / address form: German, Sie
- lead_source: Webinar "[topic]" (DD.MM.YYYY)
- lead / deal status: Lead (no deal)

Activities, emails and notes
(date | type | channel | direction | topic | summary | outcome)
- DD.MM.YYYY | Webinar | Video call | Lead → Company | [topic] | Attended the webinar. | Attended
- DD.MM.YYYY | Personal email | Email | Company → Lead | [topic] | Thanks; offers the handout on reply. | No response
- DD.MM.YYYY | Newsletter | Campaign | Company → Lead | – | Monthly newsletter. | Opened 1x; every link clicked once within 1 minute
```

文件夹中另有一个 `INDEX` 文件列出全部线索文件和数据截止日期；定时任务每次运行都重新读取全部文件。

注意最后一行：所有链接在 1 分钟内各点一次，是典型的邮件安全扫描器行为，`lead-analysis` 会把它判为自动点击，不算兴趣信号。
