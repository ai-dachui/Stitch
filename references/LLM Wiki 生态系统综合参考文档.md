# LLM Wiki 知识库生态系统 — 综合参考文档

> 基于 21 个开源项目、103 个核心文件的深度分析
> 整理日期：2026-04-20

---

## 一、起源与核心理念

2026 年 4 月 2 日，Andrej Karpathy（前 Tesla AI 总监、OpenAI 创始成员）发布 `llm-wiki.md` Gist。两周内 GitHub 涌现 30+ 实现项目，总 star 超 35,000。

### 核心命题：知识编译 vs RAG

| 维度 | RAG | LLM Wiki |
|------|-----|----------|
| 工作方式 | 每次查询从原始文档重新检索、拼凑 | 素材进入时就编译——提取、整合、更新、标记矛盾 |
| 类比 | 每次考试从课本临时翻答案 | 认真做笔记，笔记越来越厚越有结构 |
| 积累性 | 无积累，每次从零开始 | 知识编译一次，持续维护，复利增长 |
| 维护成本 | 低（无需维护） | 趋近于零（LLM 不会厌倦维护） |

### Karpathy 的核心洞察

> "维护知识库的苦活不是阅读和思考——而是记账。更新交叉引用、保持摘要最新、标记矛盾、保持一致性。人类放弃 Wiki 是因为维护负担增长超过价值增长。LLM 不会厌倦，一次可以改 15 个文件。"

### 三层架构

```
┌─────────────────────────────────────────┐
│  Schema（规则层）                         │
│  告诉 LLM 怎么组织 Wiki 的配置            │
├─────────────────────────────────────────┤
│  Wiki（知识层）                           │
│  LLM 生成和维护的 Markdown 文件集合        │
│  LLM 全权拥有                            │
├─────────────────────────────────────────┤
│  Raw Sources（原始素材）                   │
│  不可变，LLM 只读                         │
└─────────────────────────────────────────┘
```

### 三个核心操作

1. **Ingest（消化）**：扔进素材 → LLM 读完 → 写摘要页 → 更新 index → 更新相关实体/概念页 → 追加 log。一个素材可能触及 10-15 个页面。
2. **Query（查询）**：先读 index.md 定位 → 深入阅读 → 综合回答。好的回答应存回 Wiki（知识回流）。
3. **Lint（健康检查）**：矛盾检测、过时信息、孤立页面、缺失交叉引用、知识空白。还能建议下一步该研究什么。

---

## 二、生态全景（21 个项目）

### 第一梯队：基础设施与标准

| 项目 | Stars | 定位 | 核心价值 |
|------|-------|------|---------|
| **kepano/obsidian-skills** | 25,404 | AI Agent 操作 Obsidian 的标准接口 | Obsidian CEO 出品，定义了 wikilinks、callouts、frontmatter、Canvas、CLI 的 skill 规范 |
| **tobi/qmd** | 22,462 | 本地 Markdown 搜索引擎 | BM25 + 向量 + LLM 重排序，全部本地运行，CLI + MCP Server 双接口 |
| **karpathy/llm-wiki.md** | — | 原始规范 | 一切的起点，定义了三层架构和三个操作 |

### 第二梯队：完整实现

| 项目 | Stars | 定位 | 核心价值 |
|------|-------|------|---------|
| **EveryInc/compound-engineering** | 14,834 | 复利工程 | Brainstorm→Plan→Work→Review→Compound 工作流，50+ agent，42+ skill |
| **Lum1104/Understand-Anything** | 8,578 | 知识图谱可视化 | sigma.js + graphology + ForceAtlas2，10+ 输出平台 |
| **nashsu/llm_wiki** | 1,382 | 桌面应用（Tauri） | 两步链式思考 + 4 信号知识图谱 + Louvain 社区检测 + Deep Research |
| **AgriciDaniel/claude-obsidian** | 1,299 | Claude + Obsidian 伴侣 | 热缓存(hot.md)机制，跨项目引用 |
| **cosen1024/llm-wiki-skill** | 731 | 中文多平台 Skill | 支持微信公众号/YouTube/知乎/小红书，置信度标注 |
| **Ar9av/obsidian-wiki** | 379 | Obsidian Wiki 框架 | 最丰富的 skill 集（18 个文件），含 ingest-prompts 设计 |
| **NicholasSpisak/second-brain** | 190 | 开箱即用版 | npx skills add 一键安装，结构最清晰 |

