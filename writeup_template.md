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

My pipeline consisted of 5 steps. First, I converted the images to grayscale, then I applied Gaussian smoothing using Kernel size of 5. After that, images went through Canny Edge detection algorithm with threshood between 50 and 150 to find edges of that image. The images then had to be marked using quadrangle shape. After the masking process, hough transformation was used to identify lines in the images. Finally, these lines were combined with the original images to draw lines on the images.

In order to draw a single line on the left and right lanes, I modified the draw_lines() function by using linear algebra. Because we were interested in only two lines in a given image (the left lane and the right lane), we could separate these two lines using positive and negative slope. These slopes were then used to find y-interception from y=mx+c equation. Maximum y-axis value was applied to the linear eqaution to find x-axis value. Finally, the lines were drawn using these x and y values.

If you'd like to include images to show how the pipeline works, here is how to include an image: 

![alt text][image1]


### 2. Identify potential shortcomings with your current pipeline

One shortcoming would be when the roads were curve and weren't straight. As I used linear algebra to draw long lines, curve roads would be inapplicable.

One potential shortcoming would be what would happen when one of the lane disappeared. This happened optional challenge.

Another shortcoming could be the noise. As a result from my algorithm, the videos weren't very smooth as the slope of the images kept moving.

### 3. Suggest possible improvements to your pipeline

A possible improvement would be to average the slope over previous time-frames to smoothen the video.

Another potential improvement could be to used deep learning in drawing the long lines so that they are applicable to curve roads as well.
