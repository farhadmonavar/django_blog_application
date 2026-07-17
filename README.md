# Django Blog App

A full-featured blogging platform built with Django, featuring public-facing blog browsing (with categories, search, and comments) and a custom admin dashboard for managing posts, categories, and users.

## Features

**Public site**
- Browse published blog posts on the homepage, with featured posts highlighted separately
- Filter posts by category
- View individual blog posts with full content and comments
- Keyword search across post titles, descriptions, and body content
- Comment on posts (authenticated users)
- User registration and login/logout

**Admin dashboard**
- At-a-glance stats (category and post counts)
- Full CRUD for blog categories
- Full CRUD for blog posts, including featured images, status (Draft/Published), and "featured" flag
- Full CRUD for user accounts
- Dashboard access restricted to logged-in users

## Tech Stack

- **Backend:** Django 6.0
- **Forms/Styling:** django-crispy-forms with crispy-bootstrap4
- **Database:** SQLite (default, easily swappable)
- **Image handling:** Pillow

## Project Structure

```
Django_Blog_App/
├── blog_main/          # Project settings, root URLs, home/auth views
├── blogs/               # Public blog app (models, category/post views, search)
├── dashboards/          # Admin dashboard app (CRUD for posts/categories/users)
├── templates/           # HTML templates (public pages + dashboard)
├── media/                # User-uploaded images
├── manage.py
└── requirenmets.txt     # Python dependencies
```

## Getting Started

### Prerequisites
- Python 3.10+
- pip

### Installation

1. Clone the repository
   ```bash
   git clone <your-repo-url>
   cd Django_Blog_App
   ```

2. Create and activate a virtual environment
   ```bash
   python -m venv env
   # Windows
   env\Scripts\activate
   # macOS/Linux
   source env/bin/activate
   ```

3. Install dependencies
   ```bash
   pip install -r requirenmets.txt
   ```

4. Apply migrations
   ```bash
   python manage.py migrate
   ```

5. Create a superuser (to access the dashboard and Django admin)
   ```bash
   python manage.py createsuperuser
   ```

6. Run the development server
   ```bash
   python manage.py runserver
   ```

7. Visit `http://127.0.0.1:8000/` for the public site, and `http://127.0.0.1:8000/dashboards/` for the admin dashboard (login required).

## Key URLs

| Path                          | Description                       |
|-------------------------------|------------------------------------|
| `/`                            | Homepage with featured/latest posts |
| `/category/<id>/`              | Posts filtered by category         |
| `/blogs/<slug>/`                | Single blog post + comments        |
| `/blogs/search?keyword=...`     | Keyword search                     |
| `/register`                    | User registration                  |
| `/login` / `/logout`            | Authentication                     |
| `/dashboards/`                  | Admin dashboard home               |
| `/dashboards/categories/`       | Manage categories                  |
| `/dashboards/posts/`            | Manage blog posts                  |
| `/dashboards/users/`            | Manage users                       |

## Notes

- `DEBUG = True` and the `SECRET_KEY` in `blog_main/settings.py` are development defaults — replace both before deploying to production.
- Uploaded images are stored under `media/uploads/`.
