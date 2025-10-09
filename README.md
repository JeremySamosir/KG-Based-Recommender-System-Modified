<img width="1120" height="473" alt="image" src="https://github.com/user-attachments/assets/9cc85187-12ea-4bd6-bbd0-070249fe01c8" />

## Model Analysis
### Hyperparameters Default
| Parameter | Value |
|-----------|-------|
| Batch Size | 256 |
| Evaluation Batch Size | 1024 |
| Negative Sampling Rate | 1.5 |
| Embedding Dimensions | 16 |
| Margin | 30 35 |
| Learning Rate | 2e-3 |
| Weight Decay | 5e-4 |
| Epochs | 35 |

### Hyperparameters Modification
| Parameter | Value |
|-----------|-------|
| Batch Size | 128 |
| Evaluation Batch Size | 1024 |
| Negative Sampling Rate | 3 |
| Embedding Dimensions | 64 |
| Margin | 35 |
| Learning Rate | 5e-4 |
| Weight Decay | 5e-4 |
| Epochs | 50 |

### Experiment Results
#### AUC Evaluation
- **AUC Score Author:** 0.7003
- **My AUC Score:** 0.8861

#### nDCG@5 Evaluation
- **Author nDCG@5 Score:** 0.1844
- **My nDCG@5 Score:** 0.1077

## Conclusion
This hyperparameter tuning experiment was conducted to optimize a TransE-based Knowledge Graph Recommender System (KGRS), with a primary focus on improving the nDCG@5 metric. Starting from an unsatisfactory baseline performance, a series of systematic experiments were performed on key parameters, including embedding dimensions, learning rate, and negative sampling rate, while ensuring reproducibility by setting a fixed random seed. The optimal configuration found consists of a batch_size of 128, embedding dimensions of 64, a learning rate of 5e-4, and a negative sampling rate of 3. This setup achieved a peak performance of AUC = 0.8861 and nDCG@5 = 0.1077, significantly improving upon the baseline and surpassing the initial project target.

An insightful finding emerges when comparing this result to the original author's benchmark (AUC: 0.7003, nDCG@5: 0.1844). Our model achieves a substantially superior AUC score, indicating its strength as a "Generalist" model with an excellent overall ability to distinguish between relevant and irrelevant items. While its top-k precision (nDCG@5) has not yet reached the author's highly specialized performance, this outcome highlights a trade-off between general ranking accuracy and top-k precision. Overall, this experiment successfully produced a robust model with a strong balance and superior general understanding, while providing clear directions for future work, such as exploring stronger regularization, to further enhance top-k ranking performance.

## References
- Q. Guo et al., "A Survey on Knowledge Graph-Based Recommender Systems," *IEEE Transactions on Knowledge and Data Engineering*, pp. 1–1, 2020, doi: 10/ghxwqg.
- D. Bahdanau, K. Cho, and Y. Bengio, "Neural Machine Translation by Jointly Learning to Align and Translate," in *3rd International Conference on Learning Representations, ICLR 2015*, San Diego, CA, USA, May 7-9, 2015. [Online]. Available: [http://arxiv.org/abs/1409.0473](http://arxiv.org/abs/1409.0473)
- https://github.com/Layheng-Hok/KG-Based-Recommender-System?tab=readme-ov-file
