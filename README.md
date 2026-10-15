# Steam Games Recommendation System

An end-to-end recommendation system using Steam user reviews and game metadata to generate personalized game recommendations.

The project explores collaborative filtering, content-based filtering, and hybrid recommendation approaches, with an emphasis on ranking performance and handling sparse user-item interactions.

**Status:** In development — data preparation completed; recommendation modeling in progress.

## Project Overview

The goal is to build a recommendation system that allows users to select several games they enjoy and receive personalized recommendations.

The project focuses on three recommendation approaches:

- **Collaborative filtering:** Identify patterns in user-game interactions to recommend games based on similar preferences.
- **Content-based filtering:** Use game attributes, including tags and descriptions, to identify similar titles.
- **Hybrid recommendations:** Combine collaborative and content-based signals to improve recommendation relevance.

A Streamlit application is planned to provide an interactive interface for generating recommendations.

## Dataset

**Source:** [Game Recommendations on Steam — Kaggle](https://www.kaggle.com/datasets/antonkozyriev/game-recommendations-on-steam)

The original dataset contains approximately 41 million reviews and metadata for more than 50,000 games.

Following data preparation, a smaller development dataset was created to support initial modeling experiments.

| Metric | Prepared Dataset |
|---|---:|
| Users | 50,000 |
| Games | 22,521 |
| User-game interactions | 642,760 |
| Positive reviews | 559,708 (87.08%) |
| Negative reviews | 83,052 (12.92%) |
| Interaction sparsity | 99.94% |

### Data Preparation

The preprocessing workflow includes:

1. Identifying and resolving duplicate user-game reviews using DuckDB and SQL window functions.
2. Selecting users with at least five positive reviews.
3. Sampling 50,000 eligible users while retaining their interaction histories.
4. Examining interaction sparsity, game popularity, and feedback distributions.
5. Exporting the processed dataset to Parquet for subsequent modeling.

The resulting dataset preserves less-popular games to support experiments involving catalog coverage and popularity bias.

## Methodology

### 1. Data Exploration and Preparation — Completed

Analyzed user-game interaction patterns and prepared a reproducible modeling dataset.

**Key findings:**
- The user-item interaction matrix is approximately 99.94% sparse.
- Games with at least 10 reviews account for 92.99% of observed interactions.
- Positive recommendations represent approximately 87% of the sampled reviews.

### 2. Recommendation Modeling — Planned

The modeling workflow will evaluate several approaches:

| Approach | Purpose |
|---|---|
| Popularity baseline | Establish a benchmark using frequently recommended games |
| Collaborative filtering | Learn preferences from user-game interaction patterns |
| Content-based filtering | Recommend games using metadata and similarity |
| Hybrid recommender | Combine behavioral and content-based signals |

Models will be evaluated using ranking metrics such as **Recall@K** and **NDCG@K**, with additional consideration of catalog coverage and cold-start recommendations.

### 3. Interactive Application — Planned

A Streamlit application will allow users to select several favorite games and generate personalized recommendations without requiring a Steam account.

## Technologies

**Languages and data processing:** Python, SQL, pandas, NumPy, DuckDB, Parquet

**Recommendation modeling (planned):** scikit-learn, SciPy, collaborative filtering, matrix factorization

**Application (planned):** Streamlit

**Development:** Git, GitHub, Jupyter Notebook, VS Code

## Repository Structure

```text
Steam-Games-Recommender-Project/
│
├── notebooks/
│   └── 01_data_audit.ipynb
│
├── data/                         # Excluded from Git
│   ├── recommendations.csv
│   ├── games.csv
│   ├── games_metadata.json
│   └── processed/
│       └── sampled_reviews.parquet
│
├── README.md
└── .gitignore
```

**Note:** Raw and processed datasets are excluded from version control. Dataset files can be obtained from the Kaggle source linked above.

## Next Steps

- Implement a popularity-based recommendation baseline.
- Evaluate recommendation performance using held-out user interactions.
- Develop collaborative filtering and content-based models.
- Compare individual approaches against a hybrid recommender.
- Deploy an interactive Streamlit application.

## Future Evaluation Results

Model performance will be reported after completing the recommendation experiments.

| Model | Recall@10 | NDCG@10 |
|---|---|---|
| Popularity baseline | TBD | TBD |
| Collaborative filtering | TBD | TBD |
| Content-based | TBD | TBD |
| Hybrid | TBD | TBD |
