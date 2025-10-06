<div align=center>
   
# Knowledge Graph-Based Recommender System (KGRS)

</div>

This project focuses on building a **Knowledge Graph-Based Recommender System** to enhance user-item interaction predictions. The system utilizes structured knowledge to improve recommendation accuracy, overcoming limitations of traditional approaches.

The README below is just an overview of the project. For details, please refer to the [report](https://github.com/Layheng-Hok/KG-Based-Recommender-System/blob/main/reference/KGRS_Report.pdf).

## Introduction
A recommender system is a type of information filtering system that seeks to predict and show the preferences of a user, offering tailored suggestions for items such as books, movies, or music based on their browsing and selection history. These systems utilize algorithms and data analysis to provide personalized recommendations, enhancing user experience and engagement.

Knowledge Graph (KG)-based recommender system technology uses knowledge graphs as auxiliary information to improve the accuracy and explain-ability of the result of recommendations. Knowledge graphs, which are heterogeneous graphs with nodes representing entities and edges representing relationships, help to illustrate the relationships between items and their attributes, and integrate user and user-side information, capturing the relationships between users and items, as well as user preferences, more accurately.

## Problem Definition
Given a knowledge graph and a set of interaction records the system predicts user-item interactions:

- **U:** Set of users
- **W:** Set of items
- **t_train^uw:** Binary interaction label (1 = interested, 0 = not interested)
- **f(u, w):** Scoring function predicting user **u**'s interest in item **w**

### Optimization Goals
1. Maximize **AUC (Area Under the Curve)**:

$$
\underset{f}{\max} \ \text{AUC}(f, \mathcal{Y}_{\text{test}})
$$

2. Maximize **nDCG@5 (Normalized Discounted Cumulative Gain at rank 5)**:

$$
\underset{f}{\max} \ nDCG@5(f, \mathcal{Y}_{\text{test}})
$$

## Model Analysis
### Hyperparameters
| Parameter | Value |
|-----------|-------|
| Batch Size | 256 |
| Evaluation Batch Size | 1024 |
| Negative Sampling Rate | 1.5 |
| Embedding Dimensions | 16 |
| Margin | 30 |
| Learning Rate | 2e-3 |
| Weight Decay | 5e-4 |
| Epochs | 35 |

### Hyperparameters i used
| Parameter | Value |
|-----------|-------|
| Batch Size | 256 |
| Evaluation Batch Size | 1024 |
| Negative Sampling Rate | 1.5 |
| Embedding Dimensions | 16 |
| Margin | 30 |
| Learning Rate | 2e-3 |
| Weight Decay | 5e-4 |
| Epochs | 50 |

### Experiment Results
#### AUC Evaluation
- **AUC Score:** 0.7003
- Higher embedding dimensions improve performance but may overfit.

#### nDCG@5 Evaluation
- **nDCG@5 Score:** 0.1844
- Ranking accuracy is influenced by hyperparameter selection.

### My Experiment Results
#### AUC Evaluation
- **AUC Score:** 0.8494

#### nDCG@5 Evaluation
- **nDCG@5 Score:** 0.0953

## Conclusion
The conducted experiment successfully validated the potential of this Knowledge Graph-based recommender, surpassing the initial benchmark's predictive performance after a critical flaw in the evaluation methodology was resolved. The most significant finding was the importance of randomly shuffling the data before splitting, which corrected initial anomalies and confirmed the model benefits from more data. The final result was a very strong AUC score of 0.8494, outperforming the original 0.7003 benchmark and demonstrating a superior ability to differentiate between user preferences.

However, this predictive strength did not fully align with ranking performance, where the nDCG@5 score of 0.0953 was significantly lower than the 0.1844 benchmark. This discrepancy indicates that while the model excels at the binary classification task (like/dislike), it is less optimal at ordering the most relevant top items. Future work could focus on improving the nDCG score by tuning hyperparameters that influence relative scoring, such as margin and neg_rate, or by exploring more rank-oriented loss functions.

## References
- Q. Guo et al., "A Survey on Knowledge Graph-Based Recommender Systems," *IEEE Transactions on Knowledge and Data Engineering*, pp. 1–1, 2020, doi: 10/ghxwqg.
- D. Bahdanau, K. Cho, and Y. Bengio, "Neural Machine Translation by Jointly Learning to Align and Translate," in *3rd International Conference on Learning Representations, ICLR 2015*, San Diego, CA, USA, May 7-9, 2015. [Online]. Available: [http://arxiv.org/abs/1409.0473](http://arxiv.org/abs/1409.0473)
- https://github.com/Layheng-Hok/KG-Based-Recommender-System?tab=readme-ov-file
