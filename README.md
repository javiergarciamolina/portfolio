# Javier Garcia Portfolio

# [Selfie Background Removal](https://github.com/javiergarciamolina/selfie-background-removal)

![ezgif com-gif-maker (2)](https://user-images.githubusercontent.com/70718425/107150769-d453bf80-695f-11eb-967c-6b089e5d8c84.gif)

* Created an app that automatically removes the background from a selfie image.

## App:

You can try it at:

https://share.streamlit.io/javiergarciamolina/selfie-background-removal-app/main/app.py


Please take into account that the model was trained on mid-upper body selfies, with only one person in the picture and relatively near from the camera.

## Steps:

* Downloaded the AISegment.com Matting Human dataset, which consists of approximately 34 thousand pictures of mid-upper body selfies and their respective masks.
* Tried a couple U-net-like architectures and selected the best, achieving a 0.994 IoU on the test set.
* Built a web app using Streamlit so that anyone can use the model to remove the background from their selfies.

## Main techniques used:

* Deep Learning
* Modern Computer Vision
* Data Augmentation
* Image Segmentation

## Visualizing the data:

I used the AISegment.com Matting Human dataset, which consists of approximately 34 thousand pictures and masks of mid-upper body selfies, with only one person in each picture, relatively near from the camera and with a high contrast with the background.

Let's see one image along with its provided label:

![descarga (6)](https://user-images.githubusercontent.com/70718425/107150396-e7fe2680-695d-11eb-904c-843b520366cf.png)

## Model Selection:

Original U-net architecture:

![descarga (7)](https://user-images.githubusercontent.com/70718425/107150849-2694e080-6960-11eb-810e-f66ef8dc9588.png)

I built and tested three U-net-like architectures, **achieving an IoU of 0.994 on the test set** with the last one.

## [Correcting the orientation:](https://github.com/javiergarciamolina/selfie-background-removal/blob/main/correct_image_orientation.ipynb)

After deploying the web app, I saw that sometimes the server would randomly rotate the image, which lead to bad results.

**So I built a deep learning model that would tell whether an image is correctly oriented, and an algorithm that would rotate it to its correct orientation.**

## Visualizing some results:

Let's see some examples of test images plotted against their ground-truth (or at least the one provided in the dataset) and their predictions:

![descarga (1)](https://user-images.githubusercontent.com/70718425/105999038-857b6f80-60ad-11eb-9bb1-f5fdf189d9bc.png)


# [Oxford Pets](https://github.com/javiergarciamolina/oxford-pets)

* Created a model that could classify dog and cat images according to their breeds, participating in a Kaggle Competition.

## Steps:

* Downloaded the images from Kaggle.
* Implemented and trained AlexNet from scratch on the train split.
* Used Transfer Learning for better results on different models.
* Created an ensemble of the best models.
* Participated in the Kaggle Competition, achieving a better result than the winner.


## Main techniques used:

* Deep Learning
* Modern Computer Vision
* Transfer Learning
* Fine-Tuning 
* Data Augmentation
* Ensemble Learning

## Visualizing the data:

I used the Oxford Pets Kaggle dataset, which consists of 7,349 training images and comprises 37 breeds of cats or dogs, which means that it has an average of 200 training images per cat or dog breed.

Let's see some of the images along with their labels:

![descarga (4)](https://user-images.githubusercontent.com/70718425/107144586-69dd5800-693c-11eb-8012-fff76387742f.png)

## Training AlexNet from scratch:

I built the architecture and trained it on the train split, achieving a validation accuracy of 0.366. I did this to compare the results with transfer learning.

## Using Transfer Learning:

I imported some networks pretrained on the ImageNet dataset, replaced their fully connected layers and retrained them. These were the results:

|  Model | Validation Accuracy  | 
|---|---| 
|  Equal Probability Benchmark |  0.027 |
| ResNet50  |  0.889 |
| ResNet50V2  | 0.899  |
|  Xception |  0.924|
|  Inception |  0.927 |
|  NASNetLarge |  0.937 |
|  InceptionResNetV2 |  0.942 |

## Ensemble Modelling:

I created an ensemble of the networks using a weighted average of the predictions. **It had a test accuracy of 0.947.** 
Let's see the ensemble predict the labels from some images of the test set:
![descarga](https://user-images.githubusercontent.com/70718425/104301888-70f18180-54c8-11eb-9613-4f748065a9bf.png)

## Kaggle Competition Results:

After checking that the ensemble's performance was good, I retrained the models on all the data and used the ensemble to participate in the Kaggle Competition, achieving a multiclass loss of 0.27231, a better performance metric that the one achieved by the winner of the competition:

![score](https://user-images.githubusercontent.com/70718425/104302219-d6457280-54c8-11eb-8def-30a676c9f9d4.png)

With the performance metric being multiclass loss:

![multiclass_loss](https://user-images.githubusercontent.com/70718425/104302308-e6f5e880-54c8-11eb-9698-417223499f9e.png)


# [Breaking Captchas](https://github.com/javiergarciamolina/breaking-captchas)

* Created an algorithm that successfully labels full captcha images.

## Steps:

* Picked and downloaded a dataset of captcha images from Kaggle.
* Created an algorithm that could extract the digits from each image, i.e. automatically draw bounding boxes around the digits.
* Manually labelled the extracted digit images from the training and validation set.
* Created a couple VGG-like convolutional networks, trained them and tested them on the validation data, eventually achieving a validation accuracy of 0.972 on the best one.
* Built a function that could label the whole captcha images from the test set and evaluated it.

## Main techniques used:

* Deep Learning
* Classical Computer Vision
* Modern Computer Vision
* Data Augmentation
* Ensemble Learning

## Digit Extraction:

Found an appropiate threshold for the value channel and detected the main contours using the OpenCV function findContours. The algorithm ended up being able to extract the digits of each image as follows:

![descarga (2)](https://user-images.githubusercontent.com/70718425/107143212-136c1b80-6934-11eb-99ec-f11d9144d007.png)

## Manual Labelling:

I built a function that would display each digit image (from the train and validation splits) and save it along with the label that I typed.

## Model Selection:

I tried three models: a reguralized LeNet and two regularized VGG-like architectures, which I will call VGG1 and VGG2. I used data augmentation to improve generalization.
With each model, I increased the complexity and the regularization of the previous one, the results were the following:

|  Model | Validation Accuracy  | 
|---|---| 
|  Equal Probability Benchmark |  0.022 |
| LeNet  |  0.943               |
| VGG1  | 0.968  |
|  VGG2 |  0.972 |


I finally chose the last model, trained and saved it 5 times and used the trained models for ensemble learning.

## Final Algorithm:

I built a function that would extract the digits from the test images, label them using the ensemble of models trained in the last step, and write the label on the full captcha image. 
Here are some results (of the test images):

![captcha_image1](https://user-images.githubusercontent.com/70718425/104241021-4f0ee500-545d-11eb-8a14-bcd5dd128762.png)
![captcha_image2](https://user-images.githubusercontent.com/70718425/104241064-5cc46a80-545d-11eb-9b2c-aef2a6ab581c.png)
![captcha_image3](https://user-images.githubusercontent.com/70718425/104241067-5e8e2e00-545d-11eb-8b15-1a65c996b2de.png)
![captcha_image4](https://user-images.githubusercontent.com/70718425/104241071-6057f180-545d-11eb-9cbf-dace772dec32.png)
![captcha_image5](https://user-images.githubusercontent.com/70718425/104241077-62ba4b80-545d-11eb-9c28-9d09d27b464e.png)


The algorithm failed to recognize 4 digits among all the test images (which was probably due to the digit extraction algorithm), and didn't classify incorrectly any digit.




