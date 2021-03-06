# Attentive Filtering Network
This repository contains codes to reproduce the core results from our ICASSP 2019 paper: [Attentive Filtering Networks for Audio Replay Attack Detection](https://arxiv.org/pdf/1810.13048.pdf)
 
<p align="center">
 <img src="github_image/attention_filter_network.png" width="40%">
</p>

If you find the code useful, please cite
```
@inproceedings{lai2018attentive,
  title={Attentive Filtering Networks for Audio Replay Attack Detection},
  author={Lai, Cheng-I and Abad, Alberto and Richmond, Korin and Yamagishi, Junichi and Dehak, Najim and King, Simon},
  booktitle={2019 IEEE International Conference on Acoustics, Speech and Signal Processing (ICASSP)},
  year={2019},
  organization={IEEE}
}
```

## Abstract 
An attacker may use a variety of techniques to fool an automatic speaker verification system into accepting them as a genuine user. Anti-spoofing methods meanwhile aim to make the system robust against such attacks. The ASVspoof 2017 Challenge focused specifically on replay attacks, with the intention of measuring the limits of replay attack detection as well as developing countermeasures8.pdf against them. In this work, we propose our replay attacks detection system - Attentive Filtering Network, which is composed of an attention-based filtering mechanism that enhances feature representations in both the frequency and time domains, and a ResNet-based classifier. We show that the network enables us to visualize the automatically acquired feature representations that are helpful for spoofing detection. Attentive Filtering Network attains an evaluation EER of 8.99% on the ASVspoof 2017 Version 2.0 dataset. With system fusion, our best system further obtains a 30% relative improvement over the ASVspoof 2017 enhanced baseline system.

## Single Model Benchmark Results
Note: Results are on the ASVspoof 2017 Version 2.0 Dataset. Each result is averaged over 8 separate runs. 

|            Model             | dev EER (%) | eval EER (%) |  Diff  | 
| :--------------------------: | :---------: | :----------: |  :--:  |
| Attentive Filtering Network  |    6.55     |     8.99     |**2.44**|
|   Dilated Residual Network   |    7.49     |    10.16     |  2.67  |
|   Modulation Dynamic Features|    -        |   **6.32**   |  -     |
| qDFTspec                     |    -        |    11.43     |  -     |
| CQCC-GMM(CMVN)               |    9.06     |    12.24     |  3.18  |
| i-vectors (cosine similarity)|    8.99     |    14.77     |  5.78  |
| i-vectors (Gaussian class.)  |    8.81     |    15.11     |  6.30  |
| Light CNN                    |  **6.47**   |    16.08     |  9.61  |
| Evolving RNN                 |   18.70     |    18.20     |  -0.50 |
| CQCC-GMM                     |   12.08     |    29.35     |  17.27 |


## Visualization of attention heatmaps with different non-linearities
sigmoid
![sigmoid](github_image/sigmoid.png)

tanh
![tanh](github_image/tanh.png)

softmaxF (softmax on feature dimension)
![softmaxF (softmax on feature dimension)](github_image/softmaxF.png)

softmaxT (softmax on time dimension)
![softmaxT (softmax on time dimension)](github_image/softmaxT.png)

## Dependencies
This project uses Python 2.7. Before running the code, you have to install
* [PyTorch 0.4](https://pytorch.org/)
* [Kaldi](https://github.com/kaldi-asr/kaldi)

## Getting Started 
1. Download the [ASVspoof 2017 Dataset](http://www.asvspoof.org/index2017.html)
2. Extract features with [Kaldi](https://github.com/kaldi-asr/kaldi). Follow the file to extract logspec and i-vector features. 
```
./run_feature.sh 
```
3. Change the argumenents in run.sh and point them to your feature files. 

## Model Training 
```
./run.sh 0
```
Note: 
1. main.py contains detials of the training details and configurations
2. src/attention_neuro/simple_attention_network.py contains the implementation of Attentive Filtering Network.

## Visualizing Attention
```
./run.sh 1
```

## Model Forward Passing
```
./run.sh 2
```

## Authors 
Cheng-I Lai, [Alberto Abad](https://www.l2f.inesc-id.pt/w/Alberto_Abad_Gareta), Korin Richmond, [Junichi Yamagishi](https://nii-yamagishilab.github.io), [Najim Dehak](https://engineering.jhu.edu/ece/faculty/najim-dehak/), [Simon King](http://homepages.inf.ed.ac.uk/simonk/)

If you encouter any problem, feel free to contact me. 
