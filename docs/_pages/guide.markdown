---
# Feel free to add content and custom Front Matter to this file.
# To modify the layout, see https://jekyllrb.com/docs/themes/#overriding-theme-defaults

layout: default
title: "Home"
vega: true
header_type: hero #base, post, hero,image, splash
header_img: assets/images/header.svg
header_title: "UNLOCKING THE DATA BEHIND A GAME’S SUCCESS"

---


# Main steps to build a website with Jekyll

1. [Use this Jekyll template to create a new project](#1-use-the-jekyll-template-to-create-a-new-project) 
2. [How to edit files in the repository](#2-how-to-edit-files-in-the-repository)
3. [Customize the `_config.yml` file to set up your project details](#3-customize-the-_configyml-file-to-set-up-your-project-details)
4. [Publish the project on GitHub Pages](#4-publish-the-project-on-github-pages)
5. [Create pages](#5-create-pages)
6. [Multimedia content and components](#6-add-multimedia-content-and-components)
7. [Customize the layout and design](#7-customize-the-layout-and-design)
{: .lead }

<br> 

---

## 1. Use the Jekyll template to create a new project

```
├─ 🚀 Start the project using the template
│   ├─ 📥 Clone via “Import repository”
│   ├─ 🏷️ Rename the repo (e.g. g0-2025-website)
│   ├─ 👥 Invite collaborators
│   └─ 🖥️ (Optional) Local development with ruby installed:
│       ├─ 🔧 bundle install
│       └─ 👉 bundle exec jekyll serve → http://127.0.0.1:4000/<repo-name>
```

You can start by cloning the Jekyll template repository for the *Big Data Project Template*.

### Create a new repository using the template

Go to the following link:

```bash
https://github.com/danielefadda/master-projects-template-2025
```

and press on the **Use this template** button in the top right corner of the page and select **Create a new repository**.

![](assets/images/template_to_clone.png)

give it a name based on your project, using the following format:
```bash
g0-2025-website
```
**N.B. you had to substitute `g0` with your group number.**

![](assets/images/new_repo.png)

Leave the visibility of the repository **Public** and click on "Create repository".

Once the repository is cloned, you will find a folder structure similar to the following:


```bash
project-template/docs/
│
├── _config.yml              # basic site settings
├── _data/
│   └── settings.yml         # visual config and textual content (customizable)
├── _pages/
│   ├── index.md             # homepage
│   ├── project.md           # project description
│   ├── team.md              # group members
│   └── deliverables.md      # results (PDF, poster, etc.)
├── assets/
│   └── img/                 # generic images (e.g. placeholder)
├── _includes/               # jekyll components
└── _layouts/                # html layouts
```
**Invite your team members to the repository so they can collaborate on the project.** You can do this by going to the repository settings on GitHub, clicking on "Manage access", and inviting them by their GitHub username or email address. **Remember to add teachers as memebers: `danielefadda` and `Elecapp`**
{: .alert .alert-warning}
<br>

### Local development (optional)

This is an optional step, but if you want to develop the website locally, you need to install Jekyll on your computer. You can find the instructions on how to do it [in the official guide](https://jekyllrb.com/docs/installation/){:target="_blank"} or in our [local development section]({{ site.baseurl }}/local-development/){:target="_blank"}.

For a quick reference we provide these instructions:

Once the repository is cloned, run:

```bash
bundle install
```

Then launch the site with the bundle command:
```bash
bundle exec jekyll serve
```

open your browser at **http://127.0.0.1:4000/<repo-name>**

<br>

---

## 2. How to edit files in the repository

You can edit the files in the repository directly on GitHub.
You have three options to do this:
1. **Edit files directly on GitHub**: Navigate to the file you want to edit, click on the pencil icon in the top right corner, make your changes, and then commit them.
3. **Clone the repository to your local machine**: Use Git to clone the repository to your local machine, make your changes using a text editor or IDE, and then push the changes back to the repository.
2. **Use the GitHub codespace editor**: Click on the green `<> code` button in the top right corner of the window, and open the codespace editor. This allows you to edit files in a more advanced editor directly in your browser, with features like syntax highlighting. Remember to install the necessary extensions for example `Prettier code formatter` to format your code automatically. If you don't see the codespace, you can click on the `Code` button and then select `Create codespace on main` to create a new codespace.

![](assets/images/codespace.png)

![](assets/images/prettier_code.png)



<br>

---


## 3. Customize the `_config.yml` file to set up your project details

```
├─ ⚙️ Customize `_config.yml`
│   ├─ 🏷️ baseurl, url, title, description
│   └─ 🔗 github_repo (footer links)
```

The `_config.yml` file contains the basic settings for your Jekyll site. You can customize it to set up your project details, such as the title, description, author, and other configurations.
All the variables in the `_config.yml` file are used to generate the content of the site and can be accessed in the templates and pages using Liquid syntax. For example, you can use &#123;&#123; site.title &#125;&#125; to access the title of the site. More details on how to edit the file can be found directly in the file itself, where you can find comments explaining each variable.

### General settings

The first thing to do is to set the `baseurl` variable to the name of your repository, for example:

```yaml
baseurl: "/g0-2025-website"
```

You had also to set the `url` variable to the URL of your GitHub Pages site, for example:

```yaml 
url: "https://<username>.github.io"
```

Then, you can customize the following variables:
`title`, `subtitle` and `description` of the site

There are also some variables that can be used to customize the appearance of the site, such as `github_repo`. These variables are used to fill information about the repository in the footer of the site.

<br> 

---

## 4. Publish the project on GitHub Pages

```
├─ 🌐 Publish with GitHub Pages
│   ├─ ⚙️ Go to Settings → Pages
│   ├─ 📂 Select branch + root directory
│   └─ 🚀 Site is live at https://<username>.github.io/<repo>/
```

To deploy your project on GitHub Pages, you can use the following steps:

1. Go to the repository settings on GitHub.
2. Scroll down to the "GitHub Pages" section.
3. **Select the branch `main` and the `docs` folder**.
4. Click "Save" to enable GitHub Pages.
5. Your site will be published at `https://<username>.github.io/<repository-name>/`.

Once you have enabled GitHub Pages, every time you push changes to the selected branch, your site will be automatically updated.

<br>

---

## 5. Create pages

```
├─ 📄 Create and organize pages (`_pages/`)
│   ├─ 🏠 index.md
│   ├─ 📁 project.md
│   ├─ 👥 team.md
│   ├─ 📦 deliverables.md
│   └─ ✏️ Each file: front matter → layout, title, subtitle, vega, header_type, etc.
```

Each Markdown file in the `docs/_pages` directory folder corresponds to a page in the final website. Adding and editing pages can be done directly in the GitHub repository.

To add a page, follow these steps:
- navigate to docs/_pages folder and select **Add file** then **Create new file**
  ![](assets/images/add-page.png)
- Make sure your new file name ends with the file extension `.md` or `.markdown` (for example, `about.md).`
- Your new page is now ready to be edited! I recommend writing a basic front matter to begin with.

The name of the file will be used as the URL of the page. For example, if you create a file called `about.md`, it will be accessible at `https://<username>.github.io/<repository-name>/about/`.

```bash
big-data-project/
│
├── _pages/
│   ├── index.md
│   ├── about.md 
│   ├── team.md 
│   └── technical-report.md  
├── ...
└── README.md
```

### Front Matter

Each page should start with a YAML front matter block that defines the layout and other metadata for the page. 

Front Matter is a section at the beginning of a file containing metadata about the file itself.  
It is delimited by three dashes (`---`) and can include variables such as layout, title, subtitle, cover image, header type, etc.  
This information is used to customize the page content. Variables in the Front Matter are accessible via Liquid variables within the file and are used in templates with the declaration `{{ page.variable-name }}`


For example:

```yaml
---
layout: default
title: "Home"
subtitle: "A template and a guide to develop your Big Data Project website"
...
---
```

### Content

You can use headings, paragraphs, lists (and much more) to structure the content effectively. This can be done using Markdown syntax, which allows for easy formatting of text. For example, you can use **bold** or *italic* text to emphasize key points, and you can create lists to organize information clearly.

This is an example of how to format the text in a way that is visually appealing and easy to read.
In this paragraph we use a `.lead` class to highlight the main points of the project.
{: .lead}

<p class="green"> 
    You can write an entire page using only markdown syntax, but you can also use HTML tags to add more complex elements or <strong>not standard layout</strong>. In this example, we use a paragraph with a class <code>.green</code> to highlight the text in green color.
</p>

This theme is based on Bootstrap, so you can use all the Bootstrap classes to style your content. For example, you can use the `.container` class to create a responsive container, or the `.row` and `.col-*` classes to create a grid layout.

You can find more information about the Bootstrap classes at this page: [Bootstrap Documentation](https://getbootstrap.com/docs/5.3/getting-started/introduction/){:target="_blank"}.

<br>

---

## 6. Add Multimedia content and components

```
├─ 🎥 Multimedia content
│   ├─ 🖼️ Images
│   │     ├─ 📁 folder: assets/images/
│   │     ├─ 📝 use Markdown or `img` tag
│   │     └─ 🖼️ galleries via `masonry.html` + config
│   ├─ 🎬 Videos
│   │     └─ ▶️ embed YouTube using shortcode
│   ├─ 📷 Icons
│   │     └─ 🔍 use Font Awesome icons
│   ├─ 🖼️ Modals
│   │     └─ 🆕 use Bootstrap modals for pop-ups
│   └─ 📈 Charts (Vega-Altair)
│         ├─ 💾 save JSON in assets/charts/
│         ├─ ✅ include `vega: true` in front matter
│         └─ 🔗 shortcode `<vegachart schema-url=...>`
```

### Images
You can add images to your pages using the html `img` tag. To add an image, you had to save the image in the `assets/images` directory and then use the `img` tag or the markdown syntax to embed it in the page. For example:

```markdown
![DR Jekyll](assets/images/Dr_Jekyll.jpg)
``` 

![DR Jekyll](assets/images/Dr_Jekyll.jpg)

### Image Gallery

In this theme there are also some shortcodes that can be used to add images in a gallery format. Save the images in the subdirectory `assets/images/gallery_one` and then use the following syntax to embed them in the page:

{% raw %}
```
{% include_cached snippets/masonry.html internal="gallery_one" %}
```
{% endraw %}



{% raw %}
```html
<div class="container">
{% include_cached snippets/masonry.html internal="charts" %}
</div>
```
{% endraw %}

<div class="container">
{% include_cached snippets/masonry.html internal="charts" %}
</div>

`include_cached snippets/masonry.html` indicates that the `masonry.html` file is included from the `_includes/snippets` directory. The `internal` parameter is used to specify the name of the subdirectory where the images are stored. In this case, the images are stored in the `assets/images/thumb-charts` directory.

Remember to include the `assets/images/thumb-charts` directory in the `_config.yml` file, so that the images are correctly displayed in the gallery. You can do this by adding the following line to the `_config.yml` file:

```yaml
defaults:
  - scope:
      path: "assets/images/thumb-charts"
    values:
      image_col: charts
```

**N.B. pay attention to the indentation of the `yml file` variables, as it is important for the correct functioning of the theme. If you are editing the website locally, restart the service to view changes made in _config.yml**

### Videos

{% include snippets/video.html id="HrEuJO3wz3k" provider="youtube" %}

You can include youtube video using the syntax above, where `id` is the ID of the video and `provider` is the name of the video provider (in this case, `youtube`). You can also use other providers such as `vimeo` or `dailymotion`. The video will be embedded in the page and will be responsive, adapting to the width of the container in which it is placed.

### Icons

To insert icons, you can use [Font Awesome](https://fontawesome.com/search){:target="_blank"}.

```html
<i class="fa-solid fa-pen-nib"></i> To add an icon to text, simply include the corresponding HTML code.
```

<i class="fa-solid fa-pen-nib"></i> A pen

<i class="fa-solid fa-code"></i> A code icon

<i class="fa-solid fa-chart-bar"></i> A chart icon

### Modals
You can also create modals to display additional content or information in a separate window without leaving the current page. Modals are a common UI pattern used to display content in a dialog box that overlays the main content of the page. This theme uses [Bootstrap's modal component](https://getbootstrap.com/docs/4.5/components/modal/){:target="_blank"}, which provides a simple way to create modals with minimal code. To create a modal, you can use the following syntax:

```html
<button type="button" class="btn btn-primary" data-toggle="modal" data-target="#exampleModal">
  Launch demo modal
</button>
<div class="modal fade" id="exampleModal" tabindex="-1" aria-labelledby="exampleModalLabel" aria-hidden="true">
  <div class="modal-dialog modal-xl modal-dialog-centered">
    <div class="modal-content">
      <div class="modal-header">
        <h5 class="modal-title" id="exampleModalLabel">Modal title</h5>
        <button type="button" class="btn-close" data-bs-dismiss="modal" aria-label="Close"><span aria-hidden="true">×</span></button>
      </div>
      <div class="modal-body">
        This is the content of the modal. You can add any HTML content here, including images, text, and other elements.
         You can also use this space to provide additional information about your project, such as the methodology or other technical details.
        </div>
        <div class="modal-footer">
        <button type="button" class="btn btn-secondary" data-dismiss="modal">Close</button>
        </div>
    </div>
    </div>
</div>
```
A button is used to trigger the modal, and the `data-toggle` and `data-target` attributes are used to specify the modal to be opened. The modal itself is defined in a `div` with the class `modal`, and it contains a header, body, and footer. You can add any HTML content you want inside the modal body.

<button type="button" class="btn btn-primary" data-toggle="modal" data-target="#exampleModal">Launch demo modal</button>

This is an alternative version using an image as a trigger for the same modal (same ID):

<div style="border:1px solid #ccc; padding: 10px; margin-bottom: 20px;">
  <img src="{{site.baseurl}}/assets/images/Logo_SoBigData_ITA_560_X_100.png" class="img-fluid" data-toggle="modal" data-target="#exampleModal" style="cursor: pointer">
</div>
<div class="modal fade" id="exampleModal" tabindex="-1" aria-labelledby="exampleModalLabel" aria-hidden="true">
  <div class="modal-dialog modal-xl modal-dialog-centered">
    <div class="modal-content">
      <div class="modal-header">
        <h5 class="modal-title" id="exampleModalLabel">Modal title</h5>
        <button type="button" class="btn-close" data-dismiss="modal" aria-label="Close" style="border:none;"><span aria-hidden="true">×</span></button>
      </div>
      <div class="modal-body">
        This is the content of the modal. You can add any HTML content here, including images, text, and other elements.
        <br> You can also use this space to provide additional information about your project, such as the methodology or other technical details.
        </div>
        <div class="modal-footer">
        <button type="button" class="btn btn-secondary" data-dismiss="modal">Close</button>
        </div>
    </div>
    </div>
</div>

Using the class `modal-xl`, `modal-lg`, or `modal-sm` you can change the size of the modal, which is useful if you want to display a lot of content in the modal. You can also use the `modal-dialog-centered` class to center the modal vertically on the page.

### Charts

🔗 [(See full guide and example for more informations)](charts/)

1. **Create the chart in Altair**  
   Use `width='container'` for responsiveness.
   ```python
   chart = alt.Chart(data).mark_bar().encode(
       x='a:N', y='b:Q'
   ).properties(width='container', height=300)
   chart.save('chart.json')
   ```

2. **Place the file in** `assets/charts/`.

3. **Add this HTML to your page:**

   Specify the height of the chart in the `style` attribute to ensure it displays correctly.
   ```html
   <div style="height: 400px">
     <vegachart schema-url="{{site.baseurl}}/assets/charts/chart.json" style="width: 100%; height: 100%"></vegachart>
   </div>
   ```

4. **In the page front matter**, if not already present, add:
   ```yaml
   vega: true
   ```
   
This is the result:

<div style="height: 400px">
<vegachart schema-url="{{site.baseurl}}/assets/charts/chart_responsive.json" style="width: 100%; height: 100%"></vegachart>
</div>

<br>

---

## 7. Customize the layout and design

```
├─ 🎨 Layout & design
│   ├─ 🧭 Navbar and footer via config and `_includes/`
│   ├─ 🎨 Choose skin (graymor, minty, lux…)
│   ├─ 🖌️ Customize colors via `chulapa-skin.vars`
│   ├─ 🆕 Add Google Fonts (e.g. Lekton)
│   ├─ 🛠️ Add custom CSS in assets/css/custom.scss
│   ├─ 🧩 Header types: hero, base, post, image, splash
│   └─ 🧱 Use helper CSS classes: `.full-width-wrapper`, `.lead`, `.green`, etc.
```

<br>

### Navigation menu
You can customize the navigation menu by editing the `navbar` variable in the `_config.yml` file. This variable is a list of links that will be displayed in the navigation bar of the site. Each link is defined by a `title` and a `url`. You can also create submenus by using the `children` variable, which is a list of links that will be displayed as sub-items of the main link, for example:

```yaml 

navbar:
  style :  dual #don't change this, it is used to set the navbar style.
  brand: # this is the brand of the navbar, it will be displayed on the left side.
    title :  "SoBigData Master's projects Template"
    img: "./assets/images/Logo_masthead.png" # don't change this
    url: /
  nav:
    - title: Guide
      url: /guide.html
    - title: Example page
      url: /example.html
    - title: in-depth
      child:
        - title: Local development
          url: /local-development.html
        - title: Markdown
          url: /markdown.html
        - title: Charts
          url: /charts.html
        - title: Folium
          url: /folium.html
      
```

It's quite easy to add new links or modify existing ones. Just follow the structure of the example above, and you can create a navigation menu that suits your project needs. Please note that the **last item in the navbar** must be the **SoBigData Master link**, as it is used to link to the main website of the SoBigData Master's projects. Last but not least, **check the responsiveness** of the navbar, as it should work well on both desktop and mobile devices.

<br>

### General appearence

After the navigation section, you can find the *General appearence* section, which contains variables that can be used to customize the appearance of the site. You can change the colors, fonts, and other visual aspects of the site. We discuss this in more detail in the custom layout section below.

<br>

### Customizing the theme

To customize the general theme, you can modify the `skin` variable in the `_config.yml` file.  
```yaml
chulapa-skin:
  skin:  "graymor"
```

The list of available themes is as follows:  
`graymor`, `gitdev-dark`, `gitdev`, `universal`, `academia`, `gitdev`, `towards`, `pear`, `twitter-lights-out`, `twitter-dim`, `wandoo`, `lymcha`, `twitter`, `chulapa`, `sunset`, `sunset`, `minty`, `lux`, `journal`, `deeply`.

You can further customize the selected skin by modifying the color variables in the `_config.yml` file.

```yaml
chulapa-skin:
  vars:
    primary-color: "#ff0000"
    body-bg: "#fbf1ed"
```

variables are bootstrap variables that can be used to customize the appearance of the site.
You can change the primary color, body background color, and other variables to match your project's branding. A complete list of bootstrap customizable variables can be found at [this link](https://github.com/dieghernan/chulapa/blob/main/_sass/bootstrap/_variables.scss){:target="_blank"}, while a complete list of the variables used in this theme can be found at [this link](https://dieghernan.github.io/chulapa/docs/variable-dictionary){:target="_blank"}.


<br>


### Header Types
For example, you can use the `hero` layout to create a full-width header with a background image and a title:

```yaml
layout: default
title: "Home"
vega: true
header_type: hero
header_img: assets/images/Jekyll_Logo.png
header_title: "Project Template"
subtitle: "A template and a guide to develop your Big Data Project website"
```

There are several header types available, such as `base`, `post`, `hero`, `image`, and `splash`. 
You can choose the one that best fits your content and use it in the front matter of your page.

<br>

### Fonts

To import fonts different from the theme defaults using _Google Fonts_, you need to add a reference in the `_config.yml` file, which you can obtain from [Google Fonts](https://fonts.google.com/?classification=Monospace){:target="_blank"}:

```yaml
googlefonts:
  - url: "https://fonts.googleapis.com/css2?family=Lekton:ital,wght@0,400;0,700;1,400&display=swap"
```

To set the font across the entire site, add the variables in the `_config.yml` file:

```yaml
chulapa-skin:
  vars:
    headings-font-family: "Lekton"
```

Finally, you can also use fonts in a more targeted way, for example within a single class.  
Open the `assets/css/custom.scss` file to see how the `.comic-neue-regular` class was created, used in the following line:

```html
<div class="comic-neue-regular" style="font-size: 20px; color:purple">
  This is a test to check if I correctly imported the horrible font 
  <span class="comic-neue-bold">Comic Neue</span>
</div>
```

<div class="comic-neue-regular" style="font-size: 20px; color:purple">
  This is a test to check if I correctly imported the horrible font 
  <span class="comic-neue-bold">Comic Neue</span>
</div>

<br>

### Footer

The footer section is defined in the `_includes/footer.html` file. This section should not be modified directly.  
Instead, update the `_config.yml` file with the correct information.  
Specifically, update the following fields:

```yaml
github_repo:
  - name: "Group 0 - Project repository"
    url: "https://github.com/sobigdata-master/progettone-template"
  - name: "Group 0 - Website repository"
    url: "https://github.com/sobigdata-master/progettone-template"
```

Once the fields are updated, edit the `_data/members.yml` file by adding the group members' information.

<br>

### Custom CSS
You can customize the layout and design of your site using CSS. The theme uses Bootstrap, so you can use all the Bootstrap classes to style your content. You can also create your own CSS classes in the `assets/css/custom.scss` file.
For example, you can create a class called `.comic-neue-regular` to use a custom font:

```scss
.comic-neue-regular {
    font-family: 'Comic Neue', sans-serif;
    font-weight: 400;
}
.comic-neue-bold {
    font-family: 'Comic Neue', sans-serif;
    font-weight: 700;
}
```
You can then use this class in your HTML code to apply the custom font to specific elements:

```html
<div class="comic-neue-regular">This is a test to see if I have correctly imported the horrible font <span class="comic-neue-bold">Comic Neue</span></div>
```

<div class="comic-neue-regular">This is a test to see if I have correctly imported the horrible font <span class="comic-neue-bold">Comic Neue</span></div>
<br>

If you want to add a custom CSS to a specific page, you can use the {: .class-name } syntax at the end of the paragraph or element you want to style. For example, you can use the `.lead` class to highlight the main points of the project:

```html
This is an example of how to format the text
{ : .lead }
```

<br>

### The `full-width-wrapper` class

We create a special class to enlarge the width of a column: `full-width-wrapper`. You can use it to create a full-width section that spans the entire width of the page. To do this, you can wrap the content in a `div` with the class `full-width-wrapper`. For example:

```html 
<div class="full-width-wrapper">
    <img src="{{ site.baseurl }}/assets/images/header.svg" alt="sbd-pattern" class="full-width-image">
</div>
```
This will create a full-width section with the specified image.
You can also use the `full-width-wrapper` class to create a full-width section with a background color or an image. For example:


<div class="full-width-wrapper" style="border-top:1px solid; border-bottom: 1px solid;">
    <div class="container">
        <div class="row pt-2 ">
            <div class="col-md-12">
                <h4>Why use and don't use the `full-width-wrapper` class?</h4>
                <p>
                    The <code>full-width-wrapper</code> class is useful when you want to create a section that spans the entire width of the page, such as a section divider or a full-width image. However, you should avoid using it for the whole page as it can lead to a less readable layout, especially on large screens and with a lot of text. Instead, use it for specific sections where you want to create a visual impact or highlight important content or insert a gallery of images or a chart with a lot of details that needs more space to be displayed correctly.
                </p>
            </div>
        </div>
    </div>
</div>

# Recap tree

This is a synthetic overview of the steps seen in this guide:

```
💡 Guide: Building a website with Jekyll
│
├─ 1. 🚀 Use this Jekyll template to create a new project
│   ├─ 📥 Clone via “Import repository”
│   ├─ 🏷️ Rename the repo (e.g. g0-2025-website)
│   ├─ 👥 Invite collaborators
│   └─ 🖥️ (Optional) Local development with ruby installed
│       ├─ 🔧 bundle install
│       └─ 👉 bundle exec jekyll serve → http://127.0.0.1:4000/<repo-name>
│
├─ 2. 📝 How to edit files in the repository
│   ├─ ✏️ Edit on GitHub
│   ├─ 💻 Clone locally
│   └─ 🖥️ Use GitHub Codespaces
│
├─ 3. ⚙️ Customize the `_config.yml` file to set up your project details
│   ├─ 🏷️ baseurl, url, title, description
│   └─ 🔗 github_repo (footer, links)
│
├─ 4. 🌐 Publish the project on GitHub Pages
│   ├─ ⚙️ Go to Settings → Pages
│   ├─ 📂 Select branch + root directory
│   └─ 🚀 Site is live at https://<username>.github.io/<repo>/
│
├─ 5. 📄 Create pages
│   ├─ 🏠 index.md
│   ├─ 📁 project.md
│   ├─ 👥 team.md
│   ├─ 📦 deliverables.md
│   └─ ✏️ Each file: front matter → layout, title, subtitle, vega, header_type, etc.
│
├─ 6. 🎥 Multimedia content
│   ├─ 🖼️ Images
│   │     ├─ 📁 folder: assets/images/
│   │     ├─ 📝 use Markdown or `img` tag
│   │     └─ 🖼️ galleries via `masonry.html` + config
│   ├─ 🎬 Videos
│   │     └─ ▶️ embed YouTube using shortcode
│   ├─ 📷 Icons
│   │     └─ 🔍 use Font Awesome icons
│   ├─ 🖼️ Modals
│   │     └─ 🆕 use Bootstrap modals for popups
│   └─ 📈 Charts (Vega-Altair)
│         ├─ 💾 save JSON in assets/charts/
│         ├─ ✅ include `vega: true` in front matter
│         └─ 🔗 shortcode `<vegachart schema-url=...>`
│
├─ 7. 🎨 Customize the layout and design
│   ├─ 🧭 Navbar and footer via config and `_includes/`
│   ├─ 🎨 Choose skin
│   ├─ 🖌️ Customize colors
│   ├─ 🆕 Add Google Fonts
│   ├─ 🛠️ Add custom CSS
│   ├─ 🧩 Header types
│   └─ 🧱 Use helper CSS classes
│
└─ ✅ Final checklist before release
    ├─ 🔒 Repo and baseurl are correct
    ├─ 📝 Front matter in all pages
    ├─ 🔗 Navbar/footer updated
    ├─ 👥 Team listed in `_data/members.yml`
    └─ 📂 Multimedia assets properly placed
```


This guide provides a comprehensive overview of how to create a website using Jekyll, from setting up the project to customizing the layout and design. By following these steps, you can create a professional-looking website for your Big Data project that is easy to maintain and update.
