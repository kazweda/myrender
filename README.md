# myrender

Deploy a Django App on Render

https://docs.render.com/deploy-django#creating-a-new-django-project

## django-environ を使う場合
- settings.py
```py
import environ

env = environ.Env(DEBUG=(bool, False),)
environ.Env.read_env('.env')

DEBUG = env('DEBUG')
SECRET_KEY = env('SECRET_KEY')
ALLOWED_HOSTS = env.list('ALLOWED_HOSTS')
```

## os.environ を使う場合
- settings.py
```py
DEBUG = os.environ.get('DEBUG') == 'True'
SECRET_KEY = os.environ.get('SECRET_KEY', default='your secret key')
ALLOWED_HOSTS = os.environ.get('ALLOWED_HOSTS').split(',')
```

## 環境変数設定ファイル
- .env
```
DEBUG=False
SECRET_KEY=django-secret-key-here
ALLOWED_HOSTS=localhost,127.0.0.1
```

### secret keyについて
https://stackoverflow.com/questions/67240635/django-insecure-in-secret-key-in-settings-py-in-django
> security.W009: Your SECRET_KEY has less than 50 characters,
> less than 5 unique characters, or it’s prefixed with 'django-insecure-'
> indicating that it was generated automatically by Django.
> Please generate a long and random SECRET_KEY,
> otherwise many of Django’s security-critical features
> will be vulnerable to attack.

