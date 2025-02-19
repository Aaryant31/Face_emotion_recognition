# Live Class Monitoring System(Face Emotion Recognition)

## Introduction

Face emotion recognition is the process of identifying human emotion. People vary widely in their accuracy at recognizing the emotions of others. Use of technology to help people with emotion recognition is a relatively nascent research area. Generally, the technology works best if it uses multiple modalities in context. To date, the most work has been conducted on automating the recognition of facial expressions from video, spoken expressions from audio, written expressions from text, and physiology as measured by wearables.

Facial expressions are a form of nonverbal communication. Various studies have been done for the classification of these facial expressions. There is strong evidence for the universal facial expressions of seven emotions which include: neutral happy, sadness, anger, disgust, fear, and surprise. So it is very important to detect these emotions on the face as it has wide applications in the field of Computer Vision and Artificial Intelligence. These fields are researching on the facial emotions to get the sentiments of the humans automatically.

## Problem Statement

The Indian education landscape has been undergoing rapid changes for the past 10 years owing to the advancement of web-based learning services, specifically, eLearning platforms.

Global E-learning is estimated to witness an 8X over the next 5 years to reach USD 2B in 2021. India is expected to grow with a CAGR of 44% crossing the 10M users mark in 2021. Although the market is growing on a rapid scale, there are major challenges associated with digital learning when compared with brick and mortar classrooms.
One of many challenges is how to ensure quality learning for students. Digital platforms might overpower physical classrooms in terms of content quality but when it comes to understanding whether students are able to grasp the content in a live class scenario is yet an open-end challenge.
In a physical classroom during a lecturing teacher can see the faces and assess the emotion of the class and tune their lecture accordingly, whether he is going fast or slow. He can identify students who need special attention.

Digital classrooms are conducted via video telephony software program (ex-Zoom) where it’s not possible for medium scale class (25-50) to see all students and access the mood. Because of this drawback, students are not focusing on content due to lack of surveillance.

While digital platforms have limitations in terms of physical surveillance but it comes with the power of data and machines which can work for you. It provides data in the form of video, audio, and texts which can be analyzed using deep learning algorithms.

Deep learning backed system not only solves the surveillance issue, but it also removes the human bias from the system, and all information is no longer in the teacher’s brain rather translated in numbers that can be analyzed and tracked.

I will solve the above-mentioned challenge by applying deep learning algorithms to live video data.
The solution to this problem is by recognizing facial emotions.

## Dataset Information

The data comes from the past Kaggle competition “Challenges in Representation Learning: Facial Expression Recognition Challenge”. The faces have been automatically registered so that the face is more or less centered and occupies about the same amount of space in each image. 
* This dataset contains 35887 grayscale 48x48 pixel face images.
* Each image corresponds to a facial expression in one of seven categories 

    Labels: 
    > * 0 - Angry :angry:</br>
    > * 1 - Disgust :anguished:<br/>
    > * 2 - Fear :fearful:<br/>
    > * 3 - Happy :smiley:<br/>
    > * 4 - Sad :disappointed:<br/>
    > * 5 - Surprise :open_mouth:<br/>
    > * 6 - Neutral :neutral_face:<br/>


Dataset link - https://www.kaggle.com/msambare/fer2013

## Dependencies

1)	Python 3
2)	Tensorflow 2.0
3)	Streamlit
4)	Streamlit-Webrtc
5)	OpenCV


## Model Creation

### 1)	Using Transfer Learning(ResNet50)

Transfer learning (TL) is a research problem in machine learning (ML) that focuses on storing knowledge gained while solving one problem and applying it to a different but related problem. For example, knowledge gained while learning to recognize cars could apply when trying to recognize trucks. Reusing or transferring information from previously learned tasks to learning of new tasks has the potential to significantly improve the sample efficiency of a Data Scientist


![](https://github.com/Ali-Asgar-Lakdawala/Face-Emotion-Recognition/blob/main/Images/Transfer-learning.png?raw=true)
 
•	We have trained the model with ResNet50 and got the training accuracy of 46% and validation accuracy of 25% which is not axceptaable.This error is may be because the model was trained on rgb images and the data set contains grascale images. 


### 2)	Using  Convolutional Neural Network

A Convolutional Neural Network (ConvNet/CNN) is a Deep Learning algorithm which can take in an input image, assign importance (learnable weights and biases) to various aspects/objects in the image and be able to differentiate one from the other. The pre-processing required in a ConvNet is much lower as compared to other classification algorithms. While in primitive methods filters are hand-engineered, with enough training, ConvNets have the ability to learn these filters/characteristics.
The architecture of a ConvNet is analogous to that of the connectivity pattern of Neurons in the Human Brain and was inspired by the organization of the Visual Cortex. Individual neurons respond to stimuli only in a restricted region of the visual field known as the Receptive Field. A collection of such fields overlap to cover the entire visual area.

![](https://github.com/Ali-Asgar-Lakdawala/Face-Emotion-Recognition/blob/main/Images/CNN%20Structure.jpeg?raw=true)
 

•	The training gave the accuracy of 71% and test accuracy of 66%. It seems excellent. So, I save the model and the detection i got from live video was excellent.

•	One drawback of the system is the some Disgust faces are showing Neutral .Because less no. of disgust faces are given to train .This may be the reason.

•	I thought it was a good score should improve the score.

•	Thus I decided that I will deploy the model.

## Performance Metrix

![image](https://user-images.githubusercontent.com/85615221/145667263-12bcd9a2-275e-4850-b588-64e4f940b51e.png)

### Confusion Matrix (Normalized) 
![](https://github.com/Ali-Asgar-Lakdawala/Face-Emotion-Recognition/blob/main/Images/Confusion%20Matrix.PNG?raw=true)

## Realtime Local Video Face Detection
The following video contains the real time deploymnet of the app in local runtime



https://user-images.githubusercontent.com/85615221/145667271-62195d95-64fc-428c-8d73-66968de3b1fa.mp4



## Deployment of Streamlit WebApp in Heroku and Streamlit

We have created front-end using Streamlit for webapp and used streamlit-webrtc which helped to deal with real-time video streams. Image captured from the webcam is sent to VideoTransformer function to detect the emotion. Then this model was deployed on heroku platform with the help of buildpack-apt which is necessary to deploy opencv model on heroku.


| Website | Link |
| ------ | ------ |
| Heroku | https://face-recognition-emotion.herokuapp.com/ | 
| Streamlit | https://share.streamlit.io/aaryant31/face_emotion_recognition/main/app.py |


## Conclusion

* We were successfull in deploying the strealit app on heruko with the model accuracy of 66 %.
* Accuracy can be increased by training the model for longer time with more no of images which can be created by data augmentation
