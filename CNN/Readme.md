# CNN

## Vertical Edge detection using CNN

We do convolution of image and filter as shown below, this gives us area where the edge might lie.  
**Notice one thing** - after doing convolution operation, we get to know whether we are moving from light to dark or vice versa. 

<img width="1261" height="744" alt="image" src="https://github.com/user-attachments/assets/a2f6ee15-afcf-48c0-87f3-2ad60fb507ed" />

## Different types of Convolution  
1. **Padding and then convolution**

   This is done to maintain the shape of original image. As we perform convolution of image with filter the size of original image reduces. Let's consider a example Image size is 8x8, filter size 3x3 **(generally of odd dimension)** then output image is equal to **n-f+1** i.e. 8-3+1 = 6.  

   In case of padding we add extra dimensions to the orginal image, generally with zeros. Considering above example but with padding =1, then Output image size will be equal to **n +2p -f +1** i.e. 8 + 2 -3 +1 = 8.

2. **Stridded convolution**

    In this case the sliding window (strides) of filter by default is considered as 1. But in this case we can consider a different value. With same example as above, if s = 2 then output is  $$\left\lfloor \frac{n + 2p - f}{s} \right\rfloor + 1 $$ i.e. 5.

## Different kinds of layers 
1. **Conv. Layer**
2. **Pooling**
     It helps reduce dimension of the input.

   Further this can be classified into various types :
   1. **Max pooling** - We choose the max value from the filter size.
   2. **Average pooling**- We take the average of filter size.

   <img width="930" height="489" alt="image" src="https://github.com/user-attachments/assets/a7aa7963-4938-4ddd-9fe1-9e099f22412b" />


### Example of CNN

After Conv layer, pool layer is applied. Generally these both layers are considered as 1 layer as pooling layer does not have its own weights.

<img width="1257" height="607" alt="image" src="https://github.com/user-attachments/assets/10c1a8e0-2de5-42e8-b1fa-02899688c82b" />

## Different types of Networks  

If a network  architecture is working well for a particular set of images, it is expected to work for the other set of images.  
So it is good practice to use already known networks. Following are some examples.  

1. **LeNet-5**
2. **AlexNet**
3. **VGG**
4. **ResNet**

## Inception Network 

In this case Input shape is **28x28x192**, filter is **5x5** with **32** filters. To keep Output of dimension **28x28x32**, we need to use paading of 2 and stride =1 for the input (Check formulas discussed above).  

To achieve output dimension of 28x28x32, we will have to use a filter of dimension 5x5x192 with 32 filters. Think of it as, we are calculating  5x5x192 conv with 28x28x192, this will give us 28x28 as we are using padding =2 and stride =1. The same thing is done for 32 filters.

<img width="810" height="420" alt="image" src="https://github.com/user-attachments/assets/a134f937-38cb-4f1d-8b62-20f001b7e7c4" />

So computing cost is **120M** parameters which is quite high.

### Solution to above issue

As we can see the Compution of parameters have come down drastically by 10 times.

<img width="645" height="401" alt="image" src="https://github.com/user-attachments/assets/bbfae4fd-8810-4ff8-8451-f395231e1009" />

