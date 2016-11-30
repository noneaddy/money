Install psycopg2

`pip install psycopg2`

Go to `MobSF\settings.py`

Comment the following

```
DATABASES = {
    'default': {
        'ENGINE': 'django.db.backends.sqlite3',
        'NAME': DB_DIR,
    }
}
```

Now uncomment the following

```
DATABASES = {
    'default': {
        'ENGINE': 'django.db.backends.postgresql_psycopg2',
        'NAME': 'mobsf',
        'USER': 'postgres',
        'PASSWORD': '',
        'HOST': 'localhost',
        'PORT': '',
    }
}
```

Create a database in Postgres named **mobsf** and configure the above settings with correct username, password and other details.

Apply Migrations

`python manage.py makemigrations`

`python manage.py migrate`

Now you can start MobSF server and you have successfully configured Postgres as your database.