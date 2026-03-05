# Pixel Art Style Post Processing

Pixelated image abstraction to mimic pixel art style. 
The process includes three steps-
- Downsampling
- Posterization
- Dithering

## Downsampling 

The most obvious feature of pixel art is lower resolution. This can be done simply by skiping pixels and scaling up the image (using nearest neighbor interpolation). Another way to look at this is that we divide the image into squares and we replace each square with a single pixel (say the top left pixel in each square). 

<img width="2426" height="1190" alt="Frame 2" src="https://github.com/user-attachments/assets/6f8cd243-00aa-4c46-bae6-046bb0e2a56b" />

We can instead replace the square with some function of the pixel values in the square like-
- mean
- max
- min
- median

This is similar to pooling in CNN. Pooling can make the effect less sensitive to translation. Mean pooling have the effect of bluring the image, while median pooling denoises the image while preserving the edges and structure of original images. 

![Frame 3](https://github.com/user-attachments/assets/df53019a-6ba3-43fb-84f4-5b8685713111)

## Color quantization
Posterization is an effect of reducing a continous range to color to a limited range of discrete colors. Three different quantization methods are used:
- Floor: replicates quantization due to lower bit colors of older hardware
- Kmeans Clustering
- Gausian clustering
- Median Cut

  ![Frame 5](https://github.com/user-attachments/assets/21f085a4-fc54-478c-baf2-3fd31f23edb3)

## Dithering 
Nosie is added for remove banding and to show gradients. [Read more](https://surma.dev/things/ditherpunk/index.html).

Ordered bayer noise is added to the image in some proportion before color quantization 
![image 30](https://github.com/user-attachments/assets/2107a686-5733-435d-a63b-ffa1184d8e35)

### Projection based dithering
Instead of adding the noise, we can generate a scalar value for each color based on its distance from its first nearest color in the palette and next nearest color. We can use this value to dither the image. If the value is smaller than noise value than replace the original pixel with the nearest color otherwise replace it with next nearest color. 