### 第三梯队：差异化方向

| 项目 | Stars | 定位 | 核心价值 |
|------|-------|------|---------|
| **garrytan/gbrain** | — | YC CEO 个人大脑 | 17,000+ 页，可插拔引擎（PGLite/Postgres），混合搜索，45KB schema |
| **khoj-ai/khoj** | 34,086 | AI 第二大脑（RAG 路线） | 自托管 RAG，对比参考 |
| **swarmclawai/swarmvault** | 213 | RAG + 编译混合 | 30+ 文件格式，Obsidian 插件，MCP Server |
| **stevesolun/ctx** | 139 | 技能推荐引擎 | 2,253 节点 / 454K 边知识图谱，实时推荐 skill |
| **Yrzhe/pagefly** | 49 | Knowledge OS | Capture→Distill→Compile→Serve 四阶段管线 |
| **0xchamin/mcptube** | 73 | 视频 Wiki | 字幕提取 + 场景检测 + 视觉模型描述关键帧 |
| **SawyerHan-AI/TideMind** | 6 | 活的记忆系统 | 记忆代谢、8 个演化策略、跨工具统一记忆层 |
| **superuser-pal/awesome-second-brain** | 6 | 重型框架 | 27 命令 + 38 workflow + 9 agent + 257 原子 prompt |

### 补充工具

| 项目 | Stars | 定位 |
|------|-------|------|
| **noduslabs/infranodus** | 136 | 知识图谱补充（Obsidian 插件 + MCP Server） |
| **ussumant/llm-wiki-compiler** | 471 | 编译器式 Wiki 构建 |
| **lucasastorian/llmwiki** | 401 | LLM Wiki 实现 |
| **Astro-Han/karpathy-llm-wiki** | 376 | Karpathy 方案实现 |

---

## 三、关键技术创新详解

### 3.1 两步链式思考（nashsu/llm_wiki, llm-wiki-skill）

比 Karpathy 原始的一步到位质量显著更高：

**Step 1 — 分析**：LLM 阅读素材 → 提取实体、概念、论点、关联、矛盾 → 输出结构化分析

**Step 2 — 生成**：基于分析结果 → 写/更新 Wiki 页面 → 添加交叉引用

增强特性：
- SHA256 增量缓存：跳过未变化素材
- 持久化 ingest 队列：崩溃可恢复
- 自动 embedding 生成

### 3.2 置信度标注（llm-wiki-skill, obsidian-wiki）

每条知识标注来源可信度：

| 标注 | 含义 | 示例 |
|------|------|------|
| `EXTRACTED` | 直接从源文档提取的硬事实 | "GPT-4 发布于 2023 年 3 月" |
| `INFERRED` | LLM 基于上下文推断 | "该团队可能使用了 RLHF" |
| `AMBIGUOUS` | 源文档本身含糊 | "据报道约有数百万用户" |
| `UNVERIFIED` | 未经验证的声明 | 来自单一来源的数据 |

obsidian-wiki 的 lint 还会检测**来源漂移**：当 AMBIGUOUS > 15% 或 INFERRED > 40% 无源时触发警告。

### 3.3 知识图谱与社区检测

**nashsu/llm_wiki 的四信号关联度模型**：

| 信号 | 权重 | 说明 |
|------|------|------|
| 直接链接 | ×3.0 | `[[wikilinks]]` |
| 来源重叠 | ×4.0 | 共享原始资料 |
| Adamic-Adar | ×1.5 | 共享共同邻居（稀有邻居权重更高） |
| 类型亲和 | ×1.0 | 相同页面类型 |

