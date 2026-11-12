<div dir="rtl">

<p align="center">
  <a href="https://colab.research.google.com/github/NoyaAdivi/emotion_detection_ml/blob/main/Notebook.ipynb"><img src="docs/readme/banner-he.svg" width="100%" alt="Emotion Detection: מסווג רגשות בטקסט שנבנה מאפס"></a>
</p>

<p align="center"><a href="README.md"><img src="docs/readme/lang-en.svg" height="44" alt="Read in English"></a></p>

<p align="center">
  <a href="https://colab.research.google.com/github/NoyaAdivi/emotion_detection_ml/blob/main/Notebook.ipynb"><img src="https://img.shields.io/badge/%D7%9C%D7%A4%D7%AA%D7%95%D7%97_%D7%91%D6%BEColab-FFD5C9?style=for-the-badge&logo=googlecolab&logoColor=A8483A" alt="לפתוח ב־Colab"></a>
  <a href="#results"><img src="https://img.shields.io/badge/%D7%AA%D7%95%D7%A6%D7%90%D7%95%D7%AA-DAD5FF?style=for-the-badge&logo=scikitlearn&logoColor=5548C8" alt="תוצאות"></a>
  <a href="Notebook.ipynb"><img src="https://img.shields.io/badge/%D7%9C%D7%9E%D7%97%D7%91%D7%A8%D7%AA-D9F3E7?style=for-the-badge&logo=jupyter&logoColor=1F7350" alt="למחברת"></a>
</p>

<p align="center">
  <a href="LICENSE"><img src="https://img.shields.io/github/license/NoyaAdivi/emotion_detection_ml?color=DAD5FF&labelColor=5548C8" alt="License"></a>
  <a href="https://github.com/NoyaAdivi/emotion_detection_ml/commits/main"><img src="https://img.shields.io/github/last-commit/NoyaAdivi/emotion_detection_ml?color=FFD5C9&labelColor=A8483A" alt="Last commit"></a>
  <a href="https://github.com/NoyaAdivi/emotion_detection_ml"><img src="https://img.shields.io/github/languages/top/NoyaAdivi/emotion_detection_ml?color=D9F3E7&labelColor=1F7350" alt="Top language"></a>
  <a href="https://github.com/NoyaAdivi/emotion_detection_ml"><img src="https://img.shields.io/github/repo-size/NoyaAdivi/emotion_detection_ml?color=FBD5E0&labelColor=A03A5C" alt="Repo size"></a>
</p>

<h3 align="center">כותבים משפט באנגלית, והמודל אומר איזה רגש יש בו.</h3>

<p align="center">
  מסווג <b>Multinomial Naive Bayes</b> שכתבנו מאפס, אומן על 16,000 משפטים כדי לזהות<br><b>שמחה, עצב, כעס, פחד, אהבה והפתעה</b>. פרויקט הגמר בקורס למידת מכונה ב־HIT.
</p>

<table align="center">
  <tr>
    <td align="center" width="25%"><a href="#how-it-works"><b>📚 16,000</b></a><br><sub>משפטים מתויגים</sub></td>
    <td align="center" width="25%"><a href="#how-it-works"><b>🎭 6</b></a><br><sub>רגשות</sub></td>
    <td align="center" width="25%"><a href="#results"><b>📈 0.694</b></a><br><sub>Macro-F1 הכי טוב ב־CV</sub></td>
    <td align="center" width="25%"><a href="#results"><b>🎯 0.10 → 0.55</b></a><br><sub>recall על 'הפתעה'</sub></td>
  </tr>
</table>

<p align="center">
  <a href="https://colab.research.google.com/github/NoyaAdivi/emotion_detection_ml/blob/main/Notebook.ipynb"><img src="docs/readme/showcase-he.png" width="100%" alt="Emotion Detection: מסווג רגשות בטקסט שנבנה מאפס"></a>
</p>

