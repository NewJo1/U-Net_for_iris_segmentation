# U-Net_for_iris_segmentation
There are two models shown. The first model has been implemented in file "A_simple_U-net.ipynb". the second is implemented by bubbling. We use his model and do some change, then use dataset we produced. We will give a reference for this model.
## Model 1: A simple U-net
We implement it in google colab. To use this model, the first thing is build a correct folder architecture. We will talk about it later.
Here, we note some points:
* install labelme. We recommend use labelme version = 3.16.7, which is more stable.
* process dataset. We have processed the data using labelme. Here, we just need transfer json to jpg(label image) once. So here, I annotate this part of code.
* keep_image_size_open is used for resize image equally. resize image directly will cause some error.
* the dataset we processed will be given as following link:https://drive.google.com/drive/folders/1QOAUo0swBbwYzKiokeuXr00DbOoQZxd0?usp=sharing
in this google drive, you can see how we establish a folder architecture.
* for training, we use "while true". So you have to stop it manully. You can also set a epoch number. A fixed epoch number is also supported.
### Talking about folder:
* VOC2007/params/unet.pth: used for save parameters
* VOC2007/JPEDImages: save original image for training dataset
* VOC2007/SegmentationClass: save label image for training dataset
* VOC2007/before: save json get from labelme(training)
* VOC2007/show: save predicted result for test dataset
* VOC2007/training image: save forward pass result
* VOC2007/test_image: save stack result(original, label, predicted) for test dataset
* VOC2007/test/JPEDImages: save original image for test dataset
* VOC2007/test/Segmentation: save label image for test dataset
* VOC2007/test/before: save json get from labelme(test)

# Model 2: Fine tuned U-net
This model we find it on the github, and changed a lot bit, in this model we freeze and use pre-trained parameters and then unfreeze and train all the parameters. 
The original code link is :https://github.com/bubbliiiing/unet-keras.git
## we changed
* classes = ["_background_","iris"]
* num_classes = 2
* The parameters we trained: https://drive.google.com/file/d/1YKDAgz10Ugb9pDYUPkVYA5VUjWQ3UGcd/view?usp=sharing 
## Require
scipy==1.2.1
numpy==1.17.0
matplotlib==3.1.2
opencv_python==4.1.2.30
torch==1.2.0
torchvision==0.4.0
tqdm==4.60.0
Pillow==8.2.0
h5py==2.10.0
* install labelme. We recommend use labelme version = 3.16.7, which is more stable.
* process dataset. We have processed the data using labelme. Here, we just need transfer json to jpg(label image) once. So here, I annotate this part of code.
* the dataset we processed will be given as following link:https://drive.google.com/drive/folders/1QOAUo0swBbwYzKiokeuXr00DbOoQZxd0?usp=sharing
### Talking about folder:
Folder architecture is similiar to the previous model, you can just download the original code and use "we changed", parameters mentioned in previous.