**Louvain 社区检测**：自动发现知识聚类，内聚度评分（实际边数/可能边数），12 色调色板区分。

**ctx 的知识图谱**：2,253 节点 / 454,719 边 / 93 社区。边通过 frontmatter 标签和 slug-token 伪标签构建。

### 3.4 Lint 机制

各实现的 Lint 检查项汇总：

| 检查项 | second-brain | obsidian-wiki | pagefly |
|--------|:---:|:---:|:---:|
| 孤立页面（零入站链接） | ✓ | ✓ | ✓ |
| 破损 wikilinks | ✓ | ✓ | ✓ |
| 缺失 frontmatter | ✓ | ✓ | ✓ |
| 过时内容 | ✓ | ✓ | ✓ |
| 矛盾检测 | ✓ | ✓ | ✓ |
| 索引一致性 | ✓ | ✓ | ✓ |
| 来源漂移 | — | ✓ | — |
| 标签聚类碎片化 | — | ✓ | — |
| 数据缺口 | ✓ | — | — |
| 可见性标签一致性 | — | ✓ | — |

obsidian-wiki 的 lint 最为完善，引入了来源漂移检测和标签聚类分析。

### 3.5 检索分层策略

从便宜到昂贵的检索原语（obsidian-wiki 的设计）：

```
1. Frontmatter grep（最便宜）→ 标签、来源、日期过滤
2. Index.md 扫描 → 快速定位相关页面
3. 部分 grep（带上下文）→ 搜索特定段落
4. QMD 语义搜索（可选）→ 概念感知检索
5. 完整页面读取（最昂贵）→ 仅读前 3 个候选
```

### 3.6 交叉链接自动发现（obsidian-wiki/cross-linker）

复合评分系统：

| 信号 | 分值 |
|------|------|
| 精确名称匹配 | +4 |
| 共享标签 | +2 |
| 同项目无链接 | +2 |
| 提及实体/概念 | +2 |
| 跨类别连接 | +2 |
| 外围→hub 连接 | +2 |
| 部分名称匹配 | +1 |

置信度映射：≥6 → EXTRACTED，3-5 → INFERRED，1-2 → AMBIGUOUS

### 3.7 复利工程（compound-engineering）

核心理念：第一次解决问题需要研究，文档化后下次只需几分钟。

**完整工作流**：

```
Phase 0.5  自动内存扫描（检查相关条目）
    ↓
Phase 1    并行研究
           ├── Context Analyzer（提取对话历史，确定 track）
           ├── Solution Extractor（生成解决方案文档）
           ├── Related Docs Finder（搜索已有文档，评估重叠）
           └── Session Historian（搜索历史会话）
    ↓
Phase 2    组装与写入
           ├── 高重叠 → 更新现有文档
           └── 低重叠 → 创建新文档
    ↓
Phase 2.5  选择性刷新（决定是否更新旧文档）
    ↓
Phase 3    可选增强（根据问题类型调用专门 agent）
```

**两种知识轨道**：
- Bug 轨道：symptoms → root_cause → resolution → prevention
- Knowledge 轨道：context → guidance → why_this_matters → when_to_apply

---

## 四、TideMind 的"活记忆"体系

TideMind 代表了从"编译静态知识"到"活的记忆系统"的演进方向。

### 4.1 设计哲学

从 5 个学科汲取灵感：

| 学科 | 核心原则 | 在系统中的体现 |
|------|---------|--------------|
| 信息科学 | 关联优先，分类其次（Bush, 1945） | 链接比文件夹更重要 |
| 人机交互 | 工具塑造思想（Engelbart, 1962） | 系统影响用户的思维方式 |
| 社会系统论 | 必须能产生惊喜（Luhmann） | 发散扫描发现意外连接 |
| 神经科学 | 记忆通过使用而演变（再巩固研究） | Read-Write 代谢模式 |
| 复杂系统 | 遗忘对秩序出现是必要的（Prigogine） | 突触缩放、链接衰减 |

