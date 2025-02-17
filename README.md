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

## Paper2:
### Layer Normalization
https://www.cs.utoronto.ca/~hinton/absps/LayerNormalization.pdf


### Knowledge Tracing with Sequential Key-Value Memory Networks
https://arxiv.org/pdf/1910.13197.pdf


-------

## Paper3:

### Attention Is All You Need
https://arxiv.org/pdf/1706.03762.pdf


### NEURAL MACHINE TRANSLATION BY JOINTLY LEARNING TO ALIGN AND TRANSLATE
https://arxiv.org/pdf/1409.0473.pdf

### Massive Exploration of Neural Machine Translation Architectures
https://arxiv.org/pdf/1703.03906.pdf

### Long Short-Term Memory-Networks for Machine Reading
https://arxiv.org/pdf/1601.06733.pdf


### Learning Phrase Representations using RNN Encoder–Decoder for Statistical Machine Translation
https://arxiv.org/pdf/1406.1078.pdf


### Xception: Deep Learning with Depthwise Separable Convolutions
https://arxiv.org/pdf/1610.02357.pdf


-------

## GitHub:
https://github.com/riiid/ednet


-------

## SAKT-pytorch

### Pytorch Implementation of "A Self-Attentive model for Knowledge Tracing" 
https://arxiv.org/abs/1907.06837.

### arshadshk/SAKT-pytorch
https://github.com/arshadshk/SAKT-pytorch

-------

## Modeling

### LGBM
## SAKT with Randomization & State Updates
https://www.kaggle.com/leadbest/sakt-with-randomization-state-updates


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




-------

## Riiid! SAKT Model - Inference - Public
https://www.kaggle.com/manikanthr5/riiid-sakt-model-inference-public

## Riiid! SAKT Model - Training - Public
https://www.kaggle.com/manikanthr5/riiid-sakt-model-training-public

-------

## Riiid LGBM bagging2 + SAKT =0.781
https://www.kaggle.com/ammarnassanalhajali/riiid-lgbm-bagging2-sakt-0-781

### Combining of SAKT with Riiid LGBM bagging2 then remove some features

### Source Kernels:

- SAKT + Riiid LGBM bagging2 LB 0.780

https://www.kaggle.com/leadbest/sakt-riiid-lgbm-bagging2

- SAKT with Randomization & State Updates LB0.771 

https://www.kaggle.com/leadbest/sakt-with-randomization-state-updates

- Riiid! LGBM bagging2 LB0.772 

https://www.kaggle.com/zephyrwang666/riiid-lgbm-bagging2

-------


 
## Progress
### Current Best LB Score: 0.783  
### Private Score: 0.785


-------

## Riiid! SAKT Model - Inference - Public
https://www.kaggle.com/manikanthr5/riiid-sakt-model-inference-public

### MAX_SEQ: default = 100

     MAX_SEQ =  90:  #LB 0.766 (RuntimeError)   ##ver3
     MAX_SEQ = 100:  #LB 0.774                  ##ver1
     MAX_SEQ = 110:  #LB 0.767 (RuntimeError)   ##ver4
     MAX_SEQ = 120:  #LB 0.768 (RuntimeError)   ##ver5
     MAX_SEQ = 160:  #LB 0.767 (RuntimeError)   ##ver2


### self.multi_att = nn.MultiheadAttention(embed_dim=embed_dim, num_heads=8, dropout=0.2)
### Dropout: default=(0.2)

     self.dropout = nn.Dropout(0.2)  #LB 0.774:   ##vere1   #default
     self.dropout = nn.Dropout(0.5)  #LB 0.774:   ##ver10
     self.dropout = nn.Dropout(0.8)  #LB 0.774:   ##ver11
        
### self.layer_normal = nn.LayerNorm(embed_dim, eps=1e-05, elementwise_affine=True) 
### eps: default=1e-05     
        
     self.layer_normal = nn.LayerNorm(embed_dim, eps=1e-05, elementwise_affine=True)  #LB 0.774:    ##vere1  #default
     self.layer_normal = nn.LayerNorm(embed_dim, eps=1e-03, elementwise_affine=True)  #LB 0.774:    ##ver8
     self.layer_normal = nn.LayerNorm(embed_dim, eps=1e-07, elementwise_affine=True)  #LB 0.774:    ##ver9

-------

## Riiid LGBM bagging2 + SAKT =0.781
https://www.kaggle.com/ammarnassanalhajali/riiid-lgbm-bagging2-sakt-0-781

### learning_rate: defaule=0.05
Train: params = {

     learning_rate = 0.05:     #LB 0.781                ##ver2
     learning_rate = 0.005:    #LB error (>9hrs CPU)    ##ver3
     
-------

## SAKT with Randomization & State Updates
https://www.kaggle.com/leadbest/sakt-with-randomization-state-updates

     epochs = 20:  #LB 0.765   ##ver3
     epochs = 40:  #LB 0.758   ##ver4
     
     
-------

## Expanding on Simple LGBM
https://www.kaggle.com/dwit392/expanding-on-simple-lgbm

     lr: 0.1      LB 0.753  ##ver3
     lr: 0.0175   LB 0.753  ##ver1
     lr: 0.001    LB 0.752  ##ver2

--------

## Fork of Riiid LGBM bagging2.1 471152
https://www.kaggle.com/julianguo/fork-of-riiid-lgbm-bagging2-1-471152

     test_df[target]=0.5*np.array(outs)+0.5*np.array(o2)  LB 0.783:  ##ver1
     test_df[target]=0.6*np.array(outs)+0.4*np.array(o2)  LB 0.783:  ##ver2
     test_df[target]=0.4*np.array(outs)+0.6*np.array(o2)  LB 0.783:  ##ver3


### clfs = list()
     params = {
     'learning_rate': 0.5     LB 0.782   ##ver8     
     'learning_rate': 0.05    LB 0.783   ##ver7
     'learning_rate': 0.005   LB 0.774   ##ver9
     
     
-------
