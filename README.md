# Emotion-Detection-from-Speech



Given a voice detecting emotion it holds. Such as - Angry, Happy, Sad, Disgust, Neutral, Surprise &amp; Pleasant. Etc...

the accuracy of the model is really bad at the moment , Hold on .... till December 15. You will see a good model. Thanks 


Find complete 2800 stimuli here on my google drive - https://drive.google.com/drive/u/0/my-drive

Ensembles are created by @dhawal. @Manish Mishra helped me in many ways too. Heartily Thanks to both of them.

# File name & Download
The speeches used for this project had some specific naming format that one need to put attention on. 
Our file has [OAF_bite_neutral] this name format. Since we have 2 speakers old and young, here this voice was uttered by old speaker and this voice [YAF_back_fear] a young speaker. One sould visit the website of data set to understand it well enough. 
https://tspace.library.utoronto.ca/handle/1807/24487

Since there is no way to download whole data set at one click, you have to click at least 3,000 times if you will go by conventional way of downloading. Don't waste your time in downloading one and one file. Just add an extention "Download Master" for Chrome users. it will help you to collect whole data in few clicks. of course it is a time consuming process. Very soon you can get whole data on my online drive. Be patient till then. 

# For prediction
put input files (for which you want to predict emotion) in folder name new_test_sounds

run script ensemble_emotion_simulation.py

# For training 
put audio files in folder name train_sounds

run script ensemble_emotion_training.py

it will save the trained model as Ensemble_Model_protocol2.sav
