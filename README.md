# Wheat detection
Kaggle competition of wheat detection

Competition
https://www.kaggle.com/c/global-wheat-detection

"In this competition, you’ll detect wheat heads from outdoor images of wheat plants,\
including wheat datasets from around the globe. Using worldwide data, you will focus on\
a generalized solution to estimate the number and size of wheat heads."

Training baseline is very easy:
Very much augmentation + FasterRCNN (Pytorch)

Inference is more complex. To get best results were used:
1. Ensemble over KFold models
1. TTA (Test Time Augmentation)
2. WBF (Weighted Box Fusion) - better replacement of NMS (Non-Maximum Supression)

The metric used in competition is RSNAObjectDetectionAP. It some slightly modified mAP.
After all this steps on score on LB on single model was 0.7171 and with ensemble 0.7262.
This result give 24 % place on leaderbord with a very simple model (FasterRCNN paper was published in 2015, such ancient time)

But in june was introdeced YOLOv5 (there are some dispute about naming)
that first train without changing gives 0.7375 on single model.
