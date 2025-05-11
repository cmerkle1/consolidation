# News Application Setup

## Overview
This is a Django-based news application where journalists can publish articles and newsletters whih are reviewed and approved by editors. The approved articles can be subscribed to and read by readers. The project uses MySQL for the database, environment variables via python-decouple, and supports RESTful APIs with djangorestframework.

## Prerequisites
- Ensure you are using **Python 3.11** or a compatible version.
- pip
- Docker optional if containerization is the goal
- Django>=4.0,<5.0: runs the program
- pymysql: connects my MySQL, 8.0 or compatible
- python-decouple: manages environment variables
- tweepy: allows posting to Twitter
- djangorestframework: supports API endpoints

## Setup Instructions

1. **Clone the Repository**
git clone your repository
cd your-repo-name

2. **Create a Virtual Environment:**
python -m venv venv
venv\Scripts\activate

3. **Configure the Database**
Create a .env in the root of your directory
Include the following: 
DB_NAME=your_database_name
DB_USER=your_mysql_username
DB_PASSWORD=your_mysql_password
DB_HOST=localhost
DB_PORT=3306

Make sure your settings.py contains the following to match: 
from decouple import config

DATABASES = {
    'default': {
        'ENGINE': 'django.db.backends.mysql',
        'NAME': config('DB_NAME'),
        'USER': config('DB_USER'),
        'PASSWORD': config('DB_PASSWORD'),
        'HOST': config('DB_HOST'),
        'PORT': config('DB_PORT', default='3306'),
    }
}

4. **Install Dependencies**
pip install -r requirements.txt

5. **Run migrations**
python manage.py migrate

6. **Start the Development Server**
python manage.py runserver

### API Endpoints
- /api/articles/ | GET | List all articles |
- /api/articles/ | POST | Create a new article |
- /api/articles/<id>/ | GET | Retrieve an article |
- /api/articles/<id>/ | PUT | Update an article |
- /api/articles/<id>/ | DELETE | Delete an article |
- /api/subscriptions/ | GET | List subscriptions for current user |
- /api/subscriptions/ | POST | Subscribe to a publisher or journalist |
- /api/subscriptions/<id>/ | GET | Get details of a specific subscription |
- /api/subscriptions/<id>/ | PUT | Update a subscription |
- /api/subscriptions/<id>/ | DELETE | Cancel a subscription |
