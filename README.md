# **Finding Lane Lines on the Road** 
[//]: # (Image References)

[image1]: ./examples/grayscale.jpg "Grayscale"

### Reflection

### 1. Describe your pipeline. As part of the description, explain how you modified the draw_lines() function.

My pipeline consisted of following steps:

* Color Selection (Convert to grayscale)
* Edge detection (Using canny algorithim)
* Apply Gussian Blur (Smooth out the edge detection)
* Area of interest (Exclude edges in non-important area)
* Draw Lines (Daw lines to mark the edges)

In order to draw a single line on the left and right lanes, I took the following steps to modified the draw_lines() function: 

 1. Calculate slopes and center for each line points
 2. Ignore vertical lines i.e. x1 = x2 and lines having slope more then 1
 3. Seprate right and left using slope (+ve indicates right line -ve indicates left line)
 4. Identify the center points of lines using the average of lines identified
 5. To smooth out the line drawing on video. Take average of last x frames (my case x = 10).
 6. Identify right (x1,x2) and left (x1, x2). Note: Y2 = roughly mid point of image, Y1 = Image_Height
 7. Pipeline is optimized to run faster to operate less no of airthmetic opeartions

* An example video without average for x frame is [here](https://youtu.be/4qE7ZmfUu3c). Note: check time at 8, 11, 16 sec
* An example video with average x  = 10 frame is [here](https://youtu.be/cqIRP9MVjzA).


### 2. Identify potential shortcomings with your current pipeline

One potential shortcoming is with some intermittent crossing white lines near solidLefYellow can deviate lines drawn.

It may have some errornous result when there is a curved line due to image's mid point is taken as Y2 value

It doesn't work well for the shady images e.g. challange.mp4


### 3. Suggest possible improvements to your pipeline

* Apply some color filter (e.g. Yellow and white) to clearly identify lines in shaddy images. (This will help to improve result on challange.mp4)
* Improve my average function to combine into one and perform average on center(s) directly. 

