# 2027 美赛：AI 工具、插件与 Skill 推荐

整理日期：2026-11-16

## 我的核心判断

美赛最有价值的 AI 工作流不是“找一个模型一次做完”，而是四层结构：

1. **总控层**：Codex 负责理解任务、拆解流程、调用工具、维护文件和管理版本；
2. **证据层**：文献检索、事实核验、数据来源和引用管理；
3. **计算层**：Python、Jupyter、统计与优化库负责真正运行模型；
4. **交付层**：Word、LaTeX、PDF、表格、图示和 PPT 工具负责最终表达。

比赛只有约 96 小时，临场学习新工具通常不划算。真正有效的做法是赛前把工具组合固定下来，用 2025 或 2026 真题完整跑一遍。

本清单把这些工具分为：

- **S 级：建议现在就配置并熟练掌握**；
- **A 级：有明显价值，按题型或分工选用**；
- **B 级：值得试验，但不能依赖**。

---

## 一、先把 Codex 里的 Skill 和 Plugin 分清

按 [OpenAI 官方 Skills 文档](https://developers.openai.com/codex/skills)：

- **Skill** 是可复用的工作流，通常由 `SKILL.md`、脚本、参考资料和模板组成；
- **Plugin** 可以打包一个或多个 Skill，也可以附带 MCP 连接和界面能力；
- Skill 适合个人与单仓库工作流，Plugin 更适合安装和分发。

可以直接在提示词中显式调用 Skill，例如：

```text
$scientific-visualization 根据我给出的数据制作论文级多面板图
$statistical-analysis 检查这组模型假设并给出合适的检验
$presentations 把已验证的建模结果排成 8 页汇报 PPT
```

当前机器上已经装有以下可直接使用的 Codex 插件：

| 插件 | 主要用途 | 美赛中的用途 |
|---|---|---|
| `visualize` | 交互图、地图、流程、模拟、3D 和数据探索 | 探索参数、展示动态过程、做内部讨论页 |
| `documents` | 创建和编辑 Word 等文档 | 论文草稿、备忘录、团队文档 |
| `pdf` | 读取、生成、渲染和检查 PDF | 精读 O 奖论文、检查最终 PDF、页数和版面 |
| `presentations` | 创建、编辑、渲染、验证和导出 PPTX | 校内汇报、答辩、赛后复盘 |
| `spreadsheets` | 创建、编辑、分析和导出 Excel 表格 | 数据清洗、参数表、结果表、获奖率统计 |
| `template-creator` | 从已有文件或链接生成模板 | 把论文、PPT、笔记做成可复用模板 |

这些不是“额外建议”，而是你现在已经拥有的工具。

---

## 二、S 级：最值得纳入美赛工作流的 Skill

### 1. 研究、论文与引用

| Skill | 什么时候用 | 怎么用最稳 |
|---|---|---|
| `$research-lookup` | 赛前研究某一题型、方法或背景 | 要求每条结论附来源和链接 |
| `$paper-lookup` | 按 DOI、标题或主题找论文 | 只信原始论文、摘要页或出版方 |
| `$citation-management` | 导出 BibTeX、核对作者年份卷期 | 最终引用必须逐条校验 |
| `$academic-research-suite` | 系统梳理某一研究问题 | 适合赛前，不适合赛中从头学习 |
| `$nature-paper-card` | 精读单篇 O 奖或研究论文 | 用统一卡片拆方法、证据、局限 |
| `$nature-reader` | 中英对照精读论文 | 适合长论文，不直接照搬语言 |

推荐组合：

```text
$research-lookup 检索近五年“楼梯磨损/连续型建模”的论文，输出方法、数据需求、
适用条件、局限和可验证链接。不要替我写最终模型。
```

### 2. 审题、假设和模型选择

| Skill | 价值 | 风险控制 |
|---|---|---|
| `$scientific-brainstorming` | 生成多种问题拆解和建模路线 | 要求它先列假设和反例 |
| `$hypothesis-generation` | 把开放问题转成可检验假设 | 不能把假设当结论 |
| `$scientific-critical-thinking` | 反向审查假设、数据泄漏、混杂和逻辑跳跃 | 每次提交前至少跑一次 |
| `$sympy` | 符号推导、方程和代数检查 | 关键推导仍需人工确认 |

推荐提示词：

```text
$scientific-critical-thinking 逐条攻击下面的问题拆解和建模假设。
找出：题面遗漏、不可观测变量、循环论证、数据泄漏、无法验证的结论。
不要重写答案，只输出风险、原因和检验方法。
```

### 3. 数据分析、建模和求解

| Skill / 工具 | 适用题型 |
|---|---|
| `$exploratory-data-analysis` | C/E 题的数据检查、缺失值、异常值和分布 |
| `$statistical-analysis` | 选择检验、审查假设、报告效应量 |
| `$statsmodels` | 回归、时间序列、统计推断 |
| `$scikit-learn` | 分类、回归、聚类、交叉验证和基线模型 |
| `$pymc` | 不确定性和层级贝叶斯模型 |
| `$pymoo` | 多目标优化、约束优化 |
| `$networkx` | D 题网络、路径、中心性和网络结构 |
| `$simpy` | 排队、流程和离散事件仿真 |
| `$matlab` | MATLAB/Octave 代码和兼容性审查 |
| `$optimize-for-gpu` | 计算量确实很大时再做 GPU 优化 |

推荐用法不是“让 AI 直接选一个模型”，而是：

```text
根据下面题面、数据字段和计算时间，列出 3 个候选模型。
对每个模型给出：输入、输出、关键假设、需要的数据、实现难度、
可验证性、优缺点和不适用条件。暂时不要写代码。
```

确定模型后，再让 Codex 写可重复运行的脚本和测试。

### 4. 图、表、流程图和论文排版

| Skill / 插件 | 最适合做什么 | 不建议做什么 |
|---|---|---|
| `$scientific-visualization` | 论文级图表、颜色、图注、多面板图 | 代替真实计算 |
| `$matplotlib` | 精确控制坐标轴、图例和导出 | 生成虚假数据 |
| `$seaborn` | 快速统计图和高层样式 | 忽略数据分布直接美化 |
| `$markdown-mermaid-writing` | 确定性流程图、思维导图和结构图 | 复杂精确地图 |
| `$scientific-schematics` | 概念图、机制图、研究框架图 | 结果图、带精确数值的图 |
| `$nature-figure` | 接近期刊规范的多面板科研图 | 替代模型结果 |
| `$visualize` | 交互探索和展示变化过程 | 直接作为最终投稿图 |
| `$documents` / `$pdf` | Word、PDF 生成与版式检查 | 跳过人工通读 |

**我的建议：**

- 数据图用 Python 生成，保证能从代码复现；
- 流程图优先用 Mermaid、draw.io、PPT 或 Visio；
- AI 图像工具用于概念图或装饰性背景；
- AI 生成的概念图必须人工重画或核对每一条箭头、标签和公式；
- 不要把 AI 生成的图片直接当成模型结果。

### 5. PPT 和汇报

| Skill | 用途 |
|---|---|
| `$presentations` | 生成或修改真正的 `.pptx` |
| `$scientific-slides` | 设计研究汇报结构和演讲节奏 |
| `$nature-paper2ppt` | 把论文或阅读笔记转为中文科研汇报 |
| `$frontend-slides` | 制作网页型演示（如需要在线展示） |
| `$latex-posters` | 制作学术海报 |

推荐流程：

1. 用已核验的论文和结果生成大纲；
2. 人工删去不重要的模型细节；
3. 用 `$presentations` 排成 PPTX；
4. 逐页检查数字、图注和引用；
5. 最后再做配色、动画和版式。

不要让 AI 在不知道最终结果的情况下“编一页结论”。

---

## 三、A 级：外部 AI 工具

### 1. Elicit：文献证据表和研究综述

链接：<https://elicit.com/>

适合：

- 把“某个现实问题有哪些常见建模方法”转成证据表；
- 快速找到相关论文、方法和数据来源；
- 提炼论文中的变量、方法、数据、结论和限制；
- 生成带引用的研究简报。

优势：以学术论文为主要来源，并强调 sentence-level citations。

风险：

- 自动生成的表格仍可能抽错字段；
- 文献覆盖不等于与赛题完全相关；
- 不能用它代替真实论文阅读和引用核对。

推荐用途：赛前建立题型知识库；赛中快速补背景和找文献线索。

### 2. Consensus：快速判断研究共识

链接：<https://consensus.app/>

适合：

- 问“某项政策/干预/方法是否有实证证据”；
- 快速查看相关论文的结论方向；
- 做 F 题政策、E 题环境和 C 题指标背景的初步筛查。

注意：短答案容易忽略样本、条件和反例。最终必须打开原论文，确认适用范围。

### 3. ResearchRabbit：沿引用关系找文献

链接：<https://www.researchrabbit.ai/>

适合：

- 从一篇种子论文扩展相关作者、引用和相似论文；
- 快速理解一个领域的文献簇；
- 把 Zotero 收藏转成研究地图。

比赛中最适合“找方法来源”和“找数据来源”，不适合用来自动写模型。

### 4. Google Gemini Notebook（原 NotebookLM）

链接：<https://notebooklm.google.com/>

适合：

- 把赛题规定、论文、网页和资料放进同一个来源库；
- 只基于你上传的资料做问答；
- 把复杂论文转成摘要、思维导图和音频/视频概览；
- 把已有材料转成演示大纲。

推荐用途：赛前读 O 奖论文和政策文件；赛中建立“问题资料室”。

风险：来源缺失时模型会给出看似完整的概括；重要数字必须回到原文。

### 5. Mathpix：公式、表格和 PDF 转换

链接：<https://mathpix.com/>

适合：

- 截图识别数学公式为 LaTeX；
- PDF 转 Markdown、Word、LaTeX 或 Excel；
- 把论文中的表格转成 CSV；
- 快速提取 O 奖论文中的模型公式和表格。

优势：对 STEM 公式和表格比普通 OCR 更可靠。

风险：识别后的符号、上下标和表头必须人工核对。

### 6. Napkin AI：文字转流程图、思维导图和概念图

链接：<https://www.napkin.ai/>

适合：

- 把问题分析文字转成流程图草稿；
- 把模型关系转成概念图；
- 把政策建议转成信息图；
- 导出 PNG、SVG、PDF 或 PPT 元素继续编辑。

最适合在早期快速探索“图应该怎么表达”。

风险：

- 自动生成的箭头和层级可能改变原意；
- 对数学公式、网络拓扑和精确坐标支持有限；
- 最终图必须用确定性工具重画。

### 7. SciSpace

链接：<https://scispace.com/>

定位：论文阅读、解释和文献管理。

建议：如果已有 Elicit、Consensus 和 Gemini Notebook，不必再同时订阅一整套相似产品。先用免费额度测试自己的工作流。

---

## 四、非 AI 但必须掌握的高杠杆工具

这些工具往往比再装一个“万能 AI”更有价值。

### 计算与代码

- [JupyterLab](https://jupyter.org/)：数据探索、可视化和计算缓存；
- [Python](https://www.python.org/)：NumPy、SciPy、pandas、Matplotlib、scikit-learn；
- [Git](https://git-scm.com/)：代码、论文和结果版本管理；
- [VS Code](https://code.visualstudio.com/)：统一编辑代码、Markdown 和 LaTeX。

### 论文与引用

- [Overleaf](https://www.overleaf.com/)：多人协作 LaTeX；
- [Zotero](https://www.zotero.org/)：文献管理和 PDF 阅读；
- [Better BibTeX](https://retorque.re/zotero-better-bibtex/)：稳定 citation key 和 BibTeX 导出；
- [LanguageTool](https://languagetool.org/)：基础语法与拼写检查。

### 图表与图示

- [draw.io](https://www.drawio.com/)：流程图、系统图和概念图；
- [Mermaid](https://mermaid.js.org/)：文本生成的确定性流程图；
- [Inkscape](https://inkscape.org/)：SVG 矢量图后期编辑；
- [Gephi](https://gephi.org/)：大规模网络可视化；
- [Cytoscape](https://cytoscape.org/)：网络分析和可视化。

### 数据源

- [Our World in Data](https://ourworldindata.org/)：环境、能源、人口、健康和社会指标；
- [World Bank Open Data](https://data.worldbank.org/)：国家和地区发展数据；
- [OECD Data](https://data.oecd.org/)：经济、教育、环境和社会政策；
- [UN Data](https://data.un.org/)：国际统计；
- [NOAA](https://www.noaa.gov/)：海洋、大气、气候；
- [Copernicus](https://www.copernicus.eu/)：对地观测和环境数据；
- [OpenStreetMap](https://www.openstreetmap.org/)：道路、设施和城市网络。

---

## 五、推荐的比赛工具栈

### 最低配置

适合预算有限、第一次参赛：

```text
Codex
Python + JupyterLab
Git / GitHub
Zotero + Better BibTeX
Word 或 LaTeX
Mermaid 或 draw.io
```

这套已经能覆盖检索、计算、引用、制图和论文交付。

### 推荐配置

```text
最低配置
+ Elicit 或 Consensus
+ Gemini Notebook
+ Mathpix
+ Codex 的 scientific-visualization / presentations / spreadsheets
```

这套的重点是减少文献筛查、公式搬运、图表排版和汇报制作时间。

### 展示增强配置

```text
推荐配置
+ Napkin AI
+ Inkscape
+ scientific-schematics
+ nature-figure
+ scientific-slides / nature-paper2ppt
```

适合需要答辩、校内展示、赛后复盘或把成果转成 PPT 的场景。

---

## 六、赛中建议工作流

### 阶段 0：赛前

1. 建好 GitHub 仓库和统一文件夹；
2. 安装 Python、Jupyter、LaTeX/Word 模板和绘图库；
3. 用 2025 或 2026 真题测试每条命令；
4. 准备论文模板、图表模板、代码模板和 AI 使用日志；
5. 选定主模型工具，不要比赛时同时试用五种产品或五个聊天机器人。

### 阶段 1：读题

```text
先只做任务分解：
- 每一问问什么；
- 需要什么数据和变量；
- 可能的模型路线；
- 最容易遗漏的约束；
- 每问的结果应如何验证。
不要直接写答案。
```

### 阶段 2：查证据和选模型

```text
用 Codex 的研究工具或 Elicit/Consensus 找 5-10 个相关来源。
输出文献表：方法、适用条件、输入、输出、数据需求、局限、链接。
再比较至少 3 个候选模型，明确为什么淘汰其中两个。
```

### 阶段 3：数据和代码

```text
先做数据质量审计：类型、缺失、异常、重复、时间、地理和单位。
然后生成可重复运行的最小脚本，并加入至少一个已知答案或简单基线做测试。
```

### 阶段 4：图表和论文

1. 数据图必须由代码生成；
2. 流程图用 Mermaid/draw.io/PPT；
3. AI 概念图只作草稿；
4. 每张图配一句“图说明了什么”，再扩成结果分析；
5. 摘要中必须出现具体结果，不能只写“建立了一个模型”。

### 阶段 5：质量控制

提交前至少进行四轮检查：

- **数学检查**：单位、约束、边界、推导和数值合理性；
- **代码检查**：随机种子、路径、输出、基线、重复运行；
- **论文检查**：摘要、图表、引用、匿名、页眉页码和 25 页；
- **AI 合规检查**：工具清单、正文引用、参考文献和 AI 使用报告。

---

## 七、可直接套用的提示词

### 1. 审题拆解

```text
请只做审题，不要给最终答案。
把题目拆成：目标、已知条件、隐含条件、决策变量、数据需求、
必须回答的子问题、结果验证方式、可能的建模方向。
最后列出最可能被忽略的三个约束。
```

### 2. 文献证据表

```text
为下面问题检索学术来源，输出表格：
作者年份 | 研究问题 | 数据 | 方法 | 关键结果 | 适用条件 | 局限 | 原文链接。
只保留能打开并核对的来源；摘要无法支持的内容标记为“未确认”。
```

### 3. 模型比较

```text
对下面问题比较三个候选模型。
逐个说明输入、输出、假设、参数来源、计算成本、可解释性、
灵敏度验证方式、过拟合风险和不适用条件。
最后给出选择建议，但不要生成结果数据。
```

### 4. 数据审计

```text
检查这份数据的质量：
样本量、字段类型、缺失率、重复、异常值、时间范围、地理范围、
单位、潜在泄漏、类别不平衡和样本偏差。
输出清洗规则和可能改变结论的风险，不要静默删除数据。
```

### 5. 代码审查

```text
审查这段模型代码：
- 输入输出是否与题目一致；
- 是否存在数据泄漏；
- 约束是否真的生效；
- 随机性是否可复现；
- 是否有基线或简单情形测试；
- 结果单位与量级是否合理。
先列问题，再给最小修复。
```

### 6. 反方审查

```text
请扮演严格评委，攻击下面的模型和结论。
找出最可能导致奖项下降的五个问题。
每个问题给出证据、影响和修补实验，不要用空泛措辞。
```

### 7. 结果图和图注

```text
根据这组真实结果生成可复现的 Python 绘图脚本。
要求：色盲友好、统一风格、坐标轴和单位完整、图中无中文、
直接导出 PDF 和 PNG。不要修改或编造任何数据。
```

### 8. 论文一致性检查

```text
对照题面、代码和结果，检查论文是否一致：
每一问是否回答了题目、摘要是否含真实结果、图中数值与表格是否一致、
模型假设是否被正文支持、结论是否超出结果范围。
按严重程度列出问题。
```

---

## 八、AI 合规和风险

COMAP 2027 允许负责任地使用 AI，但有明确要求：

1. 在论文正文中使用内联引用；
2. 在参考文献中列出所用 AI 工具；
3. 在 25 页正文之后附加 `Report on Use of AI Tools`；
4. 不得把 AI 生成整篇论文后直接当作原创成果；
5. 必须核验 AI 生成的代码、数据、事实、引用和结论；
6. 比赛中不得向队外人员获取解题思路或答案。

建议每队维护一份 AI 使用日志：

| 日期时间 | 工具及版本 | 使用目的 | 输入摘要 | 输出在哪 | 是否核验 |
|---|---|---|---|---|---|
| 2027-01-29 08:30 | 工具名/版本 | 文献检索 | 关键词 | `01_sources/` | 已打开原文 |
| 2027-01-30 14:10 | 工具名/版本 | 代码调试 | 报错和脚本 | `02_code/` | 测试通过 |
| 2027-02-01 20:00 | 工具名/版本 | 英文润色 | 论文段落 | `05_paper/` | 三人复核 |

这份日志既能防止最后忘记写 AI 报告，也能帮助团队区分“工具建议”和“自己的模型”。

---

## 九、最终推荐

如果只选一套，我会这样配：

1. **主控与代码**：Codex + JupyterLab + Git/GitHub；
2. **研究证据**：Codex 的 `research-lookup` / `paper-lookup` + Elicit；
3. **文献地图与快速共识**：Consensus + ResearchRabbit；
4. **论文阅读**：Gemini Notebook + `nature-paper-card`；
5. **公式与表格**：Mathpix + `spreadsheets`；
6. **建模算法**：`statistical-analysis`、`scikit-learn`、`statsmodels`、`pymoo`、`networkx`、`sympy`；
7. **数据图**：`scientific-visualization` + Matplotlib；
8. **流程图/概念图**：Mermaid/draw.io；Napkin 只做草图；
9. **论文**：官方 Word/LaTeX 模板 + `documents`/`pdf`；
10. **PPT**：`presentations`，内容必须从已核验论文生成。

最不应该做的，是比赛开始后到处寻找“万能 AI 插件”、实时购买思路或在多个聊天窗口之间反复复制粘贴。工具必须在赛前固定、测试并形成模板。

