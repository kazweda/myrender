# myrender

Deploy a Django App on Render

https://docs.render.com/deploy-django#creating-a-new-django-project

## django-environを使う場合
- settings.py
```py
import environ

env = environ.Env(DEBUG=(bool, False),)
environ.Env.read_env('.env')

DEBUG = env('DEBUG')
SECRET_KEY = env('SECRET_KEY')
ALLOWED_HOSTS = env.list('ALLOWED_HOSTS')
```
- .env
```
DEBUG=False
SECRET_KEY=django-secret-key-here
ALLOWED_HOSTS=localhost,127.0.0.1
```
