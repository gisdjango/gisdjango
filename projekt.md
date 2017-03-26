---
layout: default
---

# Utworzenie i konfiguracja projektu

### Przejście do katalogu użytkownika
{% highlight bash %}
$ cd
{% endhighlight %}

### Utworzenie projektu Django
{% highlight bash %}
$ django-admin startproject gisdjango
{% endhighlight %}

# Konfiguracja projektu
### Poniżej cały czas będziemy modyfikować plik settings.py

#### Sekcja Application definition przed zmianą:
{% highlight python %}
# Application definition

INSTALLED_APPS = [
    'django.contrib.admin',
    'django.contrib.auth',
    'django.contrib.contenttypes',
    'django.contrib.sessions',
    'django.contrib.messages',
    'django.contrib.staticfiles',
]
{% endhighlight %}

#### Sekcja Application definition po zmianie:
{% highlight python %}
# Application definition

INSTALLED_APPS = [
    'django.contrib.admin',
    'django.contrib.auth',
    'django.contrib.contenttypes',
    'django.contrib.sessions',
    'django.contrib.messages',
    'django.contrib.staticfiles',
    'django.contrib.gis',
]
{% endhighlight %}

#### Sekcja Database przed zmianą:
{% highlight python %}
# Database
# https://docs.djangoproject.com/en/1.10/ref/settings/#databases

DATABASES = {
    'default': {
        'ENGINE': 'django.db.backends.sqlite3',
        'NAME': 'os.path.join(BASE_DIR, 'db.sqlite3')',
    }
}
{% endhighlight %}

#### Sekcja Database po zmianie:
{% highlight python %}
# Database
# https://docs.djangoproject.com/en/1.10/ref/settings/#databases

DATABASES = {
   'default': {
        'ENGINE': 'django.contrib.gis.db.backends.postgis',
        'NAME': 'gisdjango',
        'HOST': 'localhost',
        'PORT': '5432',
        'USER': 'geoit',
        'PASSWORD': 'postgres1234'
    }
}
{% endhighlight %}

#### Sekcja Internationalization przed zmianą:
{% highlight python %}
# Internationalization
# https://docs.djangoproject.com/en/1.10/topics/i18n/

LANGUAGE_CODE = 'en-US'

TIME_ZONE = 'UTC'

USE_I18N = True

USE_L10N = True

USE_TZ = True

{% endhighlight %}

#### Sekcja Internationalization po zmianie:
{% highlight python %}
# Internationalization
# https://docs.djangoproject.com/en/1.10/topics/i18n/

LANGUAGE_CODE = 'pl-pl'

TIME_ZONE = 'Europe/Warsaw'

USE_I18N = True

USE_L10N = True

USE_TZ = True
{% endhighlight %}

#### Sekcja Static files przed zmianą:
{% highlight python %}
# Static files (CSS, JavaScript, Images)
# https://docs.djangoproject.com/en/1.10/howto/static-files/

STATIC_URL = '/static/'
{% endhighlight %}

#### Sekcja Static files po zmianie:
{% highlight python %}
# Static files (CSS, JavaScript, Images)
# https://docs.djangoproject.com/en/1.10/howto/static-files/

STATIC_URL = '/static/'

STATIC_ROOT = os.path.join(BASE_DIR, 'static')
{% endhighlight %}

### Po zapisaniu zmian dokonujemy migracji w bazie danych
{% highlight bash %}
$ python manage.py makemigrations
$ python manage.py migrate
{% endhighlight %}

### Uruchamiamy serwer deweloperski
{% highlight bash %}
$ python manage.py runserver
{% endhighlight %}