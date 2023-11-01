# Answers

## Part 1

### Q1

$$outSize = 1*1*((x-k+2p)/s+1)*((y-k+2p)/s+1)$$
$$nbWeights = k*k*z (+1 \textit{bias}$$
$$nbWeightsFull = (x*y*z)*outSize$$

### Q2

++ smaller 
++ equivariant to transformations

-- local input so loses precision

### Q3

Get a small amount of translational invariance at each level. Reducing the number of inputs to the next layer of
feature extraction

### Q4

all until fully connected

### Q5

kernel = 4*image
padding assez grand

### Q6

Then we can use all the network. 

TODO: If we can calculate the output, what is its shape and interest ?

### Q7

1st: 224x224 - the entire image
2nd: 128x128 - A quarter of the image
deeper layers will corresponds to smaller and smaller part of the image. This is tuning, we first have a global vue on the image and then focus on smaller and smaller details.

## Part 2

### Q8

$$padding = 2$$
$$stride = 1$$

### Q9

$$padding = 0$$
$$stride = 2$$


### Q10

conv1:
    $$outputSize = 32*32*32$$
    $$nbWeights = 32*(5*5 + 1)$$, $$+1$$ for bias

pool1:
    $$outputSize = 32*16*16$$
    $$nbWeights = 0$$, no learning parameters for pooling

conv2:
    $$outputSize = 64*16*16$$
    $$nbWeights = 64*(5*5 + 1)$$, $$+1$$ for bias

pool2:
    $$outputSize = 64*8*8$$
    $$nbWeights = 0$$, no learning parameters for pooling

conv3:
    $$outputSize = 64*8*8$$
    $$nbWeights = 64*(5*5 + 1)$$, $$+1$$ for bias

pool3:
    $$outputSize = 64*4*4$$
    $$nbWeights = 0$$, no learning parameters for pooling

fc4:
    $$outputSize = 1000$$
    $$nbWeights = 1000*(64*4*4 + 1)$$, $$+1$$ for bias

fc3:
    $$outputSize = 10$$
    $$nbWeights = 10*(1000+1)$$, $$+1$$ for bias

TODO: Comment on this repartition

### Q11

$$totalNbWeights = (32*(5*5 + 1)) + 2*(64*(5*5 + 1)) + (1000*(64*4*4 + 1)) + (10*(1000+1))$$

$$totalNbWeights = 1,039,170 >> 50,000 = nbImages$$
So it would have been better if the dataset was bigger.

### Q12

TODO: Compare the number of parameters to learn with that of the BoW and SVM approach.

### Q14

For the train set, we use backpropagation and the chain rule to calculate the loss but we only use forward for the test set.

### Q16

The learning rate tweak the speed of the learning. If it is too high the model will miss the minimum for the loss, and if it is too low, the model will be super slow to learn.
The batch-size is the number of element used to recompute the error at every epoch. The bigger it is, the better the model will be but it will be very slow to compute for each epoch. If the batch-size is too low, the model will underfit.

### Q17

At the start of the first epoch, the error is about $$2.3$$ for the train set and $$2.0$$ for the test set. The weights are initialized at random so the first loss can be anything. However, the loss for the test set will be a bit smaller than the one for the train set because the model has been tuned once before running on the test set.

### Q18

The error on the test set is getting bigger and bigger. This is overffiting. The model tries to perfectly fit the input of the train sets which is not what we want.

## Part 3

### Q19

It still overfits but a bit later.

### Q20 

Validation is used for testing the model. When we willl test on unknown data, we won't use their mean value either. So to test the model properly, we have to consider our validation set as a real test set and then not use their values to compute the mean and standard deviation of the dataset.

### Q21

TODO:

### Q22

TODO:

### Q23

If the image is already symmetrical it is useless.

### Q24

If in the batches the model always select images that are close to each other, it might find descriptions that are too specific to this base image.













