Book Recommender SystemThis is a book recommender system built with Python, Flask, and Scikit-learn. It provides two main features:A "Top 50" list of the most popular and highest-rated books.A recommendation engine that suggests books similar to a user's selection using collaborative filtering.FeaturesPopularity-Based Recommendations: The main page displays the top 50 books based on a weighted calculation of the number of ratings and the average rating.Collaborative Filtering Recommendations: When a user selects a book, the system uses item-based collaborative filtering (cosine similarity) to find and display other books that similarly-minded users have also enjoyed.How It WorksThe project is divided into two main parts:1. Model Training (Jupyter Notebook)The book-recommender-system.ipynb notebook is used for all data loading, processing, and model building.It loads the raw data (books.csv, users.csv, ratings.csv).Popularity Model: It calculates the top 50 books by filtering for books with a high number of ratings (>=250) and then sorting by the average rating. This list is saved as popular.pkl.Collaborative Filtering Model:It filters the dataset to include only experienced users (who have rated > 200 books) and popular books (which have > 50 ratings).It creates a user-item pivot table where rows are book titles, columns are user IDs, and values are the ratings. This list is saved as pt.pkl.It computes the cosine similarity matrix between all books in the pivot table, creating a "similarity score" for every book pair. This matrix is saved as similarity_scores.pkl.2. Web Application (Flask)The app.py file is a Flask server that loads the pre-computed models to serve recommendations.It loads popular.pkl, pt.pkl, books.pkl, and similarity_scores.pkl./ (Main Route): Renders index.html and passes in the data for the top 50 popular books./recommend (Recommend Route): Renders recommend.html, which contains the search/recommendation form./recommend_books (POST):Takes the book title from the user's form input.Finds the book's index in the pivot table.Uses the index to retrieve its similarity scores from the similarity_scores matrix.Identifies the top 4 most similar books.Fetches their details (title, author, image URL) and sends this data back to the recommend.html template to be-displayed.Project Structure.
├── app.py                   # The main Flask web application
├── book-recommender-system.ipynb  # Jupyter Notebook for analysis and model building
├── books.pkl                # Pickled DataFrame of all books
├── popular.pkl              # Pickled DataFrame of the top 50 popular books
├── pt.pkl                   # Pickled pivot table (Book-Title vs. User-ID)
├── similarity_scores.pkl    # Pickled cosine similarity matrix
├── Procfile                 # Deployment file (for Heroku)
├── requirements.txt         # Python dependencies
└── templates/
    ├── index.html           # Main page (shows popular books)
    └── recommend.html       # Page for showing recommendations

How to RunClone the repository:git clone [https://github.com/your-username/book-recommender-system.git](https://github.com/your-username/book-recommender-system.git)
cd book-recommender-system

Install dependencies:(It's recommended to use a virtual environment)pip install -r requirements.txt

Run the Flask app:python app.py

Open your browser and navigate to http://127.0.0.1:5000/ to see the app in action.
