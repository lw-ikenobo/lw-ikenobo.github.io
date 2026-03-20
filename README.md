---
title: "README"
layout: default
permalink: /README
---

# Ikenobo Lake Washington Chapter Website

This is the website for the [Ikenobo Lake Washington Chapter](lw-ikenobo.github.io) of the Ikenobo Ikebana Society.
It is built with [Jekyll](https://jekyllrb.com/) and hosted on GitHub Pages.

The repository of this website is at [github.com/lw-ikenobo/lw-ikenobo.github.io](https://github.com/lw-ikenobo/lw-ikenobo.github.io) and is maintained by [lw-ikenobo](github.com/lw-ikenobo) GitHub Organization.

The older version of the site is located at [www.ikenobolakewashingtonchapter.com](http://www.ikenobolakewashingtonchapter.com).
We are currently in the process of migration of the old site from Weebly to this GitHub-based site.

## Directory Structure

```
/
├── index.md                 ← Home page
├── Gallery/                 ← Exhibition photo galleries
│   ├── index.md             ← Gallery listing page (auto-generated tiles)
│   └── 2024-09-01.Kirkland_Exhibition/
│       ├── index.md         ← Page text and gallery include
│       ├── photo1.jpg       ← Photos displayed automatically
│       └── photo2.jpg
├── Chapter_Activity/        ← Chapter event pages
│   ├── index.md             ← Chapter Activity listing page (auto-generated tiles)
│   └── 2017-06-01.Professor_Chino_Workshop/
│       ├── index.md
│       └── img-0949.jpg
├── Ikenobo_Ikebana.md       ← About Ikenobo Ikebana
├── Ikenobo_Styles/           ← Ikebana style descriptions
├── Lessons.md                ← Lesson information
├── Contact.md                ← Contact page
├── Calendar.md               ← Calendar page
├── _config.yml               ← Jekyll site configuration
├── _layouts/                 ← Page layout templates
├── _includes/                ← Reusable page components
│   ├── gallery.html          ← Displays all images in a page's folder
│   ├── gallery_grid.html     ← Generates the tile grid for listing pages
│   └── pptx_embed.html       ← Embeds a PowerPoint file preview
├── images/                   ← Shared images (logo, etc.)
└── style.css                 ← Site stylesheet
```

## How Pages Work

The **Gallery** and **Chapter Activity** sections share the same structure:

- The **listing page** (`Gallery/index.md` or `Chapter_Activity/index.md`) automatically shows a tile for every sub-folder. Each tile displays a thumbnail from the first image found in that folder. You never need to edit the listing page when adding new content.

- Each **leaf page** (a sub-folder with its own `index.md`) represents one event. Photos placed in the folder are automatically displayed on the page.

## Adding a New Gallery or Chapter Activity Page

### Step 1: Create the folder

Create a new folder inside `Gallery/` or `Chapter_Activity/`. Use this naming pattern:

```
YYYY-MM-DD.Short_Description
```

For example:
```
Gallery/2025-10-01.Fall_Exhibition/
Chapter_Activity/2025-06-01.Summer_Workshop/
```

The date at the beginning determines the display order on the listing page (newest first). Use underscores instead of spaces in the description.

### Step 2: Add photos

Copy your `.jpg`, `.png`, or other image files directly into the new folder. There is no limit on the number of photos. They will all be displayed automatically on the page.

### Step 3: Create the index.md file

Create a file called `index.md` inside your new folder. Here is a template you can copy and modify:

{% raw %}
```markdown
---
title: "October 2025 Fall Exhibition"
layout: default
---

# October 2025 Fall Exhibition

A short description of the event goes here.

{% include gallery.html %}
```
{% endraw %}

The three important parts are:

1. **The header** (between the `---` lines): Set the `title` to the name of your event. Always keep `layout: default`.

2. **The description**: Write a heading (`#`) and optionally a short paragraph about the event.

3. **`{% raw %}{% include gallery.html %}{% endraw %}`**: This single line automatically displays all the photos in the folder. You do not need to list individual photos.

### Step 4: Commit and push

```
git add Gallery/2025-10-01.Fall_Exhibition/
git commit -m "Add October 2025 Fall Exhibition photos"
git push
```

The website will update automatically after you push.

## Alternative Page Types

### Flickr Album Page

If your photos are hosted on Flickr instead of in the folder, use a Flickr embed instead of `{% raw %}{% include gallery.html %}{% endraw %}`:

{% raw %}
```markdown
---
title: "May 2024 Workshop with Visiting Professor Noritaka Noda"
layout: default
---

# May 2024 Workshop with Visiting Professor Noritaka Noda

<a data-flickr-embed="true" href="https://www.flickr.com/photos/YOUR_ACCOUNT/albums/ALBUM_ID" title="Album Title">
  <img src="https://live.staticflickr.com/65535/PHOTO_ID.jpg" width="1600" height="1200" alt="Album Title"/>
</a>
<script async src="//embedr.flickr.com/assets/client-code.js" charset="utf-8"></script>

[View full album on Flickr](https://www.flickr.com/photos/YOUR_ACCOUNT/albums/ALBUM_ID)
```
{% endraw %}

To get the embed code from Flickr:

1. Open your Flickr album page in a browser.
2. Click the **Share** button.
3. Select the **Embed** tab and chose "Large (1600 x 1200)" with no header or footer.
4. Copy the HTML code that Flickr shows you.
5. Paste it into your `index.md` file in place of the example code above.

### PowerPoint Presentation Page

To embed a PowerPoint file, place the `.pptx` file in the folder and use the PowerPoint embed include:

{% raw %}
```markdown
---
title: "Event Presentation"
layout: default
---

# Event Presentation

Description of the presentation.

{% include pptx_embed.html file="my_presentation.pptx" %}
```
{% endraw %}

This shows an interactive preview of the PowerPoint file in the browser, plus a download link.

## Running the Site Locally

To preview the site on your computer before pushing changes:

```
./run.sh
```

Then open your browser to the address shown (usually `http://localhost:4000`). The preview updates automatically when you save changes to files.

Note that the script requires Docker to be installed on your machine and runs Jekyll in a Docker container.
