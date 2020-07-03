# Wheat detection
Kaggle competition of wheat detection

Competition
https://www.kaggle.com/c/global-wheat-detection

"In this competition, you’ll detect wheat heads from outdoor images of wheat plants,\
including wheat datasets from around the globe. Using worldwide data, you will focus on\
a generalized solution to estimate the number and size of wheat heads."

Training baseline is very easy:\
Very much augmentation + FasterRCNN (Pytorch)

Train Colab Notebook https://colab.research.google.com/drive/1Wh1YwRZaTukzNw4Y8yTji_yRLawBH98l?usp=sharing

Also a little improvement gives pseudo labeling. The point is to use trained model to label a little test set (10 images in our case)\
and train again for a few epochs.

Pseudo labeling Colab Notebook https://colab.research.google.com/drive/1bl3ob0GpNfdHf_6dAiuUnAukpBheE-kc?usp=sharing

Inference is more complex. To get best results were used:
1. Ensemble over KFold models
2. TTA (Test Time Augmentation)
3. WBF (Weighted Box Fusion) - better replacement of NMS (Non-Maximum Supression)

It is a code competition so inference is made on Kaggle server. Code you can see in Baseline_inference.ipynb.

The metric used in competition is RSNAObjectDetectionAP. It some slightly modified mAP.\
On evaluation mAP was used.\
After all this steps on score on LB on single model was 0.7171 and with ensemble 0.7262.\
This result give 24 % place on leaderbord with a very simple model (FasterRCNN paper was published in 2015, such ancient time)

But in june was introduced YOLOv5 (there are some dispute about naming) https://github.com/ultralytics/yolov5 \
The implementation based on PyTorch but not on Darknet as other versions of YOLO.\
My first try gives 0.7375 on single model.\
You can check it https://www.kaggle.com/sergeisoly


Train Colab Notebook https://colab.research.google.com/drive/1fxHorYFsc68R_jCMs_YmH6Hb3WdFlKsg?usp=sharing
