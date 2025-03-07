# weekly-challenge
## Week 8 2025-03-07

### Challenge 1 (2 Points)
#### Basic Yolov5 Usage via pip
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
5. Run this again using a custom image. 


# Scoreboard
See [here](https://docs.google.com/spreadsheets/d/1ItVjMqHzYHVRkHvhwMLSei56EVrT7mP8-aAS8otU1YQ/edit?usp=sharing)
