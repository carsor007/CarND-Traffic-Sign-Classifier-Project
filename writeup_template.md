#**Traffic Sign Recognition** 

##Writeup Template

###You can use this file as a template for your writeup if you want to submit it as a markdown file, but feel free to use some other method and submit a pdf if you prefer.

---

**Build a Traffic Sign Recognition Project**

The goals / steps of this project are the following:
* Load the data set (see below for links to the project data set)
* Explore, summarize and visualize the data set
* Design, train and test a model architecture
* Use the model to make predictions on new images
* Analyze the softmax probabilities of the new images
* Summarize the results with a written report


[//]: # (Image References)
[image5]:  ./examples/graph.png "Graph"
[image6]:  ./german_traffic_signs/1.png "No vehicles"
[image7]:  ./german_traffic_signs/2.png "Roundabout mandatory"
[image8]:  ./german_traffic_signs/3.png "Speed limit 60km/h"
[image9]:  ./german_traffic_signs/4.png "Go straight or right"
[image10]: ./german_traffic_signs/5.png "Turn right ahead"

## Rubric Points
###Here I will consider the [rubric points](https://review.udacity.com/#!/rubrics/481/view) individually and describe how I addressed each point in my implementation.  

---
###Writeup / README

####1. Provide a Writeup / README that includes all the rubric points and how you addressed each one. You can submit your writeup as markdown or pdf. You can use this template as a guide for writing the report. The submission includes the project code.

You're reading it! and here is a link to my [project code](https://github.com/carsor007/CarND-Traffic-Sign-Classifier-Project/blob/master/Traffic_Sign_Classifier.ipynb)

###Data Set Summary & Exploration

####1. 

I used the pandas library to calculate summary statistics of the traffic
signs data set:

* The size of training set is: 34799 samples
* The size of the validation set is: 4410 samples
* The size of test set is : 12630 samples
* The shape of a traffic sign image is : 32 x 32 x 3
* The number of unique classes/labels in the data set is : 43

####2. Include an exploratory visualization of the dataset.

Here is an exploratory visualization of the data set. 
First I printed out the sign names from the csv file. I then plotted the histogram for the y_train

![alt text][image5]

###Design and Test a Model Architecture

#### 
  ###For the preprocessing steps I converted the RGB images into grayscale to focus on the important shapes. In order to focus on the shape and other characteristics of the traffic sign instead of brightness, shading, etc. I did the conversion from RGB to grayscale. 
 I added the epoch and batch size and defined the learning rate for the best possible results. I then trained the model with my training dataset. My neural network has two convolution layers and two fully connected layers. For the training dataset I defined a dropout rate to prevent overfitting.

My final model consisted of the following layers:

| Layer         		|     Description	        					| 
|:---------------------:|:---------------------------------------------:| 
| Input         		| 32x32x1 grayscaled image 						| 
| Convolution       	| 1x1 stride, valid padding, outputs 28x28x3 	|
| RELU					|												|
| Max pooling	      	| 2x2 stride, same padding, outputs 14x14x6 	|
| Convolution 3x3	    | 1x1 stride, valid padding, outputs 10x10x16	|
| RELU					|												|
| Max pooling	      	| 2x2 stride, same padding, outputs 5x5x16 		|
| Dropout				|												|
| Fully connected 1		| Output 120, dropout rate: 0.75    			|
| RELU					|												|
| Dropout				|												|
| Fully connected 2		| Output 84, dropout rate: 0.75     			|
| RELU					|												|
| Dropout				|												|
| Logits/Output layer   | Output 43 									|
 
After the train and valdiation process I tested my model against the test dataset. The accuracy is 92.1%.

* learning rate is 0.001
* epochs is 40
* batch size is 128
* dropout for train data is 0.75
* dropout for validation and test data is 1.0

My final model results were:
* training set accuracy of 99.7%
* validation set accuracy of 94.0% 
* test set accuracy of 92.1%
 


 

###Test a Model on New Images

####1. Choose five German traffic signs found on the web and provide them in the report. For each image, discuss what quality or qualities might be difficult to classify.

Here are five German traffic signs that I found on the web:

![alt text][image6]

![alt text][image7]

![alt text][image8]

![alt text][image9]

![alt text][image10]


One image was classified correctly which might be because it was a number. The "60" sign for is clear  which makes it easier for the CNN to classify it. Most images might have beeen difficult to classify because they were all sign based and not number based. Probably due to a lack of enough images to train or the train images were either too different or not similar enough to my provided image. 


Here are the results of the prediction:

| Image			        |     Prediction	        					| 
|:---------------------:|:---------------------------------------------:| 
| Roundabout mandatory      		| Keep right   									| 
| Speed limit 60km/h     			| Speed limit 60km/h										|
| Go straight or right					| Keep right										|
| No vehicles      		| Speed limit 60km/h					 				|
| Turn right ahead			| Speed limit 80km/h    							|


The model was able to correctly guess 1 of the 5 traffic signs, which gives an accuracy of 20%. 



