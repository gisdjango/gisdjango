---
layout: default
---

# Stworzenie plików statycznych

### Tworzymy katalog dla plików html
{% highlight bash %}
$ mkdir -p world/templates/world
{% endhighlight %}

### W utworzonym katalogu tworzymy plik index.html:
{% highlight html %}
<!DOCTYPE html>
<html lang="pl">
  <head>
    <meta charset="utf-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1">
    <title>World</title>
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/leaflet/1.0.3/leaflet.css" />
  </head>
  <body>
  	<div id="map"></div>
  	<script src="https://cdnjs.cloudflare.com/ajax/libs/leaflet/1.0.3/leaflet.js"></script>
  </body>
</html>
{% endhighlight %}

### Tworzymy katalog dla plików statycznych
{% highlight bash %}
$ mkdir -p world/static/world
{% endhighlight %}

### W utworzonym katalogu tworzymy plik style.css:
{% highlight css %}
html, body, .map {
	padding: 0;
	margin: 0;
	width: 100%;
	height: 100%;
}
{% endhighlight %}

### W tym samym katalogu tworzymy plik map.js:
{% highlight js %}
var map = L.map('map').setView([51.505, -0.09], 13);

L.tileLayer('http://{s}.tile.osm.org/{z}/{x}/{y}.png', {
    attribution: '&copy; <a href="http://osm.org/copyright">OpenStreetMap</a> contributors'
}).addTo(map);
{% endhighlight %}

### Dodajemy pliki statyczne do naszego pliku html
{% highlight html %}
<!DOCTYPE html>
<html lang="pl">
  <head>
    <meta charset="utf-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1">
    <title>World</title>
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/leaflet/1.0.3/leaflet.css" />
    tag load static tag
	<link rel="stylesheet" href="tag static 'world/style.css' tag" />
  </head>
  <body>
  	<div id="map"></div>
  	<script src="https://cdnjs.cloudflare.com/ajax/libs/leaflet/1.0.3/leaflet.js"></script>
  	<script src="tag static 'world/map.js' tag" /></script>
  </body>
</html>
{% endhighlight %}
