# Pakistani Multi Source News Mining Pipeline

## Overview
This project implements an end to end data mining pipeline for large scale Pakistani news articles collected from multiple media outlets. The system is designed to automatically assign incoming news articles to fixed high volume sections, enabling consistent routing, aggregation, and analysis across sources with heterogeneous category schemes.

The workflow follows an academic data mining structure, covering data integration, preprocessing, exploratory analysis, supervised learning, unsupervised mining, and reproducibility oriented deployment artifacts.

## Application Focus
The primary application is automatic section classification for a newsroom or news aggregation platform. When a new article arrives, the trained model assigns it to one of the dominant sections such as Pakistan, World, Business, Markets, or Sports without manual intervention.

## Dataset
The dataset consists of news articles collected from five major Pakistani outlets:
- Business Recorder
- Daily Times
- Dawn
- Pakistan Today
- Tribune

After integration and cleaning, the working dataset contains approximately 567k articles across the top 20 most frequent categories. Each record includes headline, description, source, date, category, and derived text fields used for modelling.

## Pipeline Structure
The project pipeline is modular and plug and play. Each stage can be replaced or extended independently without changing the rest of the system.

![Project Pipeline Flowchart](https://drive.google.com/uc?export=view&id=1TMysIzwt0fYuOd9PIlc2_AOVKyff7cnb)

## Methodology

### Data Preprocessing
- Schema unification across sources
- Handling missing text and category values
- Merging headline and description into a single story field
- Category normalization and restriction to top 20 classes
- Text cleaning including lowercasing, URL removal, and noise filtering

### Exploratory Data Analysis
- Category and source distribution analysis
- Story length statistics
- Source category cross tabulation
- Temporal trends by month

### Supervised Learning
- TF IDF vectorization with unigrams and bigrams
- Classical classifiers including Linear SVM, Logistic Regression, and Naive Bayes
- Hyperparameter tuning using cross validation
- Transformer based fine tuning using DistilBERT
- Evaluation using accuracy and macro F1 to account for class imbalance

### Unsupervised Mining
- Dimensionality reduction with Truncated SVD
- K Means clustering for latent topic structure
- Frequent itemset mining and association rules using category, source, and time attributes

## Results
Classical TF IDF models provide strong baselines, with Linear SVM reaching around 0.74 accuracy. DistilBERT achieves the best performance with approximately 0.84 accuracy and 0.70 macro F1 on held out test data, making it the preferred model for deployment in imbalanced multi source settings.

## Reproducibility
The notebook is structured as a complete reproduction pipeline:
- Deterministic train test split
- Fixed preprocessing steps
- Explicit evaluation metrics
- Saved model and label mapping artifacts

All stages can be re run sequentially to reproduce results or adapted to new data sources.

## Usage
1. Download the dataset files and place them in the expected directory structure
2. Run the notebook from top to bottom
3. Use the saved model and label mapping to classify new incoming articles

## Notes
The system is designed for extensibility. New sources, categories, or models can be added with minimal changes, making the pipeline suitable for academic experimentation as well as applied newsroom analytics.