### 4.2 活图架构（非分层容器）

TideMind 不使用"短期记忆盒"和"长期记忆盒"的分层模型，而是单个图，每个节点有四维成熟度：

| 维度 | 描述 | 动态 | 神经类比 |
|------|------|------|---------|
| Heat | 短期活动指标 | 快速衰减 | 最近神经元放电频率 |
| Refinement | 内容处理次数 | 缓慢增长 | 记忆从模糊到清晰到抽象 |
| Connectivity | 有效链接数 | 随链接创建/删除变化 | 丰富连接的记忆更易回忆 |
| Independence | 脱离原始上下文的理解程度 | 通过再巩固逐渐增加 | 从海马体依赖迁移到皮层独立 |

### 4.3 三种代谢模式

**Write-Link（摄入时触发）**：
- 内容存储为原子节点 → 计算嵌入 → 找最近邻 → 创建高置信度链接（top-2，相似度 > 0.8）
- 去重：相似度 > 0.92 时更新现有节点而非创建新节点

**Read-Write（回忆时触发）**：
- 沉默读取：仅更新热度
- 感知读取：创建 pending 链接
- 深度读取（再巩固）：LLM 分析节点，检测冲突

**空闲深度处理（安静期间触发）**：
- 日常：突触缩放（全局冷却）、链接衰减（Hebbian 学习）、Pending 链接评估
- 周维护：发散扫描（结构洞检测）、晶体涌现、关键物种识别

### 4.4 八个演化策略

| 策略 | 触发时机 | 作用 |
|------|---------|------|
| **annotate** | 摄入时 | 三维度评分（specificity/subjectivity/actuality） |
| **link-discover** | 每 60 分钟 | 纯启发式候选筛选，向量邻居 + 共同邻居发现 |
| **dedup-merge** | 摄入时 | 去重合并，新信息优先 |
| **reconsolidate** | 回忆时 | 评估记忆是否需要更新，检测矛盾和过时 |
| **crystal-emerge** | 周维护 | 从多条记忆中提炼高层洞察，标注置信度 |
| **scan-divergent** | 周维护 | 发现跨领域的深层联系（结构洞检测） |
| **keystone-enrich** | 周维护 | 分析知识枢纽的连接模式 |
| **evolution-learning** | 持续 | 根据反馈信号自动调整策略参数 |

### 4.5 冷启动门控

| 阶段 | 节点数 | 活跃特性 |
|------|--------|---------|
| Seed | 0 | 基本摄入、流日志 |
| Sprout | 1-49 | + BM25 搜索 |
| Growth | 50+ | + 向量搜索、混合检索 |
| Branching | 100+ | + 图扩展 |
| Canopy | 200+ | + 晶体生成、发散扫描 |
| Forest | 500+ | + Learning II（参数调优） |
| Ecosystem | Learning II 运行 3+ 月 | + Learning III（框架重构） |

---

## 五、各项目的 Schema 设计对比

### 5.1 目录结构对比

**Karpathy 原始**（最简）：
```
raw/          → 不可变源
wiki/         → LLM 维护
  index.md
  log.md
CLAUDE.md     → Schema
```

**second-brain**（标准）：
```
raw/          → 不可变源
wiki/
  sources/    → 源摘要
  entities/   → 人物/工具/项目
  concepts/   → 概念文章
  synthesis/  → 比较分析
  index.md
  log.md
output/       → 查询产品
CLAUDE.md
```

**pagefly**（四阶段管线）：
```
inbox/        → 待处理
raw/          → 原始文档
knowledge/    → 蒸馏后的知识（对 agent 不可变）
wiki/         → agent 编译的文章
workspace/    → 临时工作区
```

**obsidian-wiki**（最丰富）：
```
concepts/     entities/     skills/
references/   synthesis/    journal/
projects/     _raw/         _archives/
_templates/
```

