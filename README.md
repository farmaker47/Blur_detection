# Blur_detection

A summary of blur detection based on:

1. https://www.pyimagesearch.com/2015/09/07/blur-detection-with-opencv/
Using the variance of Laplacian method to give us a single floating point value to represent the “blurryness” of an image. This method simply convolves our input image with the Laplacian operator and compute the variance. If the variance falls below a predefined threshold, we mark the image as blurry.

The reason this method works is due to the definition of the Laplacian operator itself, which is used to measure the 2nd derivative of an image. The Laplacian highlights regions of an image containing rapid intensity changes, much like the Sobel and Scharr operators. And, just like these operators, the Laplacian is often used for edge detection. The assumption here is that if an image contains high variance then there is a wide spread of responses, both edge-like and non-edge like, representative of a normal, in-focus image. But if there is very low variance, then there is a tiny spread of responses, indicating there are very little edges in the image. As we know, the more an image is blurred, the less edges there are.

Obviously the trick here is setting the correct threshold which can be quite domain dependent. Too low of a threshold and you’ll incorrectly mark images as blurry when they are not. Too high of a threshold then images that are actually blurry will not be marked as blurry. This method tends to work best in environments where you can compute an acceptable focus measure range and then detect outliers.

2. https://www.pyimagesearch.com/2020/06/15/opencv-fast-fourier-transform-fft-for-blur-detection-in-images-and-video-streams/
