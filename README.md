# ML_Assignment 4


## Model Evaluation Insights

### 1. Are the results as expected? Why or why not?
- Yes, the results align with expectations due to the following observations:
  - Deeper models (e.g., VGG16) tend to perform better because they can capture more complex features due to the increased number of layers.
  - VGG16 with all layers fine-tuned achieves the highest testing accuracy (0.95), demonstrating the power of transfer learning when fully tuning a pre-trained network.
  - VGG1 performs worse than the other models because it is too shallow to capture complex patterns, despite having the highest parameter count due to its fully connected layers.


### 2. Does data augmentation help? Why or why not?
- *In this case, with data augmentation (VGG3_aug) there was slight decrease in training loss((0.18 vs. 0.20 for VGG3) but it did not help improve testing accuracy (0.75 vs. 0.775 for VGG3). Possible reasons include:
  - The dataset might already have sufficient variability, making augmentation redundant.
  - Augmentation can introduce noise, potentially decreasing performance by misleading the model during training.
  - With a small dataset, data augmentation helps primarily when the model underfits, which doesn’t seem to be the issue here.

### 3. Does it matter how many epochs you fine-tune the model? Why or why not?
- **Analysis**:
  - Yes, the number of fine-tuning epochs impacts the model's performance:
    - **Too Few Epochs**: The model may not fully learn the underlying patterns, leading to underfitting.
    - **Too Many Epochs**: The model may overfit the training data, resulting in poor generalization to unseen data.
  - It is important to monitor metrics like validation loss and accuracy to determine an optimal stopping point for training.

### 4. Are there any particular images that the model is confused about? Why or why not?
- **Analysis**:
  - The model may be confused by images with overlapping features between different classes or visually similar images from different classes.
  - Misclassifications may arise from:
    - **Poor Image Quality**: Blurry or poorly lit images can lead to incorrect predictions.
    - **Class Similarity**: Some classes might share visual characteristics, making them difficult to distinguish.
  - Analyzing a confusion matrix can help identify which classes are frequently misclassified and guide further improvements.

 ### MLP Model Insights
- MLP achieves a testing accuracy of 75%, comparable to VGG3 (75.5%), but its training accuracy (66.07%) and loss are much worse, showing poor generalization.
- VGG16 (all layers tuned) significantly outperforms MLP with a testing accuracy of 95%.
- VGG models leverage convolutional layers to extract spatial features, essential for image data. MLP lacks these layers and struggles to handle image hierarchies effectively.
- MLP is unsuitable for image tasks without feature extraction. VGG models are better for both accuracy and robustness, even with comparable parameter counts.