<a name="highlights"></a>
<p align="center"><a href="Notebook.ipynb"><img src="docs/readme/highlights-he.svg" width="100%" alt="מה מיוחד בו"></a></p>

<table>
  <tr valign="top">
    <td width="33%"><p><b>🧮 נבנה מאפס</b></p><ul><li><b>האימון והחיזוי</b> נכתבו ביד, בלי פונקציה מוכנה</li><li><b>החלקת Laplace</b> (alpha) למילים שלא הופיעו באימון</li><li><b>סינון מילים נפוצות</b> כדי להשאיר רק מילים עם משקל רגשי</li></ul></td>
    <td width="33%"><p><b>🔬 כוונון נכון</b></p><ul><li><b>Grid Search עם 5-fold CV</b> על שיטת הייצוג ועל alpha</li><li><b>Bag of Words מול TF-IDF</b> על אותן חלוקות</li><li><b>Oversampling</b> כדי שרגשות נדירים לא ייבלעו</li></ul></td>
    <td width="33%"><p><b>💡 אפשר להבין אותו</b></p><ul><li><b>Macro-F1</b> כדי שכל רגש ייספר באותה מידה</li><li><b>8 המילים</b> שהכי מעידות על כל רגש</li><li><b>תא הדגמה חי:</b> כותבים משפט ומקבלים רגש</li></ul></td>
  </tr>
</table>

<a name="how-it-works"></a>
<p align="center"><a href="https://www.kaggle.com/datasets/abhrajaiswal/emotions-detection-text-dataset"><img src="docs/readme/how-it-works-he.svg" width="100%" alt="איך זה עובד"></a></p>

```mermaid
flowchart RL
  A(["💬 משפט באנגלית"]) --> B["ניקוי הטקסט<br/>הסרת מילים נפוצות"]
  B --> C["Bag of Words<br/>או TF-IDF"]
  C --> D["Multinomial Naive Bayes<br/>עם החלקת Laplace"]
  D --> E(["😊 שמחה · 😢 עצב · 😠 כעס<br/>😨 פחד · 💗 אהבה · 😮 הפתעה"])
  G["Grid Search<br/>5-fold CV"] -.מכוונן.-> C
  G -.מכוונן alpha.-> D
  O["Oversampling<br/>לרגשות הנדירים"] -.מאזן.-> D
  style A fill:#E8E4FF,stroke:#6F60F0,color:#2C2668
  style E fill:#D9F3E7,stroke:#1F7350,color:#1F4D38
  style G fill:#FFE6DE,stroke:#E36E57,color:#2C2668
  style O fill:#FFF1C9,stroke:#B98A1E,color:#5C4410
```

