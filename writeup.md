# **Finding Lane Lines on the Road** 

---

**Finding Lane Lines on the Road**

The goals / steps of this project are the following:
* Make a pipeline that finds lane lines on the road
* Reflect on your work in a written report


### Reflection

### 1. Describe your pipeline. As part of the description, explain how you modified the draw_lines() function.

My pipeline consisted of 5 steps. First, I converted the images to grayscale, then I applied gaussian blur to reduce image noise.
Then, I have applied canny edge detection along with region of interest to get only the lane lines.After that, applied hough transform by tweaking it's various parameters to get correct left/right lanes. Finally, combined the lines with original image using weighted_img function.

In order to draw a single line on the left and right lanes, I modified the draw_lines() function by using slope and X/Y values of them.
I have used the line's slope to separate X/Y values based on a slope threshold. Negative slope threshold will be assigned to left lane list and positive slope threshold will be for right lanes.For creating a single line for left/right, I have used polyfit to get slope and intercept values for both left/right lists. Then, line is drawn with fixed Y positions and X positions are found using slope and intercept values.


### 2. Identify potential shortcomings with your current pipeline


One potential shortcoming would be when there is different surface/shadows in the video, lanes are not mapped properly.

Another shortcoming could be when there is curved lanes or any other objects(car) or no lanes found in the image.


### 3. Suggest possible improvements to your pipeline

A possible improvement would be to tune hough transform parameters to take into account shadows,curved lines if possible.

Another potential improvement could be to avoid shakiness of lines drawn in video and also to draw default line when there is no lanes.
