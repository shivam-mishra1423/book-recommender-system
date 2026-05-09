# Book Recommender System

![3D Book Recommender](https://upload.wikimedia.org/wikipedia/commons/8/82/3D_cube.svg)

## Overview

This project is a simple Flask-based Book Recommendation Web App. The user can search for a book title, and the app returns a list of similar books based on precomputed similarity data.

## Project Goals

- Provide fast book recommendations using precomputed data
- Offer a clean and easy web interface for searching and recommending books
- Use a similarity matrix for quick results and low latency responses

## What This Project Does

- `app.py` runs the Flask web server
- `templates/index.html` displays the home page with popular books
- `templates/recommend.html` provides a recommendation input page
- Pickle files store the data and similarity models used by the app

## Detailed File Explanation

- `app.py`
  - Defines the Flask web application
  - Loads the pickled data files: `popular.pkl`, `pt.pkl`, `books.pkl`, and `similarity_scores.pkl`
  - Serves the home page at `/`
  - Serves the recommendation page at `/recommend`
  - Processes user input and generates book recommendations at `/recommend_books`

- `templates/index.html`
  - Shows a list of popular books on the homepage
  - Displays book title, author, cover image, number of ratings, and average rating

- `templates/recommend.html`
  - Contains the search form for book recommendations
  - Displays the recommended books and their cover images

- `popular.pkl`
  - Stores a DataFrame of popular books
  - Includes columns such as `Book-Title`, `Book-Author`, `Image-URL-M`, `num_ratings`, and `avg_rating`

- `pt.pkl`
  - Stores a pivot table with book titles as the index
  - Used for looking up the selected book and retrieving its recommendation index

- `books.pkl`
  - Stores the full book dataset used for lookup and metadata
  - Provides author names and image URLs for the recommended books

- `similarity_scores.pkl`
  - Stores the precomputed similarity score matrix
  - Likely generated from a similarity algorithm such as cosine similarity

- `requirements.txt`
  - Lists the Python dependencies required to run the app
  - Includes `flask`, `numpy`, `pandas`, and `gunicorn`

- `Procfile`
  - Used for deployment on platforms like Heroku
  - Should contain a line like `web: gunicorn app:app`

- `main.py`
  - Currently an empty placeholder
  - The actual application logic runs from `app.py`

## How to Run Locally

1. Make sure Python 3.8 or higher is installed
2. Open a terminal in the project folder
3. Create a virtual environment:
   ```bash
   python -m venv venv
   ```
4. Activate the virtual environment:
   - On Windows:
     ```bash
     venv\Scripts\activate
     ```
   - On macOS / Linux:
     ```bash
     source venv/bin/activate
     ```
5. Install required dependencies:
   ```bash
   pip install -r requirements.txt
   ```
6. Run the Flask application:
   ```bash
   python app.py
   ```
7. Open the browser at `http://127.0.0.1:5000/`

## How the Recommendation Works

1. The app receives the user input book title from the recommendation form
2. It checks whether the title exists in the pivot table index
3. If the title exists, it finds the corresponding row in the similarity matrix
4. It sorts similar book scores in descending order
5. It selects the top 5 similar books and returns their title, author, and image URL
6. If the title is not found, it displays `No book found`

## GitHub Upload Instructions

To upload this project to GitHub, follow these steps:

```bash
cd "c:\Users\shiva\OneDrive\Desktop\BOOK-RECOMMENDER-SYSTEM"
git init
git add README.md app.py templates requirements.txt Procfile popular.pkl pt.pkl books.pkl similarity_scores.pkl
git commit -m "Initial commit: Add book recommender app and README"
git branch -M main
# Create a new GitHub repository and copy the remote URL
# Example:
git remote add origin https://github.com/<username>/<repo-name>.git
git push -u origin main
```

> Note: If you do not want to upload large `.pkl` files to GitHub, use Git LFS or exclude them from the repository and store them separately.

## Important Notes

- All `.pkl` files must remain in the project directory and be accessible by `app.py`
- The recommendation system currently requires exact book title matches
- If the book title is not found in the pivot table index, the page shows `No book found`

## Recommended Improvements

- Add autocomplete search for book titles
- Add fuzzy matching or partial title search
- Improve the recommendation algorithm with user-based or hybrid methods
- Add a data regeneration pipeline to rebuild pickle files from source data

## 3D Design Preview

This README includes a 3D-style image to represent a modern interface. For actual 3D content on GitHub, you can use a 3D preview image or an animated GIF.

![3D Book Recommender](https://upload.wikimedia.org/wikipedia/commons/8/82/3D_cube.svg)

---

**Enjoy building your Book Recommender System!**
