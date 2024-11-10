## 

In this part you will learn:

1. The Intuition of ANNs
2. How to build an ANN

# Ann Intuition

## **Activation Functions**

<img src="Images/1_ZafDv3VUm60Eh10OeJu1vw.webp" style="width: 70%; height: auto;">

1. The sigmoid function, where x is the value of weighted sums, is used in logistic regression. It's smooth and very useful for the output layer when predicting probabilities. 
2. The tanh function, which goes below 0, is another activation function.

![Screenshot 2024-11-09 at 22.50.55.png](https://prod-files-secure.s3.us-west-2.amazonaws.com/a2c22923-37af-46ad-ae9c-a8f61e62a637/faec9a35-09ef-4e9f-87b3-bcbd0a3625c2/Screenshot_2024-11-09_at_22.50.55.png)

For binary variables, we can choose between two activation functions (related to logistic regression):

1. Threshold activation function: outputs 1 or 0
2. Sigmoid activation function: outputs the probability of yes or no

![Screenshot 2024-11-09 at 22.51.24.png](https://prod-files-secure.s3.us-west-2.amazonaws.com/a2c22923-37af-46ad-ae9c-a8f61e62a637/3d0133de-6298-41f7-bd17-fd953cb99ef0/Screenshot_2024-11-09_at_22.51.24.png)

Apply the rectifier activation function to the hidden layer. The signal then passes to the output layer, where the sigmoid activation function is applied. This can predict probabilities.

## How do Neural Networks work?

We're going to examine a neural network that takes in parameters about a property and values it. Let's assume it's already trained. The output layer predicts the price. These input variables are weighted by synapses, and the price is the weighted sum of inputs.

![Screenshot 2024-11-09 at 22.52.13.png](https://prod-files-secure.s3.us-west-2.amazonaws.com/a2c22923-37af-46ad-ae9c-a8f61e62a637/9b3332cc-7d94-4184-a496-355ea2356e7f/Screenshot_2024-11-09_at_22.52.13.png)

How does that hidden layer give us extra power?

1. We have all four input variables on the left. Let's start with the top neuron in the hidden layer, which has synapses. All synapses have weights. Some weights are 0, while others are not. Essentially, not all inputs will be valid or important for every single neuron.
2. The last neuron took only one input. How could that be the case? Age could mean different things: an older property might have less value and prices drop, or it could be a historic property where older is more valuable.
    
    
    ![Screenshot 2024-11-09 at 22.52.43.png](https://prod-files-secure.s3.us-west-2.amazonaws.com/a2c22923-37af-46ad-ae9c-a8f61e62a637/7ae6658b-f7f9-45ef-a344-3ecaa28505a6/Screenshot_2024-11-09_at_22.52.43.png)
    
    This is a good example of how the rectifier function is applied. The neuron's output remains at zero until a certain threshold, such as 100 years old. After this point, as the property's age increases, so does this neuron's contribution to the overall price.
    
    ![Screenshot 2024-11-09 at 22.53.37.png](https://prod-files-secure.s3.us-west-2.amazonaws.com/a2c22923-37af-46ad-ae9c-a8f61e62a637/95ae24c8-41d4-4e10-ac12-31f09edc7de8/Screenshot_2024-11-09_at_22.53.37.png)
    

## How do Neural Networks Learn?

1. Hard-coded programming involves explicitly telling the program specific rules and desired outcomes, guiding it through each step.
2. Creating a neural network for autonomous learning avoids inputting predefined rules. For example, when distinguishing between cats and dogs, instead of describing features like ears, whiskers, face shape, and colors, you simply code the neural network architecture. The neural network then learns to understand these distinctions on its own.

These represent two different approaches to problem-solving in artificial intelligence.

In this context, y represents the actual value, while ŷ stands for the predicted value generated by the neural network.

![Screenshot 2024-11-09 at 22.54.44.png](https://prod-files-secure.s3.us-west-2.amazonaws.com/a2c22923-37af-46ad-ae9c-a8f61e62a637/b76541f9-4b39-46e1-a2c1-045d8c3d4973/Screenshot_2024-11-09_at_22.54.44.png)

We plot y and ŷ to compare the neural network's predictions with actual values. The cost function C measures the error in our prediction. Our goal is to minimize this cost function—a lower cost function means ŷ is closer to y. We then feed this information back into the neural network, updating the weights accordingly.

![Screenshot 2024-11-09 at 22.55.19.png](https://prod-files-secure.s3.us-west-2.amazonaws.com/a2c22923-37af-46ad-ae9c-a8f61e62a637/2165b6d3-3426-4e6f-b483-05d07f6c5b4f/Screenshot_2024-11-09_at_22.55.19.png)

In this simple neural network, we only have control over the weights (W1 to Wn). Our goal is to minimize the cost function, which we can only achieve by updating these weights. At this stage, we're training the network using one row of data at a time.

![Screenshot 2024-11-09 at 22.55.40.png](https://prod-files-secure.s3.us-west-2.amazonaws.com/a2c22923-37af-46ad-ae9c-a8f61e62a637/75d576d5-ccbc-4d8a-adf6-04eee76af05d/Screenshot_2024-11-09_at_22.55.40.png)

We're going to feed these into the same neural network.

1. One epoch occurs when we process the entire dataset, training our neural network on all rows. First, we feed all rows one by one to get all ŷ values.
2. Then we compare ŷ with the actual value y for each row.
3. Using these differences, we calculate the cost function—the sum of all squared differences between ŷ and y, halved. Once we have the full cost function, we go back and update the weights (W1, W2, W3, etc.).
4. It's crucial to remember that all these perceptrons form a single neural network—there aren't eight separate networks, just one.
5. We update the weights in this one neural network, and these weights are shared across all rows. That's why we look at the cost function, which is the sum of the squared differences, before updating the weights.
6. This completes one iteration. Next, we'll feed every row into the neural network again, recalculate our cost function, and repeat the entire process.
7. Our goal is to minimize the cost function. When we achieve this, it means we've adjusted the weights and found the optimal values for this dataset. After training, we move to the testing phase.

This whole process is called backpropagation.

## **Gradient Descent**

This process explains exactly how these weights are adjusted. First, we input values into the network. Next, we apply weights to these inputs. Then, we use an activation function to process the weighted inputs. This gives us our predicted value ŷ. Finally, we compare ŷ to the actual value and calculate the cost function. 

![Screenshot 2024-11-09 at 22.56.03.png](https://prod-files-secure.s3.us-west-2.amazonaws.com/a2c22923-37af-46ad-ae9c-a8f61e62a637/aa1b9be8-03ff-4166-9cc1-bbb942e0adcd/Screenshot_2024-11-09_at_22.56.03.png)

How can we minimize the cost function? 

Let's consider all possible weights and examine them on a chart. On the vertical axis, we have the cost function, and on the horizontal axis, we have ŷ (our predicted value).

![Screenshot 2024-11-09 at 22.56.21.png](https://prod-files-secure.s3.us-west-2.amazonaws.com/a2c22923-37af-46ad-ae9c-a8f61e62a637/c3392541-1bf5-4132-a8c9-9228bba7650a/Screenshot_2024-11-09_at_22.56.21.png)

As you increase the number of weights and synapses in your networks, you face the curse of dimensionality. 

![Screenshot 2024-11-09 at 22.56.40.png](https://prod-files-secure.s3.us-west-2.amazonaws.com/a2c22923-37af-46ad-ae9c-a8f61e62a637/8e6b30ba-21e0-4301-99d4-20cc729cf54e/Screenshot_2024-11-09_at_22.56.40.png)

Before training, we know the number of weights, which in this case totals 25. This represents only one neural network, so how could we brute-force our way through weights of this size? Let's do some math. FLOPS stands for floating-point operations per second. Clearly, this brute-force approach is not an optimal solution.

![Screenshot 2024-11-09 at 22.57.07.png](https://prod-files-secure.s3.us-west-2.amazonaws.com/a2c22923-37af-46ad-ae9c-a8f61e62a637/5c5eb233-c919-489a-8ff6-3990a1ce1f61/Screenshot_2024-11-09_at_22.57.07.png)

If our neural network grows as large as shown below, this method won't work well. What should we do instead?

![Screenshot 2024-11-09 at 22.57.26.png](https://prod-files-secure.s3.us-west-2.amazonaws.com/a2c22923-37af-46ad-ae9c-a8f61e62a637/a7c6ef94-1b70-4df3-a341-531593358341/Screenshot_2024-11-09_at_22.57.26.png)

The method called is Gradient Descent

![Screenshot 2024-11-09 at 22.57.45.png](https://prod-files-secure.s3.us-west-2.amazonaws.com/a2c22923-37af-46ad-ae9c-a8f61e62a637/33c615bc-8160-4ea6-88c2-d9dffb979cbb/Screenshot_2024-11-09_at_22.57.45.png)

We have our cost function, and now we can devise a faster way to find the optimal solution.

1. Start at a point, say in the top left. Examine the angle of the cost function at that point to determine the slope's direction (positive or negative).If the slope is negative, you're heading downhill.
2. Take a step to the right, recalculate the slope, then move left and recalculate again.
3. This process helps minimize your cost function and find the best weight.

![Screenshot 2024-11-09 at 22.58.01.png](https://prod-files-secure.s3.us-west-2.amazonaws.com/a2c22923-37af-46ad-ae9c-a8f61e62a637/5ce17164-09ef-4d1b-b646-5360fb1887b7/Screenshot_2024-11-09_at_22.58.01.png)

It's called gradient descent because you're descending toward the minimum of the cost function. 

![Screenshot 2024-11-09 at 22.59.59.png](https://prod-files-secure.s3.us-west-2.amazonaws.com/a2c22923-37af-46ad-ae9c-a8f61e62a637/fedcf2eb-562d-4e94-9183-00f7d7445f86/Screenshot_2024-11-09_at_22.59.59.png)

Gradient descent apply 3 d dimensions 

## **Stochastic Gradient Descent**

Gradient descent requires the cost function to be convex. Essentially, it seeks one global minimum. But what if our function isn't convex? Why might this happen?

If we choose a cost function that isn't the squared difference between ŷ and y, applying gradient descent could lead to problems. We might find a local minimum of the cost function rather than the global one. In this case, even though there's a better solution, gradient descent could settle on a suboptimal result.

![Screenshot 2024-11-09 at 23.00.24.png](https://prod-files-secure.s3.us-west-2.amazonaws.com/a2c22923-37af-46ad-ae9c-a8f61e62a637/5654770e-9f5d-4e4c-9a12-3f3e7c83b230/Screenshot_2024-11-09_at_23.00.24.png)

So what should we do in this case? We can use stochastic gradient descent, which doesn't require the cost function to be convex.

Normal gradient descent, also known as batch gradient descent, processes all rows of data through the neural network at once. Although it appears we have multiple neural networks, we're actually using the same network for each row. We take the whole batch from our sample, apply it, and then run the process.

In contrast, stochastic gradient descent processes rows one by one. It takes a single row, runs it through the neural network, and then adjusts the weights. This process is repeated for each row: we look at the cost function and adjust the weights again. We then take another row, run it through the neural network, examine the cost function, and adjust the weights once more.

The key difference is that we're adjusting weights after every single row, rather than processing all the data together before making adjustments.

![Screenshot 2024-11-09 at 23.00.47.png](https://prod-files-secure.s3.us-west-2.amazonaws.com/a2c22923-37af-46ad-ae9c-a8f61e62a637/1b725a4a-0cfe-43e6-9fa0-be533f9abdf9/Screenshot_2024-11-09_at_23.00.47.png)

Batch gradient descent adjusts the weights after processing all rows in your neural network. You run the entire dataset through the network, adjust the weights, and then repeat the process for multiple iterations.

Stochastic Gradient Descent, on the other hand, processes one row at a time. You run a single row, adjust the weights, and then move on to the next row. This process is repeated continuously.

The main difference lies in how often the weights are updated: after each complete dataset pass for batch gradient descent, or after each individual row for stochastic gradient descent.

![Screenshot 2024-11-09 at 23.01.07.png](https://prod-files-secure.s3.us-west-2.amazonaws.com/a2c22923-37af-46ad-ae9c-a8f61e62a637/2cc48447-9002-4b59-8a7e-bcbd10bd3902/Screenshot_2024-11-09_at_23.01.07.png)

Stochastic Gradient Descent (SGD) helps avoid the problem of finding local minima instead of the global minimum. This is because SGD has higher fluctuations, as it processes one row at a time. These fluctuations increase the likelihood of finding the global minimum rather than getting stuck in a local minimum. Additionally, SGD is faster compared to Batch Gradient Descent (BGD).

While BGD processes every single row one at a time, which might seem slower, SGD is actually faster. This is because it doesn't need to load all the data into memory and wait for all rows to be processed together. Instead, SGD runs rows one by one, making it a lighter and faster algorithm.

The main advantage of batch gradient descent is that it's a deterministic algorithm, unlike stochastic gradient descent, which is random. With batch gradient descent, as long as you start with the same weights for your neural network, you'll get the same iterations and results for weight updates every time you run it.

Stochastic gradient descent (SGD) differs from batch gradient descent in its randomness. With SGD, you're selecting rows randomly and updating your neural network stochastically. Consequently, each time you run the SGD method, even with the same initial weights, you'll experience a different process and different iterations to reach the solution. This variability is inherent to the stochastic nature of the method.

There's also a method that combines the two approaches called mini-batch gradient descent. Instead of processing the entire batch at once or one row at a time, you run batches of rows—perhaps 5, 10, or 100, depending on your chosen batch size. You process that number of rows, update the weights, and then move on to the next batch. This process continues until you've processed all the data. This method strikes a balance between batch and stochastic gradient descent.

## **Backpropagation**

There is a process called **forward propagation** where information is entered into the input layer and then propagated forward to obtain our predicted value ŷ. We then compare this to the actual values in our training set and calculate the errors. 

Next, these errors are **back-propagated** through the network in the opposite direction, allowing us to train the network by adjusting the weights.

The **key** advantage of backpropagation is that it's an advanced algorithm driven by sophisticated mathematics. It enables us to adjust all weights simultaneously.

This simultaneous adjustment is the huge benefit of backpropagation. During this process, we can modify all weights at once, effectively determining which part of the error each weight in the neural network is responsible for.

![Screenshot 2024-11-09 at 23.01.41.png](https://prod-files-secure.s3.us-west-2.amazonaws.com/a2c22923-37af-46ad-ae9c-a8f61e62a637/a8d14e3e-3837-43bf-85d3-8daf1912df7c/Screenshot_2024-11-09_at_23.01.41.png)

What a summary, backprop, it adjust all of the weights at the same time. 

Weights basically determine how important each neuron’s activation is.

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