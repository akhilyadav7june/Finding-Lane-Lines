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

My pipeline consisted of 6 steps. 

1.) grayscale()-> I converted the images to grayscale using cv2.cvtColor function. 
2.) gaussian_blur()-> Then i applied a Gaussian smoothing using cv2.GaussianBlur function on an grayscaled image got from 1st step.
3.) canny()-> Then i used Canny transformation to find the edges on the image using cv2.Canny.For this transform the input image came from 2nd step.
4.) region_of_interest()-> Then i masked only the region where the lane line would detect. I applied vertices for required region.
5.) hough_lines()-> Then i applied hough transform to find line segments on the masked edges found on 4th step using cv2.HoughLinesP funtion.
6.) weighted_img()-> Then i merged the output came from 5th step with actual images. And the red lines segments are visible on images and videos.

In order to draw a single line on the left and right lanes, I modified the draw_lines() function as

1.) First i seperated the left line segments and right line segments points and stored these points on left_pointX, left_pointY, right_pointX and right_pointY in this four list.
2.) Then i calculted extreme points from both side. Now i got four points from each side left and right.
3.) Now i calculated m and c (slope and constant define in standard line y = mx+c) using those four points for both left and right.
4.) Then using slope and constant value i extended those lines.

If you'd like to include images to show how the pipeline works, here is how to include an image: 

![alt text][image1]


### 2. Identify potential shortcomings with your current pipeline

1.) As per my solution detected line is shaking on the given videos.
2.) Somtimes i found in the videos that few points are comming outside the region of interest.
3.) My solution is not working for optional challenge given at the end.

### 3. Suggest possible improvements to your pipeline

1.) More better algorithm for draw line.
2.) Different approach for the optional challenge because lane line are not straight.