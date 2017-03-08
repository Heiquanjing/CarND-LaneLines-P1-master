

#**Finding Lane Lines on the Road** 

##Writeup Template

###You can use this file as a template for your writeup if you want to submit it as a markdown file. But feel free to use some other method and submit a pdf if you prefer.

---

**Finding Lane Lines on the Road**

The goals / steps of this project are the following:
* Make a pipeline that finds lane lines on the road
* Reflect on your work in a written report


[//]: # (Image References)

[image1]: ./examples/gray.jpg "Grayscale"
[image2]: ./examples/edges.jpg "CannyEdges"
[image3]: ./examples/masked_image.jpg "MaskedEdges"
[image4]: ./examples/line_image.jpg "HoughLine"
[image5]: ./examples/processed.jpg "Processed"

---

### Reflection

###1. Describe your pipeline. As part of the description, explain how you modified the draw_lines() function.

My pipeline consisted of 5 steps. First, I converted the images to grayscale, then I use the canny transform to get the edges of the images. Thirdly, I create a mask to delete those unnecessary edges and just keep the lanes'. Next step, to draw the hough lines. Lastly,  I combine the hough lines on the initial image. 

In order to draw a single line on the left and right lanes, I modified the draw_lines() function by draw__lanes(). The first step is to separate line segments by their slope ((y2-y1)/(x2-x1)) to decide which segments are part of the left line vs. the right line. Secondly, from the left line and the right line I delete some line segments their slope are a little far from others. Next job is to find the endpoints from the rest of line segments for the left and right line. At last, we can just draw the two lines using the endpoints with color and thickness.

From the following images, we can understand how the pipeline works step by step: 

![alt text][image1]
![alt text][image2]
![alt text][image3]
![alt text][image4]
![alt text][image5]

###2. Identify potential shortcomings with your current pipeline


One potential shortcoming would be that the left pipeline could be crossed with the right one when some line segments from left line has the same slope with the from right line.   



###3. Suggest possible improvements to your pipeline

A possible improvement would be to use a function to delete the wrong line segments and set up the right parameters for hough transform.
