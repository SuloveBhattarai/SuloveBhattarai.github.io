---
layout: default
title: "Twitter Datasets- Content Polluters vs Legitimate Users"
date:    2023-09-15 14:00:00
selected: true
---

# Social Honeypot Dataset: Prediction of Content Polluters vs Legitimate Users

The rapid growth of social media platforms like Twitter has made them a hotspot for both meaningful interactions and malicious activities. Between 2009 and 2010, researchers collected the **Social Honeypot Dataset**, a comprehensive dataset that includes:

- **Profiles**
- **Followings**
- **Tweets**  

The dataset comprises:  
- **22,223 content polluters (spammers)**  
- **19,276 legitimate users**

## Data Loading

To start analyzing the **Social Honeypot Dataset**, the first step involves loading the data. This dataset is divided into two main categories:  

- **Content Polluters (Spammers)**  
- **Legitimate Users**  

The data is organized across four files:  

1. **`content_polluters.txt`**: Profiles of spam accounts.  
2. **`legitimate_users.txt`**: Profiles of genuine accounts.  
3. **`content_polluters_tweets.txt`**: Tweets posted by spam accounts.  
4. **`legitimate_users_tweets.txt`**: Tweets posted by genuine accounts.

## Data Preprocessing for the Social Honeypot Dataset

After loading the data, the next step is **preprocessing** to prepare it for analysis. This involves several steps to enhance the dataset's structure and enable effective analysis of user behavior:

### 1. Combining Profiles and Tweets
- Profiles and tweets are merged into a unified dataset for each user category (spammers and legitimate users).

### 2. Aggregating Tweets
- All tweets from a single user are combined into one text entry, streamlining the analysis process.

### 3. Feature Extraction
- Additional features are derived from the dataset, such as:
  - **AccountAge**: Calculated in days to understand the longevity of accounts.

### 4. Handling Missing Data
- Missing tweets are replaced with empty strings to ensure data consistency and avoid processing errors.

These preprocessing steps create a structured and enriched dataset, making it suitable for deeper analyses and insights.

## Text Normalization and Cleaning

To focus on meaningful content and ensure uniformity, the following text preprocessing steps are applied:

### 1. Normalization
- Converts all text to lowercase for uniformity across the dataset.

### 2. Cleaning
- Removes:
  - URLs  
  - Mentions (e.g., `@username`)  
  - Hashtags (e.g., `#topic`)  
  - Non-alphabetical characters  

This helps retain only the core textual content.

### 3. Tokenization and Stemming
- **Tokenization**: Breaks text into individual words or tokens.  
- **Stemming**: Reduces words to their root forms (e.g., "running" becomes "run") using the **Natural Language Toolkit (NLTK)**.

### 4. Stopword Removal
- Common stopwords (e.g., "and," "the," "is") are eliminated to retain only the most relevant terms in the text.

These steps refine the textual data, making it ready for effective feature extraction and analysis.


## Feature Engineering for the Social Honeypot Dataset

Transforming raw data into meaningful features is a critical step for effective analysis. The following methods are applied to create features:

### 1. Numerical Features
- Extracts user-specific statistics, such as:
  - **Number of Followers**
  - **Number of Followings**  
  These features help capture user activity levels and influence.

### 2. Textual Features
- **TF-IDF Vectorization**:  
  - Converts cleaned and processed tweets into numerical representations.
  - Captures the importance of words in the context of each user's tweets, emphasizing unique terms.

### 3. Feature Combination
- Merges numerical and textual features into a unified dataset.
- Features are **horizontally stacked**, ensuring both types of data are available for modeling.

This feature engineering pipeline creates a comprehensive dataset, integrating user behavior and textual analysis for robust spam detection and user classification models.

## Model Training for Spam Detection

The final step involves building a predictive model to classify users as spammers or legitimate accounts. The following process is used:

### 1. Dataset Split
- The dataset is divided into:
  - **Training Set**: 80% of the data, used to train the model.
  - **Testing Set**: 20% of the data, used to evaluate model performance.

### 2. Model Selection: Random Forest Classifier
- A **Random Forest Classifier** is chosen for its robustness and ability to handle complex datasets.
- It is trained on the combined numerical and textual features, leveraging both user statistics and tweet content.

## Model Evaluation for Spam Detection

After training, the model's performance is evaluated using the following steps:

### 1. Predictions
- The trained model generates predictions on the **test dataset**.

### 2. Metrics Reported
- **Accuracy Score**:  
  - Measures the overall correctness of the model's predictions.

- **Classification Report**:  
  - Provides detailed metrics for each class, including:
    - **Precision**: Proportion of correctly predicted positives out of total predicted positives.
    - **Recall**: Proportion of actual positives correctly identified.
    - **F1-Score**: Harmonic mean of precision and recall, balancing both metrics.

- **Confusion Matrix**:  
  - Visualizes the model's performance by showing:
    - True Positives (TP)  
    - False Positives (FP)  
    - True Negatives (TN)  
    - False Negatives (FN)  

