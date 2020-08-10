# **Finding Lane Lines on the Road** 

## Writeup Template

### You can use this file as a template for your writeup if you want to submit it as a markdown file. But feel free to use some other method and submit a pdf if you prefer.

---

**Finding Lane Lines on the Road**

The goals / steps of this project are the following:
* Make a pipeline that finds lane lines on the road
* Reflect on your work in a written report


[//]: # (Image References)

[image1]: ./examples/grayscale.jpg "Grayscale"

---

### Reflection

### 1. Describe your pipeline. As part of the description, explain how you modified the draw_lines() function.

My pipeline consisted of 5 steps. First, I converted the images to grayscale, then I 

1. apply Gaussian blur filter to the grayscaled image in order to suppress noise in the image;
2. apply Canny edge detection to determine edges on the picture;
3. define a region of interest and fill it with 255 and the rest zero;
4. detect lines in the region of interest using Hough transformation by converting points to lines;
5. draw lines by combine initial image with lane lines image to get the final image.

In order to draw a single line on the left and right lanes, I modified the draw_lines() function by 
1. finding the gradient of each line and separting each line to either right or left lane lines based on the output (positive gradient for left lane while negetive for right lane)
2. find the line with the longest lenght form both right and left lane lines
3. using the gradient and intercept of only the longest line for both right and left lane to draw a single line on the left and right lanes.


If you'd like to include images to show how the pipeline works, here is how to include an image: 

![alt text][image1]


### 2. Identify potential shortcomings with your current pipeline


One potential shortcoming would be what would happen when the lane line is curves, the pipeline perform poorly

Another shortcoming could be the pipeline is slow and cannot be used in realtime


### 3. Suggest possible improvements to your pipeline

A possible improvement would be to increase the speed of the pipeline by using of vectorized operations 

Another potential improvement could be to use image segementation for more accuracy road detection
