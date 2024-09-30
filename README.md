# NLP-Greek-Language-Proficiency-Classification
## Project Overview
This repository is dedicated to the NLP Greek Language Proficiency Classification project, which focuses on classifying Greek texts into CEFR (Common European Framework of Reference for Languages) levels using three different machine learning models: Support Vector Machine (SVM), Multinomial Naive Bayes, and Recurrent Neural Networks (RNN). This project employs Natural Language Processing and machine learning techniques to assess language skills efficiently.

**Note**: This repository only includes the code for the Multinomial Naive Bayes model, which I developed. Other machine learning models used in this project by my colleagues are not shared here.

## Motivation
The goal of this project is to provide an automated tool for the classification of Greek language proficiency, aiding educational institutions and learners by delivering swift and accurate assessments of language capabilities.

## Dataset
The dataset used in this project was created from two main sources:

1. **329 authentic texts** from the [Greek Language Center's website](https://www.greek-language.gr/certification/dbs/teachers/index.html) (CEFR levels A1 to C2). These texts are categorized by proficiency levels and can be accessed publicly.
2. **711 generated texts** using **ChatGPT-4o** under specific prompts for Conditional Text Generation. These texts were designed to simulate various language proficiency levels (A1 to C2), ensuring a balanced and diverse dataset for training the machine learning models.

### Dataset Versions:
Due to the dataset size and limitations, we organized the texts into two versions:

- **Full CEFR Levels Dataset**: Texts classified into six levels (A1, A2, B1, B2, C1, C2).
- **Condensed Three Levels Dataset**: Texts merged into three broader categories: beginner (A1 + A2), intermediate (B1 + B2), and advanced (C1 + C2).

This dual-source and dual-structure approach enabled better training for machine learning models across different proficiency levels.

**Note**: Due to privacy and licensing reasons, the dataset is not included in this repository.

## Technologies Used
- Python
- Scikit-Learn
- NLTK
- spaCy
- SMOTE for handling class imbalance

## Features
- Advanced text preprocessing: tokenization, lemmatization, and removal of stop words.
- TF-IDF vectorization, capturing both unigrams and bigrams. We also incorporated average word count and average  sentence length as a feature.
- To further enhance accuracy, we planned to incorporate additional features, particularly the average sentence length and average word count of the texts. At lower proficiency levels (A1-B1), learners tend to use a limited range of vocabulary, often repeating basic words and phrases. Their writing is typically shorter due to a lack of language resources to express complex ideas or elaborate in detail. In contrast, learners at higher proficiency levels (B2-C2) have a broader vocabulary and can use a variety of expressions. Their essays tend to be longer because they can explore topics in greater depth, introduce nuances, and support arguments with more detailed evidence.
In terms of sentence structure, lower-level learners often produce short, simple sentences using basic grammar, which limits the length of their writing. As proficiency increases, learners use more complex sentence structures, including subordinate clauses, passive voice, and various verb tenses, naturally resulting in longer texts.
- Statistical analysis of these features confirmed our theories, revealing a significant increase in both the average word count and sentence length as proficiency levels rise. For instance, the average word count in A1-level texts is 78, whereas in C2-level texts, it reaches 390. A similar pattern emerges in sentence length: A1-level texts average about 9 words per sentence, compared to approximately 21 words in C2-level texts. These observations led us to incorporate these features, as we aimed to utilize simple, surface-level metrics to enhance the model's ability to classify proficiency levels accurately.


## Results
We evaluated the performance of three models: Support Vector Machine (SVM), Multinomial Naive Bayes, and a Recurrent Neural Network (RNN). The results showed the following:

1. **SVM Model**:
   - **Test Accuracy**: 83.65%
   - **Training Accuracy**: 87.71%
   - **Best Parameters**: `C=10, gamma=0.01`
   - The SVM model performed well overall, but there was some confusion between intermediate and advanced proficiency levels. The model demonstrated strong precision, recall, and F1-scores, particularly for the beginner category.
   - For the **Condensed Three Levels Dataset**, the model performed best, whereas with the **Full CEFR Levels Dataset**, it showed overfitting (test accuracy: 54.32%).

2. **Multinomial Naive Bayes**:
   - **Test Accuracy**: 84.62%
   - **Training Accuracy**: 88.31%
   - Naive Bayes showed slightly better performance than SVM on the test set. It was effective at identifying beginner texts but had some difficulty distinguishing between intermediate and advanced levels.

3. **RNN Model**:
   - **Test Accuracy**: 73%
   - **Training Accuracy**: 93%
   - The RNN model exhibited strong performance on the training set but suffered from overfitting, resulting in a lower test accuracy. The model struggled most with intermediate and advanced level distinctions.

## Conclusions
There were several misclassifications between Levels B and C. Models performed best at classifying Level A instances with high accuracy on both training and test sets. However, Levels B and C had lower accuracy and were often confused with each other. This is due to the nature of the proficiency levels: Level A (Basic User) is simpler and more distinct, while Levels B and C include more complex language features like advanced vocabulary and syntax. Greek’s complex morphology adds to this difficulty. Level B had the lowest accuracy, as it represents a less clearly defined intermediate level between beginner and advanced.

## Installation
To set up this project for use or development, follow these steps:

1. **Clone the repository**:
   ```bash
   git clone https://github.com/spymavro/NLP-Greek-Language-Proficiency-Classification.git
   cd NLP-Greek-Language-Proficiency-Classification
2. **Install the required Python packages**:

- Ensure you have Python installed on your system. If not, download and install it from [python.org](https://www.python.org/downloads/).
- It's recommended to create a virtual environment to keep dependencies required by different projects separate and to avoid conflicts:
  ```bash
  python -m venv venv
  source venv/bin/activate  # On Windows use `venv\Scripts\activate`
- Install the required packages:
  ```bash
  pip install scikit-learn nltk spacy gensim
- After installing spacy, you may need to download a specific language model. For Greek, you can use:
  ```bash
  python -m spacy download el_core_news_sm

3. **Proceed with project setup and usage as required**:
### Explanation:
- **Step 1**: Cloning the repository is straightforward; make sure to replace with your actual GitHub username.
- **Step 2**: This step covers:
  - Checking for Python installation.
  - Setting up a virtual environment, which is optional but recommended.
  - Direct installation of each required Python package using `pip`.
  - Additional steps for setting up `spacy` with the Greek language model are included since it's a common requirement for projects involving NLP with Greek text.

## Usage
- Run the NB classification model with the following command: 
  ```bash
  python NB_classifier.py 

**Note**: This repository only includes the code for the NB model, which I developed. Other machine learning models used in this project by my colleagues are not shared here.

## Contact
For permissions or inquiries, please contact me at katerinamastrofoti@gmail.com
