# Small_object_detection_project
Improving performance in object detection for small objects

The detection of the small object has been challenging because of the limitation of the property of the convolutional neural network. For this project, I tried two methods to improve the performance of small objects detection. The first method is upscaling or improving the details of the image by using the concept of super-resolution. The second method is the process of performing prediction over small slices of the original image and then merging predictions from all sliced images on the original image. To detect small objects, I used the DOTA dataset [12] which contains aerial images. For the super-resolution method, I used the Efficient Sub-pixel Convolutional Neural Network (ESPCN). With these methods, I could get 27.5% mAP, 46.4% mAP_50, 28.0% mAP_75 from 15.7% mAP, 26.3% mAP_50, 15.6% mAP_75 without any methods.
[Paper:](project.pdf)

## ESPCN Model
The Efficient Sub-Pixel Convolutional Neural Network (ESPCN) upscales the resolution at the end of the network. In ESPCN, the upscaling step is applied in the last layer. For this reason, the low-resolution image can be fed to the network unlike the SRCNN and FSRCNN. With this benefit, the ESPCN does not need to use the interpolation method. Moreover, the reduced input image size can make the model use a smaller kernel size that is used to extract features.

- Paper: [Real-Time Single Image and Video Super-Resolution Using an Efficient Sub-Pixel Convolutional Neural Network](https://arxiv.org/pdf/1609.05158.pdf)

## Results
![result](/data/Picture1.png)

Prediction test images - Left: without sliced inference, Right: with sliced inference

![result2](/data/Picture2.png)

Prediction on the low-resolution test images with sliced inference – Left: without super-resolution, Right: with super-resolution.


| Validation | mAP | mAP_50 | mAP_75 | mAP_S | mAP_M | mAP_L |
| ---------- | ---------- | ---------- | ---------- | ---------- | ---------- | ---------- |
| 1X - Image | 15.7% | 26.3% | 15.6% | 2.8% | 12.4% | 30.1% |
| 2X - Image | 10.9% | 18.3% | 10.8% | 0.1% | 3.9% | 14.4% |

- Table1: Results on DOTA-v1.0 validation set with Fast RCNN. – without sliced images inference.

| Validation | mAP | mAP_50 | mAP_75 | mAP_S | mAP_M | mAP_L |
| ---------- | ---------- | ---------- | ---------- | ---------- | ---------- | ---------- |
| 1X - Image | 26.9% | 45.4% | 27.1% | 8.2% | 27.1% | 39.8% |
| 2X - Image | 27.5% | 46.4% | 28.0% | 3.4% | 21.7% | 32.2% |

- Table2: Results on DOTA-v1.0 validation set with Fast RCNN. – with sliced images inference.

## Dataset
- The DOTA includes large-scale aerial images for object detection. To get the images, different sensors and platforms are used. The size of an image in DOTA data is in the range of 800×800 to 20,000×20,000 pixels. DOTA-v1.0 contains 15 common categories, 2,806 images and 188, 282 instances. The proportions of the training set, validation set, and testing set in DOTA-v1.0 are 1/2, 1/6, and 1/3, respectively.
- Paper: [DOTA: A Large-scale Dataset for Object Detection in Aerial Images](https://openaccess.thecvf.com/content_cvpr_2018/papers/Xia_DOTA_A_Large-Scale_CVPR_2018_paper.pdf)
- Data: [The Dota dataset](https://captain-whu.github.io/DOTA/dataset.html)
