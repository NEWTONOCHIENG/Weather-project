# Weather-project
STEP 1 : Set up Django project
- Install Django:
      pip install django
 - creat a django project:
      django-admin startproject weather_project cd weather_project
 - Creat an App;
       python manage.py startapp weather
 - Add "weather''to INSTALLED_APPS in setting.py.

   STEP 2 :Get a Weather API Key
         . sign up at openWeatherApp and get an API key.

  STEP 3 :Defin a Django Model (Optional for saving Data)
  - if you want to store search history,define a model in weather \models.py;
          from django ,db import models
         class Weathersearch(models.model):
           city=models.Chrfield(max_length=100)
           saerched_at =models.DateTimeField(auto_now_add=True)

      Run migration:

    python manage.py makemigrations
    python manage.py migrate

STEP 4; Create A View to Fetch Weather Data
   import requests
   from django.shortcuts import render
   from django.conf import settings

   def Weather_view (request):
      weather_data =None

         if request .method ==''post''
         city == request.post.get(''city'')
         api_key == ''YOUR-OPENWEATHERAPP_API-KEY'' #replace with your actual API Key
                  url =
                  
      f''http://api.openweathermap.org\data\2.5\weather?q={city}&appid={api_key}&units=metric''

               response = request.get (url)
               if response .status_code==200:
                    weather_data = response.json()


       return render (request,''weather /weather.html'',{''weather'':weather_data} )             


         STEP 5:Create a Template for Display
         create weather /templates/weather/weather.html:

         <!DOCTYPE html>
         <html>
         <head>
              <title>weather APP</title>
        </head>
        <body>
              <h1>wether App</h1>
              <form method=''post''>
                 {% csrf-token%}
            <input type=''text'' name=city'' placeholder="Enter city name''>

                 <button type =''submit''>Get Weather </button>
                 </form>

                 {% if weather %}
                         <h2>weather in {{weather .name }}</h2
                         <p>temperature: {{weather .main.temp }}
                         <p>weather: {{weather.weather.0.description}}<?P>
                         {% endif %}
                         </body>
                         <?mtml

                   STEP 6:Configure URLs
                   from django.urls import path
                   from.views import weather_views 

                   urlpattern={path ('''',weather_views,name=''weather),


              from django.contrib import admin
              from django.urls import path ,include

              urlpatters =[path(''admin/'', admin.site.urls),
                          path(''',include(''weather .urls''))



                STEP 7:Run The Project
                 python manage .py runserver.























    
