*This is a repository containing the lab reports for the "Computer Vision" course in ECE NTUA. Below is the description of the project from lab2 part2.*


## Video Categorization using Computer Vision and Machine Learning
<img src="https://github.com/grilio/Computer-Vision-Ntua/blob/main/lab%202/Harris_walk-ezgif.com-video-to-gif-converter.gif?raw=true" width="250" alt="Example GIF"><img src="https://github.com/grilio/Computer-Vision-Ntua/blob/main/lab%202/Harris_run-ezgif.com-video-to-gif-converter.gif?raw=true" width="250" alt="Example GIF"><img src="https://github.com/grilio/Computer-Vision-Ntua/blob/main/lab%202/Harris_box-ezgif.com-video-to-gif-converter.gif?raw=true" width="250" alt="Example GIF">



### Overview

This project aims to categorize videos into three human action classes: running, walking, and boxing, utilizing computer vision and machine learning techniques. The process involves the extraction of spatiotemporal features from the videos, followed by the construction of local representations, which are then aggregated into a global representation (e.g., bag of visual words). The final step involves using support vector machines (SVMs) for action classification.

### Harris Detector and Gabor Detector

In this phase, two detectors were implemented: the Harris detector and the Gabor detector.

#### Harris Detector
The Harris detector extends the 3D Harris-Stephens corner detector to incorporate a 2D tensor and temporal derivative. It smoothens the videos spatiotemporally using Gaussian filters and computes derivatives using central differences. The interest points are identified as local maxima of the Harris criterion. The Harris detector tends to detect motion in videos consistently.


#### Gabor Detector
The Gabor detector relies on temporal filtering of the video with a pair of Gabor filters after spatial smoothing. The Gabor filters are defined based on cosine and sine functions with a relationship between frequency and temporal scale. The interest points are determined as local maxima of the significance criterion. The Gabor detector exhibits more targeted point detection compared to Harris.


Observing the extracted videos with detected interest points, it's evident that the Harris detector consistently identifies motion, while the Gabor detector targets specific movements more accurately.

### Spatiotemporal Descriptors

In this step, Histogram of Oriented Gradients (HOG), Histogram of Optical Flow (HOF), and a combination of HOG and HOF descriptors are computed.


### Bag of Visual Words and SVM Classification

The final phase involves constructing Bag of Visual Words (BoVW) representations based on HOG/HOF features and using SVMs for video classification.

1. **Data Splitting:**
   - A code snippet is provided for splitting files into training and testing sets with corresponding labels. Users can easily modify the text file for different distributions.

2. **BoVW Representation:**
   - The `bag_of_words` function is used to obtain the final representation.

3. **SVM Training and Testing:**
   - The `svm_train_test` function is employed for model training and testing.

4. **Accuracy and Results:**
   - Accuracy and detailed confusion matrices for each combination of detectors/descriptors are presented.

### Results Summary

| Descriptor | Detector | Accuracy |
|------------|----------|----------|
| HOG        | Harris   | 58.33%   |
| HOF        | Harris   | 33.33%   |
| HOG/HOF    | Harris   | 83.33%   |
| HOG        | Gabor    | 50.00%   |
| HOF        | Gabor    | 33.33%   |
| HOG/HOF    | Gabor    | 91.67%   |

In summary, individual descriptors achieve moderate accuracy, but combining HOG and HOF results in higher overall accuracy. The Gabor/HOF combination exhibits superior performance, recognizing various actions. Fine-tuning the dataset by reducing the number of "walk" labeled videos in the training set improves HOF accuracy, addressing recognition issues.
