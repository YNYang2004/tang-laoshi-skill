# 唐老师讲电赛 · 思维操作系统

Claude Skill 是一个包含 `SKILL.md` 指令文件的文件夹，AI Agent 会在相关任务时自动加载它。本 Skill 蒸馏了唐老师讲电赛（长江大学唐老师）的思维框架与表达风格，让 AI 以唐老师的视角为电路设计、PCB layout、电源方案与元器件选型提供实战化硬件工程建议。

> **免责声明**：本 Skill 基于公开信息提炼，仅供学习和参考。Skill 中的观点与表达为框架推断，非唐老师本人立场。使用本 Skill 进行的电路设计决策请以 datasheet 和实际测试为准。

---

## ✨ 功能特性

- **🧠 5 个核心心智模型** — 实践先行、datasheet 权威、PCB layout 决定成败、真题反推、国产替代
- **🔧 8 条决策启发式** — 从芯片选型到 PCB 布线到电赛备赛，覆盖硬件工程全链路
- **🎭 完整表达 DNA** — 短句、冷幽默、参数驱动，还原唐老师的教学风格
- **📡 Agentic Protocol** — 需要事实支撑时先检索 datasheet 再回答，不凭记忆编造参数
- **⚠️ 诚实边界** — 明确标注局限性与推断内容，区分"本人原话"与"框架推断"

> 完整的心智模型（含证据与应用场景）、决策启发式、表达 DNA 与回答工作流详见 [SKILL.md](SKILL.md)。

## 📖 唐老师是谁

> "高校教师一枚，20 年的高校教学、科研与电赛指导经验，26 年的项目开发与测井仪器研发，助你快速掌握电子设计的方方面面。"

- **长江大学电子信息学院** 教师
- 教学方向：开关电源、运放选型、PCB layout、DCDC 设计、数控电源
- 开源项目：1200W 数控电源（EG1163S + STM32F103）等，全部开源原理图与 PCB
- 擅长领域：电源设计实战、EMI/EMC、国产芯片替代、电赛猜题与备赛

## 🚀 快速开始

### 文件依赖说明

本 Skill 运行时**必须**的文件：

| 文件/目录 | 是否必须 | 作用 |
|-----------|---------|------|
| `SKILL.md` | **必须** | 核心指令——心智模型、决策启发式、表达DNA、回答工作流 |
| `references/research/` | **建议保留** | 6份调研底稿（134个来源），Agent 在需要验证立场、深挖证据时回溯查阅 |
| `scripts/` | 不需要 | 构建时工具脚本，运行时不使用 |

> **最小安装**：只放 `SKILL.md` 也能工作——核心框架已蒸馏完毕，Agent 的回答工作流以实时搜索（datasheet、电赛真题）为主，而非依赖本地调研文件。保留 `references/research/` 可以让 Agent 在不确定时回溯原始证据，提升回答可信度。

---

### 多平台支持

| 工具 | 安装路径 | 说明 |
|---|---|---|
| **Claude Desktop** | `.claude/skills/tang-laoshi-perspective/` | 自动扫描 SKILL.md，无需额外配置 |
| **Claude Code** | `.claude/skills/` 或项目内任意位置 | 自动激活；或 `/plugin install` |
| **Cursor** | 项目根目录 + `.cursorrules` 引用 | 将文件夹放项目下，在 `.cursorrules` 中添加 SKILL.md 路径 |
| **Codex** | `.codex/skills/` | `npx agent-skills-cli add` 或直接复制 |
| **Windsurf** | `.windsurf/skills/` 或项目内 | 整目录放项目下，在 CAS 设置中引用 SKILL.md |

### 安装方式

#### 方法一：给 Agent 一个链接，自动安装（推荐）

直接将此仓库的 URL 发给 AI Agent，让它自行克隆整个目录（含 SKILL.md + 调研资料）：

- **GitHub/Gitee 仓库链接**：告诉 Agent 仓库地址（如 `https://github.com/YNYang2004/tang-laoshi-skill`），Agent 会克隆仓库、读取 `SKILL.md` 并加载到上下文中。整目录克隆后，Agent 还能访问 `references/research/` 中的调研底稿。
- **单文件链接**：直接分享 `SKILL.md` 的 raw 链接（如 GitHub Raw 地址），Agent 会下载并安装为 Skill。这种方式只安装核心指令，不含调研资料——够用，但 Agent 无法回溯原始证据。
- **Claude Desktop**：将仓库路径配置到 `.claude/skills/` 目录（整个文件夹，含 SKILL.md 和 references/），Claude Desktop 会自动识别并注册。

> 💡 **示例对话**：「帮我安装这个 Skill：https://github.com/YNYang2004/tang-laoshi-skill 」— Agent 会自动完成克隆、读取和配置。

#### 方法二：手动克隆/下载，在 Agent 中配置

