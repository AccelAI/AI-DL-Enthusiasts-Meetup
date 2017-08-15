Live chat

Accel AI​Welcome﻿ Everyone!!

Serdar Aslan​Do you﻿ know good techniques for source seperation which may be a nice nice alternative to ICA? Do you know good autoencoder based ones?

Serdar Aslan​Welcome﻿ by the way.

Serdar Aslan​independent component analyis﻿

Ryan Lambert​yeah﻿ it's within signal processing

Serdar Aslan​yes﻿

Ryan Lambert​it works for﻿ non-gaussian data

Serdar Aslan​For the stacked autoencoder﻿ do you have any guideline to select the neuron numbers in the hidden layers?

Serdar Aslan​For example in the﻿ Hinton work first they increase the neuron number then decrease

Serdar Aslan​what is﻿ the reason for that?

Serdar Aslan​In the﻿ book putting restrictions to the hidden layer is interpreted in probabilistic view. Can you explain more this probabilistic approach?

Serdar Aslan​Laura :)))﻿ Can you ask?

Serdar Aslan​Laura. PCA is a specially case for 1 layer﻿ autoencoder with activation function identity and L2 norm

Serdar Aslan​they are﻿ basically same

Serdar Aslan​in﻿ practice however PCA is more stable

Serdar Aslan​though they are theoretically﻿ same

Serdar Aslan​In this case there is no dimensioality reduction what is the practical use of this﻿ sparse representations?

Pat Ransil​@serdar -﻿ but there is a dim reduction - that is what the sparse penalty ensures

Serdar Aslan​In the hidden layer the﻿ number of neurons are higher than the original input dimension.

Serdar Aslan​The﻿ hidden dimension is higher so no reduction seems.

Pat Ransil​may start that way but should evolve to﻿ 'kill' some

Serdar Aslan​They are always there just in some times﻿ they do not fire. so you need more memory

Serdar Aslan​hidden layer is function﻿ data so this is not a prior.

Serdar Aslan​for that reason it﻿ is not prior knowledge

Serdar Aslan​for that reason it is not usual bayesian aproach this is what﻿ Goodfellow tries to say

Serdar Aslan​function﻿ of data

Serdar Aslan​prior﻿ knowledge does not depend of data

Serdar Aslan​however here as you see﻿ the hidden layer is of function of data.

Serdar Aslan​Do﻿ not much spend on that. Later he still tries to use the same logic

Serdar Aslan​theta is not a function of x. theta is inferred﻿ from x those are different.

Serdar Aslan​here hidden layer value﻿ is exactly function of x that is data.

Serdar Aslan​But﻿ here be careful

Serdar Aslan​log﻿ cannot distribute directly of summation

Serdar Aslan​so use of 14.4 over﻿ 14.3 is not directly possible

Serdar Aslan​there Goodfellow﻿ tries to use one more approximation.

Serdar Aslan​did you﻿ notice that?

Serdar Aslan​In 14.3 he approximated this﻿ sum by an function approximation in the most possible over h

Serdar Aslan​than this sum﻿ reduces to specific h

Serdar Aslan​than Goodfellow﻿ uses 14.4

Serdar Aslan​than one term is the usual L2 cost the other﻿ one is the sparisty condition

Serdar Aslan​that is﻿ all he tries to say

Pat Ransil​@serdar - back to sparse autoencoders. Think of a system where the training data comes from 3 very﻿ different groups. Maybe faces, buildings and handwritten characters.

Pat Ransil​If the goal is identifying specific faces, buildings and chars, a sparse encoder could﻿ train the system to effectively segregate the

Pat Ransil​hidden layers into﻿ 3 populations each only firing for the group it encodes features for.

Serdar Aslan​Yes. In that condition you﻿ are right the specific parts can be lower in dimension.

Serdar Aslan​But is there﻿ a guideline for putting sparisity condition to result in such specific feature which has real world correspondence?

Serdar Aslan​Laura can﻿ the speaker put more emphasis why this probabilistic approach important in terms of generative model?

Pat Ransil​If you have a system that will get a wide range of input types, and need to classify within each type, you﻿ can give the system enough capacity for the overall task, and still train with smaller data

Pat Ransil​sets﻿ for each group without over fitting

Serdar Aslan​14.14﻿

Serdar Aslan​this equation how is differing in﻿ the usual of backpropagation algorithm?

Serdar Aslan​We use uptonow the usual backpropagation for parameter estimation of﻿ the neural network

Serdar Aslan​putting the picture﻿ in probabilistic approach how is it used in terms of weight update of the network?

Serdar Aslan​Laura cn you ask﻿ this?

Accel AI​Ok guys﻿ we are wrapping it up for tonight

Carlos Arturo Pimentel Trujillo​thank﻿ you Laura !!

Serdar Aslan​Bye﻿

Carlos Arturo Pimentel Trujillo​Bye﻿

Pat Ransil​thanks!﻿

Accel AI
Say something...
0/200

