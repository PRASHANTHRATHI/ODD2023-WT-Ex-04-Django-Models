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

![Alt text](<Screenshot 2023-11-21 091701.png>)

add the models in the admin interface using the code admin.py

![Alt text](<Screenshot 2023-11-21 091740.png>)

write the function based view to render the data from the models to the template in views.py

![Alt text](<Screenshot 2023-11-21 091748.png>)

set up the url path for the templates using urls.py

![Alt text](<Screenshot 2023-11-21 091807.png>)

in settings.py file add the appcreated

step3: Now do the migrations process to initiate and save the models
python manage.py makemigrations python manage.py migrate create a template as user_profile.html

![Alt text](<Screenshot 2023-11-21 093222.png>)

step 4: Run the program using the following command

python manage.py runserver 8000 in the admin page you can view the models created and in the user_profile template page you can see the profile page of the user

# OUTPUT
![Alt text](<Screenshot 2023-11-21 090533.png>)

![Alt text](<Screenshot 2023-11-21 093826.png>)