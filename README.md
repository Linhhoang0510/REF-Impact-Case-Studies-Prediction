# REF Impact Case Studies Prediction

A machine learning project to classify and enhance Research Excellence Framework (REF) 2021 Impact Case Studies based on quality indicators and to improve case study quality through AI-assisted revision.

## 📋 Project Objectives

### Part 1: Impact Classification
- **Primary Goal**: Predict the quality rating (2*, 3*, or 4*) of REF 2021 Impact Case Studies using their textual content
- **Objectives**:
  - Extract and preprocess impact case study text data from REF 2021 databases
  - Build and train multiple machine learning classification models
  - Evaluate model performance using cross-validation and test sets
  - Compare model accuracy, precision, recall, and F1-scores
  - Identify the best-performing classification model

### Part 2: Quality Enhancement
- **Goal**: Enhance and improve the quality of lower-rated impact case studies
- **Approach**: Use AI-assisted revision techniques to enhance case study quality

## 📊 Dataset

### Data Sources
1. **REF 2021 Impact Case Study Database**: Complete collection of impact case studies submitted to the REF 2021 exercise
2. **REF 2021 Results Database**: Rating profiles and assessment scores for each submission

### Data Characteristics
- **Total Samples**: ~1,200+ impact case studies
- **Classes**: 
  - Class 0: 2* and 3* rated case studies (lower impact)
  - Class 1: 4* rated case studies (highest impact)
- **Text Sections Analyzed**:
  - Title
  - Summary of the impact (1. Summary of the impact)
  - Details of the impact (4. Details of the impact)

### Data Distribution
- Training Set: ~80% of data (960+ samples)
- Test Set: ~20% of data (240+ samples)
- Class Balance: Addressed using RandomOverSampling on training data

## 🛠 Requirements

### Python Libraries
```
pandas >= 1.0.0
scikit-learn >= 0.24.0
xgboost >= 1.5.0
spacy >= 3.0.0
nltk >= 3.6.0
matplotlib >= 3.3.0
seaborn >= 0.11.0
beautifulsoup4 >= 4.9.0
markdown >= 3.3.0
imbalanced-learn >= 0.8.0
```

### Models Used
- Naive Bayes (MultinomialNB)
- K-Nearest Neighbors (KNN)
- Support Vector Machine (SVM)
- Decision Tree
- Random Forest
- Gradient Boosting Classifier
- AdaBoost
- Extreme Gradient Boosting (XGBoost)

## 🔄 Methodology

### 1. Data Preprocessing
- **Text Cleaning**: 
  - Convert Markdown to plain text using BeautifulSoup
  - Remove reference tags and URLs
  - Remove extra newlines and special formatting
  
- **Tokenization & Lemmatization**:
  - Use spaCy NLP model (`en_core_web_sm`) for tokenization
  - Apply lemmatization to normalize word forms
  - Remove punctuation and special characters
  - Remove hyphens and dots for cleaner tokens

- **Feature Engineering**:
  - Combine title, summary, and detail sections into single document
  - Use CountVectorizer for word frequency-based features
  - Create binary classification labels (0 = low impact, 1 = high impact)

### 2. Model Training
- **Train-Test Split**: 80/20 split with random_state=2024
- **Handling Class Imbalance**: RandomOverSampler applied to training data
- **Cross-Validation**: 5-fold cross-validation for model evaluation
- **Vectorization**: CountVectorizer for text-to-numeric conversion

### 3. Model Evaluation
**Metrics Used**:
- Accuracy: Overall correctness of predictions
- F1-Score: Harmonic mean of precision and recall (macro-averaged)
- Precision: Correct positive predictions out of all positive predictions
- Recall: Correct positive predictions out of actual positives
- Confusion Matrix: Visualization of prediction errors

## 📈 Results

### Model Performance Comparison

All models were evaluated using 5-fold cross-validation on the oversampled training set:

| Model | Cross-Validation Accuracy | Test Accuracy | Key Findings |
|-------|--------------------------|---------------|--------------|
| Naive Bayes | High consistency | Strong baseline | Good interpretability |
| KNN | Moderate | Variable performance | Sensitive to feature scale |
| SVM (Linear) | Strong | Robust predictions | Good generalization |
| Decision Tree | Moderate | Prone to overfitting | Fast training |
| Random Forest | High | Excellent generalization | Strong feature importance |
| Gradient Boosting | Excellent | Best performance | Consistent high accuracy |
| AdaBoost | Good | Stable results | Effective error correction |
| XGBoost | Excellent | Top performance | Best overall model |

### Key Findings

1. **Best Performing Models**: 
   - **XGBoost** and **Gradient Boosting Classifier** achieved the highest cross-validation accuracy
   - Both ensemble methods demonstrated superior generalization to test data
   - Extreme Gradient Boosting (XGBoost) recommended as primary model

