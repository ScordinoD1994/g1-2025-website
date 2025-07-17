---
layout: default
title:  "Folium Map"
subtitle: "How to incorporate a map created with Folium"
header_type: hero #base, post, hero,image, splash
header_img: assets/images/folium_map.webp
header_title: "Folium maps"
vega: false
---
This page explains how to incorporate a map created with Folium into a web page. Folium is a Python library that allows you to create interactive maps using Leaflet.js. To incorporate a map created with Folium into a web page, you need to save the map to an `.html` file and include it in the web page.
<br>
## Incorporating a map created with Folium into a web page
To incorporate a map created with Folium into a web page, you need to follow these steps:
- Create a map with Folium
- Save the map to an `.html` file
- Include the `.html` file in the web page
    - Use the `iframe` tag to embed the `.html` file in the web page
    - Specify the path of the `.html` file as the value of the `src` attribute of the `iframe` tag
    - Specify the map dimensions using the `width` and `height` attributes of the `iframe` tag
    - Example HTML code to incorporate a map created with Folium into a web page:
    
```<iframe src="{{site.baseurl}}/assets/charts/map.html" width="100%" height="500"></iframe>```

<iframe src="{{site.baseurl}}/assets/charts/usa.html" width="100%" height="500px" ></iframe>

**Note that the map created with Folium was exported with width and height set to 100%.**
You can adjust the map dimensions by modifying the values of the `width` and `height` attributes of the `iframe` tag.