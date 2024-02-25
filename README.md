# GestureGenius
GestureGenius is a Tensorflow model that aims to facilitate communication between deaf people who practice the Lebanese Sign Language and other individuals. 

# Technologies used
- Python : the go-to language for machine learning projects due to its simplicity and numerous libraries
- Teachable Machine :  a user-friendly web application that creates machine learning models from collected data
- Tensorflow: an open-source library for machine learning that enables the creation, training, and deployment of neural network models

# How did I build the model?
The first step to build a machine learning model is of course to collect the data. This is where the datacollection.py code comes in handy. It's a fast way to capture hundreds of pictures within seconds from a webcam feed and allows the user to save cropped and resized images of their hand. Here's a brief explanation of the code:
1) Import the necessary libraries such as OpenCV (cv2) for computer vision tasks and HandDetector from cvzone library for hand tracking.
2) Initialize the webcam feed (cap) and the hand detector.
3) Define parameters like offset (to adjust the size of the cropped image), imgSize (size of the final cropped image), and the folder to save the images.
4) Enter a loop that continuously captures frames from the webcam and uses the HandDetector to find hands in the frame.
5) If a hand is found, it extracts the bounding box (bbox) of the hand.
6) It crops the region of interest (hand) from the frame based on the bounding box coordinates and applies resizing and padding to make it fit into a square image of size imgSize x imgSize.
7) It displays the cropped hand image (imgCrop) and the resized hand image with a white background (imgWhite).
8) If the user presses the "s" key, it saves the white-background resized hand image into the specified folder with a timestamped filename. The loop continues until the user exits by pressing a key.

Once the data is collected and cleaned, the next step would be to train the model on the data, and then test it on new unseen data to evaluate its accuracy. To do so, I used Teachable Machine which is a user-friendly web application that creates machine learning models from collected data. I opted for a TensorflowLite model. Once my model was trained, I used the main.py code to perform Lebanese-sign-language recognition and test my model. The steps are similar to the previous code with a few additions. Here's a brief break down of the code: 
1) Import the necessary libraries such as OpenCV (cv2) for computer vision tasks and HandDetector from cvzone library for hand tracking.
2) Initialize the webcam feed (cap) and the hand detector.
3) Define parameters like offset (to adjust the size of the cropped image), imgSize (size of the final cropped image), and the folder to save the images.
4) Define a list of labels corresponding to the gestures that can be recognized (available in the labels.txt file).
5) Enter a loop where it continuously captures frames from the webcam and uses the HandDetector to find hands in the frame.
6) If a hand is found, it extracts the bounding box (bbox) of the hand.
7) It crops the region of interest (hand) from the frame based on the bounding box coordinates and applies resizing and padding to make it fit into a square image of size imgSize x imgSize.
8) It feeds the resized hand image to the gesture classifier to get the prediction of the gesture.
9) It overlays the predicted gesture label on the output frame (imgOutput).
10) It displays the cropped hand image (imgCrop), the resized hand image with a white background (imgWhite), and the output frame with the predicted label. The loop continues until the user exits by pressing a key.
    
# How to use it?
1) Open PyCharm (Python IDE) or Visual Studio Code (since it supports python). 
2) Download the necessary packages (use any Python version between 3.7 and 3.10 since the new versions do not support yet MediaPipe)
3) Copy the main.py code, as well as labels.txt and keras_model.h5 available in this repo, and put them in a seperate folder than the main code
4) Run the code and check for errors
5) Try detecting signs from the available data set and have fun with it :)

# Future Improvements
- Add more words to the data set
- Add the percentage of accuracy of the predictions
- Implement the model in a website or an app for more accessibility
