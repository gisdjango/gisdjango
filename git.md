---
layout: default
---

# Dodanie projektu do repozytorium

### Przechodzimy do głównego folderu projektu
{% highlight bash %}
$ cd ~/gisdjango
{% endhighlight %}

### Tworzymy plik tekstowy .gitignore
{% highlight bash %}
# Do pliku wklejamy zawartość ze strony gitignore.io
{% endhighlight %}

### Tworzymy lokalne repozytorium
{% highlight bash %}
$ git init
{% endhighlight %}

### Dodajemy nasze pliki
{% highlight bash %}
$ git add .
$ git commit -am "Konfiguracja projektu"
{% endhighlight %}

### Ustawiamy zdalne repozytorium
{% highlight bash %}
# na stronie github.com klikamy New repository
$ git remote add origin link_do_repozytorium
{% endhighlight %}

### Wysyłamy zmiany na Gita
{% highlight bash %}
$ git push -u origin master
{% endhighlight %}
