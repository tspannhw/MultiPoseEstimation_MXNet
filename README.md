# MXNet Multi Person Pose Estimation
This is a MXNet version of Realtime_Multi-Person_Pose_Estimation, original code is here https://github.com/ZheC/Realtime_Multi-Person_Pose_Estimation 
and here https://github.com/tensorboy/pytorch_Realtime_Multi-Person_Pose_Estimation

## Introduction
Code repo for reproducing 2017 CVPR Oral paper using MXNet.  

## Require
1. [MXNet](http://mxnet.io)
2. pip install mxnet-cu92 tensorflow mxboard
3. pip install pycocotools

## Evalute
- `python evaluate.py` to evaluate the model on [images separated by the original author](https://github.com/CMU-Perceptual-Computing-Lab/caffe_rtpose/blob/master/image_info_val2014_1k.txt)
- It should have `mAP 0.598` for the original rtpose, original repo have `mAP 0.577` because we do left and right flip for heatmap and PAF for the evaluation. 

### Pretrained Models & Performance on the dataset split by the original rtpose.

|   Reported on paper (VGG19)| mAP in origin repo (VGG19)| map in PyTorch Repo (VGG19)| mAP in this Repo (resnet18 inspired by SimplePose) |
|  :------:                  | :---------:               | :---------:                | :---------:                                        | 
|   0.577                    | 0.598                     |  0.614      |              |                                                    |



## Training
- `cd data; bash getData.sh` to obtain the COCO images in `data/dataset/COCO/images/`, keypoints annotations in `data/dataset/COCO/annotations/`
- Download the mask of the unlabeled person at [Dropbox](https://www.dropbox.com/s/bd9ty7b4fqd5ebf/mask.tar.gz?dl=0) in `data/dataset/COCO/mask`
- Download the official training format at [Dropbox](https://www.dropbox.com/s/0sj2q24hipiiq5t/COCO.json?dl=0) in `data/dataset/COCO.json`

then run:

`python train_model.py --gpu_ids 0 --lr=0.001 --wd=0.00001 --momentum=0.9 --log_key="lr_1_wd_0.0001_momentum_0.9"`

<img width="356" alt="screen shot 2018-12-20 at 4 51 40 pm" src="https://user-images.githubusercontent.com/3716307/50296004-b8d48480-0479-11e9-8197-57b4c5ce123b.png">

## Related repository
- CVPR'16, [Convolutional Pose Machines](https://github.com/shihenw/convolutional-pose-machines-release).
- CVPR'17, [Realtime Multi-Person Pose Estimation](https://github.com/ZheC/Realtime_Multi-Person_Pose_Estimation).

### Network Architecture
- testing architecture
![Teaser?](https://github.com/tensorboy/pytorch_Realtime_Multi-Person_Pose_Estimation/blob/master/readme/pose.png)

- training architecture
![Teaser?](https://github.com/tensorboy/pytorch_Realtime_Multi-Person_Pose_Estimation/blob/master/readme/training_structure.png)

## Contributions

All contributions are welcomed. If you encounter any issue (including examples of images where it fails) feel free to open an issue.

## Citation
Please cite the paper in your publications if it helps your research:    

    @InProceedings{cao2017realtime,
      title = {Realtime Multi-Person 2D Pose Estimation using Part Affinity Fields},
      author = {Zhe Cao and Tomas Simon and Shih-En Wei and Yaser Sheikh},
      booktitle = {The IEEE Conference on Computer Vision and Pattern Recognition (CVPR)},
      year = {2017}
      }
      
    @INPROCEEDINGS{8486591, 
    author={H. Wang and W. P. An and X. Wang and L. Fang and J. Yuan}, 
    booktitle={2018 IEEE International Conference on Multimedia and Expo (ICME)}, 
    title={Magnify-Net for Multi-Person 2D Pose Estimation}, 
    year={2018}, 
    volume={}, 
    number={}, 
    pages={1-6}, 
    month={July},}
