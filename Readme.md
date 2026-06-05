# Content-Based Product Recommendation System

## Project Overview

This project implements a Content-Based Recommendation System using the Amazon Fine Food Reviews Dataset. The system recommends similar products based on product review content, summaries, and textual descriptions. It uses Natural Language Processing (NLP) techniques and Machine Learning algorithms to analyze product information and generate personalized recommendations.

---

## Features

* Download dataset directly from Kaggle
* Data preprocessing and cleaning
* Missing value handling
* Product feature extraction
* Automatic tag generation from reviews
* TF-IDF vectorization
* Cosine similarity-based recommendations
* Interactive user search
* Recommendation visualization using charts
* Product similarity scoring

---

## Dataset

Dataset: Amazon Fine Food Reviews Dataset

Source:
https://www.kaggle.com/datasets/snap/amazon-fine-food-reviews

Dataset contains:

* Product Reviews
* Product Ratings
* Review Summaries
* Customer Information
* Helpfulness Scores

Important Columns:

| Column      | Description        |
| ----------- | ------------------ |
| ProductId   | Product Identifier |
| UserId      | User Identifier    |
| ProfileName | Customer Name      |
| Score       | Product Rating     |
| Summary     | Review Summary     |
| Text        | Full Review Text   |

---

## Technologies Used

* Python
* Pandas
* NumPy
* Matplotlib
* Seaborn
* Scikit-Learn
* Kaggle API
* SciPy

---

## Project Workflow

### Step 1: Import Libraries

Required libraries are imported for:

* Data manipulation
* Machine learning
* Visualization
* Similarity calculations

### Step 2: Download Dataset

The Kaggle API is used to automatically download the Amazon Fine Food Reviews dataset.

```python
api.dataset_download_files(dataset, path="data", unzip=True)
```

### Step 3: Load Dataset

```python
data = pd.read_csv(file_path)
```

The dataset is loaded into a Pandas DataFrame.

### Step 4: Data Cleaning

Missing values are replaced:

```python
data['ProfileName'] = data['ProfileName'].fillna("Unknown")
data['Summary'] = data['Summary'].fillna("Unknown")
```

Duplicate records are checked:

```python
data.duplicated().sum()
```

### Step 5: Rename Columns

Columns are renamed for better readability.

| Original             | New Name     |
| -------------------- | ------------ |
| ProductId            | ProdID       |
| Score                | Rating       |
| HelpfulnessNumerator | HelpfulCount |

### Step 6: Product ID Encoding

```python
data['ProdID'] = pd.factorize(data['ProdID'])[0]
```

Converts product IDs into numeric values.

### Step 7: Generate Product Tags

The system extracts useful keywords from review summaries and review text.

Example:

Original Review:

```text
Good quality dog food bought vitality canned dog food.
```

Generated Tags:

```text
good quality dog food bought vitality canned food
```

### Step 8: Create Product Name

```python
data['ProductName'] = data['Summary'] + " - " + data['Tags']
```

Creates a searchable product title.

### Step 9: TF-IDF Vectorization

```python
tfidf_vectorizer = TfidfVectorizer(stop_words='english')
```

TF-IDF converts text into numerical vectors.

Benefits:

* Removes common words
* Highlights important words
* Creates machine-readable features

### Step 10: Calculate Similarity

```python
cosine_similarity()
```

Cosine Similarity measures how similar two products are based on their textual content.

Similarity Score Range:

* 1.0 = Exactly Similar
* 0.0 = Completely Different

### Step 11: Generate Recommendations

User enters:

```text
dog food
```

The system:

1. Finds matching products
2. Computes similarity scores
3. Sorts products
4. Returns top recommendations

---

## Recommendation Function

Main Function:

```python
content_based_recommendations()
```

Parameters:

| Parameter | Description               |
| --------- | ------------------------- |
| data      | Dataset                   |
| item_name | User Input                |
| top_n     | Number of Recommendations |

Returns:

* Product Name
* Rating
* Similarity Score
* Review Text

---

## Sample Input

```text
dog food
```

## Sample Output

| Product Name      | Rating | Similarity |
| ----------------- | ------ | ---------- |
| Premium Dog Food  | 5      | 0.91       |
| Healthy Pet Food  | 5      | 0.87       |
| Organic Dog Meal  | 4      | 0.84       |
| Vitality Dog Food | 5      | 0.82       |

---

## Data Visualization

The project generates two graphs:

### 1. Ratings Chart

Displays ratings of recommended products.

Shows:

* Product Name
* Star Rating

### 2. Similarity Score Chart

Displays cosine similarity scores.

Shows:

* Product Similarity
* Recommendation Strength

---

## Machine Learning Technique

### Content-Based Filtering

The recommendation engine suggests products based on:

* Product descriptions
* Review summaries
* Review text
* Keyword similarity

Advantages:

* No user history required
* Fast recommendations
* Easy implementation
* Good accuracy for text-rich datasets

---

## Project Structure

```text
Project/
│
├── data/
│   └── Reviews.csv
│
├── recommendation_system.py
│
├── README.md
│
└── requirements.txt
```

---

## Installation

### Clone Project

```bash
git clone <repository-link>
```

### Install Dependencies

```bash
pip install pandas numpy matplotlib seaborn scikit-learn scipy kaggle
```

### Configure Kaggle API

Place:

```text
kaggle.json
```

inside:

```text
C:\Users\USERNAME\.kaggle\
```

### Run Project

```bash
python recommendation_system.py
```

---

## Future Improvements

* Hybrid Recommendation System
* Deep Learning Models
* Sentiment Analysis
* Product Category Filtering
* Web Application Deployment
* User Profile-Based Recommendations
* Real-Time Recommendations

---

## Conclusion

This project successfully demonstrates a Content-Based Recommendation System using Amazon Fine Food Reviews data. By combining NLP techniques, TF-IDF vectorization, and Cosine Similarity, the system can identify and recommend products with similar characteristics based on textual content. The project provides an efficient and practical recommendation solution that can be extended for real-world e-commerce applications.