2. **Model Stability**:
   - Ensemble methods (Random Forest, Gradient Boosting, XGBoost) showed lower variance across folds
   - Traditional classifiers (Naive Bayes, SVM) provided faster training with competitive accuracy

3. **Feature Importance**:
   - Text features from case study titles and summaries are strong indicators of impact rating
   - Specific keywords and phrases distinguish high-impact cases from lower-rated ones

4. **Class Balance Impact**:
   - RandomOverSampling effectively improved model performance for minority class (4* studies)
   - Addressed data imbalance that would have biased models toward majority class

## 📂 Project Structure

```
REF-Impact-Case-Studies-Prediction/
├── notebook.ipynb          # Main analysis and modeling notebook
├── README.md              # Project documentation (this file)
├── category.png           # Category distribution visualization
├── train-test-category.png # Class distribution in train/test sets
└── cv.png                 # Cross-validation scores comparison
```

## 🚀 Usage

### Setup
1. Download the required datasets from the Google Drive links below
2. Place `REF-2021-results.csv` and `REF-2021-impactcase.csv` in the working directory
3. Install required libraries:
   ```bash
   pip install -r requirements.txt
   ```

### Running the Analysis
1. Open `notebook.ipynb` in Jupyter Notebook or VS Code
2. Execute cells sequentially to:
   - Load and merge datasets
   - Preprocess text data
   - Train and evaluate all models
   - Generate performance visualizations
   - Compare model results

## 📥 Download the Datasets from Google Drive

### Primary Datasets
1. **REF 2021 Impact Case Study Database**: [https://drive.google.com/file/d/1OsD3ZxbF-49HugZTsXw8J8PXBVmcXzYe/view?usp=sharing]

2. **REF 2021 All REF Results Database**: [https://drive.google.com/file/d/1fGuuhIIFSai5IhFAhliC8LTalSUBK7JM/view?usp=sharing]

### Reference Case Studies for Quality Enhancement
3. **University of Northampton** - Improving rehabilitation and advances in international practice in relation to ankle ligament surgical repair: [https://drive.google.com/file/d/1jJiU8lTee3QYpa7pZq8KW2SdT5vx3PMe/view?usp=sharing]

4. **University of Glasgow** - Deciphering the underlying immunopathology of Guillain–Barré syndrome to drive advances in targeted treatment: [https://drive.google.com/file/d/1jo-0S46JNTxuL-CjYivDaiycvzjRAQtF/view?usp=sharing]

5. **University of Glasgow** - Establishing Caldan Therapeutics Ltd: a spin-out company to exploit the first selective agonists of Free Fatty Acid Receptors: [https://drive.google.com/file/d/1tTqiRmmCFcjhb_JIj7Baipn2QGDT9zuK/view?usp=sharing]

6. **Random 4-star-rated sample** for one-shot learning: [https://drive.google.com/file/d/1bti91gu_Akd8tTY7W8OJeVTJ7DIh4A3I/view?usp=sharing]

### Enhanced Case Studies
7. **Revised Impact Case Studies by Claude**:
   - Full text: [https://docs.google.com/document/d/10bXZ6cKsv_473cZ2-fDMtFgp7JlPQsFL/edit?usp=sharing&ouid=105413206312208690662&rtpof=true&sd=true]
   - CSV file: [https://drive.google.com/file/d/1JXVyDY5gFOZIcAXmb1LXtK8nnAD6hNiM/view?usp=sharing]

## 📝 Key Technical Insights

### Text Processing Pipeline
1. **Markdown Conversion**: Convert structured Markdown to plain text
2. **Reference Removal**: Strip citation brackets and URLs
3. **Tokenization**: Break text into meaningful units
4. **Lemmatization**: Normalize word forms to root meanings
5. **Vectorization**: Convert text to numerical features using word counts

### Model Selection Rationale
- **XGBoost**: Selected as primary model due to:
  - Highest cross-validation accuracy
  - Superior generalization to unseen data
  - Efficient training and prediction
  - Built-in regularization to prevent overfitting
  - Handles class imbalance effectively

## 🎓 Learning Outcomes

This project demonstrates:
- End-to-end machine learning pipeline development
- Text preprocessing and NLP techniques
- Multiple classification algorithm implementations
- Model evaluation and comparison methodologies
- Handling imbalanced datasets
- Cross-validation best practices
- Feature engineering from unstructured text

## 📌 Notes

- All models use the same preprocessed data and feature set for fair comparison
- Random states are set to 2024 for reproducibility
- Class imbalance is addressed using RandomOverSampler on training data only
- Test set is kept untouched for unbiased evaluation

## 👥 Author & Contact

For questions about this project, please refer to the detailed analysis in `notebook.ipynb`.


