# CNN

## Vertical Edge detection using CNN

We do convolution of image and filter as shown below, this gives us area where the edge might lie.  
**Notice one thing** - after doing convolution operation, we get to know whether we are moving from light to dark or vice versa. 

<img width="1261" height="744" alt="image" src="https://github.com/user-attachments/assets/a2f6ee15-afcf-48c0-87f3-2ad60fb507ed" />

## Different types of Convolution  
1. **Padding and then convolution**

   This is done to main the shape of original image. As we perform convolution of image with filter the size of original image reduces. Let's consider a example Image size is 8x8, filter size 3x3 **(generally of odd dimension)** then output image is equal to **n-f+1** i.e. 8-3+1 = 6.  

   In case of padding we add extra dimensions to the orginal image, generally with zeros. Considering above example but with padding =1, then Output image size will be equal to **n +2p -f +1** i.e. 8 + 2 -3 +1 = 8.

2. **Stridded convolution**

    In this case the sliding window (strides) of filter by default is considered as 1. But in this case we can consider a different value. With same example as above, if s = 2 then output is  $$\left\lfloor \frac{n + 2p - f}{s} \right\rfloor + 1 $$ i.e. 5.

