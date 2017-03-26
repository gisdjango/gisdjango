---
layout: default
---

# Utworzenie bazy danych

### Wejście na konto postgres
{% highlight bash %}
$ su postgres
{% endhighlight %}

### Wejście do konsoli psql
{% highlight bash %}
$ psql
{% endhighlight %}

### Dodanie użytkownika PostgreSQL
{% highlight psql %}
# CREATE USER geoit WITH PASSWORD 'postgres1234';
{% endhighlight %}

### Rozłączanie z psql
{% highlight psql %}
# \q
{% endhighlight %}

### Stworzenie bazy danych
{% highlight bash %}
$ createdb -E utf-8 -O geoit gisdjango
{% endhighlight %}

### Zalogowanie się do utworzonej bazy
{% highlight bash %}
$ psql -d gisdjango
{% endhighlight %}

### Dodanie rozszerzenia PostGIS
{% highlight psql %}
# CREATE EXTENSION postgis;
{% endhighlight %}

### Ustawienie domyślnego schematu
{% highlight psql %}
# ALTER DATABASE gisdjango SET SEARCH_PATH TO 'public';
{% endhighlight %}

### Wyjście kolejno z psql, postgres, su
{% highlight psql %}
# \q
{% endhighlight %}
{% highlight bash %}
$ exit
$ exit
{% endhighlight %}
