# ColourIdentifier
A simple colour identifier writed in python, for my honours project, that draw textures or gradient lines over the objects 
recordeds using camera to identify the colour of that objects. 

The proposed software tries to identify the colors of an image and then by means of masks draw textures on the image that indicate which colors are 
involved. First of all, the image is obtained through a camera, because our objective
is mainly to use the software in real time, the OpenCV library is used to capture the image.

The image is then processed in order to discriminate the colors that appear in
The color discriminator based on HSV is implemented in a simple way with OpenCV using a range of values for each color implemented. 
In particular, a "own color space" based on
HSV for color discrimination, which is just a selection of the colors we are interested in discriminating in the prototype. You can understand 
as a semicircle where the three colors we discriminate (magenta, green and blue) are distributed, which serves as an intuitive way to see the 
angles that indicate what each color is and the range of HUE (H component) of each. Finally the software shows in a simple and intuitive way for the user the image that
you want to process with the information about the color of it. There is also, in a simple way, at the development level the possibility of adding colours and making it more 
complex, putting for example different types of "red" or any other color. Here is an example of a mask, with the following range values, for example for
the green one. We can see how the values for HSV are indicated, so that the low values of the range are the lower ones and the high values are the upper ones on the HSV scale.

As we can see, for each colour a range has been used, where the most relevant has been the
H component. This is used later to create a mask for each color to be discriminated, for this the inRange function has been used, passing as arguments the image captured and 
the upper and lower ranges. With the function bitwise_and we stay applying the mask only with the part of the image that has the color to discriminate. We can see in the 
drawing loop of the textures on the image, it is done by going through
the image in width and length, for according to the angle previously stipulated for that color, the point where the line will end is obtained, with its respective inclination. 
Then the line is drawn with that information and the starting point, which is the one that corresponds in the iteration. To draw this line, the line function is used, passing as a
parameter an empty image previously created. Once this processing is finished, the image with the lines is multiplied by the image in two dimensions generated with the mask, 
thus obtaining an image with the lines that correspond to the colour that we are interested in discriminating in the loop.

We proceed in this way with each color and finally compose them into a single image
to be displayed, by adding these images to the original two-dimensional image.
After the experimental development, functionalities such as the power
remove or add colors to discriminate, option to choose between gradient line or character textures, change the size of the textures, 
a legend with information about what is shown in the processed image and show recommendation to increase or decrease the amount of light. 
In the case of the options, bars have been added using the createTrackbar function, creating a selection bar for size, type of texture and for each of the colors to be
discriminated.

To add the legend, simply add the text with a considerable size and adjusting it to look good in the picture shown, for this you use the putText function. 
For the recommendation of light increase or decrease, the V component has simply been taken into account. An upper and a lower limit is created for this purpose, 
and then it is checked whether or not this value is exceeded.

As for the colors to the new textures we have the same texture drawing loop
than in the pre-test version seen before, but now we check which type of texture is selected to draw one or the other,
in the case of gradient lines we use the line function passing the start point of the line and the end point and in the
case of a character we use the putText function with the corresponding character. 


