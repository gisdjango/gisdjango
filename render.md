---
layout: default
---

# Nasz pierwszy widok

### Modyfikujemy plik world/views.py
{% highlight python %}
from django.shortcuts import render

# Create your views here.

def index(request):
    return render(request, 'world/index.html')
{% endhighlight %}

### Tworzymy plik world/urls.py
{% highlight python %}
from django.conf.urls import url

from . import views

urlpatterns = [
	url(r'^$', views.index, name='index'),
]
{% endhighlight %}

### Modyfikujemy plik gisdjango/urls.py
{% highlight python %}
from django.conf.urls import url, include
from django.contrib.gis import admin

urlpatterns = [
    url(r'^world/', include('world.urls')),
    url(r'^admin/', admin.site.urls)
]
{% endhighlight %}

### Sprawdzamy efekty naszej pracy
{% highlight bash %}
$ python manage.py runserver
{% endhighlight %}

