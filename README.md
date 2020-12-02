# Digit-Recognition-Model
Model to recognize hand-written digits provided in MNIST data.

## Data Source
The famouse MNIST digit recognition dataset was used for this project. Data was sourced from Kaggle's open competition for digit recognition [MNIST in CSV](https://www.kaggle.com/oddrationale/mnist-in-csv). Please download data before running any of the notebook. CSVs are not included in the repository.

## Data preparation
No major data preprocessing was required as it is fairly clean dataset. It contains 784 features representing each pixel in a 28x28 image. and 1 target feature containing digit label from 0 to 9. Each pixel value ranges from 0 to 255 as a simple grayscale image does. We used MinMaxScaler of sklearn to convert each pixel's value between 0 and 1.

## Data Modelling
3 different models were trained as shown in 3 different notebook files

### SVM
First SVM was trained on the dataset. Initial model gave fairly good results but took very long to train.
After hyperparameter tuning we achieved slightly better results. 
We tried SVD on our trainig data and train the last model again to see if their is any improvement in training time or accuracy. Same model was trained in less time and showed lesser overfitting and better testing accuracy. Final accuracy on test set was 97.35%

### Tree-based models
We tried decision tree models to see how it compared with SVM. Even after hyperparameter tuning, very poor performance was shown by DecisionTree. Cross-validation accuracy of only 86% was achieved by this model.
Then we used our final decision tree as base estimator of an AdaBoost model and trained it with 100 estimators. Final score of 96.4% was achieved by this model which is a huge improvement over Decision Trees.

### Neural Network based models
In a separate notebook, we tried neural networks using tensorflow and keras for this problem. First simple shallow neural network based model was tried. Multiple variations of neurons, layers, epochs, batch_size and optimization algorithms were tried. Best result was acheived by model having 3 dense layers between input and output layers with output layer having softmax activation function and RMSProp optimization. Best score on test set was 97.5%
Then in the end, CNN based neural network was tried. Multiple experiments were run before finalizing the structure. In the end 3 pairs of Conv2d and MaxPooling2D layers were used before flattening and joining to output layer. The final CNN model gave test accuracy of 98.5% which was best of all.