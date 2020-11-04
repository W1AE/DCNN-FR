# Deep Networks with Fast Retraining

## Abstract:  

Recent work [1] has utilized Moore-Penrose (MP) inverse in deep convolutional neural network (DCNN) training, which achieves better generalization performance over the DCNN with a stochastic gradient descent (SGD) pipeline. However, the MP technique cannot be processed in the GPU environment due to its high demands of computational resources. This paper proposes a fast DCNN learning strategy with MP inverse to achieve better testing performance without introducing a large calculation burden. We achieve this goal through an SGD and MP inverse-based two-stage training procedure. In each training epoch, a random learning strategy that controls the number of convolutional layers trained in backward pass is utilized, and an MP inverse-based batch-by-batch learning strategy is developed that enables the network to be implemented with GPU acceleration and to refine the parameters in dense layer. Through experiments on image classification datasets with various training images ranging in amount from 3,060 (Caltech101) to 1,803,460 (Place365), we empirically demonstrate that the fast retraining is a unified strategy that can be utilized in all DCNNs. Our method obtains up to 1\% Top-1 testing accuracy boosts over the state-of-the-art DCNN learning pipeline, yielding a savings in training time of 15\% to 25\% over the work in [1].

[1] Yimin Yang, Q.M.Jonathan Wu, et al., “Recomputation of dense layers for the performance improvement of dcnn,” IEEE Trans. Pattern Anal. Mach. Intell., 2019.

## Full-text
arXiv: [Deep Networks with Fast Retraining](https://arxiv.org/abs/2008.07387)

## Learning Structure:

<img src="https://github.com/W1AE/DCNN-FR/blob/master/1.jpg" width="700" height="400" />
Step 1 - Random learning with SGD. In each epoch, users randomly activate La number of convolutional layers, while excluding the rest Li number of convolutional layers from backward pass. La and Li are determined by a predefined hyperparameter ra.

<img src="https://github.com/W1AE/DCNN-FR/blob/master/2.jpg" width="700" height="400" />
Step 2 - Retraining with MP inverse-based batch-by-batch strategy. \eta^n and \eta^{n-1} are obtained by Procedure I, while e^{n-1} and e^{n-2} are received via Procedure II. The details for Procedure I and II can be found from Algorithm 1.

## Downloads:
### Caltech-256
* Caltech-256 dataset: [Caltech-256](http://www.vision.caltech.edu/Image_Datasets/Caltech256/#Download)
* Code: [Code-for-Caltech](https://github.com/wandongzhang/FR/blob/master/Demo0.zip)
* Code for Reproducing Results in Author Response: [Code-for-Caltech](https://github.com/wandongzhang/FR/blob/master/Demo1.zip)

## Dependencies:
* Matlab version 2020a,
* A workstation with a 256GB memory and an E5-2650 processor.

## Reproduce the experimental results

Run script "main_ResNet_ori.m" for original SGD optimization, "main_ResNet_ori_RL.m" for SGD plus random convolutional learning, "main_ResNet_FR.m" for Yang's retraining strategy, or "main_ResNet_FR_RL.m" for the proposed fast retraining algorithm (random SGD plus batch-by-batch MP).

Run script "main1.m", "main2.m", "main3.m", "main4.m", "main5.m", "main6.m" in "Demo1.zip"for reproducing results reported in the author response letter.

#The code is released in content-obscured version (p files). After acceptance of the manuscript (if decided so), the source code will be made public.
