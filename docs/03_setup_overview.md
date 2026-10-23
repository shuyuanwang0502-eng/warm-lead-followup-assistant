# 安装与使用概要

这个仓库里没有能直接安装的 Skills 和知识库。下面是我整理的交付包的安装流程概要，原版是给客户顾问用的德语指南。

## 前提条件

- Claude 桌面版 App（Windows 或 macOS），账号可使用 Skills、Projects 和 Scheduled Tasks。
- 定时任务需要电脑开机、未休眠且 App 打开；否则当次运行会跳过，可手动 “Run now”。
- 测试模式：只读本地测试文件夹；真实模式需配置 CRM（Pipedrive）和 Microsoft 365 连接器。

## 交付包结构

```
1_skills/            10 个 Skill（zip，直接上传）
2_folders/           工作文件夹：材料库工作簿、知识库 K1/K2/K3、8 个测试线索
3_scheduled_tasks/   4 个定时任务模板（每日提醒、每周简报、月度雷达、材料库同步）
4_extras/            雷达看板页面备份
Setup Guide (PDF)    10 页德语图文指南
CLAUDE_SETUP_INSTRUCTIONS.md  供 Claude 读取并代为执行安装的说明
```

## 安装步骤（约 30–45 分钟）

| # | 步骤 | 谁来做 |
|---|---|---|
| 1 | 安装 Claude 桌面版并解压交付包 | 用户 |
| 2 | 把工作文件夹复制到“文稿/Documents” | Claude 可代做 |
| 3 | 上传 10 个 Skills（Customize › Skills › Upload） | Claude 可代做（用户确认） |
| 4 | 新建 Project | 用户 |
| 5 | 把 K1/K2/K3 上传到 Project Context | 用户 |
| 6 | 创建 3 个定时任务：每日提醒（工作日 06:54）、每周简报（周一 07:19）、月度雷达（每月 1 日 07:56）；材料库同步等 OneDrive 接入后再建 | Claude 可代做（用户确认） |
| 7 | 逐个 “Run now” 测试 | 用户 |

也可以走捷径：在桌面 App 里开一个新对话，附上安装包，说一句“按这个包安装”。Claude 会读 `CLAUDE_SETUP_INSTRUCTIONS.md`，替你完成第 2、3、6 步。第 4、5 步还是要自己动手。这份说明是我写的，目的是让不懂技术的顾问也能装好。

## 日常使用

- 看单个线索：在 Project 里新开一个对话，贴上或附上线索档案和互动记录。
- 每日和每周的看板会自动生成，也可以直接问“今天要处理什么？”或者“生成本周简报”。
- 邮件草稿要顾问自己看过之后再发。
