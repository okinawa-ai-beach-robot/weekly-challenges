# weekly-challenge
## Week 9 2025-03-21

### Challenge 1 (1 Point)
#### Analyzing Yolov5 results
1. Create virtual environment, activate it, and install yolov5
2. Run the [Use from Python](https://github.com/fcakyon/yolov5-pip?tab=readme-ov-file#use-from-python) example code using your virtual environment
3. Use the pretained model rather than the custom model
4. If you encounter the following error:

```
cv2.error: OpenCV(4.10.0) :-1: error: (-5:Bad argument) in function 'rectangle'
> Overload resolution failed:
>  - img marked as output argument, but provided NumPy array marked as readonly
>  - Expected Ptr<cv::UMat> for argument 'img'
>  - argument for rectangle() given by name ('thickness') and position (4)
>  - argument for rectangle() given by name ('thickness') and position (4)
```

Add this code after generating the results object

```
# Ensure results.ims exists before modifying it
if hasattr(results, "ims") and results.ims is not None:
    results.ims = [np.ascontiguousarray(im.copy()) for im in results.ims]
```
5. Run this again using [this](https://sweetiq.com/wp-content/uploads/2017/06/iStock-513106144.jpg) image.
6. Print the number of objects detected.
7. Print the "score" or confidence level of the highest and lowest detections.  

### Challenge 2 (2 Points)
#### Analyzing Yolov5 results
Using the same code from Challenge 1:
1. Find the center of the highest detection and print as [x,y]
2. Find the bottom left corrdinate of the highest detection and print as [x,y]
3. Print the category of the highest and lowest detections. Note you will need to convert this from a number to a string somehow. The string will be a word like "person" not "7".


## Hints for those who read through all the directions
1. Insert a `breakpoint()` after you obtain the results in your code. This will bring up an interactive pdb debugger after you run the python script. Use the `p` command to print the results object. Enter `p result.` and press tab. You will see all the possible attributes not listed in the documentation. This can be VERY helpful for projects with lacking documentation without having to understand the source code. 
2. `results.xywh` is your friend (center_x, center_y, width, height)

# Scoreboard
See [here](https://docs.google.com/spreadsheets/d/1ItVjMqHzYHVRkHvhwMLSei56EVrT7mP8-aAS8otU1YQ/edit?usp=sharing)
