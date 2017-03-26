---
layout: default
---

# Dodanie panelu administratora

### Poniżej cały czas będziemy modyfikować plik world/admin.py

#### Plik admin.py przed zmianą:
{% highlight python %}
from django.contrib import admin

# Register your models here.
{% endhighlight %}

#### Plik admin.py po zmianie:
{% highlight python %}
from django.contrib.gis import admin
from .models import WorldBorder

admin.site.register(WorldBorder, admin.GeoModelAdmin)
{% endhighlight %}

### Zaglądamy do panelu administratora
{% highlight bash %}
$ python manage.py runserver
{% endhighlight %}

### Wysyłamy zmiany na Gita
{% highlight bash %}
$ git add .
$ git commit -am "Importowanie danych"
$ git push
{% endhighlight %}
