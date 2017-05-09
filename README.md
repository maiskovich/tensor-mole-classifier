## Installation steps:

Install TensorFlow([instructions](https://www.tensorflow.org/install/)). If a GPU is available is highly advised to install the GPU version of TensorFlow and use it during the training of the neural network. The dataset we will be using is heavy and the time to train it can be highly reduce with the usage of a GPU supported by TensorFlow.

Download the dataset from [ISIC Archive](https://isic-archive.com/). As some problems were found during downloading it, as the size its big and it's not possible to resume the download with a web browser, I used [this tool](https://github.com/vgupta-ai/ISIC-Dataset-Downloader) that is written in Python and allows resuming of the download, with a small modification as it was downloading only the first part of the images, please use the version provided in this repository, inside dataset folder. In case it fails will continue from the last image. I am not the author of the script, credits to vgupta-ai GitHub user.

Being inside ISIC-Dataset-Downloader folder, run `python downloadImageMetaData.py` in order to download the metadata of the dataset.

After this script finish run `python downloadImages.py` in order to download all the images(it will take time)

Inside the  ISIC-Dataset-Downloader folder you will find each source of the ISIC dataset is in an independent folder

And inside each folder there is a benign and malignant folder

We need to create a folder for training dataset, put together the images that we want to use for training(copying them from the sources folders, for example 54b6e869bae4785ee2be8652, and putting them into this new folder), divided by benign and malignant. 

Replace the path of the variable 'train_path' with the actual path of your dataset in the file skin_cnn.ipynb

For reading the images with TensorFlow we are using an auxiliary file dataset.py, that is a slight modification of the code presented in this [tutorial](http://cv-tricks.com/tensorflow-tutorial/training-convolutional-neural-network-for-image-classification/) from cv-tricks.com, in order for using this script we need to have the OpenCV library installed. In order to make this installation easier a script is provided(I am no the author, credits to to rsnk96 github user). In order to do this we just need to run  opencvinstall.sh


After this steps we are ready for training the model running the code of the file skin_cnn.ipynb

The script may take between some minutes to several hours or days according to the amount and size of the selected images for the training dataset and the specs of the computer that is running(GPU would provide huge improvements).

As the script saves the trained model on the hard disk, now we can run just run the file predict_image.ipynb specifying the full path to an image that we want to classify as benign or malignant(0 means benign and 1 means malignant, as the classes were defined as  ['benign', 'malignant'] in skin_ccn file)
