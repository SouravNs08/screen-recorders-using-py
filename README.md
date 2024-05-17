# screen-recorders-using-py
 
Python is a widely used general-purpose language. It allows for performing a variety of tasks. One of them can be recording a video. It provides a module named pyautogui which can be used for the same. This module along with NumPy and OpenCV provides a way to manipulate and save the images (screenshot in this case)

Modules needed
Numpy: To install Numpy type the below command in the terminal.
pip install numpy
pyautogui: To install pyautogui type the below command in the terminal.
pip install pyautogui
OpenCV: To install OpenCV type the below command in the terminal.
pip install opencv-python
Below is the implementation:

First, import all the required packages. 

# importing the required packages
import pyautogui
import cv2
import numpy as np
Now, before recording the screen, we have to create a VideoWriter object. Also, we have to specify the output file name, Video codec, FPS, and video resolution. In video codec, we have to specify a 4-byte code (such as XVID, MJPG, X264, etc.). We’ll be using XVID here.
# Specify resolution
resolution = (1920, 1080)
 
# Specify video codec
codec = cv2.VideoWriter_fourcc(*"XVID")
 
# Specify name of Output file
filename = "Recording.avi"
 
# Specify frames rate. We can choose 
# any value and experiment with it
fps = 60.0
 
# Creating a VideoWriter object
out = cv2.VideoWriter(filename, codec, fps, resolution)
Optional: To display the recording in real-time, we have to create an Empty window and resize it.

# Create an Empty window
cv2.namedWindow("Live", cv2.WINDOW_NORMAL)
 
# Resize this window
cv2.resizeWindow("Live", 480, 270)
Now, let’s start recording our screen. We will be running an infinite loop and in each iteration of the loop, we will take a screenshot and write it to the output file with the help of the video writer.

while True:
 
    # Take screenshot using PyAutoGUI
    img = pyautogui.screenshot()
 
    # Convert the screenshot to a numpy array
    frame = np.array(img)
 
    # Convert it from BGR(Blue, Green, Red) to
    # RGB(Red, Green, Blue)
    frame = cv2.cvtColor(frame, cv2.COLOR_BGR2RGB)
 
    # Write it to the output file
    out.write(frame)
     
    # Optional: Display the recording screen
    cv2.imshow('Live', frame)
     
    # Stop recording when we press 'q'
    if cv2.waitKey(1) == ord('q'):
        break
After everything is done, we will release the writer and destroy all windows opened by OpenCV.

# Release the Video writer
out.release()
 
# Destroy all windows
cv2.destroyAllWindows()
Full Code:

# importing the required packages
import pyautogui
import cv2
import numpy as np
 
# Specify resolution
resolution = (1920, 1080)
 
# Specify video codec
codec = cv2.VideoWriter_fourcc(*"XVID")
 
# Specify name of Output file
filename = "Recording.avi"
 
# Specify frames rate. We can choose any 
# value and experiment with it
fps = 60.0
 
 
# Creating a VideoWriter object
out = cv2.VideoWriter(filename, codec, fps, resolution)
 
# Create an Empty window
cv2.namedWindow("Live", cv2.WINDOW_NORMAL)
 
# Resize this window
cv2.resizeWindow("Live", 480, 270)
 
while True:
    # Take screenshot using PyAutoGUI
    img = pyautogui.screenshot()
 
    # Convert the screenshot to a numpy array
    frame = np.array(img)
 
    # Convert it from BGR(Blue, Green, Red) to
    # RGB(Red, Green, Blue)
    frame = cv2.cvtColor(frame, cv2.COLOR_BGR2RGB)
 
    # Write it to the output file
    out.write(frame)
     
    # Optional: Display the recording screen
    cv2.imshow('Live', frame)
     
    # Stop recording when we press 'q'
    if cv2.waitKey(1) == ord('q'):
        break
 
# Release the Video writer
out.release()
 
# Destroy all windows
cv2.destroyAllWindows()

code Explanation:

The code first imports the required packages: PyAutoGUI, cv2, and numpy.

The next line specifies the resolution of the video recording: (1920, 1080).

Next, we specify the video codec to be used: XVID.

We then create a VideoWriter object named out and set its properties as follows: filename, codec, fps (frames per second), resolution.

We then create an Empty window named Live and resize it to have a width of 480 pixels and a height of 270 pixels.

We also make sure that it is displayed in front of all other windows on the computer screen.

We keep this window open while we run the rest of the code.

Next we use PyAutoGUI to take a screenshot using img as input.

The output image frame is stored in frame variable.

The image is converted from BGR format to RGB format before being written to out using write().

If you want to see what’s happening inside pyautogui while taking screenshots, you can enable debug mode by setting DEBUG = True in pyautogui configuration file like so: DEBUG = True .

Then when you press F5 key or run python main_program.py -d ,

The code imports the required packages and sets up some basic parameters.

The resolution parameter specifies the width and height of the output file, while the codec parameter specifies the video codec to be used.

The next step is to create an instance of the VideoWriter class.

This object will take care of writing the recorded video to an output file.

The fps parameter specifies how often the video should be recorded at, while the filename and resolution parameters specify where and in what format the recording should be saved.

Once everything is set up, we can start recording by issuing a call to out.write().

This method takes as input a numpy array representing the current frame of video footage.

Once written to disk, we can stop recording by pressing ‘q’.
