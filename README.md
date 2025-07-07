# SENTIMENT-ANALYSIS

*COMPANY*: CODTECH IT SOLUTIONS

*NAME*: RUQSAR FIRDOUS

*INTERN ID*: CT04DG2858

*DOMAIN*: DATA ANALYST

*DURATION* : 4 WEEKS

*MENTOR*: NEELA SANTOSH

## 📌 **Task 4 — Sentiment Analysis of Zomato & Swiggy Play Store Reviews**

For my fourth task, I focused on a very practical and industry-relevant challenge: performing **sentiment analysis** on real user reviews of India’s two leading food delivery apps — **Zomato** and **Swiggy**. This task gave me hands-on experience in working with unstructured text data, vectorizing it, training models, evaluating performance, and preparing the results for further visualization and dashboarding.

---

### 📂 **Dataset Summary**

The dataset came in the form of **two separate CSV files**:

* `zomato.csv` — containing Zomato’s Play Store reviews.
* `swiggy.csv` — containing Swiggy’s Play Store reviews.

Both files had similar structures: `App`, `review_date`, `review_description`, `rating`, `thumbsUpCount`, `developer_response`, `developer_response_date`, and `appVersion`. These columns provide not just the user opinion but also context like when the review was written, whether the developer responded, and which app version the feedback applies to.

---

### 🗂️ **1️⃣ Combining the Data**

First, I loaded both files into **Google Colab** using pandas and combined them into a single DataFrame. Merging them allowed me to handle the entire set of customer feedback together, making it easy to compare Zomato and Swiggy side by side.

---

### 🧹 **2️⃣ Cleaning & Handling Missing Data**

The next step was to inspect the dataset for missing values and duplicates. I found that columns like `developer_response` and `developer_response_date` had a lot of missing entries because not every user receives a reply from the app developers. Instead of dropping these rows or columns — which could have removed valuable feedback — I filled missing developer responses with **‘No Response’** and missing response dates with **‘No Response Date’**. For the `appVersion` column, I filled missing values with **‘Unknown Version’**.

After this, I dropped any duplicate reviews based on the `review_description` column to ensure data consistency. Finally, I reset the index to keep the DataFrame clean.

---

### 📝 **3️⃣ Preprocessing the Text**

Since I was working with user-generated text, cleaning it was essential. I used basic NLP techniques:

* Converted all text to lowercase to maintain consistency.
* Removed punctuation, special characters, and numbers.
* Removed common stopwords to focus on the important words.
* Tokenized the text and joined it back for vectorization.

This cleaned version of the reviews was stored in a new column `cleaned_review`.

---

### 🏷️ **4️⃣ Creating Sentiment Labels**

To perform supervised learning, I converted the numerical star ratings into sentiment categories:

* Ratings **4–5** → **Positive**
* Rating **3** → **Neutral**
* Ratings **1–2** → **Negative**

This `sentiment` column became my target variable for training the model.

---

### 🔢 **5️⃣ Vectorizing the Text**

I transformed the cleaned text into numerical features using **TF-IDF Vectorization**. I limited the features to the top 5000 words to balance accuracy and resource usage, which is crucial when working in Colab with limited RAM.

---

### ✂️ **6️⃣ Splitting the Data**

I split the data into training and test sets, ensuring the model would be evaluated on unseen data. This gives a realistic measure of how well the model would generalize to new reviews.

---

### 🤖 **7️⃣ Training Multiple Models**

I experimented with three models:

* **Logistic Regression**: Simple yet very effective, giving me the highest accuracy of \~89%.
* **Random Forest**: Took longer and gave \~83% accuracy.
* **XGBoost**: Gave \~85% accuracy, but needed more runtime.

After testing, I selected **Logistic Regression** as my final model because of its balance between speed, accuracy, and ease of deployment.

---

### ✅ **8️⃣ Making Predictions**

Using the trained Logistic Regression model, I made sentiment predictions for the test data. Since the predicted labels needed to match the original format, I inverse-transformed the encoded predictions back to the text labels: **Positive**, **Neutral**, and **Negative**.

---

### 💾 **9️⃣ Exporting the Results**

Finally, I carefully merged the predictions back into my original DataFrame by matching only the test indices. This ensured that my final dataset shows both the true and predicted sentiment for test rows without overwriting the original data. I exported this as `final_reviews_with_sentiment.csv` and saved the model accuracy in a separate `.txt` file for reference.

---

### 🎯 **Outcome & Next Steps**

With this pipeline, I successfully built a practical **NLP classification workflow** — from data cleaning and vectorization to training, evaluation, and exporting results. The next logical step is to use this enriched dataset to create an **interactive sentiment dashboard** in Power BI or Tableau, where we can visually analyze user moods, detect trends by app version, track thumbs-up counts, and see how developer responses impact sentiment.

---

### 💡 **Key Learnings**

This task strengthened my confidence in:

* Handling messy, real-world text data.
* Applying NLP preprocessing techniques.
* Training and evaluating multiple models.
* Understanding the trade-offs between model complexity, runtime, and accuracy.
* Preparing data for further business intelligence use cases.

---

By doing this, I not only improved my practical data science workflow but also laid the foundation for a clear, actionable **customer sentiment analysis** — which is invaluable for companies like Swiggy or Zomato to understand customer pain points, respond better, and improve their services.

---
