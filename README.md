# Kaggle_VinBigData_chect_xray_classification

Author: Rishi Chandra 
kaggleID: @sapthrishi007

This is NOT an alternative to YOLO type object detection
This is simple image classification using resnet with soft attention (CBAM) pretrained on imagenet and demonstrates the following:¶
1. Grad-Cam visualization of the final CNN layer feature map and localizing the bounding box on the image which mostly activates this feature map.
2. Using this bounding box for the submission. Obviously this is not a replacement to yolo since the model does not trains on the input bounding boxes of the training set.
3. Soft attention CBAM: Convolutional Block Attention Module
CBAM paper ref: https://arxiv.org/pdf/1807.06521.pdf

CBAM resnet github: https://github.com/Jongchan/attention-module

4. A reusable custom Trainer with plots a variety of metrics. Trains it through Progressive Resizing of image, and checkoints best model for a variety of metrics. You can reuse this trainer for your projects too!!!
5. Resume training from last epoch, model and optimizer state, by just specifying the last checkpoint ! Also adjust no. of cycles and plot ur lr curve and see.
6. Searches for an optimum probability threshold, instead of default 0.5, for image classification. The trainer is for scenario of MultiLabelBinaryClassification, and can easily be tweaked for any scenario.
7. Uses sum of DiceLoss and BCEWithLogitsLoss. DiceLoss to take care of class sparcity, class unbalance. And class weighted BCEWithLogitsLoss for class imbalance and smoother gradients.
8. Just specify your model path in torch.load(...) statements and infer from your model
