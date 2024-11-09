## **Part 1: Artificial Neural Networks (ANN)**

In this part you will learn:

1. The Intuition of ANNs
2. How to build an ANN

# Ann Intuitionn

## **Activation Functions**


1. The sigmoid function, x is the value of weighted sums. used in logistic regression, it is smooth. very useful output, final layer when you’re trying to predict probabilities. 
2. tanh, goes below 0. 

![Screenshot 2024-10-30 at 16.39.19.png](https://prod-files-secure.s3.us-west-2.amazonaws.com/a2c22923-37af-46ad-ae9c-a8f61e62a637/1287314f-3492-4510-bf58-0d6da2a315bc/Screenshot_2024-10-30_at_16.39.19.png)

For binary variable we can choose 2(logistic regression):

1. threshold activation func, 1 or 0
2. sigmoid activation func, probability of why yes or no

![Screenshot 2024-10-30 at 16.44.19.png](https://prod-files-secure.s3.us-west-2.amazonaws.com/a2c22923-37af-46ad-ae9c-a8f61e62a637/41899f64-991d-480d-b9be-da304e837224/Screenshot_2024-10-30_at_16.44.19.png)

apply rectifier activation function on hidden layer, the signal would be passed on to the output layer where the sigmoid activation function would be applied can be predicted probability

## How do Neural Networks work?

we’re going to look at a neural network that takes in some parameters abput a property and values it.

pretend it’s already trained up.

output layer is price of our predicting.

these input variables would be weighted up by snynapses. and price is weighted sum of inputs.

![Screenshot 2024-10-30 at 16.57.48.png](https://prod-files-secure.s3.us-west-2.amazonaws.com/a2c22923-37af-46ad-ae9c-a8f61e62a637/9f791d08-ffb1-41e2-a3a7-02ca4be0dbd2/Screenshot_2024-10-30_at_16.57.48.png)

How that hidden layer gives us that extra power?

1. we have got all four input variables on the left, and going to first start with top neuron on the hidden layer with snynapses and all snypeses has weight. so some weights are 0 some weights not basically not all inputs will be valid or not all inputs will be important for every single neuron. 
2. the last neuron took one input, how could that be the case? when age could mean, older property has less valu, the prices drop, historic property, older is less valuable
    
    ![Screenshot 2024-10-31 at 15.34.06.png](https://prod-files-secure.s3.us-west-2.amazonaws.com/a2c22923-37af-46ad-ae9c-a8f61e62a637/00d58c2f-25ba-46e1-9953-0e28a948f5f2/Screenshot_2024-10-31_at_15.34.06.png)
    
    good example of rectifier function being applied. got a zero until a certain point, until 100 year olds, the older it gets, the higher the contribution of this neuron to the overall price
    

![Screenshot 2024-10-30 at 16.53.36.png](https://prod-files-secure.s3.us-west-2.amazonaws.com/a2c22923-37af-46ad-ae9c-a8f61e62a637/4320d2af-ec17-4bb6-924f-bde7a692ea0f/Screenshot_2024-10-30_at_16.53.36.png)

## How do Neural Networks Learn?

1. hard-coded coding where actually tell the program specific rules and what outcomes you want and just guide through 
2. create neural network for learning with its own, avoid try to put in rules, how do you distinguish cat and dog, cat ears whiskers shape of face, colors, describe all things , just code neural n and the architecture and neural n can understand its own. 

those are 2 different approaches

y stands for actual value and ŷ for predicted value by the neural network.

![Screenshot 2024-10-31 at 15.43.55.png](https://prod-files-secure.s3.us-west-2.amazonaws.com/a2c22923-37af-46ad-ae9c-a8f61e62a637/7dbc66a7-d8ad-462d-88ef-687ef9b54083/Screenshot_2024-10-31_at_15.43.55.png)

plot the y and ŷ to compare that the neural network to get. Cost function is C, and tells that what is the error that you have in your prediction, our goal is to minimize the cost function. lower cost function closer to ŷ to y. than we feed this information back into the neural network and there is the information going back to neural network to the weights, then the weights get updated.

![Screenshot 2024-10-31 at 15.51.31.png](https://prod-files-secure.s3.us-west-2.amazonaws.com/a2c22923-37af-46ad-ae9c-a8f61e62a637/df3269a4-36c6-4b6b-abad-ed096776843e/Screenshot_2024-10-31_at_15.51.31.png)

the only thing that we have control of this very simple neural network are the weights. W1 to Wn, our goal minimize cost function so only can do update the weights. we’re training one row right now

![Screenshot 2024-10-31 at 15.57.14.png](https://prod-files-secure.s3.us-west-2.amazonaws.com/a2c22923-37af-46ad-ae9c-a8f61e62a637/d5c896a3-76df-46f1-9784-15e22eaec25f/Screenshot_2024-10-31_at_15.57.14.png)

we’re going to be feeding these into the one same neural network.

1. one epoch is when we go through a whole dataset, and we train our neural network on all of these rows. First we feed all rows by one by than got all ŷ values. 
2. then compare the ŷ with actual value y. for every single rows we have an actual value. 
3. with all of these differences we can calculate the cost function which is the sum all of those squared differences between ŷ and y and all that is halved. And there's a cost function. And basically now, what we do after we have the full cost function, we go back and we update the weights. We update W1, W2, W3. 
4.  And the important thing to remember here is that all of these perceptrons, or all of these neural networks is actually one neural network, so there's not eight of them, there's just one. 
5. we update the weights in that one neural network basically, the weights are going to be the same for all of the rows. so all the rows share the weights. so that’s why we looked at the cost function, which is the um of the squared differences, then we updated the weights.
6. so from herem that was just one iteration. so next we’re going to feed every single row into the the neural network, find out our cost function, and do this whole process again.  
7. and the goal here is the minimize the cost function, that means your weights have been adjusted and you have found the optimal weights for tjis dataset that you’re training on, then next testing phase

and this whole process is called bakpropagation

## **Gradient Descent**

exactly how these weights are adjusted. the all process we got some input value, then we got weight, then the activation function applied, then we get ŷ than the actual value we calculate the cost function. 

![Screenshot 2024-10-31 at 16.24.54.png](https://prod-files-secure.s3.us-west-2.amazonaws.com/a2c22923-37af-46ad-ae9c-a8f61e62a637/e4086202-c718-4e25-ad2d-22ca8fe067d8/Screenshot_2024-10-31_at_16.24.54.png)

How can we minimize the cost function?

take all of possible weights and look at them and this is a chart of on the ya xis you have cost function on the vertical axis, on the horizontal axis you have ŷ. 

![Screenshot 2024-10-31 at 16.25.12.png](https://prod-files-secure.s3.us-west-2.amazonaws.com/a2c22923-37af-46ad-ae9c-a8f61e62a637/040fd690-e270-4df3-89e5-4bbb189d8833/Screenshot_2024-10-31_at_16.25.12.png)

if you increase number of weights, increate the number of synapses in your networks you have to face the curse of dimensionality. 

![Screenshot 2024-10-31 at 16.30.49.png](https://prod-files-secure.s3.us-west-2.amazonaws.com/a2c22923-37af-46ad-ae9c-a8f61e62a637/da59631d-0af6-44a0-a835-7f6a0c4e6fb6/Screenshot_2024-10-31_at_16.30.49.png)

when before it’s trained we know which are the weights and here we have a total of 25 weights. thi is only one neural network and how could we brute our way through weight of this size. let’s do some maths. flops is floating operation per second. so this is not optimal solution.

![Screenshot 2024-10-31 at 16.33.19.png](https://prod-files-secure.s3.us-west-2.amazonaws.com/a2c22923-37af-46ad-ae9c-a8f61e62a637/ebc9e29d-5bec-41c2-b881-b513079c14dd/Screenshot_2024-10-31_at_16.33.19.png)

if our neural network biggest like below, this method not going well. what should we do?

![Screenshot 2024-10-31 at 16.33.31.png](https://prod-files-secure.s3.us-west-2.amazonaws.com/a2c22923-37af-46ad-ae9c-a8f61e62a637/a778b7c3-d3c8-49db-b107-e12bb500d5b8/Screenshot_2024-10-31_at_16.33.31.png)

The method called is Gradient Descent

![Screenshot 2024-10-31 at 16.38.44.png](https://prod-files-secure.s3.us-west-2.amazonaws.com/a2c22923-37af-46ad-ae9c-a8f61e62a637/be61286d-c022-4dd8-ab98-05a49e59ee34/Screenshot_2024-10-31_at_16.38.44.png)

there is out cost function and now we can come up with a faster way to find the best option.

1. start somewhere and from that point in the top left and look at the angle of cost function at that point and find out what the slope is in that specific point and find out the slope is positive or negative. 
    
    if slope is negative, you’re going to downhill
    
2. then takes a step right, calculate slope and go to left and so on again calculate slope
3. it is the best situation that minimizes your cost function and finding best weight

![Screenshot 2024-10-31 at 16.39.07.png](https://prod-files-secure.s3.us-west-2.amazonaws.com/a2c22923-37af-46ad-ae9c-a8f61e62a637/ec1a3ded-9318-4c63-ae51-b3ed0d2d750b/Screenshot_2024-10-31_at_16.39.07.png)

it’s also called gradient descent because you’re descending into the minimum of the cost function.  

![Screenshot 2024-10-31 at 16.40.25.png](https://prod-files-secure.s3.us-west-2.amazonaws.com/a2c22923-37af-46ad-ae9c-a8f61e62a637/0eb519d4-5ebd-41b1-a2d9-99d584173762/Screenshot_2024-10-31_at_16.40.25.png)

gradient descent apply 3 d dimensions 

## **Stochastic Gradient Descent**

Gradient descent this method requires for the cost function to be convex. it in essence has one global minimum and that is the onee thing we’re going to find. But If our function is not convexed? Why it is happened?

If we choose a cost function which is ot the squared difference between ŷ and y.  So if we apply gradient descent method something like this could happen. we could find a local minimum of the cost function rahther than the global one so this one was the best one, so if used gradient descent could found wrong one. 

![Screenshot 2024-10-31 at 16.52.51.png](https://prod-files-secure.s3.us-west-2.amazonaws.com/a2c22923-37af-46ad-ae9c-a8f61e62a637/72a25d45-130b-41e2-924d-d551a2fa9062/Screenshot_2024-10-31_at_16.52.51.png)

So what should we do in this case? Stochastic gradient descent, so it doesn’t require for the cost function to be convex.

So normal gradient descent is when we take all rows and we plug them into neural network and once again and here we’ve got he neural network copied several times but the rows are being plugged into that same neural network every time so there is just only one neural network. so it’s gradient descent or batch gradient descent so we take the whole batch from our sample and we apply it and then we run. 

The stochastic gradient descent is it takes the rows one by one, take this row and run neural network and then adjust the weights.  then we take the second row and do same thing. so on we looked at the cost function and we adjust the weights again. then take a other row, run neural network and look at the cost function and adjust the weights. 

we’re adjusting weights after every single row rather than doing everything together and then adjusting weights.

![Screenshot 2024-10-31 at 16.53.12.png](https://prod-files-secure.s3.us-west-2.amazonaws.com/a2c22923-37af-46ad-ae9c-a8f61e62a637/57234b03-e3ab-4cda-b932-1ed8776122f8/Screenshot_2024-10-31_at_16.53.12.png)

Batch gradient descent where you’re adjusting the weights after you’ve run them after you’ve run all of the rows in your neural network and then basically you adjust the weights and then you run the whole thing again itereation, iteration etc.

Stochastic Gradient Descent, you run one row at a time and ou adjust the weights.   and repeated again and again. 

The main differences are iteration etc.

![Screenshot 2024-10-31 at 16.53.32.png](https://prod-files-secure.s3.us-west-2.amazonaws.com/a2c22923-37af-46ad-ae9c-a8f61e62a637/75e71846-f696-46a4-952c-c01a6521e0e2/Screenshot_2024-10-31_at_16.53.32.png)

Stochastic Gradient Descent method helps you avoid the problem where you find those local extra neural or local minimums rather than the overall global minimum. And the reason for that in simple terms is that the SGD
or the stochastic gradient descent method has much higher fluctuation because it can afford them.
It's doing one iteration or one row at at time and therefor the fluctuations are much higher and it is more likely to find the global minimum rather than just the  local minimum and the other thing about the stochastic gradient descent method compares to the batch gradient is that it's faster.

 
BGD every single row one at a time it is slower but actually in fact it is faster because it doesn't have to load up all the data into memory and run and wait until all those rows are run altogether. You can just run them one by one so it's a much lighter algorithm. It's much faster in that sense.

The main advantage of or the main kind of like pro for the batch gradient descent method is that it is a deterministic algorithm rather than a stochastic gradient descent being a stochastic algorithm meaning it's random and with the batch gradient descent method as long as you have the same starting weights for your neural network every time you run
the batch gradient descent method you will get the same iterations
the same results for the way your weights are being updated.

First for the stochastic gradient descent method you won't get that because it is a stochastic method.
You are picking your rows possible at random and you are updating your neural network in a stochastic manner and therefor you're just going to every single time you run the stochastic gradient descent method even if you have the same weights at the start you're going to have a different process a different iterations to get there.

Also there is a method in between the two called the mini batch gradient descent method where you combine the two and you basically run rather than running a whole batch or run one at a time you run batches of rows maybe 5, 10, 100 however many rows you decided to set.
You run that number of rows at a time then you update your weights and
you update your weights and so on. That's called the mini batch gradient descent method.

## **Backpropagation**

there is a process called **forward propagation** where information is entered into the input layer and then is propagated forward to get our ŷ, then we compare those to the actual values that we have in training set and then we calculate the errors.

Then the errors are **back-propagated** through the network in the opposite direction and that allows us to train the network by adjusting the weights.

the one **key** important thing is that backpropagation is an advanced algorithm driven by sophisticated maths which allows us to adjust the weights, all of them at the same time, all of the weights are adjusted simultaneously.  

The huge advantage of backprop is that during the process of backpropagation, you are able o adjust all of the weights at the same time. So you basically know which part of the error each of your weights in the neural network is responsible for. 

![Screenshot 2024-10-31 at 18.33.27.png](https://prod-files-secure.s3.us-west-2.amazonaws.com/a2c22923-37af-46ad-ae9c-a8f61e62a637/a9539f4c-95e0-4cd7-859f-d5e166ccb8bb/Screenshot_2024-10-31_at_18.33.27.png)

what a summary, backprop, it adjust all of the weights at the same time. 

weights basically determine how important each neuron’s activation is.

**Training the ANN with Stochastic Gradient Descent**

**Step 1:** Randomly initialise the weights to small numbers close to 0 (but not).

Step 2: Inout the first observation of your dataset in the input layer, each feature in one input node.

**Step 3**: Forward- Propagation: from left to right, the neurons are activated in a way that the impact of each neuron’s  activation is limited by the weights. Propagate the activations until getting the predicted result y. 

**Step 4**: Compare the predicted result to the actual result. Measure the generated error.

**Step 5**: Back-Propagation: from right to left, the error is back-propagated. Update the weights according too how much they are responsible for the error, The learning rate decides by how much we update the weights

**Step 6:** Repeat Steps1 to 5 and update the weigjts after each obseervation(Reinforcement Learning), 

Or: Repeat Steps1 to 5 but update the weights only after a batch of observations(Batch Learning)

**Step 7:** When the whole training set passed through the ANN, that makes an epoch, Redo more epochs.

### For Dataset

Tenure = the number of years they have been in the bank

NumOfProducts = they use from bank like a credit cart or a checkbook, loan or home loan

hasCRCards =  equal to 1 is the customer has credit cards

IsActiveMember = he/she is using the bank, connecting to its account or using its credit card on other card, 1 is costumer active 

EstimatedSalary= the salary of costumer estimated by the bank

Exited = dependent variable, costumer stayed in the bank or left the bank, it left the bank as in exited equals yes

this bank observed their costumers for a certain period time, let’s say 6 months, they observed if during the 6 months they left the bank or stayed in the bank, they gathered these outcomes in this last dependent variable, at the same time with all featured understand the correlations between these features and the the fact whether or not, the costumer stays in the bank or leaves the bank