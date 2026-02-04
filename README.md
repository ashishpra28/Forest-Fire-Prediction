
---

## 📊 Dataset Information

Dataset used: **Algerian Forest Fires Dataset**  
It contains weather and fire index attributes collected from two Algerian regions.

Important columns include:

- Temperature
- RH (Relative Humidity)
- Ws (Wind Speed)
- Rain
- FFMC
- DMC
- DC
- ISI
- BUI
- FWI (**Target variable**)
- Classes (fire / not fire)

✅ In this project, the target is:

> **FWI (Forest Weather Index)**

---

## ⚙️ ML Pipeline (What the project does)

### 1. Data Cleaning & Preprocessing
- Dataset loaded from CSV
- Removed noise/extra spaces in column names (dataset has trailing spaces)
- Converted required columns into numerical format
- Prepared features (X) and target (y)

### 2. Feature Scaling
Applied **StandardScaler** for normalization since Ridge Regression performs better when features are scaled.

### 3. Model Training
Trained multiple regression models and finalized:

✅ **Ridge Regression**
- Helps reduce overfitting
- Adds L2 Regularization penalty

Used `RidgeCV(cv=5)` to tune the best alpha value using cross validation.

### 4. Model Saving
Saved:
- `ridge.pkl` (Ridge model)
- `scaler.pkl` (StandardScaler)

---

## 🌐 Flask Web Application

The Flask app loads the saved Ridge model + scaler and takes user input via HTML form.

### Flask Routes:
- `/` → Welcome page (`index.html`)
- `/predictdata` → Form input + prediction output (`home.html`)

### Input Features in Web App:
The UI expects the following values:

- Temperature
- RH
- Ws
- Rain
- FFMC
- DMC
- ISI
- Classes
- Region

Then it scales the inputs and predicts FWI.



