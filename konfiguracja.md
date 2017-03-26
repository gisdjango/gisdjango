---
layout: default
---

# Konfiguracja środowiska

### Wejście na konto administratora
{% highlight bash %}
# Hasło: geoit
$ sudo su
{% endhighlight %}

### Aktualizacja pakietów
{% highlight bash %}
$ apt-get update && apt-get upgrade
{% endhighlight %}

### Instalacja Django
{% highlight bash %}
$ apt-get install python-dev python-pip 
$ apt-get install python-django
$ pip install -U Django
{% endhighlight %}

### Instalacja PostgreSQL + PostGIS
{% highlight bash %}
$ apt-get install postgresql postgis
$ apt-get install libpq-dev python-psycopg2
$ apt-get install pgadmin3
{% endhighlight %}

### Instalacja bibliotek GIS
{% highlight bash %}
$ apt-get install binutils libproj-dev
$ apt-get install gdal-bin python-gdal
{% endhighlight %}

### Instalacja edytora oraz przeglądarki
{% highlight bash %}
$ apt-get install idle 
$ apt-get install chromium-browser
{% endhighlight %}

### Instalacja Gita
{% highlight bash %}
$ apt-get install git
{% endhighlight %}

### Konfiguracja Gita
{% highlight bash %}
$ git config --global user.email "adres_email"
$ git config --global user.name "nazwa_uzytkownika"
{% endhighlight %}
