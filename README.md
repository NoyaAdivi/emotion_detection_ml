# emotion_detection_ml
# Text Emotion Recognition 🎭

> **Note:** Final project for the Machine Learning course at Holon Institute of Technology (HIT). 

## 📌 Project Overview
The goal of this project is to train a machine learning model capable of reading an English sentence and identifying the underlying emotion. This is framed as a **multi-class classification** problem within the domain of Natural Language Processing (NLP).

## 📊 The Dataset
The model is trained on a Kaggle dataset containing 16,000 English sentences. 
Each sentence is labeled with one of 6 emotions: **Joy, Sadness, Anger, Fear, Love, or Surprise**. 
The data is pre-split into an 80% training set and a 20% test set for performance evaluation.

## 🧠 The Algorithm (Built From Scratch)
We implemented a **Multinomial Naive Bayes** classifier completely from scratch. 
Instead of using pre-built library functions for the algorithm, we wrote the core training and prediction logic ourselves. We also implemented **Laplace Smoothing** (controlled by an alpha parameter) to prevent zero-probability errors when the model encounters words during testing that it did not see during training.

## ⚙️ Workflow & Preprocessing
* **Text Processing:** Text was vectorized using the **Bag of Words (BoW)** approach. 
* **Noise Reduction:** We filtered out "stop words" (common conjunctions and prepositions) that do not carry emotional weight and contribute no value to the classification process.
* **Evaluation Metric:** We selected the **Macro-average F1-score**. This metric calculates the success rate for each emotion independently and averages them equally. This was critical for our use case to ensure that rare emotions (like surprise and love) were not overshadowed by more frequent ones.

## 🚀 Advanced Features & Enhancements
* **Hyperparameter Tuning (Grid Search):** Instead of manual guessing, we ran an automated Grid Search combined with **5-fold Cross-Validation** to discover the optimal combination of text processing parameters and the model's alpha value.
* **Handling Class Imbalance:** We identified that certain emotions had very few examples. We resolved this by applying **Oversampling** to the minority classes in the training set until all emotions were perfectly balanced.
* **Model Explainability:** To demonstrate what the model actually learned, we extracted the **top 8 most indicative words** for each emotion based on the algorithm's internal probability calculations. 

## 💻 How to Run the Project
The entire pipeline is encapsulated in a single Jupyter Notebook (`.ipynb`).

1. Download the notebook [from here](Notebook.ipynb).
2. Open it in **Google Colab** or a local **Jupyter Notebook** environment.
3. Run the code cells sequentially from top to bottom. *(Note: The code automatically downloads the dataset, so no manual data fetching is required).*
4. **Interactive Demo:** At the bottom of the notebook, you will find an interactive cell. You are welcome to type any custom English sentence and watch the model predict its emotion in real-time!

## 👥 Project Team
* Noya A.
* Amit A.
* Amir M.