<div style="display: flex; justify-content: space-between;">
    <div style="flex: 1; text-align: center;">
        <img src="../images/class_report_random.png" alt="Sentiment Results 1" width="30%">
        <p>Classification Report</p>
    </div>
</div>

<div style="display: flex; justify-content: space-between;">
    <div style="flex: 1; text-align: center;">
        <img src="../images/confusion_random.png" alt="Sentiment Results 1" width="30%">
        <p>Confusion Matrix</p>
    </div>
</div>

## Accuracy:- 0.915



# Using Neural Network

The neural network is designed to effectively handle the combined numerical and textual feature set, ensuring robust binary classification.

### 1. Architecture
- **Input Layer**:  
  - Processes the merged feature set (numerical + textual).

- **Hidden Layers**:  
  - Two fully connected layers with **ReLU activations** to introduce non-linearity and capture complex patterns.  

- **Dropout Regularization**:  
  - Dropout layers are included after the hidden layers to reduce overfitting by randomly deactivating a fraction of neurons during training.

- **Output Layer**:  
  - A single neuron with a **sigmoid activation function**, designed for binary classification, outputs the probability of a user being a spammer or legitimate.

### 2. Loss Function
- The model uses **Binary Cross-Entropy Loss (BCELoss)**, which is ideal for:
  - Binary classification problems.
  - Handling outputs in the range [0, 1] produced by the sigmoid activation.


## Model Training for Neural Network

The neural network is trained over **50 epochs** to optimize its performance and ensure effective spam detection.

### 1. Training Loop
For each batch of data, the following steps are performed:

1. **Forward Pass**:  
   - Computes predictions from the neural network.  

2. **Loss Calculation**:  
   - Calculates the loss using **Binary Cross-Entropy Loss (BCELoss)**, comparing predictions to true labels.  

3. **Backpropagation**:  
   - Computes gradients of the loss with respect to model parameters.  
   - Updates model parameters using an optimizer (e.g., Adam or SGD).

4. **Zero Gradients**:  
   - Clears gradients from the previous step to prevent accumulation.

### 2. Performance Tracking
- **Average Loss Per Epoch**:  
  - Tracks the average loss at the end of each epoch to monitor model convergence.  
  - Helps ensure the model is learning effectively and not overfitting or underfitting.

## Model Evaluation for Neural Network

The trained neural network is evaluated on the test dataset to assess its performance in classifying spammers and legitimate users.

### 1. Prediction Conversion
- The **sigmoid output** from the network is converted to binary predictions:
  - Predictions ≥ 0.5 are classified as **1** (spammer).  
  - Predictions < 0.5 are classified as **0** (legitimate user).

### 2. Performance Metrics
The following metrics are used to evaluate the model:

1. **Classification Report**:
   - Provides detailed metrics for each class, including:
     - **Precision**: Proportion of correct positive predictions.
     - **Recall**: Proportion of actual positives correctly predicted.
     - **F1-Score**: Harmonic mean of precision and recall, balancing both.

2. **Confusion Matrix**:
   - Visualizes the performance by highlighting:
     - **True Positives (TP)**: Correctly identified spammers.
     - **False Positives (FP)**: Legitimate users misclassified as spammers.
     - **True Negatives (TN)**: Correctly identified legitimate users.
     - **False Negatives (FN)**: Spammers misclassified as legitimate users.

3. **Accuracy Score**:
   - Represents the overall percentage of correctly predicted labels across the test dataset.



<div style="display: flex; justify-content: space-between;">
    <div style="flex: 1; text-align: center;">
        <img src="../images/class_report_neural.png" alt="Sentiment Results 1" width="30%">
        <p>Classification Report</p>
    </div>
</div>

<div style="display: flex; justify-content: space-between;">
    <div style="flex: 1; text-align: center;">
        <img src="../images/confusion_neural.png" alt="Sentiment Results 1" width="30%">
        <p>Confusion Matrix</p>
    </div>
</div>

## Accuracy Neural Network: 0.919

# Comparative Model Performance: Neural Network vs. Random Forest

### 1. Accuracy
- **Random Forest**: 91.5%  
- **Neural Network**: 91.9%  

This suggests that the Neural Network generalized slightly better on the test dataset.

### 2. Observations
- The Neural Network demonstrated:
  - **Higher Accuracy**: Marginally outperforming the Random Forest in overall predictions.
  - **Fewer Misclassifications**: Particularly in distinguishing between spammers and legitimate users.
  - **Improved Recall for Legitimate Users**: Highlighting its ability to correctly identify genuine accounts more effectively.

- **Random Forest** remains a strong alternative due to its:
  - **Computational Efficiency**: Faster training and inference, making it suitable for scenarios with limited resources.
  - **Robust Performance**: Despite slightly lower accuracy, it performs reliably with fewer hyperparameter adjustments.

### 3. Conclusion

Both models offer effective solutions for spam detection.
