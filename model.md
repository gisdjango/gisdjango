---
layout: default
---

# Pobranie danych

### Pobranie danych
{% highlight bash %}
$ mkdir world/data
$ cd world/data
$ wget http://thematicmapping.org/downloads/TM_WORLD_BORDERS-0.3.zip
$ unzip TM_WORLD_BORDERS-0.3.zip
$ cd ../..
{% endhighlight %}

### Wygenerowanie modelu
{% highlight bash %}
$ python manage.py ogrinspect \
	world/data/TM_WORLD_BORDERS-0.3.shp \
	WorldBorder --srid=4326 --mapping --multi > model.txt
{% endhighlight %}

# Stworzenie tabeli w bazie

### Modyfikujemy plik world/models.py

#### models.py przed zmianą:
{% highlight python %}
from __future__ import unicode_literals

from django.contrib.db import models
  
# Create your models here.
{% endhighlight %}

#### models.py po zmianie:
{% highlight python %}
from __future__ import unicode_literals

# This is an auto-generated Django model module created by ogrinspect.
from django.contrib.gis.db import models

class WorldBorder(models.Model):
    fips = models.CharField(max_length=2)
    iso2 = models.CharField(max_length=2)
    iso3 = models.CharField(max_length=3)
    un = models.IntegerField()
    name = models.CharField(max_length=50)
    area = models.IntegerField()
    pop2005 = models.BigIntegerField()
    region = models.IntegerField()
    subregion = models.IntegerField()
    lon = models.FloatField()
    lat = models.FloatField()
    geom = models.MultiPolygonField(srid=4326)

    def __unicode__(self):
        return self.name
{% endhighlight %}

### Generujemy zapytanie SQL
{% highlight bash %}
$ python manage.py makemigrations
{% endhighlight %}

### Sprawdzamy jak wygląda wygenerowane zapytanie SQL
{% highlight bash %}
$ python manage.py sqlmigrate world 0001
{% endhighlight %}

### Zapisujemy zmiany w bazie danych
{% highlight bash %}
$ python manage.py migrate
{% endhighlight %}

