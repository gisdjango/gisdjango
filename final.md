---
layout: default
---

# Wdrożenie projektu

### Modyfikujemy plik gisdjango/settings.py
{% highlight python %}
# SECURITY WARNING: don't run with debug turned on in production!
DEBUG = False

ALLOWED_HOSTS = ['*']
{% endhighlight %}

### Wysyłamy zmiany na Gita
{% highlight bash %}
$ git add .
$ git commit -am "Debug=False"
$ git push
{% endhighlight %}

### Instalacja serwera Apache
{% highlight bash %}
$ sudo su
$ sudo apt-get install apache2 libapache2-mod-wsgi
$ a2enmod wsgi
{% endhighlight %}

### Konfiguracja serwera Apache
{% highlight bash %}
$ nano /etc/apache2/sites-enabled/000-default.conf
{% endhighlight %}

### Modyfikujemy plik 000-default.conf
{% highlight bash %}
WSGIDaemonProcess gisdjango python-path=/var/www/gisdjango
WSGIProcessGroup gisdjango
WSGIScriptAlias / /var/www/gisdjango/gisdjango/wsgi.py

Alias /static /var/www/gisdjango/static
<Directory /var/www/gisdjango/static/>
          Order allow,deny
          Allow from all
</Directory>
{% endhighlight %}

### Pobieramy nasz projekt do katalogu /var/www
{% highlight bash %}
$ cd /var/www
$ git clone link_do_naszego_repozytorium
{% endhighlight %}

### Przygotujmy pliki statyczne
{% highlight bash %}
$ cd gisdjango
$ python manage.py collectstatic
{% endhighlight %}

### Restartujemy serwer Apache
{% highlight bash %}
$ service apache2 restart
{% endhighlight %}
