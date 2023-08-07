# Weather-Application
Front-end (React):
Create a new React project and set up the front-end components.
using bash
"npx create-react-app weather-frontend
cd weather-frontend"
Replace the content of src/App.js in source code of front-end

Back-end (Django):
Create a new Django project and set up the back-end API.
"django-admin startproject weather_backend
cd weather_backend
django-admin startapp weather_api"
Replace the content of weather_api/views.py in the source code of backend

Add the weather_api app to the project's settings in weather_backend/settings.py:

INSTALLED_APPS = [
    # ...
    'weather_api',
    # ...
]

WEATHER_API_KEY = 'YOUR_WEATHER_API_KEY'  # Replace this with actual weather API key

Create a new URL pattern in weather_api/urls.py
from django.urls import path
from . import views

urlpatterns = [
    path('weather/', views.get_weather, name='get_weather'),
]

Front-end and Back-end Connection:
To connect the front-end and back-end, we need to set up CORS (Cross-Origin Resource Sharing) for the development environment. Install django-cors-headers to handle CORS in Django:
pip install django-cors-headers
Add 'corsheaders' to INSTALLED_APPS in weather_backend/settings.py:
INSTALLED_APPS = [
    # ...
    'corsheaders',
    # ...
]

Add 'corsheaders.middleware.CorsMiddleware' to the MIDDLEWARE setting in weather_backend/settings.py:
MIDDLEWARE = [
    # ...
    'corsheaders.middleware.CorsMiddleware',
    'django.middleware.common.CommonMiddleware',
    # ...
]

Finally, configure CORS to allow requests from the frontend in weather_backend/settings.py:
CORS_ORIGIN_ALLOW_ALL = True

Run the Development Servers:
Run both the front-end and back-end development servers:

In the weather-frontend directory:
npm start

In the weather_backend directory:
python manage.py runserver

Now you should have your Weather Application running on http://localhost:3000, and it will communicate with the Django back-end running on http://localhost:8000.
