## Finding Lane Lines on the Road


## Reflection

My line finding pipeline consisted of the following steps:



1. **Converting images to grayscale**

**	**

**	**I used the helper function grayscale() for this.

	

	

<p id="gdcalert1" ><span style="color: red; font-weight: bold">>>>>>  gd2md-html alert: inline image link here (to images/reflections0.png). Store image on your image server and adjust path/filename if necessary. </span><br>(<a href="#">Back to top</a>)(<a href="#gdcalert2">Next alert</a>)<br><span style="color: red; font-weight: bold">>>>>> </span></p>


![alt_text](images/reflections0.png "image_tooltip")




2. **Applied gaussian blur to the grayscale image**

**	**

That will smooth the image by reducing noise and making it more ready for edge-detection. 

I chosed a kernel 7



3. **Canny Edges Detection and Region Masking**

After the gaussian blur I apply the canny function with a low/high threshold of 40/80 as I thought that was a pretty clear edged image.



<p id="gdcalert2" ><span style="color: red; font-weight: bold">>>>>>  gd2md-html alert: inline image link here (to images/reflections1.png). Store image on your image server and adjust path/filename if necessary. </span><br>(<a href="#">Back to top</a>)(<a href="#gdcalert3">Next alert</a>)<br><span style="color: red; font-weight: bold">>>>>> </span></p>


![alt_text](images/reflections1.png "image_tooltip")


Now that I got the edge I had to create a masking region by creating a polygon shape limiting to the lines view.



<p id="gdcalert3" ><span style="color: red; font-weight: bold">>>>>>  gd2md-html alert: inline image link here (to images/reflections2.png). Store image on your image server and adjust path/filename if necessary. </span><br>(<a href="#">Back to top</a>)(<a href="#gdcalert4">Next alert</a>)<br><span style="color: red; font-weight: bold">>>>>> </span></p>


![alt_text](images/reflections2.png "image_tooltip")




4. **Hough Transform**

Using the **hough_lines** helper function and adding on top of **draw_lines **the logic to separate line segments by their slope  ( slope <= 0 for left ). Also used another function called **extrapolate_draw **to extrapolate and draw the straight lines



<p id="gdcalert4" ><span style="color: red; font-weight: bold">>>>>>  gd2md-html alert: inline image link here (to images/reflections3.png). Store image on your image server and adjust path/filename if necessary. </span><br>(<a href="#">Back to top</a>)(<a href="#gdcalert5">Next alert</a>)<br><span style="color: red; font-weight: bold">>>>>> </span></p>


![alt_text](images/reflections3.png "image_tooltip")


At the end I placed the final lines on top of the image using the helper function weighted_img



<p id="gdcalert5" ><span style="color: red; font-weight: bold">>>>>>  gd2md-html alert: inline image link here (to images/reflections4.png). Store image on your image server and adjust path/filename if necessary. </span><br>(<a href="#">Back to top</a>)(<a href="#gdcalert6">Next alert</a>)<br><span style="color: red; font-weight: bold">>>>>> </span></p>


![alt_text](images/reflections4.png "image_tooltip")



### ** Potential shortcomings**

A potential shortcoming would be when the video goes through a big curb and the lines would go out of region of interest. And what about other situations like passing through some trees and the parameters are not suitable for that kind of enviroment? 


### **Possible improvements**

More tests with parameters or developing some functionality to dynamically find best parameters of Edge and Hough. When passing on curbes to improve line drawing so it detects it and converts the drawn lines properly. 

