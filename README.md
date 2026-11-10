
# Multi-Class Intrusion Detection System using Machine Learning (IDS2025)

A machine learning based network intrusion detection system that classifies traffic into seven classes (Normal, Botnet ARES, Brute Force, DoS/DDoS, Infiltration, PortScan, Web Attack), with a Streamlit web app for batch prediction and analysis.

## Highlights
- Multi-class detection of 6 attack types plus normal traffic
- Class imbalance handled with SMOTE (applied to the training set only)
- Compared Decision Tree, Random Forest and KNN
- **Random Forest: 99.53% accuracy** (18,254 of 18,341 test samples correct)
- Streamlit app with file upload, attack-wise analysis, wrong-prediction analysis and result export

## Dataset
IDS2025 network flow dataset: [exact name, source and link]. Flow features were extracted from network traffic. The raw data is not included in this repository because of size and licence; download it from the link above.

## Method
1. Preprocessing: cleaning, label encoding of protocol, service and state, label encoding of classes
2. Stratified 80/20 train-test split
3. SMOTE on the training data only
4. StandardScaler feature scaling
5. Models: Decision Tree, Random Forest, KNN
6. Evaluation: accuracy, confusion matrix, attack-wise accuracy, feature importance

## Results
| Model | Accuracy |
|-------|----------|
| Decision Tree | 99.35% |
| **Random Forest** | **99.53%** |
| KNN | 98.15% |

Attack-wise accuracy (Random Forest):
| Class | Test records | Accuracy |
|-------|-------------|----------|
| Botnet ARES | 373 | 99.73% |
| Brute Force | 2040 | 100% |
| DoS/DDoS | 5199 | 99.85% |
| Infiltration | 6 | 66.67% |
| Normal | 5233 | 98.62% |
| PortScan | 5077 | 99.98% |
| Web Attack | 413 | 99.27% |

![Confusion matrix](images/confusion_matrix.png)

## Limitations
- Infiltration has very few real samples (6 in the test set), so its result is not statistically reliable; SMOTE adds synthetic data only to training.
- Results are from a single train-test split.
- Port numbers rank high in feature importance and may reflect dataset-specific patterns.

## Web App
![App screenshot](images/app_main.png)

Run locally:
1. `git clone https://github.com/REMYANAIR-CS/intrusion-detection-system-ids2025.git`
2. `pip install -r requirements.txt`
3. `streamlit run app.py`
4. Upload a test file in CSV or Excel format.

## Project Structure
- `ids_model.ipynb`: training and evaluation notebook
- `app.py`: Streamlit application
- `model/`: trained Random Forest, scaler and encoders (if under 100 MB)
- `images/`: result figures
- `requirements.txt`

## Future Work
Deep learning models (CNN, LSTM), live traffic capture, feature selection, hybrid models, explainability with SHAP and LIME.

## Author
Remya R Nair 
