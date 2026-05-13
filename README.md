# Colorectal Cancer Histopathology Classification (CNN)

This project aims to automatically classify histological image tiles of colorectal cancer using the **Kather Texture 2016 dataset** (https://www.kaggle.com/datasets/user322312312/kather-texture-2016-image-tiles-5000-1). This project demonstrates the application of Convolutional Neural Networks (CNNs) to digital pathology, aiming to assist in automated tissue characterization.

## Preprocessing

Before training the neural network, the histopathology images were preprocessed to ensure that all inputs had a consistent format.

The preprocessing pipeline included:

- Resizing all images to 64×64 pixels so that every image had the same dimensions before being passed into the CNN.
- Converting images into PyTorch tensors, which allows them to be processed by the deep learning model.
- Automatically scaling pixel intensity values from the range [0–255] to [0–1], helping stabilize training and improve numerical computation during backpropagation.

These preprocessing steps help standardize the dataset and make the training process computationally efficient.

---


## Model Architecture

This project uses a Convolutional Neural Network (CNN) for multiclass histopathology image classification.

The model learns visual patterns from tissue images gradually, starting from simple features and moving toward more complex tissue structures.

### Convolution Layers

The convolution layers scan small regions of the image using learnable filters. 

In the early layers, the model learns simple patterns such as:
- edges
- color contrasts
- nuclei boundaries

As the network becomes deeper, it starts learning more meaningful tissue features like:
- gland structures
- cell clustering
- stromal texture
- tissue organization

### ReLU Activation

After each convolution, a ReLU activation function is applied.

This helps the network focus on important patterns while ignoring weaker, irrelevant signals. It also allows the model to learn complex non-linear relationships in tissue morphology.

### Max Pooling

Max pooling layers reduce the spatial size of feature maps.

This helps:
- reduce computation
- prevent overfitting
- make the model less sensitive to small positional changes in tissue structures

The network learns to recognize features regardless of where they appear in the image.

### Fully Connected Layers

After feature extraction, the learned feature maps are flattened into a single vector and passed through fully connected layers.

These layers combine all extracted features and make the final prediction for the tissue class.

The final output layer assigns a score to each class, and the class with the highest score is selected as the prediction.
## Results & Performance Analysis

The CNN was evaluated using accuracy, precision, recall, F1-score, and confusion matrix analysis on the test dataset.

The model showed strong performance in distinguishing visually distinct tissue patterns while facing more difficulty with morphologically similar tissue classes. The model achieved approximately 80% classification accuracy on the test dataset.

### High Performing Classes

Some tissue classes achieved higher classification performance because they contain visually consistent and easily recognizable structures.

For example:
- Adipose tissue contains large empty-looking fat spaces
- Empty/background regions have minimal texture and low structural complexity

These patterns are easier for convolutional filters to learn and separate from other tissue categories.

### Challenging Classes

The model showed comparatively lower performance on tissue classes with overlapping morphology and similar textural appearance.

Classes such as:
- stromal tissue
- complex tissue regions

often contain mixed cellular structures and less clearly defined boundaries, making them harder to distinguish consistently.

These misclassifications are also reflected in the confusion matrix analysis.

### Tumor Classification

The model was able to learn important tumor-associated visual patterns from histopathology images, including:
- dense cellular organization
- irregular tissue structure
- abnormal morphology

The confusion matrix showed that the CNN could reliably identify tumor regions in most cases while still confusing some samples with morphologically similar tissue classes.

### Overall Observation

The results demonstrate that even a relatively small custom CNN can learn meaningful histopathological features directly from image data and perform effective multiclass tissue classification.

##  Getting Started
1. Open the Jupyter Notebook (`Kather_Data_CancerClassification.ipynb`) .
2. Download `arcive.zip` dataset from https://www.kaggle.com/datasets/user322312312/kather-texture-2016-image-tiles-5000-1.
3. Run the notebook cells sequentially to execute the data extraction, preprocessing, training, and evaluation phases.
