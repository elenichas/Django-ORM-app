# Django ORM Project with PostgreSQL

This is a standalone Django application that uses PostgreSQL as its database backend. The project demonstrates how to use Django's ORM for handling data models and interacting with the database. This README provides steps to set up and run the project.

## Features
- Built with Django and PostgreSQL
- Simple app (`myapp`) with basic CRUD operations for a `Book` model
- Includes custom Django management commands

## Requirements
- Python 3.6+
- PostgreSQL 13+
- pip (Python package manager)

## Setup Instructions

### 1. Clone the Repository
```bash
https://github.com/yourusername/django_orm_app.git
cd django_orm_app
```

### 2. Create a Virtual Environment
```bash
python -m venv venv
```

Activate the virtual environment:
- **Windows**: `venv\Scripts\activate`
- **macOS/Linux**: `source venv/bin/activate`

### 3. Install Dependencies
```bash
pip install -r requirements.txt
```

> Note: If `requirements.txt` is not provided, install Django and PostgreSQL driver manually:
```bash
pip install django psycopg2
```

### 4. Configure the Database
Make sure PostgreSQL is running, and create a new database named `django_orm_db` and a user with permissions for it. Update the database configuration in `config/settings.py`:

```python
DATABASES = {
    'default': {
        'ENGINE': 'django.db.backends.postgresql',
        'NAME': 'django_orm_db',
        'USER': 'django_user',
        'PASSWORD': 'your_password',
        'HOST': 'localhost',
        'PORT': '5432',
    }
}
```

### 5. Run Migrations
```bash
python manage.py makemigrations
python manage.py migrate
```

### 6. Create a Superuser (Optional)
To access the Django admin interface:
```bash
python manage.py createsuperuser
```

### 7. Run the Server
```bash
python manage.py runserver
```
Access the app at `http://127.0.0.1:8000/`.

## Using the ORM
You can use the Django shell to interact with the models. For example, to create and query books:
```bash
python manage.py shell
```
```python
from myapp.models import Book

# Create a book
book = Book.objects.create(title="Django for Beginners", author="John Doe", published_date="2024-10-06")

# Query books
books = Book.objects.all()
for book in books:
    print(book.title)
```

## Custom Management Commands
The project includes a custom management command for displaying all books:
```bash
python manage.py mycommand
```

## Project Structure
- `config/`: Contains Django project settings and configurations.
- `myapp/`: The main application containing models, views, and logic.

## Contributing
Feel free to submit issues or pull requests to improve this project.

## License
This project is licensed under the MIT License.

## Author
Developed by [Your Name](https://github.com/yourusername).

