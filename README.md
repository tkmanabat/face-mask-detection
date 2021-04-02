# face-mask-detection 😷
![](detections\sample2.png)

A face mask detection app using a **custom trained YOLOv4 model** from Darknet converted to TensorFlow.

## Dataset Used 📁

The dataset used for training was taken from [Kaggle](https://www.kaggle.com/andrewmvd/face-mask-detection). It consists of  **853 images** belonging to the 3 classes, as well as their bounding boxes in the PASCAL VOC format which was later converted to text format (.txt) to be used in the Darknet framework. 

It consists of 3 classes:
<ol>
    <li>With mask </li>
    <li>Without mask</li>
    <li>Mask Weared Incorrect</li>
</ol>



## Detection Model Used 🧙
The detection model used was **YOLOv4**. Yolo (You Only Look Once) is one of the fastest objection detection algorithms. It can provide object detections in real-time.

These were the config and metrics of the custom YOLOv4 model trained in Darknet.
* Used the baseline weights used in the COCO dataset.
* Number of Epochs: **3000** 
* Learning Rate: **0.001**
* Width and Height: **416x416**
* Number of classes: **3**
* Mean Average Precision (mAP): **87.02%** on the dataset.

### Metrics by classes 📉
  

| Class                       |   Average Precision (AP)   |   True Positive (TP)  |   False Positive (FP)  |
|-----------------------------|----------------------------|-----------------------|------------------------|
| With wask                   | 94.80 %                    | 299                   | 37                     |
| Without mask                | 84.53 %                    | 42                    | 9                      |
| Mask weared incorrect       | 81.73 %                    | 152                   | 0                      |

&nbsp;
# Usage 🧩
## Install requirements or use Conda 

### Conda 

```bash
# Tensorflow CPU
conda env create -f conda-cpu.yml
conda activate yolov4-cpu

# Tensorflow GPU
conda env create -f conda-gpu.yml
conda activate yolov4-gpu
```


### Pip
```bash
#If you have CUDA 10.1 Toolkit you can use the GPU requirements.txt
pip install -r requirements-gpu.txt

#For CPU only machines used this
pip install -r requirements-cpu.txt
```
## To Run 
```bash
# Run detections on a webcam
python detect_video.py --weights ./checkpoints/yolov4-416 --size 416 --model yolov4 --video 0 --output ./detections/results.avi

#Run detections on an image
#Put image on /data/images and replace kite.jpg
python detect.py --weights ./checkpoints/yolov4-416 --size 416 --model yolov4 --images ./data/images/kite.jpg
```
## Samples 📷
![](detections\sample1.png)
![](detections\sample3.png)
![](detections\sample4.png)

## References 🎖️
 My project is based on these previous fantastic YOLOv4 implementations:
  * [hunglc007 / tensorflow-yolov4-tflite](https://github.com/hunglc007/tensorflow-yolov4-tflite)
  * [theAIGuysCode / tensorflow-yolov4-tflite](https://github.com/theAIGuysCode/tensorflow-yolov4-tflite)