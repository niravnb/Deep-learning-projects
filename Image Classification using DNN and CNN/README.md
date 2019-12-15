# Image Classification

Topics: ANN, CNN

ANN:
1. Check your data, if features mean, std varies too much, then normalize it
2. For high features, check cumulative variance explained, for too many features, first do dimensionality reduction
3. Randomly sample mini-batch, randomly initialize weight to some small values.
4. Experiment on validation data set with the number of neurons in the hidden layer, and also with number of hidden layers
5. Adam, momentum works better in most cases
6. Experiment with activation functions --- tanh could perform better compared to sigmoid
7. Issues - Divide by zero (add small constant), number (double) overflow issues with loss, activation function

CNN:
8.  implemented Batch Normalization, dropout, data augmentation, guided backpropagation, t-SNE visualization, and fooling.

9. Data Augmentation: Scaling, Flipping, Rotating, adding noise, lightning condition, shifting, etc

10. Initialization: The neurons in the hidden layer become symmetric if the weights are initialized to zero. On the other hand, if the weights are large, the algorithm might end up in a plateau which implies that the learning will become very slow. The biases, on the other hand, has been initialized with zeros. This initialization technique also ensures that the initial weights are small, by multiplying them with some constant which is inversely proportional to the number of neurons in the network. (Xavier/He/random)

11. Batch Normalization:  As normalizing the inputs before passing it onto a model helps in effective training, similarly, for every hidden layer, we can normalize the activations so as to make the training of weights and biases more efficient. In deep networks, small changes to the network gets resonated down the network which causes the input distribution to the hidden layers to shift. Batch normalization reduces the amount by which values of the hidden layers shift around. This is also known as internal covariate shift. It also has a slight regularization effect as it adds some noise to the hidden layer’s activations.

12. Dropout: Dropout is a regularization technique where in each training phase, individual neurons are either ignored(or dropped) with a probability p or considered(or kept) with probability p, such that a reduced network remains. Dropout effectively prevents over-fitting as a fully connected layer occupies most of the parameters. The neurons, in this case, develop co-dependency amongst each other during training. Introducing dropouts, enable each neuron to learn some feature of the data independently of the other neurons in that layer.

13. Visualizing Convolutional Layers, Embedding the codes with t-SNE (t-SNE stands for t-distributed stochastic neighbor embedding. It is a non-linear dimensionality reduction technique and is often used in machine learning for visualizing higher dimensional data)

14. Guided Backpropagation, Fooling with noise

15. Hyperparameters: Number Of Layers, Filter Size, Learning Rate, Activation Functions (ReLu activation function works best with CNN models as opposed to sigmoid or tanh), Optimization Algorithms, Batch Normalization, Dropout, Data Augmentation (works like a regularization technique, -- better generalization)

16.  Bigger batch size can speed up the learning but could perform worse than lower batch size, so if increase batch size by 4, also increase learning rate by 4. (Keras has reduce learning rate of plateau)
