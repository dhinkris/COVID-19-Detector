# COVID-19-Detector
The world's best Scientists and Doctors are currently working on finding and testing the cure to COVID-19. In the middle of all of this, some countries are unable to find testing kits for the virus, making it really difficult to detect the quickly spreading virus.With the help of <a href=https://github.com/ieee8023>Joseph Paul Cohen's</a> X-ray dataset for COVID-19 patients and resources for ground glass opacities, this project is aimed at helping better and faster diagnosis of the virus while releasing the stress over Radiologists.<br>
In this matter, the biggest task for a machine to classify COVID would be to tackle
1. Detection of Lungs- The datasets currently available for opacities might lead to overfitting and diversion of attention to text or other bones in the X-ray images.<br>
2. Detection of Opacities such as Ground Glass Opacities.
<br>
This project aims to solve these issue to make a robust model which is capable of deployment in the future.
<br>
<h4> Note that the models provided here are not fully tested on real life scenarios. Further testing is essential before concrete claims</h4>
<br>
<img src=https://github.com/DarshanDeshpande/COVID-19-Detector/blob/master/images/Model.png class="center">&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;&nbsp;&nbsp;<img src=https://github.com/DarshanDeshpande/COVID-19-Detector/blob/master/images/PredictionVisualisation.png width=700 height=370 class="center">

# Testing scores(All metrics are weighted because of the intial class imbalance):
<b>Opacity Detection</b><br>
   1.<b>Accuracy</b>- 0.9381 <br>
   2. <b>Precision</b>- 0.9486 <br>
   3. <b>Recall</b>-  0.9332 <br>
   4. <b>F1-Score</b> - 0.9408 <br>
   5. <b>AUC</b> - 0.9845 <br><br>

This result has been checked multiple times on unseen images and so far, for all the testing datasets, the model is able to score similarly.<br>
It will be much appreciated if this model can be tested on further data because for now the small COVID-dataset available might not be a true test for it

# How To Use
1. Install all the requirements by using the following code while in the current directory<br>
```pip install -r requirements.txt```<br>
2. Execute the <a href=https://github.com/DarshanDeshpande/COVID-19-Detector/blob/master/OpacityDetector/Predict.py>Predict.py</a> file through the terminal or your preferred IDE, give your choice of Classification and path of the directory. Done!<br>
```
1. 'COVID-Resnet' for Resnet Based Model
2. 'Custom' for Custom Model 
```
3. After the individual results are displayed, you can choose whether to visualise the gradients of the model. If you do then a window will pop up with the image and it's attention gradients. You can move on to the next image by pressing any key.

# Model Architecture:
The model uses an Inception/Xception Model like approach for Classification. The model consists of Separable Convolutional Layers for the starting layers since it attempts to make the initial extraction process faster. These also wokred significant better than normal Convolutions in this case. At every stage, the Convolution outputs get multiplied and normalized. The use of standard Convolutions in the last layers help in increasing trainable parameters and hence more attention can be given to the smaller features. The Feature Extractor is followed by Fully Connected Layers which finally give the output. The option for gradient visualisation can be treated as a mask if the output desired is a mask.<br><br>
<b> NOTE: This has only been tested on unknown sample images received from <a href=https://github.com/ieee8023/covid-chestxray-dataset>@ieee8023's</a> and <a href=https://twitter.com/ChestImaging/status/1243928581983670272>this</a> twitter post's images. Further testing is essential before concrete claims <b>
   
Full Architecture is attached below: <br>
![Model Architecture](https://github.com/DarshanDeshpande/COVID-19-Detector/blob/master/images/OpacityModelArchitecture.png)


# DATA USED <br>
  1. <a href=https://github.com/ieee8023/covid-chestxray-dataset>COVID-19 Xray images</a>
  2. <a href=https://www.kaggle.com/paultimothymooney/chest-xray-pneumonia>Paul Mooney's Amazing Pneumonia Dataset</a>
  3. <a href=https://twitter.com/ChestImaging/status/1243928581983670272> Twitter dataset for Spanish patients</a>
  3. Link to all images and TFRecord files used for training, validation and testing can be found here on my drive -> https://drive.google.com/open?id=1TvXFMlnjA4LzNBgWLkQLYVMQ-_Kqwsyk
  
# CREDITS <br>
1. Adrian Rosebrock for his article for <a href= https://www.pyimagesearch.com/2020/03/09/grad-cam-visualize-class-activation-maps-with-keras-tensorflow-and-deep-learning/>grad-cam</a> 
