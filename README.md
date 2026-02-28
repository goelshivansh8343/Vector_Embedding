🔍 Semantic Search & Recommendation System Using Word2Vec📌
Project Overview
This project builds an intelligent semantic search and article recommendation system using Word2Vec embeddings. The model is trained from scratch on the BBC News full-text dataset, comprising 2,225 real English news articles across five distinct categories.Unlike traditional keyword-based search (which relies on exact word matches), this system understands the latent meaning of text—allowing it to find relevant articles even when the query and the document do not share the exact same vocabulary.
🗂️ Dataset InformationSource: 
BBC Full-Text Document Classification (Kaggle)
Folder Structure
The system expects the following directory layout after extraction:
Plaintextbbc-fulltext 
(document classification)/
├── business/ (e.g., 001.txt, 002.txt...)
├── tech/
├── sport/
├── entertainment/
└── politics/
Total Articles: 2,225Format: Raw .txt files containing full news stories.
🧠 System Pipeline
The architecture follows a standard NLP pipeline from raw data to multidimensional visualization:
Data Ingestion: Auto-detects the BBC folder structure.
Preprocessing: Lowercasing, punctuation removal, stopword filtering (80+ words), and tokenization.
Model Training: Word2Vec Skip-Gram model trained from scratch (100 dimensions, window=5, 100 epochs).
Vectorization: Sentence vectors generated via Mean Pooling of word embeddings.
Downstream Tasks: * Semantic Search: Ranks articles by Cosine Similarity to a query string.
Recommendation: Finds the top-N semantically similar articles for a given seed article.
Visualization: Dimensionality reduction via PCA and t-SNE.🛠️ 
Technology Stack
ComponentTechnologyLanguagePython 3.11+Embedding ModelWord2Vec (Gensim) — Skip-GramSimilarity MetricCosine Similarity (Scikit-learn)Dimensionality ReductionPCA, t-SNE (Scikit-learn)VisualizationMatplotlib, SeabornData HandlingPandas, NumPy📁 Project File StructurePlaintextproject/
├── LPU_Project8_Semantic_Search.ipynb  # Main Notebook (Run this)
├── README.md                           # Project Documentation
├── bbc-fulltext/                       # Dataset folder
└── outputs/                            # Generated Visualizations
    ├── pca_visualization.png
    ├── tsne_visualization.png
    ├── similarity_heatmap.png
    └── word_similarity_bars.png
⚙️ Setup & Installation1. Clone the ProjectBashgit clone https://github.com/goelshivansh8343/embedding.git
cd embedding
2. Install DependenciesBashpip install gensim scikit-learn matplotlib seaborn pandas numpy
3. Run the SystemOpen the .ipynb file in Jupyter Notebook or VS Code and run all cells from top to bottom.Note: If the dataset is not found, the notebook includes a 100-article built-in fallback so the code will still execute successfully.🔎 Key Features & Modules🔹 Module 1: PreprocessingGraceful fallback to sample data if Kaggle dataset is missing.Robust text cleaning to ensure high-quality embeddings.🔹 Module 2: Embedding GenerationMean Pooling: Converts variable-length articles into fixed-length 100D vectors.🔹 Module 3: Search & RecommendationSemantic Search: Accepts plain English queries (e.g., "smartphone internet").Recommendation: Article-to-article similarity, excluding the source article.🔹 Module 4: Advanced Visualizationst-SNE & PCA: 2D scatter plots colored by category to show how the model "groups" topics.Heatmaps: 20×20 pairwise similarity matrices for a deep dive into document relationships.📊 Sample Search OutputQuery: 'smartphone internet mobile technology'RankCategoryScorePreview#1TECH0.9312Mobile phone sales hit record high as smartphone manufacturers...#2TECH0.91875G network rollout accelerates as telecoms operators...#3TECH0.8934Broadband speeds slow as demand for internet access rises...🆚 Comparison: Keyword vs. Semantic SearchFeatureKeyword Search (TF-IDF/Regex)This System (Word2Vec)Matching MethodExact word matchSemantic meaningHandles Synonyms❌ No✅ YesContext Awareness❌ No✅ YesVisualizationNonePCA + t-SNE + HeatmapsRecommendationNone✅ Article-to-article
