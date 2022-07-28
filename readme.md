# SoC 2022
The repo consists of work done on the Seasons Of Code project (De)Noise
It consists of three directories namely Autoencoder, GANs and SEGAN
- The main project is at SEGAN/
- Autoencoder model can be found at Autoencoder/
- GANs/ consists of basic implementation of GAN

### Timeline 
- We were first given time to revise python and git basics
- Then we were told to do *ML crash course* offered by google to get an overview of ML and Deep Learning (mainly convolutional nueral networks) basics
- Next, we did a Udacity course on Deep Learning with Tensorflow to get used to the tensorflow framework
   * This course contains many topics like Image augmentation, Transfer Learning etc
- Then I had learnt about ResNet (Residual CNNs), where skip connections are implemented to counter the problem of vanishing gradient in nueral networks
which have very deep architecture
- Now, we were told to learn about Generative Adversarial Networks (GANs) and their implementation
- Then I had learnt about Autoencoder model
   * It's architecture is based on CNNs along with skip connections to hold the relevant info to the network
   * It is similar to the Generator's architecture what we would be implementing in the Segan paper later
- Then we were told to read the Segan paper and implement it using what we had learnt till now
### GANs
GANs, known as Generative Adversarial Networks, make use of the adversarial training to develop fake data as close as the real data. For this purpose, **Generator** and **Discriminator** are used. One generates the fake data from a prior distribution and the other tries to predict whether the input data is fake(arised from generator) or the real data. It's mathematical background can be studied [here](https://www.youtube.com/playlist?list=PLdxQ7SoCLQAMGgQAIAcyRevM8VvygTpCu)
A basic implementation of GAN can be found at *GANs/*
### Autoenoder
It consists of encoder, decoder blocks make up of CNNs (has both convolutions and deconvloutions) and skip connections. It is used to reduce noise from the audio clips.
The implementation of Autoencoder can be found at *Autoencoder/*
### SEGAN
This is the main project.
- We were told to implement the [SEGAN](https://arxiv.org/abs/1703.09452) paper.
- It consists of Generator and Discriminator
   * Generator comprises of 22 1d convolution layers of which half are convolution layers and half are deconvolution layers
   * It also has skip connections similar to the Autoencoder model
   * Discriminator as well is a deep convoluted network with a dense layer in the end
- Input and output format
   * The pair (noisydata, cleandata) is considered as real data and (noisydata, predicteddata) is considered to be fake data as stated in the SEGAN research paper
   * The output of generator is same as the input size. Discriminator's output is the prediction 0 or 1
- Loss function used: A custom loss function is defined which comprises of MSE and L1 loss. MSE is used instead of traditional sigmoid to avoid the vanishing gradient problem
- Training:
   * I had trained it for **50 epochs**  by storing checkpoints for every 5 epochs because it's taking too much time to train an epoch even in Google Colab
   * The results will be even better had the model been trained for around more (~ 90 epochs)
