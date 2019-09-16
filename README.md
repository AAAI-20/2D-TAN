# 20_AAAI

In  this  paper,  we  study  the  problem  of  moment  localization  with  natural  language,  and  propose  a  novel  2D  Temporal Adjacent Networks(2D-TAN) method. 
The core idea is to retrieve a moment on a two-dimensional temporal map, which considers adjacent moment candidates as the temporal context. 
2D-TAN is capable of encoding adjacent temporal relation, while learning discriminative feature for matching video moments with referring expressions. 
Our model is  simple  in  design  and  achieves  competitive  performance in  comparison  with  the  state-of-the-art  methods  on  three benchmark datasets.

## Framework
![alt text](imgs/pipeline.jpg)

## Main Results

#### Main results on Charades-STA 
| Method | Rank1@0.5 | Rank1@0.7 | Rank5@0.5 | Rank5@0.7 |
| ---- |:-------------:| :-----:|:-----:|:-----:|
| Pool | 39.70 | 23.31 | 80.32 | 51.26 |

#### Main results on ActivityNet Captions 
| Method | Rank1@0.3 | Rank1@0.5 | Rank1@0.7 | Rank5@0.3 | Rank5@0.5 | Rank5@0.7 |
| ---- |:-------------:| :-----:|:-----:|:-----:|:-----:|:-----:|
| Pool | 59.45 | 44.51 | 26.54 | 85.53 | 77.13 | 61.96 |

#### Main results on TACoS
| Method | Rank1@0.1 | Rank1@0.3 | Rank1@0.5 | Rank5@0.1 | Rank5@0.3 | Rank5@0.5 |
| ---- |:-------------:| :-----:|:-----:|:-----:|:-----:|:-----:|
| Pool | 47.59 | 37.29 | 25.32 | 70.31 | 57.81 | 45.04 |

## Prerequisites
- pytorch 1.1.0
- python 3.7
- torchtext
- easydict
- terminaltables


## Quick Start

#### Get the code
Codes are compressed into an encrypting .zip file. 
The password is our **paper ID** + **the 2nd word in our abstract**.
For example, if the paper id is "1234" and the abstract is "We handle the problem of ...", then the password is "1234handle".

To run our code, please run the following command first:

```
wget https://github.com/AAAI-20/2D-TAN/blob/master/code.zip
unzip code.zip
# Entering the password
cd code
```

#### Download Datasets

Next, download the visual features using the following commands. This step may take a long time.

##### Charades-STA
```
cd data/Charades-STA & sh download.sh
```

##### ActivityNet Captions
```
cd data/ActivityNet & sh download.sh
```
##### TACoS
Please download the visual features from [onedrive](https://1drv.ms/u/s!AtyV4r55ASuFde7VFGqWYGvZbKw?e=UuqAyn) and save it to the `data/TACoS` folder. 

## Evaluation

Download all the trained model from [onedrive](https://1drv.ms/u/s!AtyV4r55ASuFaln3b5PjwUhksTo?e=M5jShM) and save them to the `checkpoints` folder.

Then, run the following commands to evaluate our trained models: 
```
# Evaluate "Pool" in Table 1
python moment_localization/test.py --cfg experiments/charades/2D-TAN-16x16-pool.yaml --verbose --split test

# Evaluate "Pool" in Table 2
python moment_localization/test.py --cfg experiments/activitynet/2D-TAN-64x64-pool.yaml --verbose --split test

# Evaluate "Pool" in Table 3
python moment_localization/test.py --cfg experiments/tacos/2D-TAN-128x128-pool.yaml --verbose --split test
```
