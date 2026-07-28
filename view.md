## 机器学习指导锌离子超级电容器储能性能预测 论文复现

A Reproduction of Machine learning-guided prediction of energy storage performance of carbon cathode materials for zinc-ion hybrid capacitors

**Paper:** https://doi.org/10.1016/j.jcis.2025.138139  



#### 数据集以及变量 Dataset and variables

A dataset of 624 entries

**Variables:** O,N,SSA,PV,RMIC,Dap,ID/IG,CD

**Target Variable:** Cs # 比容量



#### 使用的模型 Using Modules

**ML Regressors:** 

Support Vector Regression(SVR)/ Random Forest/ LightGBM

**DL Models:** 

Artificial Neural Networks(ANNs), Graph Neural Networks(GNNs), Tab-Transformer

**Extend Models:**

FT-Transformer



#### 数据预处理 Data Preprocess

依据原文逻辑将字符串类型的`Anion` 变量转换为0/1

```python
data["Anion"] = data["Anion"].replace({
    "SO4": 0,
    "OTf": 1
}).astype(int)
```

采用标准化（Standardization），亦称 Z‑score 归一化。





##### Correlation Study

Using Pearson's Correlation Coefficient(PCC) and Spearman's Rank Correlation to analyze data. 

**Analyze Result:**

![pearson_spearman_correlation](F:\projects\paper-review\figures\pearson_spearman_correlation.png)



#### 预期结果 Excepted Train Result As Shown in the Paper

> LightGBM demonstrated best prediction accuracy, achieving a high coefficient of determination value (R2) of 0.986 and a low root mean square error (RMSE) of 4.88 mAh g- 1 on the test set, which highlights its strong potential in predicting ZIHCs performance.   







#### 实际复现结果 

| ML Models | Train R2 | Test R2 | Train RMSE | Test RMSE | Train MSE | Test MAE |
| --------- | -------- | ------- | ---------- | --------- | --------- | -------- |
| RF        | 0.9846   | 0.9017  | 4.8865     | 13.8077   | 3.1881    | 8.7020   |
| LightGBM  | 0.9953   | 0.9572  | 2.7041     | 9.1095    | 2.0496    | 5.1900   |
| SVR       | 0.8661   | 0.7781  | 14.4293    | 20.7395   | 10.3363   | 13.6841  |


| DL Models      | Train R2 | Test R2 | Train RMSE | Test RMSE | Train MSE | Test MAE |
| -------------- | -------- | ------- | ---------- | --------- | --------- | -------- |
| ANN            |          |         |            |           |           |          |
| GNN            |          |         |            |           |           |          |
| TabTransformer |          |         |            |           |           |          |
| FT-Transformer |          |         |            |           |           |          |

#### 

#### SHAP  Feature Importance Analysis

![shap_bar_mean_abs](F:\projects\paper-review\figures\shap_bar_mean_abs.png)

![shap_summary_scatter](F:\projects\paper-review\figures\shap_summary_scatter.png)





