# Tea-Dataset

## Instructions
The code in this repository was run on Google Colaboratory. The code has been split into modules. The Colab file has been shared as well and can be run as is provided that:
1. The Tea Leaf Disease Dataset is uploaded to the users Google Drive
2. The 'root' argument used by the main function is reset to the path to the dataset in the user's Drive.

## Note on Architecture
I first went through the existing literature on the leaf disease problem. I chose to use a CNN as CNNs are better at feature extraction. I particularly wanted a model that fulfilled two criterea:
1. Could generalise over multiple tasks (as pre-trained models cannot be used)
2. Was small, so that training, and therefore debuggging did not take time. 

ResNet18 fulfilled these two criterea. It has been used on numerous tasks and has only 11M trainable parameters. Further, LeafNet, an architecture for the particular problem of leaf disease detection, uses ResNet50 as its backbone -- further reason to consider a ResNet variant. 

## Note of Hyperparameters
I set the initial learning rate to 0.0001 with weight decay of 0.003 and momentum 0.9. The learning rate was decreased by a factor of 10 at the 14th epoch. The model was trained for 25 epochs. After each epoch, the model tested on the test set. At the end of training, the model's performance was evaluated on the validation set. 

## Note on Datasplit
I use the 80/10/10 split to divide the images into train, validation, and test sets. As a result, the train set has 709 images, the test set has 88 images, and the validation set has 88 images. 

## Note on 10-fold Cross Validation
As the dataset is small, K-Fold Cross Validation is a good method to ensure that the model is able to generalise well. I chose 10 folds (a design choice). Thus each fold is the test set once, and the validation set once.

## Results
