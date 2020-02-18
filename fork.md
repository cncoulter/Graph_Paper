---
layout: page
permalink: /fork/
title: Forking
---

### `_config.yml`

Your `_config.yml` file is where Jekyll stores the settings that affect your whole blog, so if you're forking Graph Paper to make your own website, you'll probably want to start here.

Some fields in `_config.yml` are labeled as required. For example:

```
title: Graph Paper # Required.
```

If any field is marked as required, make sure you put in some value for it. If it's marked as required, that's because another page (such as `SEO.html`) assumes it's there, so if you leave the field blank, then your SEO settings (for example) will get messed up.

### Images

#### Image Metadata

Store all your images in `/img/`.

For each image, you are required to have an HTML file in the images collection (`/collections/_images/`). The HTML file should look like this:

{% highlight html %}
---
title: notepad-593363_1920.jpg
alt: "graph paper and a pen"
caption: "Image by StartupStockPhotos from Pixabay"
link: https://pixabay.com/photos/notepad-pen-write-plan-office-593363/
---

Image by <a href="https://pixabay.com/users/StartupStockPhotos-690514/?utm_source=link-attribution&amp;utm_medium=referral&amp;utm_campaign=image&amp;utm_content=593363">StartupStockPhotos</a> from <a href="https://pixabay.com/?utm_source=link-attribution&amp;utm_medium=referral&amp;utm_campaign=image&amp;utm_content=593363">Pixabay</a>
{% endhighlight %}

This file stores the image's caption and metadata so that you personally don't need to copy that information every time you use the image.

`title:` stores the picture's name. If the picture is placed in a subfolder (for example, `/img/puppies/`), then make sure to include the subfolder in the title (for example, `title: puppies/dachshund.jpg`).

`alt:` stores the [alt attribute](https://www.w3schools.com/TAGS/att_img_alt.asp). This value should be a string, so make sure you use quotes.

`caption:` stores the caption that will be displayed as tooltip text. Write this has plain text, not HTML. This value should be a string, so make sure you use quotes.

`link:` stores a link to where the image was found online. If the image doesn't have a URL where people can find it online, leave this blank.

Finally, the main text in this file is the caption that will be displayed below the image. As you can see, you're welcome to use HTML here.

## Using Images

### As Featured Images

To set an image as a featured image for a post or page, include this line in the page's YAML preface:

```
image: glenn-carstens-peters-0iB6_GX7BXk-unsplash.jpg
```

Of course, you'll want to update the path to lead to where your image is stored. If the picture is placed in a subfolder (for example, `/img/puppies/`), then make sure to include the subfolder (for example, `image: puppies/dachshund.jpg`)

### On a Page

If you want to use an image on a page or in a post without labeling it as the featured image, simply copy and paste the below code. Make sure you replace `image-title.jpg` with your image's title.

{% highlight html %}
{% raw  %}{% assign image_title = "image-title.jpg" %}
{% assign image = site.images | where: 'title', image_title | first %}{% endraw %}
<figure class="figure">
    <img src="{{ site.baseurl }}/img/{{ image.title }}" class="figure-img img-fluid" alt="{{ image.alt }}" title="{{ image.caption }}">
    <figcaption class="figure-caption text-muted font-weight-light small">{{ image.content }}</figcaption>
</figure>
{% endhighlight %}

### Multiple Authors

* general support
* RSS feeds
