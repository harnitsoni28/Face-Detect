# Face-Detect Introduction
Face detection is a computer vision technology that helps to locate/visualize human faces in digital images. This technique is a specific use case of object detection technology that deals with detecting instances of semantic objects of a certain class (such as humans, buildings or cars) in digital images and videos. With the advent of technology, face detection has gained a lot of importance especially in fields like photography, security, and marketing.


![Screenshot](https://user-images.githubusercontent.com/42518457/102313414-a1600180-3f96-11eb-8e36-f2e72eb3d2a6.png)


# Installation 
OpenCV-Python supports all the leading platforms like Mac OS, Linux, and Windows.

run ``pip install opencv-python`` if you need only the main modules
run ``pip install opencv-contrib-python`` if you need both main and contrib modules (check extra modules listing from OpenCV documentation)

# Detecting Faces in an Image Using OpenCV
With OpenCV installed, we can import it as cv2 in our code.

To read an image in, we will use the imread() function, along with the path to the image we want to process. The imread() function simply loads the image from the specified file in an ndarray. If the image could not be read, for example in case of a missing file or an unsupported format, the function will return None.

We will be using an image from Kaggle dataset:

import cv2

path_to_image = 'Parade_12.jpg'
original_image = cv2.imread(path_to_image)
The full RGB information isn't necessary for facial detection. The color holds a lot of irrelevant information on the image, so it's more efficient to just remove it and work with a grayscale image. Additionally, the Viola-Jones algorithm, which works under the hood with OpenCV, checks the difference in intensity of an image's area. Grayscale images point this difference out more dramatically.

Note: In the case of color images, the decoded images will have the channels stored in BGR order, so when changing them to grayscale, we need to use the cv2.COLOR_BGR2GRAY flag:

image = cv2.cvtColor(original_image, cv2.COLOR_BGR2GRAY)
This could have been done directly when using imread(), by setting the cv2.IMREAD_GRAYSCALE flag:

original_image = cv2.imread(path_to_image, cv2.IMREAD_GRAYSCALE)
The OpenCV library comes with several pre-trained classifiers that are trained to find different things, like faces, eyes, smiles, upper bodies, etc.

The Haar features for detecting these objects are stored as XML, and depending on how you installed OpenCV, can most often be found in Lib\site-packages\cv2\data. They can also be found in the OpenCV GitHub repository.

In order to access them from code, you can use a cv2.data.haarcascades and add the name of the XML file you'd like to use.

# Basic Operation on Images
In this section, we will learn how we can draw various shapes on an existing image to get a flavour of working with OpenCV.

Drawing on Images
Functions & Attributes
Writing on Images

# Face Detection
Face detection is a technique that identifies or locates human faces in digital images. A typical example of face detection occurs when we take photographs through our smartphones, and it instantly detects faces in the picture. Face detection is different from Face recognition. Face detection detects merely the presence of faces in an image while facial recognition involves identifying whose face it is.

Face detection is performed by using classifiers. A classifier is essentially an algorithm that decides whether a given image is positive(face) or negative(not a face). A classifier needs to be trained on thousands of images with and without faces. Fortunately, OpenCV already has two pre-trained face detection classifiers, which can readily be used in a program. The two classifiers are: Haar Classifier and Local Binary Pattern(LBP) classifier.

Haar feature-based cascade classifiers
