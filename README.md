# 🔐 Network Intrusion Detection System

A machine learning-based cybersecurity system that classifies network traffic as **Normal** or one of four attack types — achieving **97.3% accuracy** using a Random Forest classifier on the NSL-KDD dataset.

---

## 🎯 Problem

Traditional signature-based intrusion detection systems fail against novel attack patterns. This project uses **supervised machine learning** to detect anomalous traffic in real time based on behavioral features.

---

## 🛠️ Attack Types Detected

| Label | Type | Description |
|-------|------|-------------|
| Normal | — | Legitimate network traffic |
| DoS | Denial of Service | Floods network with requests to exhaust resources |
| Probe | Port Scan | Reconnaissance — maps network topology |
| R2L | Remote to Local | Exploits vulnerabilities to gain unauthorized access |
| U2R | User to Root | Privilege escalation attacks |

---

## 📊 Key Features Used

| Feature | Description | Importance |
|---------|-------------|------------|
| `src_bytes` | Bytes sent from source | 24% |
| `error_rate` | Connection error rate | 31% |
| `same_srv_rate` | % connections to same service | 27% |
| `duration` | Connection duration (seconds) | 18% |

---

## 📈 Model Performance

| Metric | Score |
|--------|-------|
| Accuracy | **97.3%** |
| Precision | 96.8% |
| Recall | 97.1% |
| F1 Score | **0.969** |

---

## 🧠 Algorithm

```python
from sklearn.ensemble import RandomForestClassifier
from sklearn.model_selection import train_test_split
from sklearn.metrics import accuracy_score, f1_score, classification_report

# Load NSL-KDD dataset
X, y = load_nslkdd_features()

# Split — 80/20 train/test
X_train, X_test, y_train, y_test = train_test_split(X, y, test_size=0.2, random_state=42)

# Train Random Forest
model = RandomForestClassifier(n_estimators=100, random_state=42)
model.fit(X_train, y_train)

# Evaluate
y_pred = model.predict(X_test)
print(f"Accuracy: {accuracy_score(y_test, y_pred) * 100:.1f}%")  # 97.3%
print(f"F1 Score: {f1_score(y_test, y_pred, average='weighted'):.3f}")  # 0.969
print(classification_report(y_test, y_pred))
```

---

## 🗂️ Dataset

**NSL-KDD** — improved version of the KDD Cup 1999 dataset.
- Removes duplicate records from training and test sets
- Includes 41 features per network connection record
- 5 classes: Normal, DoS, Probe, R2L, U2R

---

## 🔧 Tech Stack

- **Python** — data processing and model training
- **Scikit-learn** — Random Forest classifier
- **Pandas / NumPy** — feature engineering
- **Jupyter Notebook** — exploratory data analysis
- **Matplotlib / Seaborn** — visualization

---

## 🚀 How to Run

```bash
pip install scikit-learn pandas numpy matplotlib jupyter
jupyter notebook "NETWORK INTRUSION DETECTION_FINAL.ipynb"
```
