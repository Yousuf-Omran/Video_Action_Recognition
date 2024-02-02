
![image](https://github.com/Yousuf-Omran/Video_Action_Recognition/assets/134161427/165ba1ee-1a3a-44ac-b213-bdfa8c9ad5ab)


# Video_Action_Recognition 🧐#️⃣

#### Enable machines to understand and classify activities performed by individuals by analyzing data acquired from various sensors.
## Challenges 🔥

#### “ The main challenge is how to deal with spatial and temporal information extracted from the video ”

## Methodology

### Data Review 📝
The dataset used was UCF11 (exists in "Dataset_Link_to_Website" above) categorized into 11 classes, each class has approximately 100 videos with 30FPS for each video, and the average video duration ranges from 2 to 7 seconds.

I selected just 4 classes for training which are:
  
    1) volleyball spiking

    2) basketball
    
    3) trampoline jumping
    
    4) diving
you can notice that the jumping action exists in almost all videos in selected classes, which makes it challenging to evaluate the model performance.

### References Method 📄
I performed the “CNN with LSTM” method which is based on the following:

    a- The “Long-term Recurrent Convolutional Networks for Visual Recognition and Description” paper https://arxiv.org/abs/1411.4389.

    b- “Robust Real-Time Violence Detection in Video Using CNN And LSTM” paper https://ieeexplore.ieee.org/document/8852616.


## Performing Steps ✔️  

#### Preprocessing:
-  I resized the height and width to 128 pixels; normalization is performed to reduce the computation time.

-  I reduced the video frames to 25 frames, which selected frames are distributed consistently along the video. 

-  The final dataset shape is (529, 25, 128, 128, 3) indicates (videos, frame, height, width, channel)

-  The data is split into training 80%, validation 10%, and testing 10% set.

-  I resized the height and width to 128 pixels; normalization is performed to reduce the computation time.

#### Model Construction:
-  I used a “MobileNetV2” pre-trained model as a backbone with the “ImageNet” weights to leverage the feature extraction (spatial information) from each frame.

-  The time-distributed layer has been used to store the temporal information before entering the model

-  Then after flattening, I passed the extracted information to the many-to-one LSTM layer to handle sequence data.

-  The video action recognition task is performed by the “SoftMax” activation function.

## Model visualization: 🎨
![frames_for_word](https://github.com/Yousuf-Omran/Video_Action_Recognition/assets/134161427/66606d21-4ee4-4d3c-9af5-796994ef7612)

## Results 📈
The evaluation metrics results from the model are:
    
    1) Accuracy = 98.11% 
    2) Loss = 0.0419
    3) Average Precision = 0.98% 
    4) Average Recall = 0.98%
    5) Average F1-Score = 0.98%

The accuracy and loss graph for the training and validation set exhibited below:
![image](https://github.com/Yousuf-Omran/Video_Action_Recognition/assets/134161427/8c2c84da-1961-4a2c-907a-44c6826396da)
![image](https://github.com/Yousuf-Omran/Video_Action_Recognition/assets/134161427/27c6b37d-9ffb-402a-8d8c-785fd73b879e)

## Limitation & Suggested Solution ➖➕
- #### Number of Frames:
     Identifying an appropriate number of frames is a critical factor in enhancing the model performance, I selected just 25 frames from videos that have approximately (60 to 210) frames. The low number of frames may mislead the model to classify well.

    Suggested Solution:
    
        1) Increase the number of frames despite the high computation time and resources.
      
        2) Using the “Pose Detection and LSTM” method to enhance interpreting of the human interaction with things. 


- #### Number of Trainable Parameters:
    The number of trainable parameters equals 2,625,796 parameters, which is considered slightly high.

    Suggested Solution:
    
        1) Using another reference method to construct the model with low parameters.
      
        2) Constructing the model from scratch leads to control of the number of parameters.

- #### Training Speed:
     The average training time in my model equals 32sec per epoch, reaching 98% accuracy, which is not the lowest training time that exists, I found another model with a time of training reached 13sec with 92% accuracy. You might prefer this accuracy with high speed in training to save time and money especially while training on big data or while you have a real-time application.

    Suggested Solution:
    
        1) Decrease the number of parameters.
      
        2) Utilizing other methods that exist in real-world research papers.

- ####  Insufficient Data:
     I noticed that the data is insufficient, for example, the “trampoline jumping” class contains videos that all have a circular trampoline and have no idea about the modern trampoline hall. After training the model, the model thinks it is a “pool” and misclassifies the action as “diving”.


    Suggested Solution:
    
        1) Collect more diverse data.
      
        2) Augment the data by changing the contrast and color using the OpenCV library.

## Links 🔗 

#### If you have any questions or feedback don't hesitate and reach out to me via email: yousufomran619@gmail.com

#### Or via my LinkedIn account: [![linkedin](https://img.shields.io/badge/linkedin-0A66C2?style=for-the-badge&logo=linkedin&logoColor=white)](https://www.linkedin.com/in/yousuf-omran-5b2884243/)



