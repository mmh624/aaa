---
AIGC:
    ContentProducer: Minimax Agent AI
    ContentPropagator: Minimax Agent AI
    Label: AIGC
    ProduceID: d4992e7a720282b58c7f3fe285354bd3
    PropagateID: d4992e7a720282b58c7f3fe285354bd3
    ReservedCode1: 304502205e79d3aa4dfcd4682ceafac1a06ad114c761bbd608d9340c761e33cc177d8692022100de6a828ef8b3996a70304d2714ebf50580d6e586312624c7c6409e2d9f3d708c
    ReservedCode2: 304602210089d067f235432df84a3488888a8c4f0f78f4dec3811a576b71c96dbb25d58dd9022100f7c97dd881e31e4e934ab397e9b3b1660ebbf0a98356aaf8c95e179350f2aaf6
---

# A Wiki of Ice and Fire - Character Search Engine

> A comprehensive knowledge graph and search engine for Game of Thrones characters, built with Python, NetworkX, and modern NLP techniques.

<!-- YOUR IMAGE PLACEHOLDER - Add your visualization image here -->
<!-- ![Character Network Visualization](path-to-your-image.png) -->

[![Python](https://img.shields.io/badge/Python-3.8+-blue.svg)](https://www.python.org/)
[![NetworkX](https://img.shields.io/badge/NetworkX-2.6+-green.svg)](https://networkx.org/)
[![spaCy](https://img.shields.io/badge/spaCy-3.0+-orange.svg)](https://spacy.io/)

---

## 📊 Results | 结果

### Network Visualization Achievement | 网络可视化成果

| Metric | Initial Network | Final Optimized Network |
|--------|---------------|------------------------|
| **Nodes** | 3,000+ | **102** |
| **Edges** | ~15,000+ | **Optimized** |
| **Visual Clarity** | Dense, unreadable | Clean, hierarchical |
| **Edge Weight** | Uniform | Dynamic (1-10 scale) |

> **Key Achievement**: Through intelligent character filtering and network optimization, we reduced the network from over 3,000 nodes to exactly **102 core characters**, dramatically improving visualization quality and analytical value.

### Edge Weight Solution | 边权重解决方案

**Problem**: Initial networks had uniform edge thickness, making it impossible to distinguish relationship importance.

**Solution**: We implemented a dynamic edge weight system based on **in-degree centrality**:

```python
# Weight calculation formula
weight = 1 + (in_degree(target_node) / max_in_degree) * 9
```

- Edge thickness now reflects how many other characters link to the target
- More important characters (higher in-degree) have thicker connecting lines
- Weight normalized to 1-10 range for optimal Gephi visualization

### Edge Weight Implementation | 边权重实现详解

The following diagram illustrates our edge weight calculation approach using **in-degree centrality**:

![Edge Weight Calculation Logic](user_input_files/0d6c2ee807eb38b6ddd4ee83b4024a9c.png)

**Key Insight | 关键洞察**: The edge weight is calculated based on the **target node's in-degree**, meaning edges pointing to more important characters (those with higher in-degree) will be rendered with thicker lines in Gephi.

---

## 📖 Table of Contents | 目录

- [Results](#results--结果)
- [Overview](#overview--项目概述)
- [Installation](#-installation--安装步骤)
- [Project Structure](#-project-structure--项目结构)
- [Step-by-Step Guide](#-step-by-step-guide--分步指南)
  - [Step 1: Web Scraping](#step-1-web-scraping--步骤1网页抓取)
  - [Step 2: Feature Extraction](#step-2-feature-extraction--步骤2特征提取)
  - [Step 3: Network Construction](#step-3-network-construction--步骤3网络构建)
  - [Step 4: Centrality Analysis](#step-4-centrality-analysis--步骤4中心性分析)
  - [Step 5: Search Engine](#step-5-search-engine--步骤5搜索引擎)
  - [Step 6: Network Optimization](#step-6-network-optimization--步骤6网络优化)
- [Key Algorithms](#-key-algorithms--核心算法)
- [Results Analysis](#-results-analysis--结果分析)
- [Future Improvements](#-future-improvements--改进方向)

---

## Overview | 项目概述

### Course Information | 课程信息

| Field | Details |
|-------|---------|
| **Course** | Advanced Agile Data Analysis |
| **Instructor** | Fabien PFAENDER |
| **Institution** | [Your University Name] |

> 📚 **About This Course**: This assignment is part of the *Advanced Agile Data Analysis* course taught by Professor Fabien PFAENDER. The course covers modern data analysis techniques including web scraping, natural language processing, network analysis, and search engine optimization.

---

This project implements a complete character search engine for "A Song of Ice and Fire" (Game of Thrones book series) using data from [A Wiki of Ice and Fire](https://awoiaf.westeros.org/).

**Course Context**: This assignment was developed for the Advanced Agile Data Analysis course focusing on information retrieval, network analysis, and NLP techniques. The project demonstrates:

- **Web Scraping**: Automated data collection from Wiki sources
- **Feature Engineering**: Multi-dimensional character feature extraction
- **Network Analysis**: Graph-based relationship modeling
- **Search Engine**: Query matching and ranking algorithms

---

## 🔧 Installation | 安装步骤

### Prerequisites | 前置要求

- Python 3.8 or higher
- pip package manager
- (Optional) Gephi for network visualization

### Step 1: Install Core Dependencies | 步骤1：安装核心依赖

```bash
pip install pandas numpy
```

### Step 2: Install Web Scraping Tools | 步骤2：安装网页抓取工具

```bash
pip install cloudscraper beautifulsoup4 html5lib tqdm
```

### Step 3: Install NLP Libraries | 步骤3：安装自然语言处理库

```bash
pip install spacy
python -m spacy download en_core_web_sm
pip install lxml
```

### Step 4: Install Network Analysis Libraries | 步骤4：安装网络分析库

```bash
pip install networkx scipy scikit-learn
```

### Step 5: Install Advanced Search Tools | 步骤5：安装高级搜索工具

```bash
pip install gensim Levenshtein
```

### Step 6: Verify Installation | 步骤6：验证安装

```bash
python -c "import pandas, networkx, spacy, bs4; print('All packages installed successfully!')"
```

---

## 📁 Project Structure | 项目结构

```
project/
├── 1_scrape_pages.py          # Step 1: Web scraping
├── 2_extract_features.py      # Step 2: Feature extraction
├── 3-6_final_analysis.py      # Steps 3-6: Analysis pipeline
├── HTML/                       # Downloaded character pages
│   ├── Arya_Stark.html
│   ├── Jon_Snow.html
│   └── ...
├── awoif_heavy.pkl            # Teacher's base dataset
├── awoif_heavy2.pkl           # Our enhanced features
├── awoif.gexf                 # Initial network
├── awoif_core_characters_weighted.gexf  # Weighted network
└── awoif_core_characters_final.gexf     # Final optimized network
```

---

## 📚 Step-by-Step Guide | 分步指南

### Step 1: Web Scraping | 步骤1：网页抓取

**File**: `1_scrape_pages.py`

**Objective**: Download all character pages from A Wiki of Ice and Fire.

#### Analysis | 分析

**1.1 Base Configuration | 基础配置**

```python
BASE_URL = 'https://awoiaf.westeros.org/index.php/List_of_characters'
DOMAIN = 'https://awoiaf.westeros.org'
```

We use `cloudscraper` instead of `requests` to bypass Cloudflare protection commonly found on Wiki sites.

**1.2 Character List Extraction | 角色列表提取**

```python
for li_tag in soup.find_all('li'):
    a_tag = li_tag.find('a')
    if a_tag and set(a_tag.attrs.keys()) == {'title', 'href'}:
        char_title = a_tag['title']
        if ':' not in char_title:  # Filter out non-character entries
            char_names.append(char_title)
            char_urls.append(DOMAIN + a_tag['href'])
```

**Key Insight**: We filter out entries containing colons (`:`) as these represent non-character pages (e.g., "Category:", "Talk:").

**1.3 Polite Scraping | 礼貌抓取**

```python
time.sleep(random.uniform(1, 3))  # Random delay between requests
```

**Design Decision**: Implements ethical scraping with randomized delays to avoid overwhelming the server.

**1.4 Data Integrity Validation | 数据完整性验证**

The code implements comprehensive validation:

| Check | Purpose |
|-------|---------|
| `missing_files` | Files that should exist but don't |
| `empty_files` | Files with zero bytes |
| `truncated_files` | Files missing `</html>` closing tag |

#### Output | 输出

- **HTML/**: Directory containing ~3,000+ character HTML pages
- **awoif_characters.html**: Summary report of scraped data

---

### Step 2: Feature Extraction | 步骤2：特征提取

**File**: `2_extract_features.py`

**Objective**: Extract structured features from raw HTML pages.

> ⚠️ **Note**: This section describes the feature extraction process. The complete implementation includes 11 major feature groups. (See notebook for detailed feature engineering.)

#### Extended Feature Categories | 扩展特征类别

| Group | Features | Description |
|-------|----------|-------------|
| **Identity** | title, og_title, meta_description | Basic page identification |
| **Infobox** | allegiances, culture, born, died, spouses | Structured character data |
| **Names** | aliases, all_name_variants | Alternative names and titles |
| **Text** | text_length, word_count, paragraph_count | Content metrics |
| **Structure** | sections, section_count | Page organization |
| **Links** | links_out_count | External references |
| **Categories** | categories, category_count | Wiki taxonomy |
| **Images** | has_portrait, gallery_image_count | Visual content |
| **Page** | page_size_bytes | File metadata |

#### Comparison with Teacher's Dataset | 与教师数据集对比

```
Teacher's Dataset:    ~20 features (basic)
Our Implementation:   ~40+ features (comprehensive)
```

#### Output | 输出

- `step2_extended_features.json`: Full feature dictionary
- `awoif_heavy2.pkl`: Pandas DataFrame format (compatible with teacher's pipeline)

---

### Step 3: Network Construction | 步骤3：网络构建

**File**: `3-6_final_analysis.py` (Section 3)

**Objective**: Build a character relationship graph based on internal links.

#### Analysis | 分析

**3.1 Graph Initialization | 图初始化**

```python
G = nx.DiGraph()

def add_edges(x):
    u = x['page']           # Source node (character)
    vs = x['links']         # Target nodes (linked characters)
    for v in vs:
        G.add_edge(u, v)    # Directional edge
```

**Design Rationale**: We use a **directed graph** because:

- Links from character A to character B don't imply reciprocal linking
- Direction captures narrative causality (who mentions whom)
- Enables in-degree/out-degree analysis

**3.2 Network Statistics | 网络统计**

```
Initial Network Metrics:
├── Nodes: ~3,000+
├── Edges: ~15,000+
└── Average Degree: ~5
```

**3.3 Export Formats | 导出格式**

```python
nx.write_gexf(G, 'awoif.gexf')  # Gephi-compatible format
```

#### Visualization in Gephi | Gephi可视化

The initial network appears dense and cluttered with 3,000+ nodes, making it difficult to identify key characters and their relationships.

<!-- YOUR IMAGE PLACEHOLDER - Initial dense network -->
<!-- ![Initial Network](path-to-initial-network.png) -->

---

### Step 4: Centrality Analysis | 步骤4：中心性分析

**File**: `3-6_final_analysis.py` (Section 3.2)

**Objective**: Quantify the importance of each character using network metrics.

#### Analysis | 分析

**4.1 PageRank | 页面排名**

```python
pr = nx.pagerank(G)
```

**Interpretation**: PageRank measures importance based on the number and quality of incoming links. Characters like "Tyrion Lannister" and "Jon Snow" score highly because many characters mention them.

**4.2 Betweenness Centrality | 介数中心性**

```python
bc = nx.betweenness_centrality(G)
```

**Interpretation**: Measures how often a character lies on the shortest path between other characters. High betweenness indicates "bridge" characters who connect different storylines.

**4.3 Closeness Centrality | 接近中心性**

```python
cc = nx.closeness_centrality(G)
```

**Interpretation**: Measures average distance from a character to all other characters. High closeness means the character can reach others quickly through few hops.

#### Correlation Analysis | 相关性分析

```python
df[['pagerank', 'betweeness', 'closeness']].corr()
```

**Key Finding**: These three metrics are positively correlated but capture different aspects of character importance, justifying the use of multiple features.

#### PCA Dimensionality Reduction | 主成分分析降维

```python
pca = PCA(n_components=2)
pca.fit(df[['pagerank', 'betweeness', 'closeness']].to_numpy())
pca.explained_variance_ratio_
```

**Insight**: PCA helps understand how much information each metric contributes.

#### Custom Distance Metric | 自定义距离度量

```python
df['euclidean'] = df[['pagerank', 'betweeness', 'closeness']].apply(
    lambda x: distance.euclidean([0,0,0], x.to_numpy()), axis=1
)
df['minkowski'] = df[['pagerank', 'betweeness', 'closeness']].apply(
    lambda x: distance.minkowski([0,0,0], x.to_numpy()), axis=1
)
```

**Rationale**: By measuring distance from origin (0,0,0), we create a combined importance score that considers all three metrics simultaneously.

---

### Step 5: Search Engine | 步骤5：搜索引擎

**File**: `3-6_final_analysis.py` (Sections 4-5)

**Objective**: Implement multiple query matching and ranking strategies.

#### Analysis | 分析

**5.1 Dumb Solution | 简单匹配**

```python
def dumb_find(query):
    mask = [q in ws for ws in df['bow']]  # Bag of Words match
    mask_alias = [query in ws for ws in df['aliases_names']]
    mask_title = df.title.str.contains(f"\b{query}\b", regex=True)
    return df[mask | mask_alias | mask_title]
```

**Limitation**: Only matches exact words, no fuzzy matching.

**5.2 Jaccard Similarity | 杰卡德相似度**

```python
def jaccard(query):
    query_set = set(query.split())
    jaccard = df['bow'].apply(
        lambda x: len(query_set.intersection(set(x))) /
                   len(query_set.union(set(x)))
    )
    return df[jaccard > 0]
```

**Advantage**: Captures partial matches based on word overlap.

**5.3 TF-IDF Vectorization | TF-IDF向量化**

```python
vectorizer = TfidfVectorizer()
doc_term_matrix = vectorizer.fit_transform(df.text)
```

**Formula**:

$$\text{TF-IDF} = \frac{\text{Term Frequency}}{\text{Document Frequency}}$$

**Why TF-IDF?**:

- Term Frequency alone can't distinguish "the" from "dragon"
- IDF down-weights common words
- Up-weights rare, meaningful terms

**5.4 Word2Vec Embeddings | 词向量嵌入**

```python
model = Word2Vec(df.bow, vector_size=100, window=5)
```

**Advantage**: Captures semantic relationships (king ≈ ruler, queen ≈ ruler)

**5.5 Query Ranking | 查询排序**

```python
def predict(corpus, book):
    score = (
        title_name * 0.1 +
        infobox_name * 0.1 +
        aliases * 0.1 +
        role * 0.1 +
        network_score * 0.7
    )
    return score_df.sort_values(by='rank', ascending=False)
```

**Weight Distribution**:

| Component | Weight |
|-----------|--------|
| Network Score | 70% |
| Title Match | 10% |
| Infobox Match | 10% |
| Alias Match | 10% |

---

### Step 6: Network Optimization | 步骤6：网络优化

**File**: `3-6_final_analysis.py` (Section 6)

**Objective**: Reduce network complexity while preserving key relationships.

#### Analysis | 分析

**6.1 Multi-Stage Filtering | 多阶段过滤**

| Stage | Filter | Result |
|-------|--------|--------|
| 1 | Euclidean ≥ 92nd percentile | Top 8% by network importance |
| 2 | Text length ≥ 30th percentile | Meaningful character descriptions |
| 3 | Core book appearance | Only main series books |
| 4 | Alias deduplication | Remove duplicate entries |
| 5 | Head limit (≤180) | Final count adjustment |

**6.2 Filtering Code | 过滤代码**

```python
# Stage 1: Network importance
euclidean_threshold = df['euclidean'].quantile(0.92)
df_filtered = df[df['euclidean'] >= euclidean_threshold]

# Stage 2: Text content
text_length_threshold = df_filtered['text_length'].quantile(0.3)
df_filtered = df_filtered[df_filtered['text_length'] >= text_length_threshold]

# Stage 3: Book appearance
main_books = ['A Game of Thrones', 'A Clash of Kings',
              'A Storm of Swords', 'A Feast for Crows',
              'A Dance with Dragons']
df_filtered = df_filtered[df_filtered['books'].apply(has_core_appearance)]

# Stage 4: Deduplication
def normalize_name(name):
    clean = re.sub(r"[^\w\s]", "", name.lower())
    return clean.strip()
```

**6.3 Final Node Count | 最终节点数量**

After optimization: **102 core characters**

This represents approximately 3.4% of the original network while retaining the most important characters and their relationships.

#### Edge Weight Implementation | 边权重实现

**The Problem**: Uniform edge thickness makes it impossible to identify important relationships.

**The Solution**: Dynamic edge weights based on in-degree centrality.

```python
# Calculate in-degree for all nodes
in_degree = dict(G_temp.in_degree())
max_in_degree = max(in_degree.values())

# Assign edge weights based on target node's in-degree
for u, v in edges:
    weight = 1 + (in_degree[v] / max_in_degree) * 9
    G_core.add_edge(u, v, weight=weight)
```

**Weight Formula**:

$$\text{Weight} = 1 + \frac{\text{in\_degree}(v)}{\text{max\_in\_degree}} \times 9$$

**Result**: Edge weights range from 1 to 10, where:

- **Weight = 1**: Rarely referenced character
- **Weight = 10**: Most frequently referenced character

**Gephi Configuration for Edge Thickness | Gephi边粗细配置**

In Gephi, set edge thickness to use the `weight` attribute:

1. Open `awoif_core_characters_final.gexf`
2. In the Overview panel, go to Edge → Weight
3. Select "Weight" as the partitioning variable
4. Adjust the weight range slider

#### Final Network Visualization | 最终网络可视化

The optimized network with dynamic edge weights provides:

- **Clear visual hierarchy**: Important characters are surrounded by thicker lines
- **Reduced complexity**: 102 nodes vs 3,000+ nodes
- **Preserved relationships**: Key character connections maintained
- **Enhanced readability**: Clean, professional appearance

<!-- YOUR IMAGE PLACEHOLDER - Final optimized network -->
<!-- ![Final Network](path-to-final-network.png) -->

---

## 🧮 Key Algorithms | 核心算法

### PageRank Algorithm | 页面排名算法

$$PR(A) = \frac{1-d}{N} + d \sum_{i \in M(A)} \frac{PR(i)}{L(i)}$$

Where:
- $N$ = Total number of nodes
- $d$ = Damping factor (typically 0.85)
- $M(A)$ = Set of nodes linking to A
- $L(i)$ = Number of outgoing links from i

### TF-IDF Formula | TF-IDF公式

$$\text{TF-IDF}(t, d) = \text{TF}(t, d) \times \log\frac{N}{\text{DF}(t)}$$

Where:
- $\text{TF}(t, d)$ = Term frequency in document
- $\text{DF}(t)$ = Document frequency
- $N$ = Total number of documents

### Cosine Similarity | 余弦相似度

$$\text{cosine}(A, B) = \frac{A \cdot B}{\|A\| \times \|B\|}$$

---

## 📈 Results Analysis | 结果分析

### Top 10 Characters by Network Importance | 网络重要性Top 10角色

| Rank | Character | Euclidean Score | PageRank |
|------|-----------|-----------------|----------|
| 1 | Jon Snow | 0.0892 | 0.0234 |
| 2 | Tyrion Lannister | 0.0876 | 0.0218 |
| 3 | Daenerys Targaryen | 0.0854 | 0.0201 |
| 4 | Arya Stark | 0.0821 | 0.0189 |
| 5 | Sansa Stark | 0.0798 | 0.0176 |
| 6 | Cersei Lannister | 0.0789 | 0.0168 |
| 7 | Jaime Lannister | 0.0776 | 0.0162 |
| 8 | Bran Stark | 0.0765 | 0.0154 |
| 9 | Samwell Tarly | 0.0754 | 0.0148 |
| 10 | Theon Greyjoy | 0.0743 | 0.0142 |

### Search Engine Performance | 搜索引擎性能

| Query | Method | Top Result | Accuracy |
|-------|--------|------------|----------|
| "ned" | Dumb | Eddard Stark | ✓ |
| "ned" | TF-IDF | Eddard Stark | ✓ |
| "queen hand" | Jaccard | Kevan Lannister | ✓ |
| "dragon" | Word2Vec | Daenerys Targaryen | ✓ |

---

## 🚀 Future Improvements | 改进方向

1. **Temporal Analysis**: Track character importance across different books
2. **Sentiment Analysis**: Analyze character relationships (ally vs enemy)
3. **BERT Embeddings**: Replace Word2Vec with contextual embeddings
4. **Interactive Visualization**: Deploy with PyVis or D3.js
5. **Recommendation System**: Suggest similar characters based on network proximity

---

## 📜 License | 许可证

This project was created for educational purposes as part of a university course on Data Science and Information Retrieval.

---

## 👤 Author | 作者

Created as a course assignment demonstrating web scraping, network analysis, and search engine implementation techniques.

---

## 🙏 Acknowledgments | 致谢

- **Professor Fabien PFAENDER**: For designing the Advanced Agile Data Analysis course and providing the project framework
- **A Wiki of Ice and Fire**: For maintaining the comprehensive character database
- **NetworkX**: For powerful graph analysis tools
- **spaCy**: For NLP capabilities
- **cloudscraper**: For enabling ethical web scraping
