## Hierarchical Invariant Learning for Domain Generalization Recommendation

## 1 Abstract

Most cross-domain recommenders require samples on target domains or source-target overlaps to carry out domain adaptation. However, in many real-world situations, target domains are lack of such knowledge. Seldom work discusses this problem, whose essence is domain generalization recommendation. In this paper, we figure out domain generalization recommendation with a clear symbolized defination and propose corresponding models. Moreover, we illustrate its strong connection with zero-shot recommendation, pretrained recommendation and cold-start recommendation, distinguishing it from content-based recommendation. By analyzing its properties, we propose HIRL+ and a series of heuristic methods to solve this problem. We propose hierarchical invariant learning to expel the specific patterns in both domain-level and environment-level and find the common patterns in generalization space. To make divisions flexible, fine-grained and balanced, we put forward a learnable environment assignment. To improve model robustness against distribution shifts inside domain generalization, we present an adversarial environment refinement. In addition, we conduct experiments on real-word datasets to verify the effectiveness of our models, and carry out further studies on domain distance and domain diversity. To benefit the research community and promote this direction, we have released our project at https://anonymous-hirl.github.io/HIRL.

## 2 Contributions

In conclusion, the main contributions of this paper can be summarized as follows:

- We give a clear symbolized definition of domain generalization recommendation, which can be considered as a new type of method for cold-start problem, pretrained recommendation and zero-shot recommendation.

- We prepose HIRL to obtain common and significant patterns on more fine-grained environment level. We propose learnable environment assignment to make divisions flexible and balanced. We further improve robustness against distribution mismatch by proposing adversarial environment refinement. We put forward HIRL+ with the three components, which is effective on domain generalization recommendation task.

- We conduct experiments on several datasets to compare our model with baselines, and analyse the results. We carry out further studies on domain distance and domain diversity, and we release our project at Github.

## 3 Dataset Overview

| Dataset       | #User   | #Item  | #Inter  | #Domain |
| ------------- | ------- | ------ | ------- | ------- |
| CloudTheme-10 | 61,856  | 23,604 | 99,113  | 10      |
| CloudTheme-20 | 107,439 | 44,097 | 172,119 | 20      |
| CloudTheme-50 | 234,444 | 89,386 | 378,641 | 50      |
| KuaiRec-8     | 6,971   | 3,984  | 113,288 | 8       |
| KuaiRec-16    | 7,151   | 8,465  | 189,221 | 16      |
| KuaiRec-all   | 7,166   | 8,809  | 216,784 | 20      |



## 4 Quick Start

### Step 1: Download the project

First of all, download our project `HIRL_project.zip` from [Github](https://github.com/anonymous-hirl/HIRL/tree/main/project) and unzip the file. The file includes both codes and datasets.

### Step 2: Create the running environment

Create `Python 3.9` enviroment and install the packages that the project requires.
- numpy==1.23.5
- scikit_learn==1.2.0
- torch==1.13.0

You can install the packages with the following command.

```
    pip install -r requirements.txt
```

### Step 3: Run the project

Choose a dataset to run (e.g. kuairec_8) and a model (e.g. DNN) to run with the following command.

```
    python run.py DNN dataset/kuairec_8.pickle DNN_kuairec_8 hidden_dim1 16 hidden_dim2 16 batch_size 1024 lr 0.05 epoch 10 
```

You can also use `quick_start.py` to run the project conveniently.

```
    python quick_start.py
```

You can also change the hyper-parameters as you want. The necessary hyper-parameters for each model have been recorded in the `hyper_parameters.py`.

### Step 4: Check the performance

The performance will be saved in `result` dictionary. The first column is the running time. The second column is the name of models. The third to the fourth columns are metrices `NDCG@10, HR@10` in order.


## 5 Hyper-parameters search range

We tune hyper-parameters accordingly, and the common hyper-parameters are presented on the following table.

| Hyper-parameter     | Explanation | Range |
| ------------------- | ---------------------------------------------------- | ------------------- |
| embedding_dim   | dimension of profiles      | \{16, 32, 64, 128\}             |
| hidden_dim1     | dimension of hidden layer1 | \{16, 32, 64, 128\}             |
| hidden_dim2     | dimension of hidden layer2 | \{16, 32, 64, 128\}             |
| lr              | learning rate of model     | \{0.001, 0.01, 0.05, 0.1, 0.2\} |
| batch_size      | batch size of model        | \{64, 128, 256, 512, 1024\}     |

As different base models have different hyper-paramerters to tune, you can view the details in the corresponding model files.
