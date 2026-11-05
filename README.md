# ICTHub-ChatBot-2026
[![Python](https://img.shields.io/badge/Python-3.9%2B-3776AB?logo=python&logoColor=white)](https://www.python.org/)
[![scikit-learn](https://img.shields.io/badge/scikit--learn-ML-F7931E?logo=scikit-learn&logoColor=white)](https://scikit-learn.org/)
[![NLTK](https://img.shields.io/badge/NLTK-NLP-154F5C)](https://www.nltk.org/)
[![Google Colab](https://img.shields.io/badge/Run%20in-Google%20Colab-F9AB00?logo=googlecolab&logoColor=white)](https://colab.research.google.com/)
An intent-classification chatbot for ICT Hub, built with Python and developed in the Google Colab notebook [`ICTHub_ChatBot2026.ipynb`](ICTHub_ChatBot2026.ipynb). The chatbot reads a user message, predicts one of 11 intent categories, and uses fuzzy matching to reject messages that appear unrelated to the vocabulary represented in the training data.
## Features
- Cleans and normalizes user input with lowercasing, punctuation cleanup, whitespace cleanup, tokenization, stopword removal, and Porter stemming.
- Removes duplicate records from the training dataset.
- Encodes intent labels with scikit-learn's `LabelEncoder`.
- Converts text into numerical features using TF-IDF vectorization.
- Compares five supervised machine-learning models:
  - Logistic Regression
  - Linear Support Vector Classification
  - K-Nearest Neighbors
  - Random Forest
  - Multinomial Naive Bayes
- Evaluates models with an 80/20 stratified train-test split, accuracy scores, and confusion matrices.
- Automatically selects the best-performing model.
- Uses a `difflib` fuzzy-matching check with a cutoff of `0.75` to identify input that does not resemble the known training vocabulary.
## Project Structure
```text
ICTHub-ChatBot-2026/
├── ICTHub_ChatBot2026.ipynb   # Data preparation, training, evaluation, and chatbot demo
├── icthub_dataset.xlsx        # Labeled training dataset
└── README.md                  # Project documentation
```
## Tech Stack
- **Language:** Python
- **Notebook environment:** Google Colab or Jupyter Notebook
- **Natural language processing:** NLTK
- **Machine learning:** scikit-learn
- **Data handling:** pandas
- **Dataset format:** Microsoft Excel (`.xlsx`)
- **Vocabulary validation:** Python `difflib`
## Installation and Setup
### 1. Clone the repository
```bash
git clone https://github.com/MohabMansour88/ChatBot-using-ML.git
cd ChatBot-using-ML
```
### 2. Install dependencies
```bash
pip install -r requirements.txt
```
If a `requirements.txt` file is not available yet, install the main packages manually:
```bash
pip install pandas openpyxl scikit-learn nltk jupyter
```
### 3. Download NLTK resources
Run the following once before preprocessing text:
```python
import nltk
nltk.download("punkt")
nltk.download("stopwords")
```
Depending on the NLTK version, you may also need:
```python
nltk.download("punkt_tab")
```
## Running the Notebook
### Google Colab
1. Open [`ICTHub_ChatBot2026.ipynb`](ICTHub_ChatBot2026.ipynb) in the repository.
2. Upload or mount the repository files in Colab.
3. Ensure `icthub_dataset.xlsx` is available in the notebook's working directory.
4. Run the cells from top to bottom.
5. Follow the final chatbot prompt to test intent predictions.
### Local Jupyter Notebook
```bash
jupyter notebook ICTHub_ChatBot2026.ipynb
```
Run the cells sequentially after installing the dependencies and downloading the required NLTK resources.
## Dataset
The chatbot uses `icthub_dataset.xlsx`, which contains two columns:
| Column | Description |
|---|---|
| `User Input` | Example message written by a user |
| `Category` | Intent label associated with the message |
Duplicate records are removed before training. The project currently supports 11 intent categories:
| # | Intent Category |
|---:|---|
## Machine-Learning Pipeline
1. Load the Excel dataset and remove duplicates.
2. Normalize text by lowercasing and cleaning punctuation and whitespace.
3. Tokenize with NLTK, remove stopwords, and apply Porter stemming.
4. Encode the 11 categories with `LabelEncoder`.
5. Generate TF-IDF features.
6. Split the data into stratified training and testing sets using an 80/20 ratio.
7. Train and compare five classification models.
8. Review accuracy scores and confusion matrices.
9. Select the best-performing model for chatbot inference.
10. Check whether an input resembles the known vocabulary before predicting its intent.
## Model Comparison
The notebook compares the following models. Replace the placeholders with the measured test-set accuracies after running the notebook.
| Model | Accuracy |
|---|---:|
| Logistic Regression | _TBD_ |
| Linear SVC | _TBD_ |
| K-Nearest Neighbors | _TBD_ |
| Random Forest | _TBD_ |
| Multinomial Naive Bayes | _TBD_ |
## Example Usage
Example input:
```text
How can I register for an ICT Hub training program?
```
Example prediction:
```text
Predicted intent: <intent-category>
```
If the message does not contain words sufficiently similar to the training vocabulary, the fuzzy-matching validation reports that the input appears unrelated instead of returning an unreliable intent prediction.
## Future Improvements
- Fine-tune transformer-based models such as BERT or DistilBERT.
- Add response generation instead of returning only the predicted intent.
- Add confidence scores and a fallback response for uncertain predictions.
- Expand and rebalance the dataset with more real-world user examples.
- Deploy the chatbot as a web application.
- Integrate the chatbot with Telegram or another messaging platform.
## Contributing
Contributions are welcome. To contribute:
1. Fork the repository.
2. Create a feature branch.
3. Make and test your changes.
4. Open a pull request with a clear description of the improvement.
Please keep dataset changes labeled consistently and document any changes to the preprocessing or model pipeline.
