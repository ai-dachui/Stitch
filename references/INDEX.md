# LLM Wiki 参考资料索引

> 下载日期：2026-04-20
> 用途：构建个人知识库系统（第二大脑）的参考实现和设计灵感
> 统计：21 个项目，103 个文件，1.4MB

---

## karpathy-llm-wiki.md

- **来源**: [Karpathy Gist](https://gist.github.com/karpathy/442a6bf555914893e9891c11519de94f)
- **作用**: 一切的起点。Andrej Karpathy 定义的 LLM Wiki 模式原始规范
- **核心内容**: 三层架构（Raw Sources → Wiki → Schema）、三个操作（Ingest/Query/Lint）、index.md + log.md 设计
- **参考要点**: 作为设计原则的北极星，所有实现都基于此

---

## obsidian-skills/ (kepano/obsidian-skills ⭐25,404)

- **来源**: https://github.com/kepano/obsidian-skills
- **作用**: Obsidian CEO 出品，教 AI Agent 原生操作 Obsidian 的 skill 规范
- **参考要点**: skill 定义格式、wikilinks 语法规范、CLI 集成方式

| 文件 | 说明 |
|------|------|
| README.md | 项目总览和安装说明 |
| obsidian-markdown.md | Obsidian Flavored Markdown 语法规范（wikilinks、embeds、callouts、frontmatter） |
| obsidian-bases.md | Obsidian Bases 数据库视图（.base 文件的 YAML schema、过滤器、公式） |
| json-canvas.md | JSON Canvas 规范（节点、边、布局，用于可视化知识图谱） |
| obsidian-cli.md | Obsidian CLI 操作（读写笔记、搜索、插件开发调试） |
| defuddle.md | 网页内容提取工具（去除导航/广告，转为干净 markdown） |

---

## compound-engineering/ (EveryInc/compound-engineering-plugin ⭐14,834)

- **来源**: https://github.com/EveryInc/compound-engineering-plugin
- **作用**: "复利工程"理念 — 工程知识应像复利一样持续积累。完整的 Brainstorm→Plan→Work→Review→Compound 工作流
- **参考要点**: plugin 架构设计、多平台适配、learnings 积累机制、agent/skill 定义规范

| 文件 | 说明 |
|------|------|
| README.md | 项目说明、安装方式、工作流概览 |
| AGENTS.md | 50+ agent 定义和开发规范（含 skill 合规检查清单，非常详尽） |
| CLAUDE.md | 仅一行指针 `@AGENTS.md` |
| skills/ce-brainstorm.md | 头脑风暴 skill — 在编码前探索需求和方案 |
| skills/ce-plan.md | 规划 skill — 将想法转为技术实施计划 |
| skills/ce-work.md | 执行 skill — 按计划系统性完成工作 |
| skills/ce-compound.md | 复利 skill — 将解决的问题文档化为可复用知识 |
| skills/ce-compound-refresh.md | 复利刷新 — 更新已有的 learnings |
| skills/ce-code-review.md | 代码审查 skill — 多 agent 协作审查 |
| skills/ce-ideate.md | 构思 skill — 发现高影响力改进点 |
| skills/ce-debug.md | 调试 skill — 系统化调试流程 |

---

## second-brain/ (NicholasSpisak/second-brain ⭐190)

- **来源**: https://github.com/NicholasSpisak/second-brain
- **作用**: 最开箱即用的 LLM Wiki 实现，4 个 skill 覆盖完整工作流
- **参考要点**: wiki-schema 设计（最有价值）、ingest/query/lint 三个 skill 的 prompt 设计

| 文件 | 说明 |
|------|------|
| README.md | 项目说明、目录结构、安装方式 |
| wiki-schema.md | Wiki Schema 规范 — 定义 wiki 的组织规则（页面类型、frontmatter、命名约定） |
| llm-wiki-reference.md | Karpathy 原始规范的项目内副本 |
| skills/second-brain-setup.md | 初始化向导 — 创建目录结构和配置 |
| skills/second-brain-ingest.md | 消化 skill — 处理 raw/ 中的素材，生成 wiki 页面 |
| skills/second-brain-query.md | 查询 skill — 基于 wiki 回答问题 |
| skills/second-brain-lint.md | 健康检查 skill — 发现断链、孤页、矛盾、知识空白 |

---

## qmd/ (tobi/qmd ⭐22,462)

- **来源**: https://github.com/tobi/qmd
- **作用**: Shopify CEO 出品的本地 Markdown 搜索引擎，Karpathy 推荐
- **参考要点**: 混合搜索架构（BM25 + 向量 + LLM 重排序）、MCP Server 实现、smart chunking 策略

| 文件 | 说明 |
|------|------|
| README.md | 完整架构说明、搜索管线设计、安装和使用方法 |

---

## understand-anything/ (Lum1104/Understand-Anything ⭐8,578)

- **来源**: https://github.com/Lum1104/Understand-Anything
- **作用**: 知识图谱可视化，支持代码库 + 知识库，10+ 输出平台
- **参考要点**: 知识图谱生成和可视化方案

| 文件 | 说明 |
|------|------|
| README.md | 项目说明、支持平台、使用方式 |
| CLAUDE.md | Agent 配置 |

---

## nashsu-llm-wiki/ (nashsu/llm_wiki ⭐1,382)

- **来源**: https://github.com/nashsu/llm_wiki
- **作用**: 跨平台桌面应用（Tauri），两步链式思考 + 4 信号知识图谱 + Louvain 社区检测 + Deep Research
- **参考要点**: 两步链式思考实现、知识图谱算法、Chrome Web Clipper 集成

| 文件 | 说明 |
|------|------|
| README.md | 英文项目说明 |
| README_CN.md | 中文项目说明 |
| llm-wiki.md | 内嵌的 Karpathy 规范副本 |

---

## claude-obsidian/ (AgriciDaniel/claude-obsidian ⭐1,299)

- **来源**: https://github.com/AgriciDaniel/claude-obsidian
- **作用**: Claude + Obsidian 知识伴侣，/wiki /save 命令
- **参考要点**: Claude 与 Obsidian 集成的 skill 设计

| 文件 | 说明 |
|------|------|
| README.md | 项目说明和使用方式 |
| CLAUDE.md | Agent 配置 |
| wiki-skill.md | Wiki 操作 skill 定义 |
| save-skill.md | 保存操作 skill 定义 |

---

## llm-wiki-skill/ (cosen1024/llm-wiki-skill ⭐731)

- **来源**: https://github.com/cosen1024/llm-wiki-skill
- **作用**: 中文项目！多平台 Skill，自动提取网页/X/微信公众号/YouTube/知乎/小红书，置信度标注 + 两步链式思考 + 增量缓存
- **参考要点**: 中文生态适配、置信度标注实现、多来源自动提取

| 文件 | 说明 |
|------|------|
| README.md | 项目说明、功能特性、支持平台 |
| llm-wiki-skill.md | 核心 skill 定义（置信度标注、两步链式思考的完整 prompt） |

---

## llm-wiki-compiler/ (ussumant/llm-wiki-compiler ⭐471)

- **来源**: https://github.com/ussumant/llm-wiki-compiler
- **参考要点**: 编译器式的 Wiki 构建方案

| 文件 | 说明 |
|------|------|
| README.md | 项目说明和架构设计 |

---

## llmwiki/ (lucasastorian/llmwiki ⭐401)

- **来源**: https://github.com/lucasastorian/llmwiki
- **参考要点**: 另一种 LLM Wiki 实现思路

| 文件 | 说明 |
|------|------|
| README.md | 项目说明 |

---

## obsidian-wiki/ (Ar9av/obsidian-wiki ⭐379)

- **来源**: https://github.com/Ar9av/obsidian-wiki
- **作用**: AI Agent 在 Obsidian 中构建和维护 Wiki 的框架，skill 最丰富的实现之一
- **参考要点**: 完整的 wiki 操作 skill 集（ingest/query/lint/setup/rebuild/export/cross-link/tag），ingest prompt 设计

| 文件 | 说明 |
|------|------|
| README.md | 项目说明 |
| CLAUDE.md | Agent 配置 |
| AGENTS.md | Agent 定义和协作规范 |
| SETUP.md | 安装和配置指南 |
| skills/llm-wiki.md | LLM Wiki 核心 skill |
| skills/karpathy-pattern.md | Karpathy 模式参考 |
| skills/wiki-ingest.md | 素材消化 skill |
| skills/ingest-prompts.md | ingest 的详细 prompt 设计 |
| skills/wiki-query.md | 查询 skill |
| skills/wiki-lint.md | 健康检查 skill |
| skills/wiki-setup.md | 初始化 skill |
| skills/wiki-rebuild.md | 重建 skill |
| skills/wiki-update.md | 更新 skill |
| skills/wiki-export.md | 导出 skill |
| skills/wiki-status.md | 状态检查 skill |
| skills/cross-linker.md | 交叉链接 skill |
| skills/data-ingest.md | 数据消化 skill |
| skills/tag-taxonomy.md | 标签分类 skill |

---

## karpathy-llm-wiki-impl/ (Astro-Han/karpathy-llm-wiki ⭐376)

- **来源**: https://github.com/Astro-Han/karpathy-llm-wiki
- **参考要点**: Karpathy 方案的另一种实现

| 文件 | 说明 |
|------|------|
| README.md | 项目说明 |

---

## gbrain/ (garrytan/gbrain — Garry Tan, YC CEO)

- **来源**: https://github.com/garrytan/gbrain
- **作用**: 个人第二大脑，已超过 17,000 页，MIT 开源，12 天构建
- **参考要点**: 大规模个人知识库的实际运作经验、CLAUDE.md schema 设计

| 文件 | 说明 |
|------|------|
| README.md | 项目说明和使用经验 |
| CLAUDE.md | Agent 配置（45KB，非常详尽的 schema 设计） |

---

## khoj/ (khoj-ai/khoj ⭐34,086)

- **来源**: https://github.com/khoj-ai/khoj
- **作用**: AI 第二大脑，自托管，RAG 路线（对比参考）
- **参考要点**: RAG 路线的成熟实现，与 LLM Wiki 编译路线的对比

| 文件 | 说明 |
|------|------|
| README.md | 项目说明 |

---

## swarmvault/ (swarmclawai/swarmvault ⭐213)

- **来源**: https://github.com/swarmclawai/swarmvault
- **作用**: Local-first RAG + 知识编译混合方案，MCP Server，有 Obsidian 插件
- **参考要点**: RAG 与知识编译的混合架构、llm-wiki-schema 模板、扩展性设计

| 文件 | 说明 |
|------|------|
| README.md | 英文项目说明 |
| README_CN.md | 中文项目说明 |
| SCALE.md | 扩展性设计文档 |
| llm-wiki-schema.md | LLM Wiki Schema 模板 |
| skills/swarmvault.md | 核心 skill 定义 |
| skills/commands.md | 命令参考 |
| skills/artifacts.md | 产物定义 |

---

## ctx/ (stevesolun/ctx ⭐139)

- **来源**: https://github.com/stevesolun/ctx
- **作用**: 技能推荐引擎，基于知识图谱索引 1,789 个 skills + 464 个 agents，实时推荐
- **参考要点**: Wiki 不只存知识还能做推荐、知识图谱构建、skill 路由机制

| 文件 | 说明 |
|------|------|
| README.md | 项目说明 |
| docs/SKILL.md | Skill 规范文档 |
| docs/knowledge-graph.md | 知识图谱设计文档 |
| docs/skill-lifecycle.md | Skill 生命周期和 Dashboard |
| docs/memory-anchor.md | 记忆锚点机制 |
| skills/skill-router.md | Skill 路由 skill 定义 |
| graph-report.md | 知识图谱分析报告 |
| llm-wiki-v2-analysis.md | LLM Wiki v2 分析评审 |

---

## tidemind/ (SawyerHan-AI/TideMind ⭐6)

- **来源**: https://github.com/SawyerHan-AI/TideMind
- **作用**: 跨工具记忆层，SQLite 知识图谱做统一记忆，MCP 协议连接所有 AI 工具，记忆动态演化
- **参考要点**: "活的记忆系统"思路、记忆代谢机制、演化策略 prompt 设计（非常有价值）

| 文件 | 说明 |
|------|------|
| README.md | 项目说明和架构设计 |
| architecture.md | 系统架构文档 |
| design-philosophy.md | 设计哲学 |
| metabolism.md | 记忆代谢机制（淡化/强化/涌现） |
| integrations.md | 集成方式 |
| skills/base-skill.md | 基础 skill 定义 |
| skills/claude-code-skill.md | Claude Code 专用 skill |
| strategies/crystal-emerge.md | 结晶涌现策略 |
| strategies/evolution-learning.md | 演化学习策略 |
| strategies/link-discover.md | 链接发现策略 |
| strategies/reconsolidate.md | 记忆再巩固策略 |
| strategies/dedup-merge.md | 去重合并策略 |
| strategies/annotate.md | 标注策略 |
| strategies/scan-divergent.md | 发散扫描策略 |
| strategies/keystone-enrich.md | 关键节点丰富策略 |

---

## pagefly/ (Yrzhe/pagefly ⭐49)

- **来源**: https://github.com/Yrzhe/pagefly
- **作用**: Personal Knowledge OS，完整的 Capture → Distill → Compile → Serve 管线
- **参考要点**: 四阶段管线设计、Schema 定义、分类器 prompt、完整的 skill 集

| 文件 | 说明 |
|------|------|
| README.md | 项目说明和架构设计 |
| SCHEMA.md | 知识库 Schema 定义 |
| classifier-prompt.md | 素材自动分类的 prompt |
| skills/compiler.md | 编译 skill — 将素材编译为 wiki 页面 |
| skills/linker.md | 链接 skill — 建立交叉引用 |
| skills/query.md | 查询 skill |
| skills/review.md | 审查 skill |
| skills/review-lint.md | Lint 审查 |
| skills/summarizer.md | 摘要 skill |
| skills/pagefly-main.md | 主 skill 入口 |

---

## mcptube/ (0xchamin/mcptube ⭐73)

- **来源**: https://github.com/0xchamin/mcptube
- **作用**: 将 Karpathy Wiki 应用到视频，字幕提取 + 场景检测 + 视觉模型描述关键帧
- **参考要点**: 视频素材的 ingest 方案、FTS5 + 两阶段 agent 检索

| 文件 | 说明 |
|------|------|
| README.md | 项目说明和架构设计 |

---

## awesome-second-brain/ (superuser-pal/awesome-second-brain ⭐6)

- **来源**: https://github.com/superuser-pal/awesome-second-brain
- **作用**: 重型框架，27 命令 + 38 workflow + 9 agent + 257 原子 prompt + 22 思维策略
- **参考要点**: /open-day（晨间加载上下文）、/brain-dump（捕获碎片）、/process（结构化）、/distribute（分发）

| 文件 | 说明 |
|------|------|
| README.md | 项目说明和完整命令列表 |
| CLAUDE.md | Agent 配置（18KB，包含完整的 schema 和工作流定义） |

---

## infranodus/ (noduslabs/infranodus-obsidian-plugin ⭐136)

- **来源**: https://github.com/noduslabs/infranodus-obsidian-plugin
- **作用**: 知识图谱补充工具，用文本分析和主题建模补 LLM Wiki 的结构化短板
- **参考要点**: 知识图谱可视化、主题建模

| 文件 | 说明 |
|------|------|
| README.md | 项目说明和使用方式 |

---

## 关键技术洞察速查

1. **两步链式思考**: 先分析（提取实体/概念/矛盾）再生成（写 Wiki 页面），质量 > 一步到位
2. **置信度标注**: EXTRACTED / INFERRED / AMBIGUOUS / UNVERIFIED
3. **Lint 机制**: 自动发现矛盾、过时信息、孤立页面、知识空白
4. **增量缓存**: SHA256 哈希跳过未变化素材
5. **中等规模不需要向量数据库**: ~100 素材下 index.md 足够，大了再接 qmd
6. **复利工程**: 每次解决问题都文档化为可复用知识（compound-engineering 的核心理念）
