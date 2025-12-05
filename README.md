
# 🛡️ URL Classification System

This project detects whether a given URL is **SAFE**, **DEFACEMENT**, **PHISHING**, or **MALWARE** using machine learning. A Random Forest model is trained on URL patterns and feature engineering to identify malicious behavior.

---

## 📌 Project Overview

The model analyses URLs using multiple handcrafted features such as URL length, number of symbols, presence of suspicious words, IP usage, directory depth, and more. These features help the Random Forest classifier understand patterns commonly found in harmful URLs.

After training, the program allows the user to enter any URL through the terminal and receive an instant prediction about its safety.

---

## 📂 Dataset

The dataset used in this project is:

```
malicious_phish.csv
```

It contains:

* `url` → the URL string
* `type` → label category

  * SAFE
  * DEFACEMENT
  * PHISHING
  * MALWARE

---

## 🧠 Feature Engineering

Each URL is converted into numeric features, including:

* `use_of_ip` → Checks for IP address
* `abnormal_url` → Detects mismatched hostname patterns
* `count.` → Counts number of dots
* `count@` → Checks for '@' symbol
* `count_dir` → Number of '/' in path
* `url_length` → Total characters in URL
* `hostname_length` → Length of domain
* `short_url` → Detects URL shorteners (bit.ly, t.co, etc.)
* `sus_url` → Searches for suspicious terms (login, secure, bank, etc.)
* `digit_count` → Number of digits
* `letter_count` → Number of alphabets
* `fd_length` → Length of first directory

These features help the model distinguish normal vs malicious behavior.

---

## ⚙️ Model Used

The project uses:

```
RandomForestClassifier(n_estimators=100, max_features="sqrt")
```

Random Forest performs well for URL classification due to its robustness and ability to handle many features without heavy preprocessing.

---

## 🏃 How to Run the Project

### 1️⃣ Install Python Dependencies

```
pip install numpy pandas scikit-learn
```

### 2️⃣ Ensure Dataset is Available

Place `malicious_phish.csv` in the same folder as your Python script.

### 3️⃣ Run the Script

```
python url_classifier.py
```

### 4️⃣ Enter URLs to Test

Example:

```
Enter a URL to check: https://example-login-free-bonus-update.com
The URL is classified as: PHISHING
```

To exit:

```
Enter a URL to check: 0
```

---

## 🧪 Model Evaluation

After training, the script prints a classification report that includes:

* Precision
* Recall
* F1-score
* Accuracy

This shows how well the model performs across the four classes.

---

## 🧩 Prediction Label Mapping

| Code | Meaning    |
| ---- | ---------- |
| 0    | SAFE       |
| 1    | DEFACEMENT |
| 2    | PHISHING   |
| 3    | MALWARE    |

---

## 📦 Project Structure

```
│── url_classifier.py
│── malicious_phish.csv
│── README.md
```

---

## 🚀 Future Enhancements

* Add a graphical or web-based frontend
* Improve feature extraction
* Save model as `.pkl` for deployment
* Integrate WHOIS and SSL-based features

