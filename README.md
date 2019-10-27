# django-heroku-deploy
The simplest way to deploy your django app in the heroku sky.


Deploying in heroku is super easy now. I have almost 10 running applications surve by heroku.
Here is the most simplified steps that i did follow everytime.

Step 1. 
Create a Procfile in your project root(linux: touch Procfile)
add this inside the Procfile.

`web: gunicorn project_name.wsgi`

Step 2. 
Add this in your app/settings.py
```
# add this under import os
import django_heroku 
# Then all the way at the bottom of the file
# ... 
django_heroku.settings(locals())
```

step-3:
add this in your requirements.txt:
```
django
gunicorn
django-heroku
psycopg2
psycopg2-binary
```

** `psycopg2` will be need for postgres db setup in production.

step-4:
login to your heroku cli
`heroku login`

step-5:
create new app if one doesn't yet exist
`heroku create my-app-name`

step-6:
create a new postgres database for your app
`heroku addons:create heroku-postgresql:hobby-dev`

step-7: 
run: `./manage.py makemigrations`
you need to send migration files to heroku before migrate it there.

step-8:
```
git add .
git commit -m "My application gonna fly in the heroku sky"
pit push heroku master
```

step-9:
After successfull deploy, run: `heroku run python manage.py migrate`

step-10: 
create super-admin:
`heroku run python manage.py createsuperuser`

Here you go. Your app is live now. Yaaaayy....

If you got something helpful here hit on the `star` button for this project.
And if there has any issue with your deploying, feel free to Create an Issue. Cheers!

