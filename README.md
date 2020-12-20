# Kaggle-Riiid-Answer-Correctness-Prediction
Kaggle-Riiid-Answer-Correctness-Prediction

## End Date
### Final Submission Deadline: January 7, 2021 11:59 PM UTC

-------

## Riiid! Answer Correctness Prediction
### Track knowledge states of 1M+ students in the wild

## goal
In this competition, your challenge is to create algorithms for "Knowledge Tracing," the modeling of student knowledge over time. 

### The goal is to accurately predict how students will perform on future interactions. 

You will pair your machine learning skills using Riiid’s EdNet data.


-------

# Evaluation
Submissions are evaluated on area under the ROC curve between the predicted probability and the observed target.

## How to Use ROC Curves and Precision-Recall Curves for Classification in Python
https://machinelearningmastery.com/roc-curves-and-precision-recall-curves-for-classification-in-python/


## Articles

### Receiver operating characteristic
https://en.wikipedia.org/wiki/Receiver_operating_characteristic

### Sensitivity and specificity
https://en.wikipedia.org/wiki/Sensitivity_and_specificity

### Precision and recall
https://en.wikipedia.org/wiki/Precision_and_recall

### Information retrieval
https://en.wikipedia.org/wiki/Information_retrieval

### F-score
https://en.wikipedia.org/wiki/F-score

### ROC and precision-recall with imbalanced datasets
https://classeval.wordpress.com/simulation-analysis/roc-and-precision-recall-with-imbalanced-datasets/


-------

## EdNet

Established in 2020, EdNet is the largest publicly available dataset in the global education sector containing 130M+ interactions from 780K+ users on ‘Santa’, Riiid’s AI-based learning solution. 

Riiid’s mission through EdNet is to drive advancement of cutting-edge AI education technology and advance the industry as a whole. We believe that this initiative will help make optimized, personalized, and thus the most efficient education available to every learner in the world.

### What is EdNet?

EdNet is the dataset of all student-system interactions collected over 2 years by Santa a multi-platform AI tutoring service with more than 780K users in Korea available through Android, iOS and web.

In EdNet, there are four datasets named KT1, KT2, KT3, and KT4 with different extents. In this challenge, we only use EdNet-KT1 datasets consist of students’ question-solving logs, which is the most basic and fundamental information that can be used by various deep-learning knowledge tracing models.

### EdNet: A Large-Scale Hierarchical Dataset in Education
http://ednet-leaderboard.s3-website-ap-northeast-1.amazonaws.com/


-------

## Paper:
### EdNet: A Large-Scale Hierarchical Dataset in Education: 
https://arxiv.org/pdf/1912.03072.pdf

### SAINT+: Integrating Temporal Features for EdNet Correctness Prediction
https://arxiv.org/pdf/2010.12042.pdf

### A Self-Attentive model for Knowledge Tracing
https://arxiv.org/pdf/1907.06837.pdf

### Creating A Neural Pedagogical Agent by Jointly Learning to Review and Assess
https://arxiv.org/pdf/1906.10910.pdf


### Towards an Appropriate Query, Key, and Value Computation for Knowledge Tracing
https://arxiv.org/pdf/2002.07033.pdf



-------

## GitHub:
https://github.com/riiid/ednet


-------


## Progress

Best Score : 0.762


## Modeling

### LGBM

    import lightgbm as lgb

    params = {
        'objective': 'binary',
        'max_bin': 700,
        'learning_rate': 0.0175,
        'num_leaves': 80
    }

    lgb_train = lgb.Dataset(X, y, categorical_feature = ['part', 'prior_question_had_explanation_enc'])
    lgb_eval = lgb.Dataset(X_val, y_val, categorical_feature = ['part', 'prior_question_had_explanation_enc'], reference=lgb_train)



    model = lgb.train(
        params, lgb_train,
        valid_sets=[lgb_train, lgb_eval],
        verbose_eval=50,
        num_boost_round=10000,
        early_stopping_rounds=12
     )

### 'learning_rate': 
    - lr: 0.0175   LB 0.753
    - lr: 0.001    LB 




-------

## Riiid! SAKT Model - Inference - Public
https://www.kaggle.com/manikanthr5/riiid-sakt-model-inference-public

## Riiid! SAKT Model - Training - Public
https://www.kaggle.com/manikanthr5/riiid-sakt-model-training-public


