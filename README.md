# Sentiment Classification of Steam Reviews using Big Data

![PySpark](https://img.shields.io/badge/Apache%20Spark-PySpark-orange?logo=apachespark)
![GCP](https://img.shields.io/badge/Google%20Cloud-Dataproc-blue?logo=googlecloud)
![Machine Learning](https://img.shields.io/badge/ML-Classification-green)

Acest proiect abordează o problemă de procesare a limbajului natural (NLP): clasificarea sentimentelor din recenziile utilizatorilor de pe platforma Steam folosind tehnologii Big Data. Focusul principal a fost evaluarea performanței modelelor de clasificare într-un mediu distribuit, gestionând volume mari de date textuale.

## Setul de Date
Am utilizat un set de date masiv de recenzii de pe Steam (Steam Reviews Dataset) provenit de pe Kaggle.
* **Sursă:** [Kaggle - Steam Reviews Dataset](https://www.kaggle.com/datasets/forgemaster/steam-reviews-dataset)
* **Etichetare:** Deoarece datele brute nu aveau etichete de sentiment explicite pentru această sarcină, am utilizat librăria **VADER SentimentIntensityAnalyzer** pentru a genera automat clasele: Negativ, Neutru, Pozitiv.
* **Tehnologie:** Procesare prin **PySpark** pentru încărcarea, curățarea și transformarea datelor.

---

## Arhitectura Tehnică & Algoritmi

Proiectul a fost testat atât local, cât și într-un mediu distribuit folosind **Google Cloud Platform (GCP)**, demonstrând scalabilitatea soluției.

### Algoritmi Implementați:
1.  **Naive Bayes:** S-a dovedit a fi cel mai performant model, obținând o acuratețe de aproximativ **79.98%** în setările multiclass.
2.  **Support Vector Machine (SVM):** Implementat prin `LinearSVC` cu strategia **OneVsRest** pentru a permite clasificarea în mai multe clase.
3.  **Random Forest Classifier:** Utilizat pentru a evalua performanța algoritmilor bazați pe arbori de decizie pe date vectorizate.

### Evaluare:
Performanța a fost măsurată folosind metrici standard pentru clasificare multiclass:
* **Acuratețe (Accuracy)**
* **F1-Score**
* **Weighted Precision & Recall**

---

## Funcționalități și Pipeline
* **Preprocessing:** Normalizarea textului (lowercase, trim), eliminarea caracterelor speciale și filtrarea valorilor nule.
* **Feature Engineering:** Tokenizare, eliminarea cuvintelor de legătură (StopWordsRemover) și vectorizare prin **TF-IDF** (HashingTF + IDF).
* **Scalabilitate:** Optimizarea partiționării datelor (`repartition`) pentru a maximiza paralelismul în Spark.

---

## Cum se rulează

1.  **Cerințe:**
    * Python 3.10
    * Java 8/11 (necesar pentru Spark)
    * Librării: `pyspark`, `vaderSentiment`
2.  **Instalare:**
    ```bash
    pip install pyspark vaderSentiment
    ```
3.  **Execuție:**
    Deschide `notebook.ipynb` într-un mediu compatibil Spark (Jupyter, Google Colab sau Kaggle). Asigură-te că setul de date este accesibil la calea definită în script (`/kaggle/input/steam-reviews/dataset.csv` sau similar).
