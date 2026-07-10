# capstone-project-part-3
 ⁠part 3 explanation -Model Analysis
Decision Tree Comparison
 Unconstrained (Baseline) Model: This model achieved a training accuracy of 1.0, clearly demonstrating overfitting. It successfully memorized the training data, leading to high variance and poor performance on unseen test data.
 Controlled Model: By applying ⁠max_depth=5⁠ and ⁠min_samples_split=20⁠, the model's training accuracy dropped to 0.625. While this seems like a decrease in performance, it is a necessary step to reduce variance and improve the model's ability to generalize to new data.
 Technical Notes:
 ⁠max_depth⁠ limits how deep the tree grows, effectively preventing the model from capturing noise as a pattern.
 ⁠min_samples_split⁠ ensures nodes are only split if they contain sufficient data, preventing decisions based on small, unrepresentative subsets.
2.⁠ ⁠Gini vs. Entropy Comparison
We experimented with different criteria for node splitting to observe their impact on performance:
 Gini Impurity Formula: 1 - ∑▒〖(P) 〖^2〗i^ 〗
 Entropy Formula: -  pi log2(pi)
 Observation: The Gini criterion performed slightly better in this dataset (0.45 accuracy) compared to Entropy (0.40 accuracy). A Gini impurity of 0 means the node is perfectly pure, meaning all samples in that node belong to a single class.
3.⁠ ⁠Ensemble Modeling: Random Forest
To improve predictive stability, we utilized a Random Forest Classifier.
 Bagging Concept: The model uses bootstrap sampling, where each tree is trained on a random subset of the data with replacement. By averaging the predictions of 100 trees, we significantly reduce the variance inherent in a single, deep decision tree.
 Performance: The Random Forest outperformed the single decision trees, achieving a ROC-AUC score of 0.71.
4.⁠ ⁠Pipeline and Serialization
To ensure the model is reproducible and deployment-ready, we implemented a ⁠scikit-learn⁠ pipeline. This pipeline ensures that the ⁠StandardScaler⁠ preprocessing is applied consistently before the model makes predictions. The final model was serialized into the ⁠best_model.pkl⁠ file using ⁠joblib⁠ for future use.
5.⁠ ⁠Summary 
Model                                                 training accuracy                     test/roc-auc score
Baseline decisoin tree                                      1.0                                     N/A
Controlled decision tree                                   0.625                                    N/A
Gini criterion tree                                         N/A                                     0.45
Entropy criterion.                                          N/A                                     0.40
<img width="468" height="648" alt="image" src="https://github.com/user-attachments/assets/6c879299-dc8e-4f33-8a5b-0cc5c211d1cf" />
