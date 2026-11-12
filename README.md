<p align="center">
  <a href="https://colab.research.google.com/github/NoyaAdivi/emotion_detection_ml/blob/main/Notebook.ipynb"><img src="docs/readme/banner-en.svg" width="100%" alt="Emotion Detection: a text emotion classifier built from scratch"></a>
</p>

<p align="center"><a href="README.he.md"><img src="docs/readme/lang-he.svg" height="44" alt="לגרסה בעברית"></a></p>

<p align="center">
  <a href="https://colab.research.google.com/github/NoyaAdivi/emotion_detection_ml/blob/main/Notebook.ipynb"><img src="https://img.shields.io/badge/Open_in_Colab-FFD5C9?style=for-the-badge&logo=googlecolab&logoColor=A8483A" alt="Open in Colab"></a>
  <a href="#results"><img src="https://img.shields.io/badge/Results-DAD5FF?style=for-the-badge&logo=scikitlearn&logoColor=5548C8" alt="Results"></a>
  <a href="Notebook.ipynb"><img src="https://img.shields.io/badge/Notebook-D9F3E7?style=for-the-badge&logo=jupyter&logoColor=1F7350" alt="Notebook"></a>
</p>

<p align="center">
  <a href="LICENSE"><img src="https://img.shields.io/github/license/NoyaAdivi/emotion_detection_ml?color=DAD5FF&labelColor=5548C8" alt="License"></a>
  <a href="https://github.com/NoyaAdivi/emotion_detection_ml/commits/main"><img src="https://img.shields.io/github/last-commit/NoyaAdivi/emotion_detection_ml?color=FFD5C9&labelColor=A8483A" alt="Last commit"></a>
  <a href="https://github.com/NoyaAdivi/emotion_detection_ml"><img src="https://img.shields.io/github/languages/top/NoyaAdivi/emotion_detection_ml?color=D9F3E7&labelColor=1F7350" alt="Top language"></a>
  <a href="https://github.com/NoyaAdivi/emotion_detection_ml"><img src="https://img.shields.io/github/repo-size/NoyaAdivi/emotion_detection_ml?color=FBD5E0&labelColor=A03A5C" alt="Repo size"></a>
</p>

<h3 align="center">Type any English sentence and the model tells you how it feels.</h3>

<p align="center">
  A <b>Multinomial Naive Bayes</b> classifier written from scratch, trained on 16,000 sentences to recognize<br><b>joy, sadness, anger, fear, love and surprise</b>. Final project of the Machine Learning course at HIT.
</p>

<table align="center">
  <tr>
    <td align="center" width="25%"><a href="#how-it-works"><b>📚 16,000</b></a><br><sub>labeled sentences</sub></td>
    <td align="center" width="25%"><a href="#how-it-works"><b>🎭 6</b></a><br><sub>emotions</sub></td>
    <td align="center" width="25%"><a href="#results"><b>📈 0.694</b></a><br><sub>best CV Macro-F1</sub></td>
    <td align="center" width="25%"><a href="#results"><b>🎯 0.10 → 0.55</b></a><br><sub>recall on 'surprise'</sub></td>
  </tr>
</table>

<a name="highlights"></a>
<p align="center"><a href="#highlights"><img src="docs/readme/highlights-en.svg" width="100%" alt="Highlights"></a></p>

<table>
  <tr valign="top">
    <td width="33%"><p><b>🧮 Built from scratch</b></p><ul><li><b>Training and prediction</b> written by hand, not a library call</li><li><b>Laplace smoothing</b> (alpha) for words never seen in training</li><li><b>Stop-word filtering</b> to keep only words with emotional weight</li></ul></td>
    <td width="33%"><p><b>🔬 Tuned the right way</b></p><ul><li><b>Grid Search + 5-fold CV</b> over vectorizer and alpha</li><li><b>Bag of Words vs. TF-IDF</b> compared on the same folds</li><li><b>Oversampling</b> so rare emotions are not drowned out</li></ul></td>
    <td width="33%"><p><b>💡 Explainable</b></p><ul><li><b>Macro-F1</b> so every emotion counts equally</li><li><b>Top 8 words</b> that point to each emotion</li><li><b>Live demo cell:</b> type a sentence, get an emotion</li></ul></td>
  </tr>
</table>

<a name="how-it-works"></a>
<p align="center"><a href="#how-it-works"><img src="docs/readme/how-it-works-en.svg" width="100%" alt="How it works"></a></p>

```mermaid
flowchart LR
  A([💬 English sentence]) --> B[Clean text<br/>remove stop words]
  B --> C[Bag of Words<br/>or TF-IDF]
  C --> D[Multinomial Naive Bayes<br/>with Laplace smoothing]
  D --> E([😊 joy · 😢 sadness · 😠 anger<br/>😨 fear · 💗 love · 😮 surprise])
  G[Grid Search<br/>5-fold CV] -.tunes.-> C
  G -.tunes alpha.-> D
  O[Oversampling<br/>minority classes] -.balances.-> D
  style A fill:#E8E4FF,stroke:#6F60F0,color:#2C2668
  style E fill:#D9F3E7,stroke:#1F7350,color:#1F4D38
  style G fill:#FFE6DE,stroke:#E36E57,color:#2C2668
  style O fill:#FFF1C9,stroke:#B98A1E,color:#5C4410
```

