# Image Compression Using two-dimensional Fourier Transform

<p align="justify"> The changes in the elements of the image matrix are visible in the photo by changing the intensity of light and color and are known as the edges of the image. Therefore, element changes occur faster at the edges of the photo, and it is expected that these fast changes represent high frequencies, and similarly, slow changes represent the low frequencies of the photo in the frequency domain. With the 2D Fourier transform of simple black and white photos, this point is well established. </p>

The two-dimensional discrete Fourier transform of a 𝑁 × 𝑀 matrix is ​​as follows:

![image](https://github.com/SogolGoodarzi/Image-compression-using-two-dimensional-Fourier-transform/assets/125180530/8a0fb3fd-c153-413b-a963-31ec8e781c9f)

<p align="justify"> It should be noted that the inverse of this transformation is calculated by placing the elements of the transformation matrix in the following formula. </p>

![image](https://github.com/SogolGoodarzi/Image-compression-using-two-dimensional-Fourier-transform/assets/125180530/0039c955-7cf0-4a0a-a055-36d57fe27800)

### Part 1.
<p align="justify"> We form the desired following images with appropriate commands. The white parts are equivalent to 1 and the black parts are equivalent to 0. </p>
* For the first image, we have to zero half the columns. That is, from index 129 to 256, we make zero.
* <p align="justify"> We need a square for the middle image, so we divide the horizontal and vertical sides by 4 and make two parts of each black, that is, we set the index corresponding to them to zero. (from index 65 to 19). </p>
* <p align="justify"> For the third image, we form the shape by writing two circles. The first ring is for the upper part of a rhombus or the upper triangle and the second ring is for the lower part of the shape. </p>

![image](https://github.com/SogolGoodarzi/Image-compression-using-two-dimensional-Fourier-transform/assets/125180530/f8d71872-0738-4e6f-a037-476fe947b5e3)

### Part 2.
<p align="justify"> Using the fft2 two-dimensional Fourier transform command, we take the above three images and plot their size. According to the graphs plottd  for each of the figures, we provide the following analysis. </p>

#### Figure 1. Rectangle
<p align="justify"> For this shape, according to the definition of the edge that was presented, we can see that there is a vertical edge where the shape has changed from white to black, so it can be said that this is the reason for creating the peak that can be seen in its Fourier transform diagram. In addition, it can be said that in the figure, since we only have one vertical edge, we can see with a little precision that a line on the blue screen is very faintly visible in the figure, and its existence is also due to this vertical edge in the original figure. </p>

![image](https://github.com/SogolGoodarzi/Image-compression-using-two-dimensional-Fourier-transform/assets/125180530/65d67ea7-928a-411a-959b-a2795c47baed)

#### Figure 2. Square
<p align="justify"> For this figure, we have 4 edges, which are both horizontal and vertical edges. Because in this figure, we have a color change from white to black at the edges, so this is the reason for the peak that appears in the Fourier transform figure. In addition, because this shape, unlike the rectangular shape, also includes a horizontal edge, so we can see that there is another line in it. (Pay attention to the + sign you see in the picture. </p>

![image](https://github.com/SogolGoodarzi/Image-compression-using-two-dimensional-Fourier-transform/assets/125180530/a0a7c6eb-7285-4110-a384-a186ab89183a)

#### Figure 3. Diamond 
<p align="justify"> In this figure, similar to the previous two analyses, we see edges, and this is the reason for the peak we see in the graph. In this figure, unlike the other two figures, the lines where the edges occur are diagonal. So we expect to see diagonal lines in the two-dimensional Fourier transformation of this image, which can also be seen in the figure. </p>

![image](https://github.com/SogolGoodarzi/Image-compression-using-two-dimensional-Fourier-transform/assets/125180530/bf2753fc-e7c1-4e85-ba74-770f83ad68bb)

### Part 3.
<p align="justify"> For this section, you are going to compress the "tiger.jpg" image. Take a two-dimensional Fourier transform from this image and implement a policy that reduces the size of the image by approximately 5%. </p>

<p align="justify"> To reduce the size of the image by 5%, after loading the image, we take a two-dimensional Fourier transform from its matrix. The policy we have used to reduce the size of the image is to choose a threshold to remove the Fourier transform points. In order to remove very small values ​​and details of the image, the selected threshold should be a small factor of the maximum of the image matrix. Be careful, because the image matrix is ​​two-dimensional, it should be maxed twice. The method of determining this threshold coefficient is as follows: since the size of the original image is 441 kilobytes. If we reduce it by 5%, in fact, 95% of its data should remain, and we expect that the size of the image will be reduced by 5%, that is: </p>

![image](https://github.com/SogolGoodarzi/Image-compression-using-two-dimensional-Fourier-transform/assets/125180530/6816d365-63ce-4e7a-833d-4cc70cddd1f5)

<p align="justify"> So by trial and error, we see that if we take the desired threshold as $3.3*10^{-4}$ times the peak of the Fourier transform, the size of the final image reaches 419KB. We have the output image and the main image as follows. </p>

![image](https://github.com/SogolGoodarzi/Image-compression-using-two-dimensional-Fourier-transform/assets/125180530/057c9dde-3399-487b-96fe-4b7e3342da2f)

### Part 4.
To reduce by 50%, we implement the process of the previous part.

![image](https://github.com/SogolGoodarzi/Image-compression-using-two-dimensional-Fourier-transform/assets/125180530/ad2b7053-3d22-40bd-9ee1-65840c87fb3b)

<p align="justify"> By trial and error, we can see that if we choose a threshold of $1.275*10^{-3}$ times the peak of the Fourier transform of the image, the original image has a volume reduction of 50%. </p>

![image](https://github.com/SogolGoodarzi/Image-compression-using-two-dimensional-Fourier-transform/assets/125180530/90aaba1d-dc65-4c62-8f04-fc321907e96a)

### Part 5. 
<p align="justify"> The reason why the fft2 function cannot be used to reduce the volume of color images is that these images contain several channels and only if these channels are displayed together, the image will be visible with all its colors. The best option that comes to mind to express the reason in this context are RGB images. These images contain three grayscale channels (one channel for R, one channel for G and one channel for B), each of which has a different brightness and intensity. According to the description, we can conclude that if we want to apply fft2 conversion to these images and compress them, we must do this for each channel separately and again place these three channels next to each other when displaying them so that the same image will be obtained, which of course is reduced in size this time. Another method is to take the image to the grayscale area and reduce its volume, similar to the image of the previous parts. </p>




















