# **Finding Lane Lines on the Road** 

**Finding Lane Lines on the Road**

The goals / steps of this project are the following:
* Make a pipeline that finds lane lines on the road
* Reflect on your work in a written report


[//]: # (Image References)

[image1]: ./examples/grayscale.jpg "Grayscale"

---

### Reflection

### 1. Describe your pipeline. As part of the description, explain how you modified the draw_lines() function.

My pipeline consisted of 5 steps:
1. First, I converted the images to grayscale, then I apply Gaussian Smoothing to remove noises and speckles within the image.

2. I detect edges using the Canny Edge function with proper thresholds, then I set up a region of interest to focus on just the lane lines on the road and get away from other edges that not necessary for this program.

3. Once having the edges, it's time to use the Hough Transform function to detect all the straight lines in the region of interest.

4. I use a function from the OpenCV library to draw lines detected from Hough Transform on a blank image that has the same shape as the original one.

5. Finally, I use another supported function from OpenCV to match both images together, one is the result from the draw_line() function, one is the initial image.

In order to draw a single line on the left and right lanes, I modified the draw_lines() function by:
- Finding the averaged centers and averaged slopes from all the lines detected from Hough Transform for the left and right line. 
- Calculate new coordinates of both lines based on function (y-y') = m(x-x') (m: averaged slopes - x,y: averaged centers), and the height (y') of the region of interest. 


### 2. Identify potential shortcomings with your current pipeline


One potential shortcoming would be what would happen when the car takes turns or on the winding road where lane lines are curved which cannot detected by the current technique used for this project.

Another shortcoming could be the distortion of images of the road, it's hard to detect lane lines during the night or road full of water.


### 3. Suggest possible improvements to your pipeline

A possible improvement would be to finetune the region of interest so we can capture more accurate lines, remove all the noises.

Another potential improvement could be to develop the Hough Transform function that can detect curve lane lines, also can capture more details for images in poor light conditions.  
