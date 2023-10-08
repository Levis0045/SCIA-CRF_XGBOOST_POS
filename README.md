# Sangkak session septembre 2023

Contextualize CRF/XGBOOST and Linguistic based feature for POS detection in Ghomala

- CRF

- XGBOOST

- Position to position augmentation algorithm


# Get Masakhane POS dataset for project

- if not exist, create data source folder for POS in this repository

```sh

mkdir data_source
cd data_source

```

- clone Masakhane POS dataset in `data_source` folder

```sh

git clone https://github.com/masakhane-io/masakhane-pos.git

```

- if you want to experiment with main dataset produce by NTeALan teams, use this folder instead: `lacuna_ntealan_data` (you will need to split the dataset)

# Install Python dependencies

- Reproduice poetry environnement

```sh

poetry install --only dev && poetry shell

or 

pip install -r requirements.txt

```


# Run all my mlflow experimentations

- Reproduice all my mlflow experimentations 

```sh

./run_experiments.sh

```

# Run CRF mlflow experimentations

- CRF usage

```
python3 experimentations/mlflow_crf.py --help

usage: mlflow_crf.py [-h] [--lang LANG] [--augment] [--description DESCRIPTION]
                     [--re-organised-data] [--shuffle] [--iter ITER] [--c2 C2]
                     [--algo ALGO] [--c1 C1]

sklearn CRF Sangkak

options:
  -h, --help            show this help message and exit
  --lang LANG           language of training data
  --augment             Augment training data
  --description DESCRIPTION
                        description of experiment
  --re-organised-data   re-organised data of training
  --shuffle             shuffle training data
  --iter ITER           number of iterations
  --c2 C2               c2 regularization value for algorithm (default: 0.3)
  --algo ALGO           crf algorithm (default: lbfgs)
  --c1 C1               c1 regularization value for algorithm (default: 0.0920512484757745)

```

- CRF run sample

```sh

    python3 experimentations/mlflow_crf.py --lang bbj --description "crf: iter 100" --iter 100

```

# Run XGBOOST mlflow experimentations


- XGBOOST usage


```sh

python3 experimentations/mlflow_xgboost.py --help

usage: mlflow_xgboost.py [-h] [--lang LANG] [--augment] [--description DESCRIPTION] [--shuffle]
                         [--early_stop EARLY_STOP] [--learning-rate LEARNING_RATE]
                         [--colsample-bytree COLSAMPLE_BYTREE] [--subsample SUBSAMPLE] [--reg-alpha REG_ALPHA]
                         [--reg-lambda REG_LAMBDA] [--n-estimators N_ESTIMATORS] [--nthread NTHREAD]
                         [--n-jobs N_JOBS]

XGBoost Sangkak

options:
  -h, --help            show this help message and exit
  --lang LANG           language of training data
  --augment             Augment training data
  --description DESCRIPTION
                        description of experiment
  --shuffle             shuffle training data
  --early_stop EARLY_STOP
                        number of early_stopping round
  --learning-rate LEARNING_RATE
                        learning rate to update step size at each boosting step (default: 0.3)
  --colsample-bytree COLSAMPLE_BYTREE
                        subsample ratio of columns when constructing each tree (default: 1.0)
  --subsample SUBSAMPLE
                        subsample ratio of the training instances (default: 1.0)
  --reg-alpha REG_ALPHA
                        L1 regularization (default: 0)
  --reg-lambda REG_LAMBDA
                        L2 regularization (default: 1.8)
  --n-estimators N_ESTIMATORS
                        n_estimators (default: 10060)
  --nthread NTHREAD     nthread (default: 1.8)
  --n-jobs N_JOBS       n_jobs (default: 10060)

```

- XGBOOST run sample

```sh

    python3 experimentations/mlflow_xgboost.py --lang bbj --description "xgb: n_estimator 5060 + lr=0.01" --n-estimators 5060 --learning-rate 0.01

```


# Analyse mlflow experimentations (web ui)

- launch mlflow server

```sh

    mlflow ui

```

- open this link to your webserver

```sh

    http://127.0.0.1:5000

```