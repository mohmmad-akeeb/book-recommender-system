# 📚 Book Recommender System

This project is a **Book Recommender System** built using **Python**, **Flask**, and **Scikit-learn**.  
It provides two powerful features:
<p align="left"> <img src="https://img.shields.io/badge/Python-3.9+-blue?logo=python&logoColor=white" /> <img src="https://img.shields.io/badge/Flask-2.x-black?logo=flask" /> <img src="https://img.shields.io/badge/Scikit--Learn-ML-orange?logo=scikit-learn" /> <img src="https://img.shields.io/badge/Status-Active-success" /> <img src="https://img.shields.io/badge/License-MIT-green" /> <img src="https://img.shields.io/badge/Made%20With-%F0%9F%92%9A%20Love-pink" /> </p>

- **Top 50 most popular & highest-rated books**
- **Collaborative filtering-based recommendations**

---

## 🚀 Features

### ⭐ Popularity-Based Recommendations
- Homepage displays the **Top 50 books**.
- Ranking is calculated using:
  - Number of ratings  
  - Average rating  
  - Weighted popularity score  
- Stored in **`popular.pkl`**

### 🤝 Collaborative Filtering Recommendations
- Suggests books similar to the one selected by the user.
- Uses **item-based collaborative filtering** with **cosine similarity**.
- Retrieves and displays the **top 4 similar books**.

---

## 🧠 How It Works

The project is divided into two main parts:

---

## 1️⃣ Model Training (Jupyter Notebook)

File: **`book-recommender-system.ipynb`**

This notebook performs all data loading, cleaning, and model building.

### 📥 Data Loading
- Loads:
  - `books.csv`
  - `users.csv`
  - `ratings.csv`

### ⭐ Popularity Model
- Filters books with **>= 250 ratings**.
- Calculates average rating.
- Creates a ranked list of **Top 50 books**.
- Saves the result as **`popular.pkl`**

### 🤝 Collaborative Filtering Model
Steps:

1. Keeps **experienced users** (rated > 200 books)
2. Keeps **popular books** (books with > 50 ratings)
3. Builds a **user–item pivot table**  
   - Rows → Book titles  
   - Columns → User IDs  
   - Values → Ratings  
   - Saved as **`pt.pkl`**
4. Computes **cosine similarity matrix**  
   - Saved as **`similarity_scores.pkl`**

---

## 2️⃣ Web Application (Flask)

File: **`app.py`**

The Flask server loads all pre-computed models and serves recommendations.

### Routes

| Route | Description |
|-------|-------------|
| `/` | Shows Top 50 books (index page) |
| `/recommend` | Displays search & recommendation page |
| `/recommend_books` (POST) | Retrieves similar books and displays them |

### Recommendation Flow

1. User enters a book name  
2. System finds its index in the pivot table  
3. Gets similarity scores from **`similarity_scores.pkl`**  
4. Selects **top 4 similar books**  
5. Fetches title, author, and image URL  
6. Displays results on `recommend.html`

---

## 📁 Project Structure
```
.
├── app.py                           # Flask backend
├── book-recommender-system.ipynb    # Jupyter Notebook
├── books.pkl                        # All books DataFrame
├── popular.pkl                      # Top 50 books
├── pt.pkl                           # Pivot table (Book vs User)
├── similarity_scores.pkl            # Cosine similarity matrix
├── Procfile                         # Heroku deployment file
├── requirements.txt                 # Dependencies
└── templates/
    ├── index.html                   # Popular books page
    └── recommend.html               # Recommendation page
```
---

## 🛠️ Installation & Setup

Follow these steps to set up the project on your system.

---

### 1️⃣ Clone the Repository
```bash
git clone https://github.com/your-username/book-recommender-system.git
cd book-recommender-system
```

### 2️⃣ Install Dependencies

It is recommended to use a virtual environment.
```bash
pip install -r requirements.txt
```
### 3️⃣ Run the Flask Server
```bash
python app.py
```
### 4️⃣ Open the Application

Go to your browser:
```bash
http://127.0.0.1:5000/
```
Your Book Recommender System is now running 🎉

## 🧑‍💻 Author

Mohmmad Akeeb