ב־[מאגר הנתונים מ־Kaggle](https://www.kaggle.com/datasets/abhrajaiswal/emotions-detection-text-dataset) יש 16,000 משפטים מתויגים באנגלית, 80% לאימון ו־20% לבדיקה. המחברת מורידה אותו לבד.

<a name="results"></a>
<p align="center"><a href="https://colab.research.google.com/github/NoyaAdivi/emotion_detection_ml/blob/main/Notebook.ipynb"><img src="docs/readme/results-he.svg" width="100%" alt="תוצאות"></a></p>

| מודל | Macro-F1 בבדיקה | דיוק |
|---|:---:|:---:|
| בסיס (alpha = 1.0) | 0.63 | 78% |
| **אחרי כוונון ו־Oversampling** | **0.67** | 73% |

- **ההגדרה הכי טובה (5-fold CV):** Bag of Words עם alpha = 0.1, ממוצע Macro-F1 של **0.694** (TF-IDF הגיע ל־0.609).
- **Oversampling** העלה את ה־recall של הרגש הנדיר ביותר, *הפתעה*, מ־**0.10 ל־0.55**, במחיר קטן בדיוק הכללי. זו הבחירה הנכונה כשהמטרה היא Macro-F1.

<a name="tech-stack"></a>
<p align="center"><a href="requirements.txt"><img src="docs/readme/tech-stack-he.svg" width="100%" alt="טכנולוגיות"></a></p>

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
<p align="center"><a href="https://colab.research.google.com/github/NoyaAdivi/emotion_detection_ml/blob/main/Notebook.ipynb"><img src="docs/readme/run-it-he.svg" width="100%" alt="הרצה"></a></p>

1. לוחצים על <a href="https://colab.research.google.com/github/NoyaAdivi/emotion_detection_ml/blob/main/Notebook.ipynb"><b>לפתוח ב־Colab</b></a>, או מורידים את [`Notebook.ipynb`](Notebook.ipynb) ופותחים ב־Jupyter (`pip install -r` [`requirements.txt`](requirements.txt)).
2. מריצים את התאים לפי הסדר. הנתונים יורדים אוטומטית.
3. בתא האחרון כותבים משפט באנגלית ורואים את החיזוי.

<p><b>👥 הצוות:</b> נויה א. · עמית א. · אמיר מ.</p>

<a name="contact"></a>
<p align="center"><a href="https://www.linkedin.com/in/noya-adivi/"><img src="docs/readme/footer-he.svg" width="100%" alt="נוצר על ידי נויה אדיבי"></a></p>

<p align="center">
  <a href="https://colab.research.google.com/github/NoyaAdivi/emotion_detection_ml/blob/main/Notebook.ipynb"><img src="https://img.shields.io/badge/%D7%9C%D7%A4%D7%A8%D7%95%D7%99%D7%A7%D7%98-FFD5C9?style=for-the-badge&logo=github&logoColor=A8483A" alt="לפרויקט"></a>
  <a href="https://www.linkedin.com/in/noya-adivi/"><img src="https://img.shields.io/badge/LinkedIn-DAD5FF?style=for-the-badge&logo=data:image/svg%2bxml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHZpZXdCb3g9IjAgMCAyNCAyNCI+PHBhdGggZmlsbD0iIzU1NDhDOCIgZD0iTTIwLjQ1IDIwLjQ1aC0zLjU2di01LjU3YzAtMS4zMy0uMDMtMy4wNC0xLjg1LTMuMDQtMS44NiAwLTIuMTQgMS40NS0yLjE0IDIuOTR2NS42N0g5LjM1VjloMy40MXYxLjU2aC4wNWMuNDgtLjkgMS42NC0xLjg1IDMuMzctMS44NSAzLjYgMCA0LjI3IDIuMzcgNC4yNyA1LjQ2djYuMjh6TTUuMzQgNy40M2EyLjA2IDIuMDYgMCAxIDEgMC00LjEzIDIuMDYgMi4wNiAwIDAgMSAwIDQuMTN6TTcuMTIgMjAuNDVIMy41NlY5aDMuNTZ2MTEuNDV6TTIyLjIyIDBIMS43N0MuNzkgMCAwIC43NyAwIDEuNzN2MjAuNTRDMCAyMy4yMy43OSAyNCAxLjc3IDI0aDIwLjQ1Yy45OCAwIDEuNzgtLjc3IDEuNzgtMS43M1YxLjczQzI0IC43NyAyMy4yIDAgMjIuMjIgMHoiLz48L3N2Zz4=" alt="LinkedIn"></a>
  <a href="https://noyaadivi.github.io/noya-website"><img src="https://img.shields.io/badge/%D7%AA%D7%99%D7%A7_%D7%A2%D7%91%D7%95%D7%93%D7%95%D7%AA-D9F3E7?style=for-the-badge&logo=githubpages&logoColor=1F7350" alt="תיק עבודות"></a>
  <a href="https://github.com/NoyaAdivi"><img src="https://img.shields.io/badge/%D7%A2%D7%95%D7%93_%D7%A4%D7%A8%D7%95%D7%99%D7%A7%D7%98%D7%99%D7%9D-FBD5E0?style=for-the-badge&logo=github&logoColor=A03A5C" alt="עוד פרויקטים"></a>
</p>

</div>
