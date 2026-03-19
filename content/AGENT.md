# AGENT.md

## 仓库概述

这是一个 Obsidian 知识库，用于记录 ICT (Inner Circle Trader) 交易方法论的学习笔记。目标是兼顾系统学习和实战交易参考。

## 内容来源

`videos/` 目录下存放两套课程的视频及处理数据：

- `videos/ICT Mentorship 2016/` ICT 2016
- `videos/2017 ICT Private Mentorship Core Content/` ICT 2017

每个课程文件夹包含：

- `chapters.txt` — 中文章节标题（带时间戳）
- `*_synthesized.srt` — 中文字幕
- `result.json` — 完整翻译处理数据
- `*_synthesized.mp4` — 中文配音视频

## 文件夹结构

```
00-MOC/          → 索引/地图文件
01-课程笔记/      → 按视频合集组织的课程笔记
  ├── ICT Mentorship 2016/
  └── 2017 ICT Core Content/
02-概念/          → ICT 概念页面（由 wikilink 自然创建，不预设）
03-模型/          → 交易模型/策略页面（由 wikilink 自然创建，不预设）
templates/       → Obsidian 模板
videos/          → 视频资源（不在笔记体系内）
```

## 核心约定

### 概念自下而上生长

- **禁止**预设概念列表或概念间关系
- **禁止**用 AI 凭空生成概念定义、层级结构或关联关系
- 概念页面只能在用户做课程笔记时通过 wikilink 自然产生
- 所有笔记内容由用户通过提示填写，AI 只负责结构性辅助

### 术语规范

- 中英结合：`EnglishTerm 中文`（如 `OrderBlock 订单块`、`FairValueGap 公允价值缺口`）
- 文件名和 wikilink 都使用此格式
- aliases 中可以分别放纯英文和纯中文便于搜索

### 文件命名

- 2016 课程笔记：`M{月}-{序号} {中文标题}.md`（如 `M1-01 交易设置的要素.md`）
- 2017 课程笔记：`{序号} {中文标题}.md`（如 `01 季度转换与IPDA数据区间.md`）
- 概念/模型页面：`EnglishTerm 中文.md`（如 `OrderBlock 订单块.md`）

### 模板

`templates/` 下有三个模板：

- `课程笔记模板.md` — frontmatter 含合集、月份、课序、视频路径、tags
- `概念笔记模板.md` — frontmatter 含 aliases、tags
- `模型笔记模板.md` — frontmatter 含 aliases、tags，包括构成要素和执行步骤

### 语言

- 笔记内容使用中文
- ICT 专有术语使用中英结合格式
- 主动读取可能的字幕
- 积极使用Mermaid画图，并且Mermaid图只能从上往下画

## 工具能力

### 视频截图

可以使用 `ffmpeg` 从课程视频中截取关键画面，嵌入到笔记中作为图解。

用法示例：

```bash
ffmpeg -ss 00:12:34 -i "videos/ICT Mentorship 2016/Month1 01 .../xxx.mp4" -frames:v 1 -q:v 2 "attachments/M1-01_截图说明.jpg"
```

- 截图存放到 `attachments/` 文件夹
- 文件名建议：`{课程编号}_{内容描述}.jpg`
- 在笔记中用 `![[M1-01_截图说明.jpg]]` 嵌入

**截图应主动、积极地执行，不需要等用户逐一要求：**

- 写笔记时，每个章节/知识点都应主动从视频中截取至少一张关键帧
- 当字幕或笔记内容涉及图表、K线图、示意图、价格走势等视觉内容时，必须主动截图
- AI 应根据字幕中的时间戳和上下文，自行判断最佳截图时机，主动执行 ffmpeg 命令
- 截图是笔记的标准组成部分，而不是可选的附加操作

## AI 行为准则

1. **不编造内容** — 不从字幕中自动生成笔记内容，不猜测概念定义
2. **不预设结构** — 不批量创建占位笔记，不预设概念网络
3. **尊重来源** — 如需引用课程内容，必须基于 `chapters.txt` 或 `.srt` 文件中的实际文本
4. **辅助为主** — 帮助用户管理结构、创建文件、查找信息，但内容决策权在用户
