# Small_object_detection_project
Improving performance in object detection for small objects

The detection of the small object has been challenging because of the limitation of the property of the convolutional neural network. For this project, I tried two methods to improve the performance of small objects detection. The first method is upscaling or improving the details of the image by using the concept of super-resolution. The second method is the process of performing prediction over small slices of the original image and then merging predictions from all sliced images on the original image. To detect small objects, I used the DOTA dataset [12] which contains aerial images. For the super-resolution method, I used the Efficient Sub-pixel Convolutional Neural Network (ESPCN). With these methods, I could get 27.5% mAP, 46.4% mAP_50, 28.0% mAP_75 from 15.7% mAP, 26.3% mAP_50, 15.6% mAP_75 without any methods.


## Data
