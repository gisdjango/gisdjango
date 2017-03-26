---
layout: default
---

# Stworzenie aplikacji

### Wydajemy polecenie w folderze z plikiem manage.py
{% highlight bash %}
$ python manage.py startapp world
{% endhighlight %}

### Modyfikujemy plik konfiguracyjny settings.py

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
    'django.contrib.gis',
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
    'world',
]
{% endhighlight %}

### Po zapisaniu zmian uruchamiamy serwer deweloperski
{% highlight bash %}
$ python manage.py runserver
{% endhighlight %}

### Wysyłamy aplikację world na Gita
{% highlight bash %}
$ git add .
$ git commit -am "Dodanie aplikacji do projektu"
$ git push -u origin master
{% endhighlight %}
