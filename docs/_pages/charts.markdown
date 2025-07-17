---
# Feel free to add content and custom Front Matter to this file.
# To modify the layout, see https://jekyllrb.com/docs/themes/#overriding-theme-defaults

layout: default
title: "Charts"
vega: true

header_type: hero #base, post, hero,image, splash
header_img: assets/images/altair-gallery.png
header_title: "Altair Charts"
subtitle: "How to embed Altair charts in your Jekyll pages"
---

You can add charts to your pages using the `vegachart` tag. To embed a chart you had to save the chart as a json file in the `assets/charts` directory and then use the `vegachart` tag to embed it in the page. 

# From Python to the Web

Altair is a data visualization library for Python, based on Vega and Vega-Lite. This means that Altair generates Vega-Lite specifications, which are then converted into Vega specifications and finally into charts viewable in a web browser. To embed an Altair chart in a web page, you need to convert the Vega-Lite specification into a JSON object and save it as a `.json` file.

The procedure in `altair` to save the Vega-Lite specification as a `.json` file is as follows:

Given any `altair` `chart`:
```python
# Example data
data = pd.DataFrame({
    'a': ['A', 'B', 'C', 'D', 'E'],
    'b': [28, 55, 43, 91, 81]
})
```
If you want to make the chart responsive, when saving the `.json` file you can specify the property `width='container'`.
```python
# Create the chart
chart = alt.Chart(data).mark_bar().encode(
    x='a:N',
    y='b:Q'
).properties(
    width='container',
    height=300 
)

# Save the chart as a JSON file
chart_json = chart.to_json()
with open('chart.json', 'w') as f:
    f.write(chart_json)
```
> [Link to the Colab Notebook with the example above](https://colab.research.google.com/drive/1ySTEzV2se1buHZ7X5p2fX5RlDUXyAfaX?usp=sharing)

The `chart.json` file can then be used in a web page to display the chart. To do this, you can use the Jekyll `vegachart` tag, specifying the path to the `.json` file as the value of the `schema-url` attribute.
{% raw %}
```html
<div style="height: 400px">
<vegachart schema-url="{{site.baseurl}}/assets/charts/chart_responsive.json" style="width: 100%; height: 100%"></vegachart>
</div>
```
{% endraw %}

This theme has been customized to support Vega charts without complications: if the page where you want to display the chart has `vega: true` in the front matter, the `vegachart` tag will be interpreted and the chart will be displayed correctly.
`vega: true` is a variable that tells the page to load the Vega plugin.
In this way, the chart will be displayed responsively, adapting to the width of the container in which it is placed.

# Example of embedding a chart created with Altair

<div style="height: 400px">
<vegachart schema-url="{{site.baseurl}}/assets/charts/chart_responsive.json" style="width: 100%; height: 100%"></vegachart>
</div>

- The chart was saved as `chart_responsive.json` and placed in the `assets/charts` folder.
- If you try to display the chart in a web page without specifying the property `width='container'`, the chart will not be responsive and will be displayed with a fixed width.
- If you try to display the chart in a Jupyter notebook, the chart will not be visible because the `width='container'` property is not supported in that environment. In this case, you can specify a fixed width in pixels and change the width property only during export.
