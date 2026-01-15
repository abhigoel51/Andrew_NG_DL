# Basic of Neural Network and Deep learning

## Gradient descent

**Backpropagation** is basically calculcation of derivatives. We get to know how weights affect loss.

<img width="573" height="178" alt="image" src="https://github.com/user-attachments/assets/e3bb8187-6cfb-4f75-962b-5f6ddcadff22" />


<img width="1470" height="653" alt="image" src="https://github.com/user-attachments/assets/bbab4945-68ef-4d52-821b-288fd19afc9d" />

We are calculating differential value at all the nodes  

$\frac{\mathrm{d}L}{\mathrm{d}a} = - \frac{y}{a} + \frac{1-y}{1-a}$

Similarly 

$\frac{\mathrm{d}L}{\mathrm{d}z} = \frac{\mathrm{d}L}{\mathrm{d}a} * \frac{\mathrm{d}a}{\mathrm{d}z} = a - y$

$\frac{\mathrm{d}L}{\mathrm{d}w1} = \frac{\mathrm{d}L}{\mathrm{d}a} * \frac{\mathrm{d}a}{\mathrm{d}z} * \frac{\mathrm{d}z}{\mathrm{d}w1}= (a - y)* x1$

## Normalising input vectors using numpy

$$x = \begin{bmatrix}
        0 & 3 & 4 \\
        2 & 6 & 4 \\
\end{bmatrix}\tag{3}$$ 
then 
$$\| x\| = \text{np.linalg.norm(x, axis=1, keepdims=True)} = \begin{bmatrix}
    5 \\
    \sqrt{56} \\
\end{bmatrix}\tag{4} $$
and
$$ x\_normalized = \frac{x}{\| x\|} = \begin{bmatrix}
    0 & \frac{3}{5} & \frac{4}{5} \\
    \frac{2}{\sqrt{56}} & \frac{6}{\sqrt{56}} & \frac{4}{\sqrt{56}} \\
\end{bmatrix}\tag{5}$$ 

**ord in np.linalg.norm**, we are using L2 norm in below example

<img width="187" height="76" alt="image" src="https://github.com/user-attachments/assets/3ca1cc08-d6d8-4ab4-80f2-65a1b9fffbf7" />


```python
x = np.array([[0., 3., 4.],
              [1., 6., 4.]])

x_norm = np.linalg.norm(x,ord=2,axis=1,keepdims=True) # axis 1 means row wise, for columnwise use axis =0
print(x_norm,'\n') 
# [[5.        ]
 [7.28010989]]

x = x/x_norm
print(x)
#[[0.         0.6        0.8       ]
 [0.13736056 0.82416338 0.54944226]]

```
## Bias and Variance

<img width="1250" height="378" alt="image" src="https://github.com/user-attachments/assets/ae8abd65-9525-4fea-a6af-6fd5ecd27587" />

**High bias** means underfitting the data.  
**Low variance** means overfitting the data.

## Regularization

1. **L2 Regularization** - Used for reducing overfitting.


   Choosing Large value of lambda ensures, weight are reduced that mimicks a deep neural network with less complex neurons i.e
   it will move towards underfitting from overfitting.
   
   <img width="612" height="224" alt="image" src="https://github.com/user-attachments/assets/78c6fec3-4e86-4ac2-8a32-45607b070d8f" />

### What is L2-regularization actually doing?:

L2-regularization relies on the assumption that a model with small weights is simpler than a model with large weights. Thus, by penalizing the square values of the weights in the cost function you drive all the weights to smaller values. It becomes too costly for the cost to have large weights! This leads to a smoother model in which the output changes more slowly as the input changes.

What you should remember: the implications of L2-regularization on:  

    The cost computation:  
        A regularization term is added to the cost.  
    The backpropagation function:  
        There are extra terms in the gradients with respect to weight matrices.  
    Weights end up smaller ("weight decay"):  
        Weights are pushed to smaller values.  



2. **Dropout** - This is also used to reduce overfitting.
     
It randomly shuts down some neurons in each iteration based on the probabilty we choose.  

At each iteration, you shut down (= set to zero) each neuron of a layer with probability 1−𝑘𝑒𝑒𝑝_𝑝𝑟𝑜𝑏 or keep it with
probability 𝑘𝑒𝑒𝑝_𝑝𝑟𝑜𝑏 (50% here). The dropped neurons don't contribute to the training in both the forward and backward            propagations of the iteration.   



### What we need to remember about dropout

    Dropout is a regularization technique.
    You only use dropout during training. Don't use dropout (randomly eliminate nodes) during test time.
    Apply dropout both during forward and backward propagation.  
    
    During training time, divide each dropout layer by keep_prob to keep the same expected value for the activations. For example, if keep_prob is 0.5, then we will on average shut down half the nodes, so the output will be scaled by 0.5 since only the remaining half are contributing to the solution. Dividing by 0.5 is equivalent to multiplying by 2. Hence, the output now has the same expected value. You can check that this works even when keep_prob is other values than 0.5.


