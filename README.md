# Image_classification
The aim of this project was to classify images from the 5-flower dataset using the MobileNetV2 architecture. I completed this project as part of my learning journey in computer vision, with the goal of developing practical experience in image classification and deep learning. Here, the question I aim to ask is: How do different transfer learning methods affect MobileNetV2's performance in classifying the 5-flower dataset? 

## 💮 The dataset 
The 5-flowers dataset contains around 4000 images of sunflowers, roses, daisies, dandelions, and tulips. The data can be found here: [5-flowers dataset](https://www.tensorflow.org/datasets/catalog/tf_flowers) 

## 💻 Model architecture
**Base model**: MobileNetV2 </br>
- It is a deep CNN architecture designed for image classification and object detection in mobile and embedded vision applications
- Initialized with weights pre-trained on the [ImageNet dataset](https://www.image-net.org/)

**Layers**
-  The original MobileNet classification head was removed by setting ```include_top = False```
- The new classification head structure is as follows:
  - **Global Average pooling 2D**: Reduces the dimensions of the feature maps produced by the model into a compact vector
  - **Dense Layers**:
     - 128 hidden units with ReLU activation
  - **Batch Normalization**: Prevents overfitting of the model 
  - **Output layer**
     - 5 output units corresponding to the 5 flower classes with Softmax activation to produce class probabilities

**Optimizer**
- The model is trained with the Adam optimizer with a learning rate of 0.0001 which was determined through hyperparameter tuning

**Fixed feature extractor**
- The base model layers were frozen by setting ```basemodel.trainable = False```

**Fine tuning**
- The base model layers were trainable by setting ```basemodel.trainable = True```. This allows for fine-tuning of model parameters per the flower dataset

## 🗒️ Setup
**Weights & Biases account**: The training sweep is tracked using [Weights & Biases](https://wandb.ai/site/), a platform for experiment tracking, visualization, and hyperparameter optimization. A W&B account is required to run and monitor the training sweep.

 **Requirements:** </br>
```bash
pip install -r requirements.txt
```

## 📈 Comparison of model performance 
Graphs computing the training and validation accuracies and losses obtained from both methods can be found in the output folder. </br>
Fine_tuning_accuracy.png </br>
Fixed_accuracy.png </br>
Fine_tuning_loss.png </br>
Fixed_loss.png 

## Conclusions