The [Kaggle dataset](https://www.kaggle.com/datasets/abhrajaiswal/emotions-detection-text-dataset) has 16,000 labeled English sentences, split 80% for training and 20% for testing. The notebook downloads it by itself.

<a name="results"></a>
<p align="center"><a href="#results"><img src="docs/readme/results-en.svg" width="100%" alt="Results"></a></p>

| Model | Test Macro-F1 | Accuracy |
|---|:---:|:---:|
| Baseline (alpha = 1.0) | 0.63 | 78% |
| **After tuning + oversampling** | **0.67** | 73% |

- **Best configuration (5-fold CV):** Bag of Words with alpha = 0.1, mean CV Macro-F1 = **0.694** (TF-IDF reached 0.609).
- **Oversampling** raised recall for the rarest emotion, *surprise*, from **0.10 to 0.55**, at a small cost in overall accuracy. That is the right trade-off when the goal is Macro-F1.

<a name="tech-stack"></a>
<p align="center"><a href="#tech-stack"><img src="docs/readme/tech-stack-en.svg" width="100%" alt="Tech Stack"></a></p>

<p align="center">
  <a href="https://www.python.org"><img src="https://img.shields.io/badge/Python-CFE6FA?style=for-the-badge&logo=python&logoColor=3F6D9F" alt="Python"></a>
  <a href="https://scikit-learn.org"><img src="https://img.shields.io/badge/Scikit--Learn-BFEBD9?style=for-the-badge&logo=scikitlearn&logoColor=1F7350" alt="Scikit-Learn"></a>
  <a href="https://pandas.pydata.org"><img src="https://img.shields.io/badge/pandas-FFD5C9?style=for-the-badge&logo=pandas&logoColor=A8483A" alt="pandas"></a>
  <a href="https://numpy.org"><img src="https://img.shields.io/badge/NumPy-DAD5FF?style=for-the-badge&logo=numpy&logoColor=5548C8" alt="NumPy"></a>
  <a href="https://matplotlib.org"><img src="https://img.shields.io/badge/Matplotlib-FBD5E0?style=for-the-badge&logo=python&logoColor=A03A5C" alt="Matplotlib"></a>
  <a href="https://jupyter.org"><img src="https://img.shields.io/badge/Jupyter-FFD5C9?style=for-the-badge&logo=jupyter&logoColor=A8483A" alt="Jupyter"></a>
  <a href="https://www.kaggle.com"><img src="https://img.shields.io/badge/Kaggle-CFE6FA?style=for-the-badge&logo=kaggle&logoColor=3F6D9F" alt="Kaggle"></a>
</p>

<a name="run-it"></a>
<p align="center"><a href="#run-it"><img src="docs/readme/run-it-en.svg" width="100%" alt="Run it"></a></p>

1. Click <a href="https://colab.research.google.com/github/NoyaAdivi/emotion_detection_ml/blob/main/Notebook.ipynb"><b>Open in Colab</b></a>, or download [`Notebook.ipynb`](Notebook.ipynb) and open it in Jupyter (`pip install -r` [`requirements.txt`](requirements.txt)).
2. Run the cells in order. The dataset downloads automatically.
3. Scroll to the last cell, type any English sentence and watch the prediction.

<p><b>👥 Team:</b> Noya A. · Amit A. · Amir M.</p>

<a name="contact"></a>
<p align="center"><a href="#contact"><img src="docs/readme/footer-en.svg" width="100%" alt="Built by Noya Adivi"></a></p>

<p align="center">
  <a href="https://colab.research.google.com/github/NoyaAdivi/emotion_detection_ml/blob/main/Notebook.ipynb"><img src="https://img.shields.io/badge/Open_project-FFD5C9?style=for-the-badge&logo=github&logoColor=A8483A" alt="Open project"></a>
  <a href="https://www.linkedin.com/in/noya-adivi/"><img src="https://img.shields.io/badge/LinkedIn-DAD5FF?style=for-the-badge&logo=data:image/svg%2bxml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHZpZXdCb3g9IjAgMCAyNCAyNCI+PHBhdGggZmlsbD0iIzU1NDhDOCIgZD0iTTIwLjQ1IDIwLjQ1aC0zLjU2di01LjU3YzAtMS4zMy0uMDMtMy4wNC0xLjg1LTMuMDQtMS44NiAwLTIuMTQgMS40NS0yLjE0IDIuOTR2NS42N0g5LjM1VjloMy40MXYxLjU2aC4wNWMuNDgtLjkgMS42NC0xLjg1IDMuMzctMS44NSAzLjYgMCA0LjI3IDIuMzcgNC4yNyA1LjQ2djYuMjh6TTUuMzQgNy40M2EyLjA2IDIuMDYgMCAxIDEgMC00LjEzIDIuMDYgMi4wNiAwIDAgMSAwIDQuMTN6TTcuMTIgMjAuNDVIMy41NlY5aDMuNTZ2MTEuNDV6TTIyLjIyIDBIMS43N0MuNzkgMCAwIC43NyAwIDEuNzN2MjAuNTRDMCAyMy4yMy43OSAyNCAxLjc3IDI0aDIwLjQ1Yy45OCAwIDEuNzgtLjc3IDEuNzgtMS43M1YxLjczQzI0IC43NyAyMy4yIDAgMjIuMjIgMHoiLz48L3N2Zz4=" alt="LinkedIn"></a>
  <a href="https://noyaadivi.github.io/noya-website"><img src="https://img.shields.io/badge/Portfolio-D9F3E7?style=for-the-badge&logo=githubpages&logoColor=1F7350" alt="Portfolio"></a>
  <a href="https://github.com/NoyaAdivi"><img src="https://img.shields.io/badge/More_projects-FBD5E0?style=for-the-badge&logo=github&logoColor=A03A5C" alt="More projects"></a>
</p>
