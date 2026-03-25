# Privacy-Preserving Financial Recommendation System (Santander Case Study)
## 1. Business Understanding
Objective: Build a personalized financial product recommender while preserving customer privacy.
Problem: Traditional centralized models conflict with GDPR/CCPA.
Solution: Federated Learning (FL) to train models locally without sharing raw data.
Success Criteria: F1 score > 0.70, explainable recommendations, deployable interface.
## 2. Data Understanding
Dataset: Santander Product Recommendation (50,000 samples, 24 products).
Features: Demographics (age, income, gender), behavior (tenure, activity), product ownership.
Insights:
- Current accounts dominate.
- Majority customers are young (20–30).
- Weak correlation between income and product ownership.
## 3. Data Preparation
Steps:
- Removed duplicates and high-missing columns.
- Imputed missing income values.
- Renamed columns for clarity.
- Standardized numerical features.
Feature Engineering:
- Total products owned
- High-income indicator
## 4. Modeling
Approach: Multi-label classification using OneVsRest Logistic Regression.
Why Logistic Regression:
- Interpretable
- Efficient
- Suitable for FL weight aggregation
Clients:
- Young (≤30)
- Middle (31–50)
- Senior (>50)
## 5. Federated Learning
Framework: Flower (flwr)
Algorithm: Federated Averaging (FedAvg)
Process:
1. Local training on clients
2. Share model weights
3. Aggregate on server
4. Repeat (5 rounds)
Advantage: No raw data sharing → privacy preserved
## 6. Evaluation
Metrics: F1 Score, Precision, Recall
Results:
- Young: 0.9489
- Middle: 0.7036
- Senior: 0.6795
Observation:
- Performance depends on data size
- FL improves smaller clients via shared learning
## 7. Hyperparameter Tuning
Best Parameters:
- C = 1
- Solver = lbfgs
Impact:
- Middle +0.31 F1 improvement
- Senior +0.32 F1 improvement
Conclusion: Critical for smaller datasets
## 8. Deployment
Tools: Gradio + Joblib
Outputs:
- Top product recommendations
- Confidence scores
- Explanations
Use Case: Bank staff or customers interact with system in real time
9. Insights & Business Value
- University segment = biggest cross-sell opportunity
- Product bundling (e.g., payroll + pension)
- Personalized targeting improves engagement
- Privacy compliance builds trust
10. Conclusion & Future Work
Conclusion:
Federated Learning enables accurate, privacy-preserving recommendations.
Future Work:
- Use full dataset (13M records)
- Add differential privacy
- Hybrid recommender systems
- Real-time model updates
