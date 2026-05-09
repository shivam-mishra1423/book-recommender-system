# Book Recommender System

![3D Book Recommender](https://upload.wikimedia.org/wikipedia/commons/8/82/3D_cube.svg)

## Overview

Yeh project ek simple Flask based Book Recommendation Web App hai. User ek book title choose karta hai, aur system similar books recommend karta hai, precomputed similarity scores ke basis par.

### Project ka goal
- Fast book recommendation dena
- Simple web interface for search and recommendation
- Precomputed similarity matrix use karna for quick results

## Kya kaam karta hai
- `app.py` Flask server chalata hai
- `index.html` home page show karta hai top books
- `recommend.html` recommend page show karta hai
- Pickle files mein precomputed data store hota hai

## Files ka detailed explanation

- `app.py`
  - Flask application define karta hai
  - `/` route par popular books show karta hai
  - `/recommend` par recommendation form dikhata hai
  - `/recommend_books` par selected book ke similar books recommend kar ke `recommend.html` render karta hai

- `templates/index.html`
  - Popular books ka gallery dikhata hai
  - Top book title, author, image, votes aur rating show karta hai

- `templates/recommend.html`
  - Book search form deta hai
  - Recommendation results par similar books ka list show karta hai

- `popular.pkl`
  - Popular books ka data frame store karta hai
  - `Book-Title`, `Book-Author`, `Image-URL-M`, `num_ratings`, `avg_rating` jaise columns hain

- `pt.pkl`
  - Pivot table store karta hai jisme book titles index hote hain
  - Recommendation lookup yahin se hoti hai

- `books.pkl`
  - Complete book dataset store karta hai
  - Title se author aur image URLs fetch karne ke liye use hota hai

- `similarity_scores.pkl`
  - Similarity matrix store karta hai
  - Ye precomputed cosine similarity ya kisi aur similarity method se bana ho sakta hai

- `requrement.txt`
  - Python dependencies list karta hai
  - Standard convention ke liye ab `requirements.txt` bhi add kiya gaya hai

- `Procfile`
  - Heroku style deployment ke liye basis file hai
  - `web: gunicorn app:app` waisa content hona chahiye

- `main.py`
  - Abhi empty placeholder hai
  - Project ke run logic actually `app.py` mein hai

## Kaise run kare locally

1. Python install karein (Python 3.8+ recommended)
2. Project folder mein terminal kholen
3. Virtual environment banayen:
   ```bash
   python -m venv venv
   ```
4. Activate karein:
   - Windows:
     ```bash
     venv\Scripts\activate
     ```
   - macOS / Linux:
     ```bash
     source venv/bin/activate
     ```
5. Dependencies install karein:
   ```bash
   pip install -r requirements.txt
   ```
6. Flask app chalayein:
   ```bash
   python app.py
   ```
7. Browser mein `http://127.0.0.1:5000/` open karein

## GitHub pe upload karne ke steps

Agar aap GitHub pe upload karna chahte hain, to ye steps follow karein:

```bash
cd "c:\Users\shiva\OneDrive\Desktop\BOOK-RECOMMENDER-SYSTEM"
git init
git add README.md app.py templates requirements.txt Procfile popular.pkl pt.pkl books.pkl similarity_scores.pkl
git commit -m "Initial commit: Add book recommender app and README"
git branch -M main
# GitHub par repository banayein aur remote URL copy karein
# Example:
git remote add origin https://github.com/<username>/<repo-name>.git
git push -u origin main
```

> Note: Agar aap `.pkl` files GitHub par upload nahi karna chahte, to unko commit se pehle ignore karein ya unke source data ko git mein use karein.

## Important Notes

- Model aur similarity data `*.pkl` files mein hai, isliye ye files sahi path par hi rahni chahiye
- `app.py` mein user input exact book title ke matches leta hai
- Agar book title list mein nahi milta, to `recommend.html` par `No book found` show hota hai

## Future improvements

- Book title auto-complete search add karein
- Approximate matching ya fuzzy search implement karein
- Recommendation algorithm improve karein (user-based, content-based ya hybrid)
- Data update workflow banayein jisse pickle files automatically regenerate ho sakte hain

## 3D Design Preview

Yaha par image 3D style ka representation use kiya gaya hai. Agar aap GitHub README mein actual 3D model chahte hain, to aap 3D asset ka preview image ya animated GIF add kar sakte hain.

![3D Book Recommender](https://upload.wikimedia.org/wikipedia/commons/8/82/3D_cube.svg)

---

**Enjoy building your Book Recommender System!**
