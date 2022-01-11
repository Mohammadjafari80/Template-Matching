# Template Matching

Template matching is a technique in digital image processing for finding small parts of an image which match a template image. It can be used in manufacturing as a part of quality control, a way to navigate a mobile robot, or as a way to detect edges in images.

In this program we want to detect metal bars in the image below.

![Greek Ship](./images/Greek-ship.jpg)

First, we define a patch to work with. We just crop one of the current bars as a patch.

<p align='center'>
    <img src='./images/patch.png'>
</p>

To make our search easier we crop it even more.

<p align='center'>
    <img src='./images/patch-small.jpg'>
</p>

Now we perform cross-correlation on the given image with provided patch. Here is the result:

![Cross Correlation 2](./images/cross-correlation.jpg)

If we pay attention to the result we can see that places that was placed a bar are generally brighter but if filter that by bright pixels there are some unwanted places that passes the filter. So to solve that we have to look for clusters of bright pixels. One simple way to do that is to template match using a white rectangle patch. This will look for cluster of white pixels.
<br/>
Here is the performed cross-correlation:

<p align='center'>
    <img src='./images/rectangle.jpg' style='heigh:10%'>
    <img src='./images/cross-correlation-2.jpg' style='width:70%'>
</p>

Now we can see that the bars are much better separated.
We filter pixels that have high intensity and get their coordinates. Then we find clusters that are closed together and look for the highest intesity in the first cross-correlation becuase that is the best possible matching. If we filter these out and draw a rectangle around them, the result will be like this:

![Matching](./images/matching.jpg)

As we can see the bars have been detected perfectly.
