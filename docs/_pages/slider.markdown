---
layout: default
title: "Slider Page"
header_type: hero
header_img: assets/images/sliding_dog.jpg
header_title: "Slider Component Page"
subtitle: "An Example Page for the Slider Component"
---

# Slider Component Example
This page demonstrates the use of the slider component in the SoBigData Big Data Project Template. The slider allows users to navigate through different sections or content dynamically.

{% include slider.html data="sliders" label="Choose a carousel" %}

---

{% raw %}
```
{% include slider.html data="sliders" label="Choose a carousel" %}
```
{% endraw %}

Through this component, you can load different content dynamically, starting from a yml file (in this case: `sliders.yml`) that contains the data for the slider. The slider can be used to showcase images, text, or any other content that fits within the carousel format. This component allows for easy updates and changes to the content without modifying the HTML structure.

In case you have more than one slider, you had to specify the `label` parameter to provide a descriptive label for the slider selector, enhancing the user experience by making it clear what the slider is for.

The structure of the yml file is the following:

```yaml 
sliders:
  - id: slider1
    title: "Slider 1"
    items:
      - image: "assets/images/slider1_image1.jpg"
        caption: "Caption for Image 1"
      - image: "assets/images/slider1_image2.jpg"
        caption: "Caption for Image 2"
  - id: slider2
    title: "Slider 2"
    items:
      - image: "assets/images/slider2_image1.jpg"
        caption: "Caption for Image 3"
      - image: "assets/images/slider2_image2.jpg"
        caption: "Caption for Image 4"
```