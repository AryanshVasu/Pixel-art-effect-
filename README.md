# Pixel Art Style Post Processing

Pipeline to replicate pixel art style for normal images. 
The process includes three steps-
- Downsampling
- Noise addition
- Color quantization

## Downsampling 

The most obvious feature of pixel art is lower resolution. This can be done simply by skiping pixels and scaling up the image (using nearest neighbor interpolation). Another way to look at this is that we divide the image into squares and we replace each square with a single pixel (say the top left pixel in each square). 

<img width="2426" height="1190" alt="Frame 2" src="https://github.com/user-attachments/assets/6f8cd243-00aa-4c46-bae6-046bb0e2a56b" />

We can instead replace the square with some function of the pixel values in the square like-
- mean
- max
- min
- median

This is similar to pooling in CNN. Pooling can make the effect less sensitive to translation. Mean pooling have the effect of bluring the image, while median pooling denoises the image while preserving the edges and structure of original images. 

![Frame 3](https://github.com/user-attachments/assets/596f53cc-2815-45c3-91b8-cf521560e267)
