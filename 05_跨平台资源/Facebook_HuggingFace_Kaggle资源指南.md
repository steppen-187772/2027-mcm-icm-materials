# Facebook/Meta、Hugging Face 与 Kaggle 资源指南

核对日期：2026-11-18

## 先说结论

三个平台里，对美赛帮助最大的是 **Kaggle 和 Hugging Face**，Facebook 本身不是主要学习平台。

- **Facebook**：只建议关注 COMAP 官方页面，用来接收比赛公告；Facebook 群组中的二手消息无法稳定核验，不作为核心资料。
- **Hugging Face**：适合找特定用途的模型、数据集和在线 Demo。它不是“建模方法大全”，更不能代替自己的模型假设、代码和验证。
- **Kaggle**：最适合补齐 Pandas、数据可视化、机器学习、时间序列和地理空间分析；公开数据集与优秀 Notebook 也有较高参考价值。

这三个平台都不应替代以下核心资料：

- COMAP 官方赛题、规则、Results Report 和 O 奖论文；
- 自己能够复现的 Python 代码；
- 自行核验过的数据和引用；
- 团队自己的建模判断和结果解释。

---

## 一、Facebook / Meta

### 1. COMAP 官方 Facebook 页面

链接：<https://www.facebook.com/comapmath/>

用途：

- 查看 COMAP 的赛事通知、活动信息和宣传内容；
- 辅助了解 HiMCM、MidMCM、MCM/ICM 的最新动态。

局限：

- 内容更新频率和完整度不如 COMAP 官网；
- 页面可能要求登录；
- 不能用来代替官方 Rules、Instructions 或 Problems and Results。

结论：可以关注，但只作为通知补充。

### 2. Meta AI Resources

入口：<https://ai.meta.com/resources/>

这是 Meta 官方集中整理框架、模型、数据集、Demo、系统卡和论文的入口。

适合查找：

- 开源模型；
- 计算机视觉工具；
- 文本和翻译相关资源；
- 数据集与研究论文。

### 3. Prophet 时间序列预测

链接：<https://meta.github.io/prophet/>

适用场景：

- C/E 题中的趋势和季节性预测；
- 数据存在缺失值、异常点或明显节假日效应；
- 需要一个快速、可解释的时间序列基线。

优点：

- Python 和 R 均可使用；
- 可分解趋势、季节性和节假日效应；
- 能输出不确定性区间；
- 参数可解释，适合论文讨论。

局限：

- 更适合有明显年度、周度或日度季节性的数据；
- 不能自动产生高质量因果关系；
- 不能替代 ARIMA、状态空间模型、机器学习基线或题目特定机理模型。

### 4. PyTorch

链接：<https://pytorch.org/>

用途：

- 神经网络；
- 图像与视频模型；
- 时间序列深度学习；
- 需要自定义损失的优化问题。

建议：美赛不应默认使用 PyTorch。只有数据量、任务复杂度和验证结果足以支持神经网络时再用。

### 5. Detectron2

链接：<https://github.com/facebookresearch/detectron2>

用途：

- 目标检测；
- 实例分割；
- 图片中的对象识别。

适合 C 题涉及图像或视频，且确实需要视觉检测时使用。

风险：

- 环境配置和模型下载成本较高；
- 可能占用大量比赛时间；
- 只给检测结果，不会自动形成有意义的模型结论。

### 6. Segment Anything Model 2（SAM 2）

链接：<https://ai.meta.com/research/sam2/>

用途：

- 图像或视频中的对象分割；
- 为图像数据分析生成区域掩码。

只建议作为视觉处理组件。最终仍要回答“分割结果怎样进入数学模型、怎样影响结论”。

### 7. Meta Datasets

链接：<https://ai.meta.com/datasets/>

适合查找 Meta 公开的数据集和基准。

注意：这些数据更偏 AI 研究与视觉/语言任务，与 MCM 现实问题不一定匹配。使用前核对许可证、样本来源和地理范围。

### Facebook 使用判断

我会保留的只有：

- COMAP 官方通知；
- Meta 的开源工具和数据集。

不建议把 Facebook 群组里的“往年题思路”“O 奖论文分享”“赛中思路”当正式资料。这类内容有登录限制、转载失真和无法核对原始来源的问题；比赛期间更不能用它寻求队外帮助。

---

## 二、Hugging Face

### 1. 总入口

