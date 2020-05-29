Dialogue
=============================

2019百度知识驱动对话竞赛参赛模型

[比赛链接][1]
## Requirements

* cuda=9.0
* cudnn=7.0
* python>=3.6
* pytorch>=1.0
* tqdm
* numpy
* nltk
* scikit-learn

## Reproduce the result

### Prepare data

Put the data provided by the organizer under the data folder and rename them  train/dev/test.txt: 

```
./data/resource/train.txt
./data/resource/dev.txt
./data/resource/test.txt
```

### Execute the generate process
We train GRU、LSTM、TextCNN、Transformer as different encoders and decoders to ensemble

**train**
```
python preprocess.py
python train.py

```

**test**
```
python predict.py
```


### Execute the rerank process
We extract semantic features and put them into XGBoost model, rank and select the best one as the ﬁnal response.

**create dataset**
```
python rank/create_dataset.py
python rank/feature_util.py
```

**train**
```
python rank/train.py
``` 

**test**
```
python rank/predict.py
```




  [1]: http://lic2019.ccf.org.cn/talk