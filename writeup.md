# **Finding Lane Lines on the Road** 

## Writeup

The pipeline for the identification of the lane lines consists of the following steps:

1. Since lane lines are either white or yellow, we apply a mask to the image that will single out the white and yellow lane lines.
2. We transform the image to the gray scale.
3. We apply a Gaussian filter in order to get rid of noise on the image.
4. We transform the image using Canny Edge detection. By taking the gradient of the pixels in the image this algorithm allows to detect edges in the image.
5. We mask all the pixels in the image outside our region of interest, a trapezoid on the bottom half of the image, where the lane lines must be.
6. Using the Hough transform we detect the lines in the image.
7. In order to mark the lines on the image/video, we do the following:
  * We separate the line segments detected by the Hough algorithm into those that belong to the left lane line and those that belong to the right lane line.
  * We fit a polynomial y = mx + b to the points belonging to the left line segments and another polynomial to the right line segments.
  * For videos, in order to avoid flickering, we average the slope m and the y-intercept b over several frames.
  * Using the polynomials we draw the left and right lines on the image.






