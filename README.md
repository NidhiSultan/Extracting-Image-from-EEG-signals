# Extracting-Image-from-EEG-signals
## Abstract
Consider that we were able to read the human mind, vision, and hearing, and transfer them into a machine. Without any shadow of doubt, this tempting idea can pave the way for quite a few advancements in the technology. Take, for instance; we were able to use human sight in a machine. By doing so, we could use human vision potentials in many machine vision applications. <br />
In general, the goal of this project is reconstructing an digit, seen by a human, from the EEG signals which are captured when the very human was looking at the digit. In particular, I am using MindBigData the "MNIST" of Brain Digits dataset, about which I have explained in the follwoing sections. <br />
To achieve that aim, I have used several deep learning approaches. In the first place, I tried to use transfer learning. Therefore, I read several papers, and I looked at several projects with a similar objective. In the first place, I balanced the dataset, in that it was heterogeneous. In the second place, I used an auto-encoder network to reduce the dimension of the data( then I decided not to use that in the final model!). So far, I have implemented several deep CNNs and LSTMs with different architectures. Note that all of the models are implemented with Teolnsorflow and Keras. Moreover, I used Talos, which is a hyper-parameter optimization tool, to achieve the best model.<br />
Currently, I am working on a decision forest which decides between more than 50 sparse CNNs outputs, all of which are trained with the mentioned dataset, and several other features such as signals mean and standarad deviation.

## Mind big data

This dataset, provided by David Vivancos, is composed of records of 2 seconds of EEG signals using several non-medical grade headsets. During the experiment, the subject was presented digits (0 - 9) on a computer, and tried to focus on the digit for about two seconds. The goal is classifying EEG signals into 10 categories, each of which represent a number between 0 and 9 which is obseverd by the subject. <br />
Data is selected from 14 different location of the brain, the graph of which is shown below.

![alt text](epoc-20-10.jpg) <br />
[http://www.mindbigdata.com/] <br />

## Common LSTM
All 14 channels are fed into the LSTM network, which means that the input shape is 14 * 256. The size of the output of the LSTM layer is 14*1024. Then, it is flatend to 14336 neurons, which are connected to a MLP with 10 layers at output. The network implementaion is available in *CommonLSTM.ipynb*
![alt text](CommonLSTM.jpg) <br />


## Stacked LSTM
All 14 channels are fed into the LSTM networks, which are placed sequentially. Then, the output flatend to 896 neurons, which are connected to a MLP with 10 layers at output. The network implementaion is available in *StackedLSTM.ipynb*


![alt text](StackedLSTM.jpg) <br />


## Per Channel LSTM
Each channel is fed into a specific LSTM network, then the output of all networks are concatinated. Then, the output flatend to 3584 neurons, which are connected to a MLP with 10 layers at output.The network implementaion is available in *PerChanLSTM.ipynb*

![alt text](PerChanLSTM.jpg) <br />


![alt text](PerChanLSTM_2.jpg) <br />
## Sparse Networks with Decision Forest (SNDF)
This section will be completed ASAP. <br />

General Structure of Sparse networks is depicted below:

![alt text](Sparse_CNN.png) <br />

## Results
| Algorithm  | Validaion Accuracy | Network Size |
| ------------- | ------------- | ------------- |
| Common LSTM  | 35.1%  | ------------- |
| Stacked LSTM | 39.7%  | ------------- |
| Per Channel LSTM | 39.6% %  | ------------- |
| 1D CNN | 48%  | ------------- |
| SNDF | ---  | ------------- |


## Note
Feel free to use these codes and documents if it can be helpful for you!
<br />
Author : Ali Abyaneh
## Refrences
- Deep Learning Human Mind for Automated Visual Classification [https://arxiv.org/pdf/1609.00344.pdf] <br />
- Personalized Image Classification from EEG Signals Using Deep Learning [https://upcommons.upc.edu/bitstream/handle/2117/109756/Personalized-Image-Classification-of-EEG-Signals-using-Deep-Learning.pdf]
- Brain2Image:Converting Brain Signals into Images,  I.Kavasidis,S.Palazzo,C.Spampinato,D. Giordano 
- [http://www.mindbigdata.com/] <br />


