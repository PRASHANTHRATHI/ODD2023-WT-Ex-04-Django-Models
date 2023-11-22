# Ex-04-Django-Models
# Name :Prashanth
# reference number:23002136
# Department: AIDS



# AIM:
 To create django model

# DESIGN PROCEDURE
django models

step 1: Create django project and app using the following
commands
django-admin startproject mymodels
python manage.py startapp myapp

step 2:
create a user_profile models in model.py
```python
from django.db import models
# Create your models here.
from django.contrib.auth.models import User


class UserProfile (models.Model):
    user = models.OneToOneField(User, on_delete=models.CASCADE) 
    first_name = models.CharField(max_length=100)
    last_name = models.CharField(max_length=100)
    email = models.EmailField()

```



add the models in the admin interface using the code admin.py
```python
from django.contrib import admin
 
#register your models here

from.models import UserProfile

admin.site.register(UserProfile)

```


write the function based view to render the data from the models to the template in views.py

```python
from django.shortcuts import render
from django.views import View
from django.contrib.auth.decorators import login_required
# Create your views here.

from .models import UserProfile
@login_required
def user_profile(request):
    user = request.user # Get the currently logged-in user
    user_profile = UserProfile.objects.get(user=user)#retrieve the associated profile
    context = {
        'user': user,
        'user_profile': user_profile,
        'firstname': user_profile.first_name, 
        'lastname': user_profile.last_name,
    }
    return render(request, 'myapp/user_profile.html', context)

```

set up the url path for the templates using urls.py

```python
from django.contrib import admin
from django.urls import path
from MYAPPS import views
from MYAPPS.views import user_profile

urlpatterns = [
    path('admin/', admin.site.urls),
    path('profile/',views.user_profile,name='user_profile')
]

```

in settings.py file add the appcreated

step3: Now do the migrations process to initiate and save the models
python manage.py makemigrations python manage.py migrate create a template as user_profile.html

```python
<!DOCTYPE html>
<html>
<head>
<title>User Profile</title>
</head>
<body>
<h1>User Profile</h1>
<p><strong>Username:</strong> {{ user.username }} </p> 
<p><strong>First Name:</strong> {{ firstname }}</p>
<p><strong>Last Name:</strong>{{ lastname }}</p>
 <p><strong>Email:</strong> {{ user.name }}</p>
<p><strong>Custom Profile Data:</strong> {{ user_profile.custom_field }}</p> 
<!-- Include more profile fields as needed -->
</body>
 </html>
```

step 4: Run the program using the following command

python manage.py runserver 8000 in the admin page you can view the models created and in the user_profile template page you can see the profile page of the user

# OUTPUT
![Alt text](<Screenshot 2023-11-21 090533.png>)

![Alt text](<Screenshot 2023-11-21 093826.png>)