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
