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
