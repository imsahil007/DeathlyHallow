# DeathlyHallow
Cloak of invisibility in python

## ABOUT:
The project is based on computer-vision. Built using opencv-python.
It works by segmenting a single predefined choosen color from a live video stream & replace it with the background which we captured earlier in the time frame of a loop. This makes the color invisible and the background which was present earlier is segemented over it.

This technique is opposite to the Green Screening. In green screening, we remove background but here we will remove the foreground frame.

# About HSV:
We will use HSV instead of RBG as the colors we will use can have different intensity and shadow.
**H** : Hue is the colour portion of the model, expressed as a number from 0 to 360 degrees:
- Red falls between 0 and 60 degrees.
- Yellow falls between 61 and 120 degrees.
- Green falls between 121–180 degrees.
- Cyan falls between 181–240 degrees.
- Blue falls between 241–300 degrees.
- Magenta falls between 301–360 degrees.

**S** : Saturation
Saturation describes the amount of grey in a particular colour, from 0 to 100 percent. Reducing this component toward zero introduces more grey and produces a faded effect. Sometimes, saturation appears as a range from just 0–1, where 0 is grey, and 1 is a primary colour.
**V** : Value (Brightness)
Value works in conjunction with saturation and describes the brightness or intensity of the colour, from 0–100 percent, where 0 is completely black, and 100 is the brightest and reveals the most colour.

# Steps:
- Choose a color
- Record a livestream for capturing the background.
- Change color space of video from BGR to HSV & then flip the capture image(s).
- Segment it to create masks with some low & high threshold color values(HSV).
- Segment the final livestream by opencv technique morphologyEx. Read about it [here](https://docs.opencv.org/trunk/d9/d61/tutorial_py_morphological_ops.html)
- Another inverted mask is generated from the above mask by performing bitwise not operation.
- Bitwise and operation is performed on the background and the mask to get resultant mask 1.
- Similarly bitwise and operation is performed on the video feed images and the inverted mask to get resultant mask 2
- Both the resultant masks are added via Linear Blend, i,e, the addWeighted method of openCV
```
 Finally the output is saved in your local directory as output.avi
```
Note: You can exit the stream by pressing q 