**gbrain**（生产级）：
```
src/core/operations.ts    → 41 个操作定义
src/core/engine.ts        → 可插拔引擎接口
src/core/pglite-engine.ts → PGLite（Postgres via WASM）
src/core/postgres-engine.ts
src/core/minions/         → 作业队列
skills/                   → 26 个技能
```

### 5.2 页面类型对比

| 类型 | second-brain | pagefly | obsidian-wiki |
|------|:---:|:---:|:---:|
| 源摘要（summary） | ✓ | ✓（1:1 映射） | ✓ |
| 实体页（entity） | ✓ | — | ✓ |
| 概念页（concept） | ✓ | ✓（持续更新） | ✓ |
| 连接页（connection） | — | ✓（A↔B 关系） | ✓（synthesis） |
| 洞察页（insight） | — | ✓（按需） | — |
| Q&A 页 | — | ✓（按需） | ✓（questions） |
| Lint 报告 | — | ✓（每次 lint） | ✓ |
| 日志（log） | ✓ | — | ✓ |
| 概览（overview） | ✓ | — | ✓ |

### 5.3 Frontmatter 规范

**标准字段**（所有项目共有）：
```yaml
---
tags: [relevant, tags]
sources: [original-filename.md]
created: YYYY-MM-DD
updated: YYYY-MM-DD
---
```

**obsidian-wiki 扩展**：
```yaml
---
provenance:
  extracted: 0.7
  inferred: 0.2
  ambiguous: 0.1
visibility: [internal]  # 或 pii
---
```

**pagefly 扩展**：
```yaml
---
type: summary | concept | connection | insight | qa | lint
summary: "≤150 字符的单行摘要"
source_doc_ids: [doc-id-1, doc-id-2]
references:
  - target: "[[concept-name]]"
    relation: supports | contradicts | extends
    confidence: 0.85
---
```

---

## 六、Ingest 流程深度对比

### 6.1 基础流程（second-brain）

```
读源 → 讨论关键要点（等待用户确认）→ 创建源摘要页
→ 更新实体/概念页 → 添加 wikilinks → 更新 index.md + log.md
```

### 6.2 两步链式思考（nashsu/llm_wiki）

```
Step 1 分析：
  读素材 → 提取实体列表 → 提取概念列表 → 提取论点
  → 识别关联 → 检测矛盾 → 输出结构化 JSON

Step 2 生成：
  读分析结果 → 匹配已有页面 → 更新或创建页面
  → 生成 wikilinks → 更新图谱 → 追加 log
```

### 6.3 多模态摄入（obsidian-wiki）

支持的源类型和处理方式：

| 源类型 | 处理方式 |
|--------|---------|
| Markdown | 直接蒸馏 |
| PDF | 文本提取 → 蒸馏 |
| 图像 | 转录文本 → 描述结构 → 提取概念 → 标注模糊性 |
| 网页剪辑 | Readability.js 提取 → Turndown.js 转 Markdown |
| 音频转录 | 转录文本 → 蒸馏 |
| Claude/Codex 历史 | 解析对话格式 → 提取知识点 |

### 6.4 知识蒸馏框架（obsidian-wiki/ingest-prompts）

五个关键提取问题：
1. 3-5 个最重要的想法是什么？
2. 谁或什么值得拥有自己的页面？
3. 这个文档教你如何做什么？
4. 这个文档做了什么声明？
5. 这如何连接到 wiki 已知的内容？

交叉引用发现模式：Is-a、Uses、Contrasts-with、Part-of、Created-by、Applied-in

### 6.5 矛盾处理

所有项目的共识：**标注矛盾而非隐藏**。

```markdown
> ⚠️ 矛盾：[旧声明（来源A，日期）] vs [新声明（来源B，日期）]
```

---

## 七、GBrain 的生产级架构

Garry Tan（YC CEO）的个人知识库，17,000+ 页，MIT 开源。