- [Models](https://huggingface.co/models)
- [Datasets](https://huggingface.co/datasets)
- [Spaces](https://huggingface.co/spaces)
- [Tasks](https://huggingface.co/tasks)
- [Learn](https://huggingface.co/learn)
- [Daily Papers](https://huggingface.co/papers)
- [Datasets 官方文档](https://huggingface.co/docs/datasets/index)
- [Transformers 任务文档](https://huggingface.co/docs/transformers/task_summary)

### 2. 对美赛最有用的任务类型

| 任务 | 适合题型 | 典型用途 |
|---|---|---|
| Tabular Classification | C/E/F | 表格分类、风险分类、政策对象分类 |
| Tabular Regression | C/E | 数值预测、需求或指标回归 |
| Time Series Forecasting | C/E | 趋势、季节性和多变量预测 |
| Sentence Similarity / Feature Extraction | 全题型 | 文献语义检索、聚类和知识库构建 |
| Document Question Answering | 数据准备 | 从扫描件、PDF 和表格中抽取字段 |
| Image Segmentation / Object Detection | C/E | 图像或遥感对象识别与计数 |
| Image-to-Text | C | 图像说明、辅助理解赛题数据 |

### 3. 可直接浏览的任务页

- [表格分类模型](https://huggingface.co/models?pipeline_tag=tabular-classification)
- [表格回归模型](https://huggingface.co/models?pipeline_tag=tabular-regression)
- [时间序列预测模型](https://huggingface.co/models?pipeline_tag=time-series-forecasting)
- [文档问答模型](https://huggingface.co/models?pipeline_tag=document-question-answering)
- [图像分割模型](https://huggingface.co/models?pipeline_tag=image-segmentation)
- [目标检测模型](https://huggingface.co/models?pipeline_tag=object-detection)
- [句子相似度模型](https://huggingface.co/models?pipeline_tag=sentence-similarity)

### 4. 值得研究的模型类别和示例

模型排行会变化。下面只作为“检查时可找到的示例”，不是获奖保证。

| 方向 | 示例模型 | 适合的用途 | 主要风险 |
|---|---|---|---|
| 时间序列 | [google/timesfm-3.0-pytorch](https://huggingface.co/google/timesfm-3.0-pytorch) | 零样本或少样本时间序列预测 | 模型较大、预测结果需和简单基线比较 |
| 时间序列 | [amazon/chronos-2](https://huggingface.co/amazon/chronos-2) | 通用时间序列预测实验 | 不能自动解决数据泄漏和因果问题 |
| 表格回归 | [Prior-Labs/TabPFN-v2-reg](https://huggingface.co/Prior-Labs/TabPFN-v2-reg) | 中小型表格回归实验 | 表结构、缺失值和数据分布会影响效果 |
| 文档问答 | [impira/layoutlm-document-qa](https://huggingface.co/impira/layoutlm-document-qa) | 从文档版式中抽取字段 | 对扫描件质量敏感 |
| 目标检测 | [facebook/detr-resnet-50](https://huggingface.co/facebook/detr-resnet-50) | 通用对象检测示例 | 预训练类别有限，可能需要微调 |

### 5. 数据集筛选入口

- [表格数据](https://huggingface.co/datasets?modality=modality%3Atabular)
- [时间序列数据](https://huggingface.co/datasets?modality=modality%3Atimeseries)
- [文档数据](https://huggingface.co/datasets?modality=modality%3Adocument)
- [地理空间数据](https://huggingface.co/datasets?modality=modality%3Ageospatial)

Datasets 库支持 Arrow、Pandas、Polars、流式读取和 Dataset Viewer。数据很大时，先用 Viewer 查看字段，再决定是否下载。

### 6. Hugging Face Spaces 怎么用

链接：<https://huggingface.co/spaces>

Spaces 是社区公开的模型 Demo，可以直接测试：

- OCR 和文档抽取；
- 图像分割；
- 文本分类；
- 时间序列预测；
- 文本嵌入和相似度。

最佳用途是“快速判断某类模型是否值得进一步使用”。

不要把它当作比赛运行依赖：公开 Space 可能排队、休眠、限流或暂时不可用。正式计算必须在本地或自己控制的运行环境中完成。

### 7. Hugging Face 使用顺序

1. 先确定数学任务，不先搜模型；
2. 在 Tasks 页面找到对应任务；
3. 查看模型卡的数据、限制、许可证和推理示例；
4. 先用小样本测试；
5. 和简单基线比较；
6. 记录模型 ID、版本和用途；
7. 把结果接入自己的模型链，而不是停在“跑通模型”。

---

## 三、Kaggle

### 1. Kaggle Learn 课程

总入口：<https://www.kaggle.com/learn>

最值得美赛队伍使用的是：

| 课程 | 链接 | 对应能力 |
|---|---|---|
| Python | <https://www.kaggle.com/learn/python> | Python 基础 |
| Pandas | <https://www.kaggle.com/learn/pandas> | 数据表和清洗 |
| Data Cleaning | <https://www.kaggle.com/learn/data-cleaning> | 缺失值、异常值、格式整理 |
| Data Visualization | <https://www.kaggle.com/learn/data-visualization> | 图表表达 |
| Intro to Machine Learning | <https://www.kaggle.com/learn/intro-to-machine-learning> | 训练、验证和基础模型 |
| Intermediate Machine Learning | <https://www.kaggle.com/learn/intermediate-machine-learning> | 缺失值、类别变量、泄漏和管道 |
| Feature Engineering | <https://www.kaggle.com/learn/feature-engineering> | 特征构建 |
| Time Series | <https://www.kaggle.com/learn/time-series> | 趋势、季节性和预测验证 |
| Geospatial Analysis | <https://www.kaggle.com/learn/geospatial-analysis> | D/E 题地图与空间分析 |
| Machine Learning Explainability | <https://www.kaggle.com/learn/machine-learning-explainability> | 模型解释 |

推荐组合：

- 第一次做 C 题：Pandas → Data Cleaning → Data Visualization → Intro ML → Intermediate ML。
- 主攻预测：Time Series → Feature Engineering → Store Sales Notebook。
- 主攻 D 题：Geospatial Analysis → NetworkX / 图算法。
- 论文手：Data Visualization + 图表规则，不必刷完机器学习。

### 2. Kaggle Competitions 指南

链接：<https://www.kaggle.com/learn-guide/kaggle-competitions>

内容包括：

- 如何理解竞赛指标；
- 如何查看数据和提交；
- 如何学习公开 Notebook；
- 如何避免数据泄漏；
- 推荐的学习顺序；
- Kaggle 获奖方案汇总。

重点推荐的通用 Notebook：

- [Kaggle 获奖方案合集](https://www.kaggle.com/code/sudalairajkumar/winning-solutions-of-kaggle-competitions)
- [Titanic Data Science Solutions](https://www.kaggle.com/code/startupsci/titanic-data-science-solutions)
- [Titanic Advanced Feature Engineering](https://www.kaggle.com/code/gunesevitan/titanic-advanced-feature-engineering-tutorial)

虽然 Titanic 本身与美赛无关，但它适合学习完整的数据检查、特征、交叉验证和提交流程。

### 3. 适合训练美赛能力的竞赛

| 竞赛 | 链接 | 可迁移能力 |
|---|---|---|
| Titanic | <https://www.kaggle.com/competitions/titanic> | 完整入门流程 |
| House Prices | <https://www.kaggle.com/competitions/house-prices-advanced-regression-techniques> | 特征工程、回归和验证 |
| Store Sales | <https://www.kaggle.com/competitions/store-sales-time-series-forecasting> | 时间序列、日历特征和预测 |
| M5 Forecasting | <https://www.kaggle.com/competitions/m5-forecasting-accuracy> | 层级时间序列和不确定性 |

重点学习：

- 训练/验证如何按时间切分；
- 缺失值和异常值如何处理；
- 基线为什么不能省略；
- 为什么高排行榜模型不一定适合解释型论文；
- 如何把结果组织成图表和结论。

不要为了追求排行榜分数而使用复杂的模型堆叠。美赛评委更关心模型是否合理、结果是否解释得通、假设和检验是否完整。

### 4. 公开数据集

- [Kaggle Datasets](https://www.kaggle.com/datasets)
- [World Development Indicators](https://www.kaggle.com/datasets/theworldbank/world-development-indicators)
- [Sustainable Development Goals](https://www.kaggle.com/datasets/theworldbank/sustainable-development-goals)
- [Climate Change: Earth Surface Temperature Data](https://www.kaggle.com/datasets/berkeleyearth/climate-change-earth-surface-temperature-data)

适合：

- E 题的可持续发展、气候和能源分析；
- F 题的国家发展、教育和社会政策分析；
- C 题的表格数据清洗和预测练习。

使用前核对：

- 数据集最后由谁整理；
- 原始来源是什么；
- 更新时间；
- 许可证；
- 缺失值和口径；
- 能否追溯到官方统计网站。

Kaggle 上的转载版不能自动获得“官方数据”的权威性。

### 5. Kaggle Notebooks

链接：<https://www.kaggle.com/code>

用途：

- 阅读别人的数据处理与建模流程；
- 复制一个 Notebook 后修改；
- 使用平台提供的 CPU/GPU 测试代码；
- 查看绘图和解释性分析案例。

比赛风险：

- 网络、运行时间和资源可能变化；
- 外部 Notebook 可能包含数据泄漏或错误验证；
- 比赛期间如果依赖他人实时发布的内容，可能违反“不能向队外人员寻求解题帮助”的规则。

最稳妥的做法是赛前把 Kaggle 上的通用方法转化为自己的代码模板，比赛时只在本地或个人受控环境中运行。

### 6. Kaggle API 和 kagglehub

官方文档：<https://www.kaggle.com/docs/api>

- `kaggle` CLI：适合命令行下载数据和提交；
- `kagglehub`：适合在 Python 工作流中下载 datasets、models 和 competition resources。

使用原则：

- 保存数据集版本和 URL；
- 不要把自己的账号 token 写进代码或仓库；
- 下载后检查许可证和文件完整性；
- 对下载的数据建立校验和或至少保存下载日期。

---

## 四、按美赛题型使用三个平台

| 题型 | Facebook/Meta | Hugging Face | Kaggle |
|---|---|---|---|
| A 连续型 | 基本不用 | 只有在需要神经网络近似或视觉数据时考虑 | 可作为数值计算和可视化练习来源 |
| B 离散型 | 基本不用 | 一般不用 | 可参考组合优化和特征工程 Notebook |
| C 数据洞察 | 通知和少数视觉模型 | 表格、时间序列、文档抽取和图像任务最有价值 | 最核心：课程、数据、Notebook 和竞赛方法 |
| D 运筹/网络 | 基本不用 | 少用 | 地理空间分析、网络特征和可视化 |
| E 可持续性 | Prophet、Meta 数据 | 时间序列、图像和遥感模型 | 世界发展、SDG、气候数据非常有用 |
| F 政策 | COMAP 官方动态 | 文本分类、嵌入、文档抽取 | 社会经济数据和解释性模型 |

---

## 五、推荐的最小学习组合

### 只选 5 项

1. Prophet 官方文档；
2. Kaggle Pandas；
3. Kaggle Data Visualization；
4. Kaggle Intermediate Machine Learning；
5. Hugging Face Tasks。

### 主攻 C/E 题

```text
Kaggle Pandas
→ Data Cleaning
→ Data Visualization
→ Intermediate ML
→ Time Series
→ Prophet 基线
→ Hugging Face 时间序列任务页
→ Kaggle Store Sales / M5 的验证方法
```

### 主攻 D 题

```text
Kaggle Geospatial Analysis
→ NetworkX
→ OpenStreetMap / 官方地理数据
→ Kaggle 地图与分析 Notebook
```

### 主攻 F 题

```text
World Development Indicators / SDG
→ Kaggle 数据清洗和解释性模型
→ Hugging Face 文本分类或文档抽取
→ 官方政策和统计来源复核
```

---

## 六、平台使用的风险与合规

### Facebook

- 不使用 Facebook 群组寻求实时思路；
- 不把群里转发的“O 奖原文”当作已核验版本；
- 官方页面只用来补充通知。

### Hugging Face

- 模型卡不等于质量认证；
- 需核对许可证、训练数据、输入要求和限制；
- 必须与简单基线比较；
- 不能只因为模型下载量高就选它。

### Kaggle

- 数据集许可证各不相同；
- 转载数据要继续追溯原始权威来源；
- Notebook 可能泄漏目标或错误验证；
- 比赛期间不得依赖他人实时发布的解题内容。

### COMAP AI 规则

如果使用了生成式 AI、翻译、嵌入模型、代码助手或其他 AI 工具，应在论文正文引用、在参考文献列明，并在 25 页论文后附 `Report on Use of AI Tools`。工具输出必须经过团队核验。

---

## 七、最终判断

如果比赛只允许保留一个平台账号，我会选择 **Kaggle**，因为它的课程、数据和 Notebook 能最快补齐 C/E/F 题的数据能力。

如果比赛中出现明确的多模态、时间序列或文档抽取任务，再加 **Hugging Face**。

Facebook 只保留 COMAP 官方页面作为公告来源。它不应成为建模、训练或论文资料的主渠道。
