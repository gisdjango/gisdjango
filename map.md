---
layout: default
---

# Modyfikujemy plik world/static/map.js
{% highlight js %}
var map = L.map('map');

L.tileLayer('http://{s}.tile.osm.org/{z}/{x}/{y}.png', {
    attribution: '&copy; <a href="http://osm.org/copyright">OpenStreetMap</a> contributors'
}).addTo(map);

var myborder = new L.GeoJSON(border).addTo(map);
map.fitBounds(myborder.getBounds());
{% endhighlight %}
