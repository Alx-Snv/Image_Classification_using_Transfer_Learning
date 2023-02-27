# Image Classification using Transfer Learning
The reuse of a previously learned model on a new problem is known as transfer learning. It’s particularly popular in deep learning right now since it can train deep neural networks with a small amount of data.
It is beneficial to save time and resources while also helping to take advantage of the data from the first time to draw out information that may be useful when directly making predictions for some other setting.
The model used here is VGG16, a pre-trained model whose weights can be used to create our own model. This model can give us the output of 1000 categories since they were trained on image net datasetbut in our case we require only 3 categories.
Image classification is assigning labels to images based on certain parameters or features present in the image.
# About the dataset
- The image classification performed today will be a fruit image classification where we will be using a dataset containing labelled images of three fruits: apple, banana and oranges.
These images are already split into training and testing.
# Data processing
- The training and testing data are read into two different variables and using ImageDataGenerator we rescale the images.
- The data is further augmented by setting the target size of the images, batch size containing number of images to sent per batch and mode depending on the number of output categories. We will be selecting 
categorical as we have 3 categories.
# Data modeling
- We import the VGG16 model from tensorflow and using the same weights applied during imagenet competition and excluding the top layers from the training phase as our data has only 3 output categories.
- Generating a sequential model and adding the VGG16 model architecture.
- Adding on flatten layer to create a single dimensional array and utilizing softmax function in the ouptut layer.
- Compiling the model using categorical cross entropy, adam optimizer and accuracy as metric for evaluation.
- After training the model we then proceed to testing the model, where we will create a variable to accept the test image and then resize the image to the target size previously mentioned.
- Once the resizing is done, we will convert the image into a array and then we will expand the dimensions of the array because keras expects input with 4D shape. But most libraries load input with 3D shapei.e. it will expand from (height, width, channels) to (n_samples, height, width, channels).
- Keras then preprocesses the input to adequate your image to the format the model requires. Some models use images with values ranging from 0 to 1. Others from -1 to +1.
- A variale is created to store the prediction result and another variable is created to store the category labels. As the output is an array which depicts the likelihood of each category being the output, argmax function is used to give the one category which has the maximum probability of being the output.
- This output is then inserted into the category labels to give the name of the output category.
# Results
- The training accuracy of the model was upto 99%
-The testing accuracy however reached upto only 84% which is quite a drop, but overall still gave fairly correct output when tested multiple times against different test images.
