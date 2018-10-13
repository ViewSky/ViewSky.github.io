---
title: My Projects
tags: 
- Deep Learning
- ResNet
- Classification
- FPGA
- PCB
categories:
- Projects
---
# I. ResNet-SSD
  As Intel CPU has its high throughput advantage to handle object detection tasks with supporting of enough memory, the new SSD（Single Shot MultiBox Detector) model based on ResNet-18 was proposed and implemented. I replaced the VGG-16 in original SSD with the fully-reduced ResNet-18. I retrained and accelerated the training process with Intel®MKL on Xeon®E5-2699 v4. The two pictures below showed the detection effect between original VGG-SSD and new ResNet-SSD.
 <div align="center">![“Bottle Detection Result”](/images/bottle.png) Fig1.1 detection evaluation on bottle </div>
 
---------------------
 <div align="center">![“Bus Detection Result”](/images/bus2.png)
 Fig1.2 detection evaluation on bus </div>
For the purpose of improving detection accuracy, I tried several ResNet-18 SSD models and finetuned models with special skills. The final ** mAP ** achieved ** 66.2% ** on VOC2007 validation dataset compared to YOLO V2(76.8%), SSD(77.2%). 
 <div align="center">Fig1.3 Results of 120K iterations 
 ![“ResNet-SSD Train Loss&mAP”](/images/ssd_loss_map.png)</div>

# II. Lung abnormal detection
Huiying medical corporation support us origin medical images of lung X-Ray from hospitals in China. I labeled all lung images and made two lmdb datasets in order to train and validate models. The figure showed the classification result of lung images based on my model. 
<div align="center">Fig2.1  Classification demo
![“Lung classification”](/images/lung.png)</div>
I finetuned ResNet-12, ResNet-15, ResNet-18 and ResNet-23 with pretrained models based on Image1K and improved the ** AUC ** of test dataset to ** 0.88 **.
<div align="center">![“resnet-18_dropout51200”](/images/resnet-18_dropout51200.png)
Fig2.2  Result of 51200 iterations(resnet-18)</div>
 
---------------------
# III. Hardware(Shematic&PCB design)
The prototype board has been accomplished and can be stably and reliably used in the KTX system. I proposed new feedback design of the active control system which can reduce error field of vertical gap in KTX.  
<div align="center">![“ktx board”](/images/board.jpg)
Fig3.1  KTX board design</div>
The feedback system contained 16 Rogowski coils, two-stage amplifiers, high-speed ** ADCs, Cyclone V FPGA, DDR2, RS-485, USB2.0, 100M Ethernet **. The main work was to implement the matrix algorithm parallel calculation using FPGA in real time which has lower latency than implementing it in the software on computer.
 <div align="center">Fig3.2  KTX feedback formula
 ![“ktx formula”](/images/formula.png)</div>
 
---------------------
# IV. STM32F407 VOIP SYSTEM
To ensure the security of elevator system, I transplanted ** LwIP ** network protocol into the STM32F407 platform and designed the distributed monitoring system based on IoT. I wrote ** bootloader ** code to realize remote upgrade of the system through ethernet. Meanwhile I realized network ** real-time ** talking between passengers in the elevator with people in the remote control center. To reduce bandwidth consumption of distributed management system, I transplanted the ** Speex ** codecs algorithm into the STM32 platform, and the data compression ratio achieved 32:1.
 
---------------------