### 核心设计

- **可插拔引擎**：PGLite（嵌入式 Postgres 17.5 via WASM，零配置）或 Postgres + pgvector
- **41 个共享操作**：CLI 和 MCP Server 从 `src/core/operations.ts` 单一源生成
- **信任边界**：`OperationContext.remote` 区分本地 CLI 和代理调用

### 混合搜索管线

```
查询 → 意图分类（entity/temporal/event/general）
     → 多查询扩展
     → 并行执行：向量搜索 + 关键字搜索
     → RRF（Reciprocal Rank Fusion）合并
     → 去重
     → 返回结果
```

### 三层分块策略

1. **递归分块**：按自然边界（标题、段落）
2. **语义分块**：按语义相似度
3. **LLM 引导分块**：LLM 判断最佳切分点

### 检索评估框架

| 指标 | 说明 |
|------|------|
| P@k | 前 k 个结果中相关的比例 |
| R@k | 前 k 个结果覆盖的相关文档比例 |
| MRR | 第一个相关结果的排名倒数 |
| nDCG@k | 归一化折损累积增益 |

---

## 八、趋势判断与演进方向

### 8.1 六个演进方向

1. **从"编译知识"到"活的记忆系统"**
   - TideMind 代表：记忆动态演化（自动关联、淡化、强化、涌现新认知）

2. **从"个人 Wiki"到"跨工具统一记忆"**
   - 痛点从"没有知识库"变成"知识散落在 10 个工具里"
   - MCP 协议成为连接层

3. **从"存储"到"推荐"**
   - ctx 的思路：Wiki 不只被动查询，还能主动推荐该加载哪些 skill

4. **开箱即用化**
   - second-brain 的 `npx skills add` 一键安装

5. **垂直化**
   - mcptube 把 Wiki 应用到视频
   - InfraNodus 补知识图谱短板

6. **平台化**
   - PageFly 从 Wiki 升级为 Knowledge OS（带 API/Bot/Web）
   - GBrain 的可插拔引擎架构

### 8.2 关键设计决策参考

| 决策点 | 建议 | 理由 |
|--------|------|------|
| 向量数据库 | 中等规模暂不需要 | ~100 素材下 index.md 足够导航，大了再接 qmd |
| 两步链式思考 | 值得采用 | 质量显著优于一步到位，多个项目验证 |
| 置信度标注 | 值得采用 | 知识可信度可追溯，lint 可检测来源漂移 |
| 热缓存(hot.md) | 值得采用 | 避免每次都读整个 wiki，~500 tokens 即可 |
| 知识回流 | 值得采用 | 查询结果存回 wiki，知识复利 |
| 记忆代谢 | 观望 | TideMind 思路好但 star 低，可借鉴衰减和涌现机制 |
| 社区检测 | 中后期采用 | 100+ 页面后才有意义 |

---

## 九、与我们现有体系的关系

### 已确定的三层数据流（4/17）

```
sources（信息采集）→ wiki（LLM 编译）→ zones（结构化归档）
```

### LLM Wiki 的核心升级点

1. **自动消化**：扔进素材，LLM 自动提取实体、概念、生成互联页面
2. **持续积累**：每次 ingest 都更新已有页面
3. **矛盾检测**：新素材和旧知识冲突时自动标记
4. **知识图谱**：wikilink 自动生成可视化图谱
5. **知识回流**：查询结果存回 wiki，复利增长

### 推荐参考优先级

1. **second-brain** 的 wiki-schema → 作为基础 schema 模板
2. **obsidian-wiki** 的 skill 集 → 作为 ingest/query/lint 的 prompt 参考
3. **gbrain** 的 CLAUDE.md → 作为大规模 schema 的参考
4. **pagefly** 的 SCHEMA.md → 作为分类系统的参考
5. **TideMind** 的策略 → 作为记忆演化机制的灵感
6. **compound-engineering** 的 ce-compound → 作为知识复利机制的参考
