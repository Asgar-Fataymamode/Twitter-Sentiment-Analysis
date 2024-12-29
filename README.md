# **Twitter Sentiment Analysis Report**

---

## **1. Introduction**

### **Objective:**
The goal of this project is to develop a **multi-class classification model** for **entity-level sentiment analysis** on tweets. The task is to classify tweets into **Positive**, **Negative**, **Neutral**, or **Irrelevant** categories based on their sentiment towards specific entities.

### **Key Questions:**
1. How accurately can we predict the sentiment of tweets?  
2. Are there patterns in tweet length, word frequency, or sentiment trends that can be leveraged for modeling?  
3. Which machine learning model—**Logistic Regression** or **Random Forest**—performs better on this dataset?  

---

## **2. Dataset Overview**

### **Data Source:**
Two datasets were used:
1. **Training Data:** 74,681 tweets for model training.  
2. **Validation Data:** 999 tweets for testing and evaluation.

### **Columns:**
- **ID**: Unique identifier.  
- **Entity**: Subject or topic of the tweet.  
- **Sentiment**: Sentiment label (Positive, Negative, Neutral, Irrelevant).  
- **Text**: The tweet content.  

### **Preprocessing Steps:**
- Filled missing text values with empty strings.  
- Encoded sentiment labels using **LabelEncoder**.  
- Transformed text data into numerical format using **TF-IDF Vectorizer** (top 5000 features).  

---

## **3. Exploratory Data Analysis (EDA)**

### **Key Insights:**
1. **Sentiment Distribution**:  
   - Tweets were well-distributed across the sentiment categories, with slight dominance of **Positive** and **Neutral** sentiments.  

2. **Entity Trends**:  
   - Top entities like **Borderlands**, **Google**, and **Facebook** showed distinct sentiment patterns.  
   - For example, **Borderlands** had more **Positive** tweets, while **Microsoft** leaned towards **Negative**.  

3. **Text Length**:  
   - Longer tweets tended to be **Positive** or **Negative**, while shorter tweets were often **Neutral** or **Irrelevant**.  

4. **Word Clouds**:  
   - Positive tweets featured words like **love, great, happy**, while negative tweets focused on **hate, problem, issue**.  

### **EDA Visualizations:**
- Sentiment distributions in training and validation sets.  
- Top entities and their sentiment patterns.  
- Text length distributions and sentiment-specific boxplots.  
- Word clouds for each sentiment.  

---

## **4. Modeling Approach**

### **Feature Engineering:**
- **TF-IDF Vectorizer** was used to convert tweet text into a numerical format with 5000 features.  

### **Models Trained:**
1. **Logistic Regression**:  
   - Linear classifier optimized for multi-class predictions.  
2. **Random Forest Classifier**:  
   - Ensemble method capturing non-linear relationships through decision trees.  

### **Training and Testing Split:**
- Training size: **74,681 tweets**  
- Validation size: **999 tweets**  

---

## **5. Model Evaluation**

### **Logistic Regression Results:**
- **Accuracy:** **82.3%**  
- **Precision, Recall, and F1-scores:**
  - Positive: **84% F1-score**  
  - Negative: **83% F1-score**  
  - Neutral: **82% F1-score**  
  - Irrelevant: **78% F1-score**  

**Observations:**
- Performed well but struggled slightly with **Neutral** tweets, often misclassifying them as **Positive**.  
- **ROC Curve Analysis**: AUC values ranged between **0.94 and 0.96**, indicating good separability across classes.  
- **Sentiment Distribution Plot**: Predicted values closely matched actual values, but some smoothing issues were observed in class overlaps.  

---

### **Random Forest Results:**
- **Accuracy:** **93.8%**  
- **Precision, Recall, and F1-scores:**
  - Positive: **94% F1-score**  
  - Negative: **94% F1-score**  
  - Neutral: **94% F1-score**  
  - Irrelevant: **93% F1-score**  

**Observations:**
- Performed significantly better than Logistic Regression, especially in handling **Neutral** tweets.  
- Feature Importance analysis highlighted key words like **"great," "issue," and "love"** as critical indicators.  
- **Confusion Matrix**: Showed balanced performance with fewer misclassifications.  
- **ROC Curve Analysis**: AUC values exceeded **0.95**, confirming excellent class separability.  

---

### **Model Comparison:**

| Metric                  | Logistic Regression | Random Forest |
|-------------------------|---------------------|---------------|
| **Accuracy**            | 82.3%               | **93.8%**     |
| **F1-Score (Avg)**      | 82%                 | **94%**       |
| **ROC-AUC (Avg)**       | 0.95                | **0.96+**     |
| **Misclassification**   | More errors on Neutral | Fewer errors across all classes |

**Key Finding:**  
The **Random Forest Classifier** significantly outperformed **Logistic Regression** across all metrics, particularly in distinguishing **Neutral** tweets.

---

## **6. Observations**
1. **Random Forest** emerged as the superior model, achieving **93.8% accuracy** and high F1-scores across all classes.  
2. **Logistic Regression**, while simpler, showed acceptable performance (**82.3% accuracy**) and was faster to train.  
3. **Text Length** and **Word Frequencies** provided useful insights for feature engineering.  
4. Both models faced slight challenges in distinguishing **Neutral** tweets, highlighting areas for improvement.  

## **7. Conclusion**

This project successfully implemented **entity-level sentiment analysis** using machine learning models to classify tweets into **Positive**, **Negative**, **Neutral**, and **Irrelevant** sentiments.

### **Key Takeaways:**
- **EDA** highlighted patterns in tweet length, sentiment distributions, and word frequencies.  
- **Random Forest** significantly outperformed **Logistic Regression** with **93.8% accuracy** and better handling of edge cases.  
- **ROC Curves** confirmed high class separability, supporting the reliability of both models.  

### **Next Steps:**
- Implement deep learning techniques like **BERT** for state-of-the-art text classification.  
- Integrate real-time sentiment monitoring to assess live tweets dynamically.  
