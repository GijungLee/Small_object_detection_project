# Small_object_detection_project
Improving performance in object detection for small objects

The detection of the small object has been challenging because of the limitation of the property of the convolutional neural network. For this project, I tried two methods to improve the performance of small objects detection. The first method is upscaling or improving the details of the image by using the concept of super-resolution. The second method is the process of performing prediction over small slices of the original image and then merging predictions from all sliced images on the original image. To detect small objects, I used the DOTA dataset [12] which contains aerial images. For the super-resolution method, I used the Efficient Sub-pixel Convolutional Neural Network (ESPCN). With these methods, I could get 27.5% mAP, 46.4% mAP_50, 28.0% mAP_75 from 15.7% mAP, 26.3% mAP_50, 15.6% mAP_75 without any methods.

## Results
![result](/data/Picture3.png)

- Results on DOTA-v1.0 validation set with Fast RCNN. – without sliced images inference.

| Validation | mAP | mAP_50 | mAP_75 | mAP_S | mAP_M | mAP_L |
| ---------- | ---------- | ---------- | ---------- | ---------- | ---------- | ---------- |
| 1X - Image | 15.7% | 26.3% | 15.6% | 2.8% | 12.4% | 30.1% |
| 2X - Image | 10.9% | 18.3% | 10.8% | 0.1% | 3.9% | 14.4% |

- Results on DOTA-v1.0 validation set with Fast RCNN. – with sliced images inference.

| Validation | mAP | mAP_50 | mAP_75 | mAP_S | mAP_M | mAP_L |
| ---------- | ---------- | ---------- | ---------- | ---------- | ---------- | ---------- |
| 1X - Image | 26.9% | 45.4% | 27.1% | 8.2% | 27.1% | 39.8% |
| 2X - Image | 27.5% | 46.4% | 28.0% | 3.4% | 21.7% | 32.2% |

Results of video summarization. PL: Pseudo labels, RL: Reconstruction loss

### Confusion Matrix
![result2](/data/Picture4.png)



## Dataset
- The brackish dataset contains 89 videos are provided with annotations in the AAU Bounding Box, YOLO Darknet, and MS COCO formats. Fish are annotated in six coarse categories. Categories: Big fish, Small fish, Crab, Shrimp, Jellyfish, Starfish.
- Paper: [Detection of Marine Animals in a New Underwater Dataset with Varying Visibility](https://openaccess.thecvf.com/content_CVPRW_2019/papers/AAMVEM/Pedersen_Detection_of_Marine_Animals_in_a_New_Underwater_Dataset_with_CVPRW_2019_paper.pdf)
- Data: [The Brackish Dataset](https://www.kaggle.com/aalborguniversity/brackish-dataset)
![A group of Sticklebacks](/data/ex1-980x551.png) ![Lumpsucker in clear water](/data/BigFish1.png)
