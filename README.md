
![GitHub](https://img.shields.io/github/license/mashape/apistatus.svg) ![Depfu](https://img.shields.io/depfu/depfu/example-ruby.svg) 
![Travis (.org)](https://img.shields.io/travis/:user/:repo.svg) [![Open Source Love](https://badges.frapsoft.com/os/v1/open-source.svg?v=103)](https://github.com/ellerbrock/open-source-badges/)





# Emotion-Detection-from-Speech



Given a voice detecting emotion it holds. Such as - Angry, Happy, Sad, Disgust, Neutral, Surprise &amp; Pleasant. Etc... 

`dhawal`& `Manish Mishra` helped me in many ways. Heartily Thanks to both of them.

## File name & Download
The speeches used for this project had some specific naming format that one need to put attention on. 
Our file has `OAF_bite_neutral` this name format. Since we have 2 speakers old and young, here this voice was uttered by old speaker and this voice `YAF_back_fear` a young speaker. One sould visit the website of data set to understand it well enough. 
https://tspace.library.utoronto.ca/handle/1807/24487

Since there is no way to download whole data set at one click, you have to click at least 3,000 times if you will go by conventional way of downloading. Don't waste your time in downloading one and one file. Just add an extention `Download Master` for Chrome users. it will help you to collect whole data in few clicks. of course it is a time consuming process. Very soon you can get whole data on my online drive. Be patient till then. 

### Librosa was used to extract the feature out of a given voice. 
```python
def extract_feature(file_name):
    X, sample_rate = librosa.load(file_name)
    stft = np.abs(librosa.stft(X))
    mfccs = np.mean(librosa.feature.mfcc(y=X, sr=sample_rate, n_mfcc=40).T, axis=0)
    chroma = np.mean(librosa.feature.chroma_stft(S=stft, sr=sample_rate).T, axis=0)
    mel = np.mean(librosa.feature.melspectrogram(X, sr=sample_rate).T, axis=0)
    contrast = np.mean(librosa.feature.spectral_contrast(S=stft, sr=sample_rate).T, axis=0)
    tonnetz = np.mean(librosa.feature.tonnetz(y=librosa.effects.harmonic(X),
                                              sr=sample_rate).T, axis=0)
    return mfccs, chroma, mel, contrast, tonnetz

``` 
the function take the files and return 5 features. Namely, `MFCC`,`Chroma`,`Mel`,`Contrast` & `Tonnetz`

thereafter, wee need to parse the files as follows 

```python
def parse_audio_files(path):
    features, labels = np.empty((0, 193)), np.empty(0)
    labels = []
    for fn in glob.glob(path):
        try:
            mfccs, chroma, mel, contrast, tonnetz = extract_feature(fn)
        except Exception as e:
            print("Error encountered while parsing file: ", fn)
            continue
        ext_features = np.hstack([mfccs, chroma, mel, contrast, tonnetz])
        features = np.vstack([features, ext_features])
        labels = np.append(labels, fn.split("_")[3].split(".")[0])
        print(fn)
    return np.array(features), np.array(labels)
```

## For training 
put audio files in folder name train_sounds

run the training script

it will save the trained model as xyz_Model_protocol2.sav

## For prediction
put input files (for which you want to predict emotion) in folder name test_sounds

run the test script


here is what we achieved when `training` on `Decision tree` 

![title](https://github.com/nirajdevpandey/Emotion-Detection-from-Speech/blob/master/results/images/decision%20tree_train.PNG)

### During test 

![title](https://github.com/nirajdevpandey/Emotion-Detection-from-Speech/blob/master/results/images/decision%20tree_test.PNG)

The best accuracy I got was from Keras `(Neural Network)` and with `ExtraTreeClassifier`


### While training on `ExtraTreeClassifier`

![title](https://github.com/nirajdevpandey/Emotion-Detection-from-Speech/blob/master/results/images/ExtraTreeClassifier_train.PNG)

### During Test 

![title](https://github.com/nirajdevpandey/Emotion-Detection-from-Speech/blob/master/results/images/ExtraTreeClassifier_test.PNG)

It's preety good..!! 
Isn't it ??




