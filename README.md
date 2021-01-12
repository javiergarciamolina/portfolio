# Javier Garcia Portfolio

# [Oxford Pets](https://github.com/javiergarciamolina/oxford_pets)

## Objective:

In this project we tried to classify dog and cat images according to their breeds. We used the dataset from the Oxford Pets Kaggle competition, which consists of 7,349 training images and comprises 37 breeds of cats or dogs, which means that we have an average of less than 200 training images per cat or dog breed.

## Result:

 Our model ended up being able to, given the original images, label them like this: 
 
 ![descarga](https://user-images.githubusercontent.com/70718425/104301888-70f18180-54c8-11eb-9613-4f748065a9bf.png)

Our model achieved a testing accuracy of approximately 0.947, with the equal probability benchmark accuracy being 0.027.
After checking that the model's performance was good, I retrained it in all the data, and I used it to participate in the Kaggle competition from which I took the dataset, achieving a multiclass loss of 0.27231, a better performance metric that the one achieved by the winner of the competition:

![score](https://user-images.githubusercontent.com/70718425/104302219-d6457280-54c8-11eb-8def-30a676c9f9d4.png)

With the performance metric being multiclass loss:

![multiclass_loss](https://user-images.githubusercontent.com/70718425/104302308-e6f5e880-54c8-11eb-9698-417223499f9e.png)

## Main technologies used:

* Tensorflow
* Keras
* Matplotlib
* OpenCV
* ImageNet
* Pandas

## Main techniques used:

* Deep Learning
* Modern Computer Vision
* Transfer Learning
* Fine-Tuning 
* Data Augmentation
* Ensemble Learning

## Model:

The final model was an ensemble of ResNet50, ResNet50V2, Xception, Inception, NASNetLarge and InceptionResNetV2, all of them pretrained on the ImageNet dataset, with a new head of units and some regularization.

# [Breaking Captchas](https://github.com/javiergarciamolina/breaking_captchas)

## Objective:
In this project we downloaded a dataset of captcha images and went through the end-to-end process of splitting it into training, validation and test sets, extracting the digits from the images, labelling the ones from the training and validation sets so that we could feed them to a neural network, training a model that could successfully learn to identify the digits, and then using this model for labelling the whole captcha images of the test set. We had 45 classes and 1236 training images.

## Result:
Our algorithm ended up being able to, given the original images, label them like this:
![captcha_image1](https://user-images.githubusercontent.com/70718425/104241021-4f0ee500-545d-11eb-8a14-bcd5dd128762.png)
![captcha_image2](https://user-images.githubusercontent.com/70718425/104241064-5cc46a80-545d-11eb-9b2c-aef2a6ab581c.png)
![captcha_image3](https://user-images.githubusercontent.com/70718425/104241067-5e8e2e00-545d-11eb-8b15-1a65c996b2de.png)
![captcha_image4](https://user-images.githubusercontent.com/70718425/104241071-6057f180-545d-11eb-9cbf-dace772dec32.png)
![captcha_image5](https://user-images.githubusercontent.com/70718425/104241077-62ba4b80-545d-11eb-9c28-9d09d27b464e.png)


Out of 36 testing images (i.e. 144 digits), our algorithm failed to recognize 4 digits, which was probably due to the digit extraction algorithm. It didn't missclassify any digit. Our model achieved a validation accuracy of 0.9677, with the equal probability benchmark accuracy being 0.022.

## Main technologies used:

* Tensorflow
* Keras
* OpenCV
* Matplotlib

## Main techniques used:

* Deep Learning
* Classic Computer Vision
* Modern Computer Vision
* Data Augmentation
* Ensemble Learning

## Model:

The final model used was the regularized MiniVGG network that follows:

![descarga (6)](https://user-images.githubusercontent.com/70718425/104305822-769d9600-54cd-11eb-8e48-4141b5d0b5f4.png)