1. **克隆或下载仓库**
   ```bash
   git clone https://github.com/YNYang2004/tang-laoshi-skill.git
   cd tang-laoshi-skill
   ```
   或从 GitHub/Gitee 直接下载 ZIP 包并解压。

2. **将 Skill 配置到 AI 工具**

   **完整目录方式（推荐，保留调研资料回溯能力）**：将整个 `tang-laoshi-skill/` 文件夹放到 AI 工具可访问的位置，让 Agent 通过文件路径读取 SKILL.md 和 references/。
   - **Claude Desktop**：复制到 `.claude/skills/tang-laoshi-perspective/` 目录。Claude Desktop 自动扫描此目录下的 SKILL.md。
   - **Claude Code**：在项目根目录保留整个文件夹，Agent 可直接读取 `./tang-laoshi-skill/SKILL.md` 和 `./tang-laoshi-skill/references/`。
   - **Cursor**：将整个文件夹放在项目根目录下，在 `.cursorrules` 中添加「遇到问题时可参考 `tang-laoshi-skill/SKILL.md` 中的思维框架，`tang-laoshi-skill/references/research/` 中有调研底稿」。
   - **Windsurf**：类似 Cursor，整目录放项目下，在 CAS 设置中引用 SKILL.md 路径。

   **单文件方式（最小安装，仅核心指令）**：如果只需要核心框架、不需要调研回溯，可将 SKILL.md 内容嵌入到工具的规则文件中。
   - **Cursor / Windsurf**：将 `SKILL.md` 全部内容追加到 `.cursorrules` / `.windsurfrules`。
   - **通用方式**：在系统提示词（system prompt）中直接追加 `SKILL.md` 全部内容。


### 触发关键词

在对话中使用以下关键词即可激活唐老师模式：

- `用唐老师的视角...`
- `唐老师会怎么看...`
- `唐老师讲电赛模式`

**退出角色**：说 `退出`、`切回正常`、`不用扮演了` 即可恢复正常模式。

## 📂 项目结构

```
├── SKILL.md                      # Skill 主文件（核心内容）
├── README.md                     # 本文件
├── references/
│   ├── research/                 # 深度调研文件（6 份，134 个来源）
│   │   ├── 01-writings.md        # 文字作品分析
│   │   ├── 02-conversations.md   # 对话互动分析
│   │   ├── 03-expression-dna.md  # 表达 DNA 分析
│   │   ├── 04-external-views.md  # 外部评价分析
│   │   ├── 05-decisions.md       # 决策模式分析
│   │   ├── 06-timeline.md        # 人物时间线
│   │   └── 07-quality-validation.md  # 质量验证报告
│   ├── extraction-framework.md   # 知识提取框架（构建时参考，可选）
│   ├── fidelity-scorecard.md     # 忠实度评分表（构建时参考，可选）
│   └── skill-template.md         # Skill 模板说明（构建时参考，可选）
└── scripts/                      # 工具脚本（构建时工具，运行时不使用）
    ├── download_subtitles.sh     # 字幕下载
    ├── merge_research.py         # 调研数据合并
    ├── quality_check.py          # 质量检查
    └── srt_to_transcript.py      # SRT 转文本
```

## ⚠️ 诚实边界

此 Skill 基于公开信息提炼，存在以下局限：

- 视频内容未完整观看，基于标题、简介和他人笔记反推
- B 站评论区互动不可见，回答追问方式为推测
- 军事电子拆解领域深度有限，置信度低于电赛教学领域
- 测井仪器研发方向未覆盖
- 心智模型从行为模式反推，非本人原话总结
- 调研截止时间：2026-08-12

> 完整的局限性分析、内在张力与矛盾详见 [SKILL.md — 诚实边界](SKILL.md#诚实边界)。

## 📚 调研来源

调研基于 **134 个独立来源**，详见 `references/research/` 目录。

**一手来源**：
- [B 站主页](https://space.bilibili.com/28143041) — 1700+ 视频
- [头条号](https://www.dongchedi.com/user/3749812677116039) — 军事拆解、新能源汽车电子
- [长江大学官网](https://faculty.yangtzeu.edu.cn/tangtaobo/zh_CN/index.htm) — 身份确认
- [超星学习通](https://mooc1.chaoxing.com/course/244648946.html) — 立创 EDA 正式课程

**二手来源**：
- CSDN 学习笔记、EET-China 论坛、EEWorld 论坛、立创开源平台等

## 📝 许可

MIT License — 详见 [LICENSE](LICENSE)

## 🔗 相关链接

- 唐老师 B 站主页：<https://space.bilibili.com/28143041>
- 唐老师 Youtube 主页：<https://www.youtube.com/@%E5%94%90%E8%80%81%E5%B8%88%E8%AE%B2%E7%94%B5%E8%B5%9B>