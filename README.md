# Kaggle-Riiid-Answer-Correctness-Prediction
Kaggle-Riiid-Answer-Correctness-Prediction

## End Date
### Final Submission Deadline: January 7, 2021 11:59 PM UTC

## Riiid! Answer Correctness Prediction
### Track knowledge states of 1M+ students in the wild

## goal
In this competition, your challenge is to create algorithms for "Knowledge Tracing," the modeling of student knowledge over time. 

### The goal is to accurately predict how students will perform on future interactions. 

You will pair your machine learning skills using Riiid’s EdNet data.

## Evaluation
Submissions are evaluated on area under the ROC curve between the predicted probability and the observed target.



## EdNet

Established in 2020, EdNet is the largest publicly available dataset in the global education sector containing 130M+ interactions from 780K+ users on ‘Santa’, Riiid’s AI-based learning solution. 

Riiid’s mission through EdNet is to drive advancement of cutting-edge AI education technology and advance the industry as a whole. We believe that this initiative will help make optimized, personalized, and thus the most efficient education available to every learner in the world.


### Paper:
EdNet: A Large-Scale Hierarchical Dataset in Education: 

https://arxiv.org/pdf/1912.03072.pdf


### GitHub:
https://github.com/riiid/ednet


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


