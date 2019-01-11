# SQUEEZENET: ALEXNET-LEVEL ACCURACY WITH 50X FEWER PARAMETERS AND <0.5MB MODEL SIZE

## Paper:
### 1 Introduction
Smaller CNN architecture advantages:

- Smaller CNNs require less communication across servers during distributed training.

- Smaller CNNs require less bandwidth to export a new model from the cloud to an autonomous car.

- Smaller CNNs are more feasible to deploy on FPGAs and other hardware with limited memory.

FPGA - a field programmable gate array. 

Video: https://youtu.be/8POZhFHxBLs

Semiconductor devices that are based around a matrix of configurable logic blocks (CLBs) connected via programmable interconnects. FPGAs can be reprogrammed to desired application or functionality requirements after manufacturing. This feature distinguishes FPGAs from Application Specific Integrated Circuits (ASICs), which are custom manufactured for specific design tasks. 

An FPGA can be used to solve any problem which is computable. Their advantage lies in that they are sometimes significantly faster for some applications because of their parallel nature and optimality in terms of the number of gates used for a certain process. Specific applications of FPGAs include digital signal processing, software-defined radio, ASIC prototyping, medical imaging, computer vision, speech recognition, cryptography, bioinformatics, computer hardware emulation, radio astronomy, metal detection and a growing range of other areas.

### 2 Related Work

2.1 Model Compression

Take an existing CNN model and compress it in a lossy fashion to preserve accuracy with fewer parameters. 

Approaches:

- Apply singular value decomposition (A matrix represented as the product of three matrices).

    * SVD Reference Video: 1976 Matrix Singular Value Decomposition Film
    * Reference Image: http://images.slideplayer.com/16/5189063/slides/slide_6.jpg

- Network Pruning, which begins with a pretrained model, then replaces parameters that are below a certain threshold with zeros to form a sparse matrix, and finally performs a few iterations of training on the sparse CNN

- Network Pruning with quantization (to 8 bits or less) and huffman encoding to create an approach called Deep Compression, and further designed a hardware accelerator called EIE that operates directly on the compressed model, achieving substantial speedups and energy savings.


2.2 CNN MICROARCHITECTURE

CNN microarchitecture to refer to the particular organization and dimensions of the individual inception modules.

VGG - deep convolutional network for object recognition developed and trained by Oxford's renowned Visual Geometry Group (VGG), which achieved very good performance on the ImageNet dataset.

GoogleNet - 
The GoogLeNet papers propose Inception modules, which are comprised of a number of different dimensionalities of filters, usually including 1x1 and 3x3, plus sometimes 5x5.

Reference Video: https://youtu.be/_XF7N6rp9Jw

- Won Imagenet challenge in 2014 for efficiency and practicality
12 times lesser parameters than Alexnet from 2012

- Significantly more accurate

- Lower memory-use and lower power-use acutely important for mobile devices

- Computational cost “less than 2x compared to AlexNet”
Intuition behind the Inception Module

- Cluster neurons according to the correlation statistics in the dataset

- We already know that, in lower layers, there exists high correlations in image patches that are local and near local
These can be covered by 1x1 convolutions

- Architecture is a combination of all the convolutions, the 1x1, 3x3, 5x5 (filters), as input to the next stage

- Since max-pooling had been successful, it suggests adding a pooling layer in parallel

- Conceptually, the inception module is a concatenation across three convolutional scales

2.3 CNN MACROARCHITECTURE

CNN macroarchitecture as the system-level organization of multiple modules into an end-to-end CNN architecture. 

Specifically the impact of depth (number of layers) in networks.

ResNet-  Deep residual learning for image recognition.

Propose the use of connections that skip over multiple layers, for example additively connecting the activations from layer 3 to the activations from layer 6. We refer to these connections as bypass connections.

Reference Video: https://youtu.be/C6tLw-rPQ2o

- Over 152 layers deep cnn

- Just stacking more layers is not enough

- At 156 layers, higher training and testing error

- You can turn a plain net into a Resnet by adding identity shortcut connections

- Deep ResNets can be trained without difficulties

- Deeper ResNets can have lower training error, and also lower test error

- ResNet also good feature extractors

- Applications:

    * Visual Recognition
    * Image Generation
    * Speech Recognition
    * Advertising, user prediction

2.4 NEURAL NETWORK DESIGN SPACE EXPLORATION

Much of the work on design space exploration (DSE) of NNs has focused on developing automated approaches for finding NN architectures that deliver higher accuracy.

* Bayesian optimization
* Simulated annealing
* Randomized search
* Genetic algorithms

Each of these papers provides a case in which the proposed DSE approach produces a NN architecture that achieves higher accuracy compared to a representative baseline. However, these papers make no attempt to provide intuition about the shape of the NN design space.

### 3 SQUEEZENET

3.1 ARCHITECTURAL DESIGN STRATEGIES

STRATEGIES:

- Replace 3x3 filters with 1x1 filters.
    * 1x1 filter has 9X fewer parameters than a 3x3 filter reducing budget
- Decrease the number of input channels to 3x3 filters.
- Downsample late in the network so that convolution layers have large activation maps.


THE FIRE MODULE

A Fire module is comprised of: a squeeze convolution layer (which has only 1x1 filters), feeding into an expand layer that has a mix of 1x1 and 3x3 convolution filters


THE SQUEEZENET ARCHITECTURE

SqueezeNet begins with a standalone convolution layer (conv1), followed by 8 Fire modules (fire2-9), ending with a final conv layer (conv10). We gradually increase the number of filters per fire module from the beginning to the end of the network. SqueezeNet performs max-pooling with a stride of 2 after layers conv1, fire4, fire8, and conv10; these relatively late placements of pooling are per Strategy 3 from Section 3.1.


### 7 CONCLUSIONS

- 50× fewer parameters than AlexNet and maintains AlexNet-level accuracy on ImageNet

- compressed SqueezeNet to less than 0.5MB, or 510× smaller than AlexNet without compression

- Gschwend has developed a variant of SqueezeNet and implemented it on an FPGA
    * Gschwend was able to able to store the parameters of a SqueezeNet-like model entirely within the FPGA and eliminate the need for off-chip memory accesses to load model parameters





