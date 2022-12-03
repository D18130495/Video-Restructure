# Video-Restructure
## Introduction

The project is to combine two input frames under the same scene to generate a large landscape model view.

The program will take two device video inputs as the source, then perform feature matching based on similar parts of the input source, and after that rotate the input frame by using the matched feature points to achieve the function of recombination.

More details can be visited through:
- GitHub: https://github.com/D18130495/Video-Restructure
- Yushong He Blog: https://imageprocessing.yuhong.me/
- Yushun Zeng Blog: https://imageprocessing.huaruoyumu.com/
- Xinyu Zhang Blog: https://imageprocessing633246182.wordpress.com/

## User guide:

### Actual Running

1. Two video input equipment connected to the program run machine.
2. Make sure that the two video input device input views have some similarity under the same scenes.
3. Run ```RealtimeRestructure.ipynb```.
4. Move two video input devices wider or narrower to find the best angle you want the output to be.
5. Click on the "result" window to recombine two input videos again.

### Vedio Testing

1. Run ```VideoRestructure.ipynb```.
2. Click on the "result" window to recombine two input videos again.

In the Testing case, two embeded video are used: 

1. https://imageprocessing.yuhong.me/wp-content/uploads/2022/12/1.mp4
2. https://imageprocessing.yuhong.me/wp-content/uploads/2022/12/2.mp4

## Project Workflow and Used Algorithms

1. Ask system open two videos to capture input videos:
Use cv2.VideoCapture to get two webcam inputs and use while loop to continuously show the frame.
2. Detect key points of two video inputs with OpenCV SIFT algorithm and calculate feature description information:
  Use cv2.xfeatures2d.SIFT_create() to create SIFT with .detectAndCompute() to calculate the key points and features.
  After having the result of the key points, perusing each point to get the X, Y for each point and store them in an array.
1. Match the detected keypoints:
Use cv2.BFMatcher() to create the Brute-force matcher, with cv2.knnMatch to match the detected keypoints.
1. Filtering out the best-matched keypoints:
Use cv2.drawMatchesKnn() to draw the relationship between two input frames for the not filtered keypoints, and use the appropriate parameter to filter out the best-matched keypoint, after that draw the relationship again with the filtered keypoints.
1. Using filtered keypoints with homography matrix to rotate input frame:
Use cv2.findHomography() with filtered keypoints to rotate one of the input frames, and after that put another frame on the rotated frame, and the two frames will be combined.
1. Stabilize the output and add mouse click event to make the program can restructure two frames again:
Use variables to store whether the result has been calculated once, if the result already exists program will not calculate again, and use the mouse click call back function to make the program can calculate the result again to restructure the two frames again.

## Citation of Peer-Reviewed Research:

#### Comparison with other design peer-reviewed research:

[1] Rosebrock, A. (2021) Image inpainting with opencv and python, PyImageSearch. Available at: https://pyimagesearch.com/2020/05/18/image-inpainting-with-opencv-and-python/ [Accessed: 7 October, 2022].

[2] Rosebrock, A. (2021) Multi-class object detection and bounding box regression with Keras, tensorflow, and Deep Learning, PyImageSearch. Available at: https://pyimagesearch.com/2020/10/12/multi-class-object-detection-and-bounding-box-regression-with-keras-tensorflow-and-deep-learning/ [Accessed: 7 October, 2022].


[3] Rosebrock, A. (2021) OpenCV text detection (East text detector), PyImageSearch. Available at: https://pyimagesearch.com/2018/08/20/opencv-text-detection-east-text-detector/ [Accessed: 7 October, 2022].

#### Project peer-reviewed research:

[1] Introduction to SIFT (Scale-Invariant Feature Transform).
Available at: https://docs.opencv.org/4.x/da/df5/tutorial_py_sift_intro.html [accessed 16 October, 2022].

[2] Feature Matching. Available at: https://opencv24-python-tutorials.readthedocs.io/en/latest/py_tutorials/py_feature2d/py_matcher/py_matcher.html [accessed 16 October, 2022].

[3] Evaluating OpenCV’s new RANSACs.
Available at: https://opencv.org/evaluating-opencvs-new-ransacs/ [accessed 16 October, 2022].

[4] Basic concepts of the homography explained with code.
Available at: https://docs.opencv.org/4.x/d9/dab/tutorial_homography.html [accessed 16 October, 2022].

[5] Feature Detection OpenCV.
Available at: https://docs.opencv.org/4.x/d7/d66/tutorial_feature_detection.html [accessed 31 October, 2022].

[6] Feature Matching OpenCV.
Available at: https://docs.opencv.org/4.x/dc/dc3/tutorial_py_matcher.html [accessed 31 October, 2022].

[7] Pless, R. and Let (no date) Lecture 3: Camera rotations and homographies - ppt download, SlidePlayer. Available at: https://slideplayer.com/slide/14746373/ [Accessed: 16 November, 2022].

[8] Feature Matching + Homography to find Objects. Available at: https://docs.opencv.org/3.4/d1/de0/tutorial_py_feature_homography.html
[accessed 16 November, 2022].
