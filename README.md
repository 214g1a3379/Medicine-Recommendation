<h1 align="center">Medicine-Recommendation </h1>

**Business Problem:**
* In healthcare, diagnosing diseases based on symptoms and recommending appropriate medicines is crucial.
* However, manual diagnosis can be time-consuming, error-prone, and inconsistent. Patients often struggle to find the right medication for their symptoms without consulting a doctor, leading to self-medication risks.

**Problem Statement:**
* This project aims to develop an AI-driven Medicine Recommendation System that suggests appropriate medicines based on a user’s symptoms. By leveraging ChromaDB for similarity-based retrieval and Sentence Transformers for symptom embeddings, the system identifies the most relevant disease and provides medication recommendations.

**Solution Description:**
The proposed solution automates and improves symptom-to-medicine mapping, ensuring efficient and accurate medical recommendations while minimizing human error.

# Dataset:

1. **disease_symptoms.csv:**
   This dataset contains mappings between diseases and their associated symptoms. It helps the model identify diseases based on user-provided symptoms.
           **Dataset Characteristics:**
           * Size of the dataset: 304
           * No. of columns: 2 - Disease, Symptoms
   * Purpose: Used to match user symptoms to possible diseases.
2. **disease_medicine_dosage.csv:**
   This dataset provides information about recommended medicines and dosages for specific diseases.
           **Dataset Characteristics:**
           * Size of the dataset: 41
           * No. of columns: 3 - Disease, Medicine, Dosage
   * Purpose: Once a disease is identified, this dataset provides the corresponding medicine recommendation and dosage.

# Data Preprocessing:
**Handling Missing Values:**
df1.isnull().sum() and df2.isnull().sum() are used to count missing values in each column.
**Handling Duplicate Entries:**
df1.duplicated().sum() and df2.duplicated().sum() are used to check for duplicate rows.

# ChromaDB
ChromaDB is an open-source vector database optimized for handling embeddings efficiently. It allows for fast similarity searches using distance metrics like cosine similarity.
**Characteristics:**
* Fast similarity search: ChromaDB enables quick retrieval of diseases based on symptoms.
* Efficient storage of embeddings: Instead of comparing text directly, it works with compact numerical embeddings.
* Scalability: Can handle large datasets with many diseases and symptoms.
* Flexible querying: Users can search for diseases based on symptoms, even if symptoms don’t match exactly.

# Modeling 
* ChromaDB is used as a vector database to store and retrieve symptom embeddings for disease-medicine recommendations.
* A ChromaDB client is created. A collection (disease_collection) is initialized to store symptom embeddings. Cosine similarity is used as the distance function for comparing embeddings.
* all-mpnet-base-v2 is used to convert symptoms into vector embeddings. The model generates high-dimensional embeddings, representing symptoms in a way that enables similarity comparisons.
* Each disease’s symptom embedding is stored in ChromaDB. Metadata (disease name) is also stored for retrieval.
* When a user enters symptoms, they are converted into an embedding. ChromaDB retrieves the top most similar disease embeddings. This enables symptom-based disease matching.
* ChromaDB acts as a disease-symptom retrieval system using vector embeddings. It helps match user-input symptoms to the closest known diseases, which can then be used to suggest appropriate medicines and dosage.

# Results
![Screenshot 2025-03-16 230647](https://github.com/user-attachments/assets/bd81fe0f-0343-4eab-b2d0-16bf44225f59)

![Screenshot 2025-03-16 230701](https://github.com/user-attachments/assets/ee0b3c45-cebc-46f9-84e7-4cf15fc526b9)

   
