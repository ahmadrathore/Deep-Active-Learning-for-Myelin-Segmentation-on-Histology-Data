- # Deep-Active-Learning-for-Myelin-Segmentation-on-Histology-Data

AIM:  which sample to annotate, limit the annotation efforts
Model: Framework relies on the U-Net architecture 
Segmenting myelin from histology data
Method: Uncertainty measure to suggest which sample to annotate

![image](https://user-images.githubusercontent.com/30137669/124531270-1fa7c680-de49-11eb-954f-41fb4e1654db.png)

Uncertainty measure by Monte Carlo samples, using Dropout regularization scheme

## Method

- Initial (small) labeled dataset is used to train a train a FCN U-Net.
- The pool of unlabeled data is fed to the U-Net,
- A measure of uncertainty is computed for each unlabeled sample
- To asses uncertainty measure used Monte-Carlo Dropout (MC-Dropout) 
- Select the samples to be annotated for the next iteration. 
- Ranked based on this uncertainty measure. (#3)
- The most uncertain samples is then selected to be annotated by an oracle such as a human expert and added to the training set [4. Active Learning Loop, in 11]
- The U-Net is then re-trained from scratch with this updated set of images
- Output additional information: uncertainty maps for each unlabeled samples.

