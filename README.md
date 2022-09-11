# Assessment Assistant

We are going to design an assessment assistant to evaluate the difficulty of doing a ML project.

Before doing a ML project, we often use these information to evaluate the difficulty:

1. Target size in the images
2. Number of Targets in the images
3. Target color composition
4. Target color variation
5. Background and Target color difference
6. Existing similar objects in the images
7. Sample images with labels

This assistant will take these information and return a difficulty score.


## Proof of Concept (PoC) Design

In this design notebook, instead of realizing a full product, we are drafting a simple ML solution for the PoC.

In the PoC, we explore how many images will we need to come out with a reasonable accuracy. In ideal situation, we might be able to only use 1 to 2 images to get the difficulty score.

### Feature Generation

Using MSCOCO dataset, we select each category, and calculate these data:
 - Target size ratio (bbox/segmentation)
 - Number of targets
 - ResNet Features
 - After unsupervised decomposition
   - Number of color composition
   - Color variation across images
   - Color difference to nearby background
   - Similar color composition and size in the background
 - Human Impression
   - Does the target has multiple color composition (Yes/No)
   - Does the target has multiple color variation (Yes/No)
   - Can there have multiple targets in an image (Yes/No)
   - Is there similar non-target objects in an image (Yes/No)
 - Target Value
   - Classification false positive, false negative, true positive
   - Mean Average Precision (mAP)
   
### Model Evaluation

 - XGBoost Model
 - Wide & Deep Neural Network

