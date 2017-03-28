---
layout: default
---

# Tworzymy uniwersalny widok

### Modyfikujemy plik world/views.py:
{% highlight python %}
from django.shortcuts import render
from .models import WorldBorder
from django.core.serializers import serialize

# Create your views here.

def index(request, fips):
    border = WorldBorder.objects.filter(fips=fips.upper())
    fields=('name', 'area', 'pop2005', 'region', 'subregion', 'lon', 'lat', )
    geojson = serialize('geojson', border, geometry_field='geom', fields=fields)
    return render(request, 'world/index.html', { 'border': geojson })
{% endhighlight %}


### Modyfikujemy plik world/urls.py:
{% highlight python %}
from django.conf.urls import url

from . import views

urlpatterns = [
	url(r'^(?P<fips>\w+)$', views.index, name='index'),
]
{% endhighlight %}

### Modyfikujemy plik world/templates/index.html:
{% highlight html %}
<!DOCTYPE html>
<html lang="pl">
  <head>
    <meta charset="utf-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1">
    <title>World</title>
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/leaflet/1.0.3/leaflet.css" />
    <% load static %>
	<link rel="stylesheet" href="<% static 'world/style.css' %>" />
	<script>var border = {{ border|safe }};</script>
  </head>
  <body>
  	<div id="map"></div>
  	<script src="https://cdnjs.cloudflare.com/ajax/libs/leaflet/1.0.3/leaflet.js"></script>
  	<script src="<% static 'world/map.js' %>" /></script>
  </body>
</html>
{% endhighlight %}

### Sprawdzamy czy dane są dostępne na stronie
{% highlight bash %}
 $ python manage.py runserver
{% endhighlight %}
