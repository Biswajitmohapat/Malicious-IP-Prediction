# 🛡️ Malicious IP Prediction using Logistic Regression

This machine learning project aims to **classify IP addresses as either malicious or benign** based on behavioral features observed in network logs. It simulates real-world cybersecurity scenarios and provides a baseline model for threat detection using Logistic Regression.

---

## 🎯 Objective

To develop a binary classification model that predicts whether an IP address is **malicious (1)** or **benign (0)** using the following features:

- Number of ports accessed
- Frequency of failed connections
- Country code (ISO numeric)
- Blacklist history

---

## 📊 Dataset: `malicious_ip_logs_1000.csv`

This dataset contains **1,000 rows** of simulated network log data.

### Columns:

| Column Name         | Description                                                                 |
|---------------------|-----------------------------------------------------------------------------|
| `IP_Address`        | Simulated IPv4 address (excluded from training)                            |
| `Ports_Accessed`    | Number of ports accessed by the IP                                          |
| `Failed_Connections`| Number of failed connection attempts                                        |
| `Country_Code`      | ISO numeric country code (e.g., 840 for USA)                                |
| `Blacklist_History` | 1 if the IP has been blacklisted before, otherwise 0                        |
| `Label`             | Target variable: 1 = Malicious, 0 = Benign                                  |

✅ Some features may contain null values to simulate real-world scenarios.

---

## 🧠 Why Logistic Regression?

- Easy to interpret and implement  
- Suitable for binary classification tasks  
- Useful as a baseline model for cybersecurity applications

---

## 🛠️ Project Workflow

1. Load and explore the dataset  
2. Handle missing values (impute using mean/median)  
3. Perform EDA (Exploratory Data Analysis)  
4. Prepare features and split data  
5. Train Logistic Regression model  
6. Evaluate using accuracy, precision, recall, F1-score  
7. Make predictions on new inputs  

---

## 🔍 Sample Code Snippet

```python
# Load and clean dataset
df.fillna(df.median(), inplace=True)

# Train-test split
X = df[['Ports_Accessed', 'Failed_Connections', 'Country_Code', 'Blacklist_History']]
y = df['Label']
X_train, X_test, y_train, y_test = train_test_split(X, y, test_size=0.2)

# Train model
model = LogisticRegression()
model.fit(X_train, y_train)

# Predict new data
model.predict([[20, 4, 356, 1]])
