---
layout: fork
permalink: /fork/
title: Fork
---

# Initial Setup

## Jekyll

First, install [Jekyll](https://jekyllrb.com/docs/).

Next, you'll need to install the following Ruby gems: `jekyll-paginate jekyll-redirect-from jekyll-sitemap`

```
$ gem install jekyll-paginate jekyll-redirect-from jekyll-sitemap
```

## Git

Make sure you have [Git](https://git-scm.com/) installed. Then, clone this project:

```
$ git clone https://github.com/cncoulter/graph-paper/
```

## Configuration

Your `_config.yml` file is where Jekyll stores the settings that affect your whole blog, so if you're forking Graph Paper to make your own website, start by updating `_config.yml`.

Some fields in `_config.yml` are labeled as required. For example:

```
title: Graph Paper # Required.
```

If any field is marked as required, make sure you put in some value for it. If it's marked as required, that's because another page (such as `SEO.html`) assumes it's there, so if you leave the field blank, then your SEO settings (for example) will get messed up.

---

# Multiple Authors

Graph Paper is designed to support [multiple authors]({{ site.baseurl }}/people/). Once you set up a new author, it's easy to mark them as a post's author and have their bio automatically included below the post. Graph Paper will also display links to an author's website, email, and social media profiles, and you can also set up an personal [Atom feed](https://en.wikipedia.org/wiki/Atom_(Web_standard)) for each author that shares their posts. Additionally, each author gets [their own page]({{ site.baseurl }}/people/Lorri-Ipsum) which displays their bio, links, photo, and posts.
For all of this to work smoothly, however, it does take a little bit of work to set up a new author.

Graph Paper stores info about authors within a [collection](https://jekyllrb.com/docs/collections/), so each author should have their own file under `collections/_people/`.

Whatever you title that file will be the URL for the author's page. For example, Lorri Ipsum's file is named `Lorri Ipsum.md`, so the URL for her page is [https://graphpaper.cncoulter.com/people/Lorri-Ipsum/](https://graphpaper.cncoulter.com/people/Lorri-Ipsum/). If we titled her page `lorri.md`, then the URL for her page would be [https://graphpaper.cncoulter.com/people/lorri/](https://graphpaper.cncoulter.com/people/lorri/).

The content of their file should be their bio (in Markdown), and the YAML frontmatter stores their info. For example, here's `collections/_people/Lorri Ipsum.md`:

```
---
layout: people
title: Lorri Ipsum
code_name: lorri
photo: lorri.jpg
website: https://unsplash.com/photos/qO-PIF84Vxg
facebook: tk
instagram: tk
twitter: tk
tumblr: tk
patreon: tk
youtube: tk
spotify: tk
bandcamp: tk
linkedin: tk
github: tk
email: tk
feed: yes
---

Lorem ipsum dolor sit amet, consectetur adipiscing elit. Morbi volutpat ac ligula maximus commodo. Donec mollis finibus cursus. Phasellus at tortor sit amet odio eleifend finibus. Sed gravida ante a est porttitor volutpat. Aliquam sollicitudin sem sed lobortis vehicula. Sed varius leo vitae velit vulputate, nec laoreet lorem semper. Fusce sit amet nunc rutrum tellus egestas varius. Sed ultrices consequat turpis, a varius quam sodales id. Pellentesque vestibulum aliquam magna vitae egestas. Fusce sagittis enim mauris, vitae interdum urna commodo a.
```

`layout` should be `people`, and `title` should be the person's name as you want it to appear on site. `photo` should be the filename for a picture of the person. The picture should be stored in `img/`.

`code_name` is a shorthand used in the YAML frontmatter of blog posts to refer to the author. For example, Lorri Ipsum's code_name is `lorri`, so blog posts written by Lorri include this line in the YAML frontmatter:

```
author: lorri
```

`website` through `feed` are all optional. If you include text there, it'll show up as links displayed below the author's bio. You only need to include the handle. For example, if Lorri's Twitter profile is [https://twitter.com/getbootstrap](https://twitter.com/getbootstrap), then Lorri's frontmatter should be:

```
twitter: getbootstrap
```

Finally, do you want the author to have their own individual [Atom feed](https://en.wikipedia.org/wiki/Atom_(Web_standard))? If so include:

```
feed: yes
```

That will include a link to the author's Atom feed, but *it won't set up* an Atom feed. To set one up, add a folder to `people/`. Title the new folder with the author's display name (using hyphens instead of spaces). For example, for Cam Coulter, create `people/Cam-Coulter/`. Then, copy `people/Lorri-Ipsum/feed.xml` to the new author's folder. For example:

```
$ cp ./people/Lorri-Ipsum/feed.xml ./people/Cam-Coulter/feed.xml
```

Finally, open the new file and in line seven, change "lorri" to the new author's code_name.

Now, your new author is all set up with their own [author page]({{ site.baseurl }}/people/Lorri-Ipsum/) and their own personal [Atom feed]({{ site.baseurl }}/people/Lorri-Ipsum/feed.xml)!

---

# Images

Like with authors, it takes a little work to set up images in Graph Paper. However, once you get it set up, it's easy to include featured images with blog posts that display on the post itself, on archive pages, and when shared on social media (through Twitter card support --- see `_includes/SEO.html`).

Additionally, if you want to add an image anywhere else in the site, just use the following line of code to add the image as a [responsive image](https://getbootstrap.com/docs/4.4/content/images/#responsive-images) with a [caption](https://getbootstrap.com/docs/4.4/content/figures/).

{% raw %}
```
{% include image.html file="glenn-carstens-peters-0iB6_GX7BXk-unsplash.jpg" %}
```
{% endraw %}

(The above line of code produces the picture below.)

{% include image.html file="glenn-carstens-peters-0iB6_GX7BXk-unsplash.jpg" %}

## Image Metadata

You should store all of your images in `img/`.

Graph Paper stores image metadata and captions within a [collection](https://jekyllrb.com/docs/collections/). For each image, you are required to have an HTML file in the images collection (`/collections/_images/`). This file stores the image's caption and metadata so that you personally don't need to copy that information every time you use the image. The caption in the above photo is pulled from `collections/_images/glenn-carstens-peters-0iB6_GX7BXk-unsplash.html`. As you can see in this example, give the image itself and its metadata file the same filename (just change the extension). Neither the image itself nor its metadata file should include spaces in its filename.

The HTML file should look like this:

{% highlight html %}
---
title: notepad-593363_1920.jpg
alt: "graph paper and a pen"
caption: "Image by StartupStockPhotos from Pixabay"
link: https://pixabay.com/photos/notepad-pen-write-plan-office-593363/
---

Image by <a href="https://pixabay.com/users/StartupStockPhotos-690514/?utm_source=link-attribution&amp;utm_medium=referral&amp;utm_campaign=image&amp;utm_content=593363">StartupStockPhotos</a> from <a href="https://pixabay.com/?utm_source=link-attribution&amp;utm_medium=referral&amp;utm_campaign=image&amp;utm_content=593363">Pixabay</a>
{% endhighlight %}

`title:` stores the picture's name. If the picture is placed in a subfolder (for example, `/img/puppies/`), then make sure to include the subfolder in the title (for example, `title: puppies/dachshund.jpg`).

`alt:` stores the [alt attribute](https://www.w3schools.com/TAGS/att_img_alt.asp). This value should be a string, so make sure you use quotes.

`caption:` stores the caption that will be displayed as tooltip text. Write this has plain text, not HTML. This value should be a string, so make sure you use quotes.

`link:` stores a link to where the image was found online. If the image doesn't have a URL where people can find it online, leave this blank.

Finally, the main text in this file is the caption that will be displayed below the image. As you can see, you can use HTML to add links or particular formatting to the caption.

## Using Images

### As Featured Images

To set an image as a featured image for a post or page, include this line in the page's YAML preface:

```
image: glenn-carstens-peters-0iB6_GX7BXk-unsplash.jpg
```

Of course, you'll want to update the path to lead to where your image is stored. If the picture is placed in a subfolder (for example, `/img/puppies/`), then make sure to include the subfolder (for example, `image: puppies/dachshund.jpg`)

On the post (`layout: post`), the featured image will automatically display at the top of the page.

On a page (`layout: page`), the featured image will not automatically display. However, if the page is shared on social media, the featured image will be shown (through Twitter card support --- again, see `_includes/SEO.html`).

### On a Page

If you want to use an image on a page or in a post without labeling it as the featured image, simply use the include statement below.

{% raw %}
```
{% include image.html file="glenn-carstens-peters-0iB6_GX7BXk-unsplash.jpg" %}
```
{% endraw %}

---

# Posts

Once you get authors and images set up, adding new posts is easy.

Store your posts in `collections/_posts/`.

## YAML Frontmatter

What [YAML frontmatter](https://jekyllrb.com/docs/front-matter/) should you include with your posts? There's an unpublished template that you can use as a reference: `collections/_posts/2020-01-01-Unpublished-Template.md`. It looks like this:

{% highlight html %}
---
layout: post
published: false
title: "Unpubished Template"
date: 2020-01-01 06:00
date_modified: 2020-01-08 13:00
author: lorri # This should be a person's code_name from your people collection
description: Lorem ipsum dolor sit amet, consectetur adipiscing elit.
categories:
- Lorem Ipsum
tags:
- Lorem Ipsum
image: notepad-593363_1920.jpg
comments: true
excerpt_separator: "[//]: #more"
---

Lorem ipsum dolor sit amet, consectetur adipiscing elit. Integer dapibus nec odio sit amet sollicitudin. Aliquam et finibus augue, eu egestas ipsum. Sed quis laoreet orci. Pellentesque placerat rutrum mi, ut imperdiet risus rhoncus ac. Maecenas commodo urna non elit aliquam rutrum. Quisque id nibh luctus, placerat turpis tempor, elementum mauris. Proin in varius arcu, ac fermentum mauris. Cras fringilla efficitur tortor, nec imperdiet sapien lobortis sit amet. Praesent mollis felis eget augue feugiat, vel semper nulla lobortis. Vivamus rhoncus lectus metus, vitae sodales massa ultricies sed.
{% endhighlight %}

`title:` is required.

`date:` is required.

`date_modified:` is optional.

`author:` is required. This must be the author's code_name from `collections/_people/`.

`description:` is optional. You can set archive pages to display either this description of the post, an excerpt of the post, or the complete post. Additionally, when shared on social media, this description is usually shown (through Twitter card support --- again, see `_includes/SEO.html`). You can use `description:` both when `layout: post` as well as when `layout: page`. In the example below, the post title is "Favorite 2019 Short Stories" and the post description is "Here are my favorite short stories from 2019."

{% include image.html file="Screenshot-Twitter-Card-Validator.png" %}

`categories:` is optional.

`tags:` is optional.

`image:` is optional. All you have to do is include the image file name, and on posts, the featured image will automatically appear on archive pages and at the top of the post itself (with its caption! Assuming you set up the [image metadata file](#image-metadata) correctly). You can also use `image:` when `layout: page`. On pages, the image will not automatically display; however, it will appear when shared on social media (through Twitter card support --- again, see `_includes/SEO.html`).

`comments:` is optional. If you want comments on the page, set this to `true`. If the value is `false` or if you delete this line, the page will not include comments.

`excerpt_separator:` is optional. By default, Graph Paper displays post excerpts on archive pages. By default, [Jekyll selects the first paragraph](https://jekyllrb.com/docs/posts/#post-excerpts) of a post as the excerpt. If you want more paragraphs to be included in the excerpt, then include `excerpt_separator: [//]: #more` in the YAML frontmatter and place `[//]: #more` to mark where you want the excerpt to end. If you leave `excerpt_separator: [//]: #more` *and don't include* `[//]: #more` somewhere in the file, Jekyll will by default excerpt *the entire post*. Therefore, you should either (1) delete this line from the YAML frontmatter and the post's excerpt will be its first paragraph, or (2) include this line and make sure you place `[//]: #more` somewhere in the post.

## Headings

The post title is formatted as `<h1>`, so make sure any section headings in a post start with `<h2>`. (When `layout: page`, Graph Paper styles the title as `<h1 class="display-4">`, so pages in Graph Paper can be styled starting with regular `<h1>`.)

## Syntax Highlighting

You can use backticks to style a word or a phrase as code. For example: \`code\` appears as `code`.

You can use three backticks before and after a section to designate the section as code. For example:

````
```
Lorem ipsum dolor sit amet, consectetur adipiscing elit. Morbi volutpat ac ligula maximus commodo. Donec mollis finibus cursus.
```
````

is rendered as:

```
Lorem ipsum dolor sit amet, consectetur adipiscing elit. Morbi volutpat ac ligula maximus commodo. Donec mollis finibus cursus.
```

You can use {% raw %}`{% highlight html %}` and `{% endhighlight %}`{% endraw %} to designate a section as code and use syntax highlighting. For example:

```
{% raw %}{% highlight html %}{% endraw %}
<h1>Heading 1</h1>
<p>Lorem ipsum dolor sit amet, <em>consectetur adipiscing elit</em>. Morbi volutpat ac ligula maximus commodo. Donec mollis finibus cursus.</p>
{% raw %}{% endhighlight %}{% endraw %}
```

is rendered as:

{% highlight html %}
<h1>Heading 1</h1>
<p>Lorem ipsum dolor sit amet, <em>consectetur adipiscing elit</em>. Morbi volutpat ac ligula maximus commodo. Donec mollis finibus cursus.</p>
{% endhighlight %}

---

# Share!

After you finish forking Graph Paper to make your own website, let us know!

Send Cam a [tweet](https://twitter.com/camncoulter) or an [email](https://www.cncoulter.com/about/), or if you want, you can write a blog post which shows off your site and explains how you set it up. You can email your blog post to Cam or submit it via pull request. We ask that any blog posts you send us are licensed under a [Creative Commons license](https://creativecommons.org/).
