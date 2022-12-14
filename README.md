# Jekyll + Chicago Design System

This is a [Jekyll theme](https://jekyllrb.com/docs/themes/) for the
[Chicago Design System](https://chicagodesignsystem.org) (CDS). It is built off a fork from the
[US Web Design System](https://github.com/18F/uswds-jekyll) v1.0, and is adaptable to your organization's needs.

## Table of contents
1. [Using the CDS in your jekyll Site](#Using-the-Chicago-Design-System-in-your-Jekyll-Site)
1. [Contributing to the CDS](#contributing-to-the-cds)
1. [Jekyll basics](#jekyll-basics)
    - [Getting started](#getting-started-with-jekyll)
    - [Site configuration](#site-configuration)
        - [Site title](#site-title)
        - [Site description](#site-description)
        - [Navigation](#navigation)
        - [Search](#search)
        - [Analytics](#analytics)
        - [Anchor JS](#anchor-js)
1. [Pages](#pages)
    - [Front matter](#front-matter)
        - [Page title](#page-title)
        - [Page subnavigation](#page-subnavigation)
        - [Hero](#hero)
        - [Tagline intro](#tagline-intro)
        - [Graphics list](#graphics-list)
    - [Body](#body)
1. [Assets](#assets)
    - [Stylesheets](#stylesheets)
    - [Scripts](#scripts)
    - [Asset load order](#asset-load-order)
1. [Customization](#customization)
    - [Customizing with Sass](#customizing-with-sass)
    - [Customizing with CSS overrides](#customizing-with-css-overrides)
    - [Overriding includes and layouts](#overriding-includes-and-layouts)
1. [Components](#components)
    - [Header](#header)
    - [Footer](#footer)
    - [Cards](#cards)
1. [Layouts](#layouts)
    - [Default](#layout-default)
    - [Page](#layout-page)
    - [Home](#layout-home)
    - [Post](#layout-post)
    - [Project](#layout-project)
    - [Splash](#layout-splash)
    - [Team member](#layout-team-member)


## Using the Chicago Design System in your Jekyll Site

The Chicago Design System is currently in development. To access the most up-to-date system, include the CDS as a remote theme. 

1. Include the `jekyll-feed` and `jekyll-remote-theme` plugins in your gemfile. Remove any other theme gems, such as the default `gem "minima", "~> 2.0"`, from your gemfile.

    ```ruby
    gem "github-pages", group: :jekyll_plugins

    # If you have any plugins, put them here!
    group :jekyll_plugins do
      gem "jekyll-feed", "~> 0.6"
      gem "jekyll-remote-theme"
    end
    ```

1. Open a command shell. Navigate to the main folder of your jekyll site. Fetch and update your bundled gems by running:

    ```sh
    bundle update
    ```

1. Adjust the build settings in your `_config.yml` file to include the Chicago Design System.

    ```yml
    # Build settings
    markdown: kramdown
    remote_theme: Chicago/design-cds-jekyll
    plugins:
      - jekyll-feed
      - jekyll-remote-theme
    ```

You will need to restart your Jekyll server to see the effects.

## Contributing to the CDS

You can get involved by contributing code to this repo, [writing an issue](https://github.com/Chicago/chicagodesignsystem.org/issues/new), or finding [other ways to get involved](https://opensource.guide/how-to-contribute/).

We communicate about this project in our [CDS slack workspace](https://chicagodesignsystem.slack.com/messages). Request an invitation by emailing us at [Chicago Design System](design.system@cityofchicago.org) or using our [shared invite link](https://join.slack.com/t/chicagodesignsystem/shared_invite/enQtMzM2OTA4MTQyNzIzLWVlOWFkOWQ4YWE0NWQ2YTAzOTFmYWFlMGVjNTEwZjA5ZWNmYjFkZTNhNDNhMmM1MTJiYmQ3MDk2NWZkNzg2Mjg).

To develop this theme and/or test it locally:

1. Clone this repo
    1. Navigate to the Chicago Design System [main repo](https://github.com/Chicago/design-library).
    1. In the top-right corner of the page, click *Fork*.
    1. Make a local copy to edit. Go to the *code* section of your fork and click *Clone or download*.
    1. Copy the URL provided.
    1. Open your command line or terminal application. Navigate to the directory where you would like to copy the repository (download the code).
    1. Clone the repository by typing `git clone <URL>`, replacing `<URL>` with the url you copied.
1. Install ruby, a bundler, and jekyll by following the [quickstart instructions](https://jekyllrb.com/docs/) in the official jekyll documentation.
1. If you already have ruby or jekyll installed, navigate to the folder containing your local clone of this repository, open a command terminal, and run `bundle update` to ensure all necessary gems and plugins are up to date.
1. Run Jekyll (`jekyll serve`) in the local clone of this repo.


## Jekyll Basics

Jekyll is a static website generator that converts markdown files to webpages in pre-made themes and layouts. In this case, the themes and layouts are provided by the Chicago Design System. 

### Why Jekyll?

A Jekyll theme is lightweight and easily edited. Jekyll separates the content (markdown files) from the theme (this repository), which means that content editors don't need any knowledge of ruby or stylesheets to generate a uniformly formatted webpage.

### Getting Started with Jekyll

Visit the [official Jekyll documentation](https://jekyllrb.com/docs/) for instructions on how to install Jekyll.

**If you've never used Jekyll before, reading this [step-by-step tutorial](https://jekyllrb.com/docs/step-by-step/01-setup/) from the official Jekyll documentation is strongly recommended.**

### Site Configuration

Configuration of common elements ([header](#header),
[footer](#footer), [navigation](#navigation), etc.) happens in your
project's [data files](https://jekyllrb.com/docs/datafiles/). 

The [default layout](#layout-default) also provides a mechanism for
automatically including [stylesheets](#stylesheets) and
[scripts](#scripts) on a site-wide, layout-wide, and per-page
basis. See [asset load order](#asset-load-order) for more
information.

#### Site title

You can change your site's title with the `title` field in your
`_config.yml`.  If you want to provide an alternate title for use
_only_ in the site header, you can set the `title` field in
`_data/header.yml`.

#### Site description

You can change your site's description with the `description` field in your
`_config.yml`. If you want to override it for a particular page, you can set the `description` field in that page's front matter.

#### Navigation

This theme's navigation system is powerful and flexible. Named
navigational lists live in your project's `_data/navigation.yml`,
e.g.

By default all links are assumed to be internal to the site. You can add `external: true` to links that are external. You can also add `class: class-name` to add a class to a specific link.

```yml
# _data/navigation.yml
primary:
  - text: Documentation
    href: /docs/
  - text: Support
    href: /help/
  - text: External link
    href: https://cityofchicago.org
    external: true

  # link objects with a 'links' field will be presented as
  # collapsible link lists. The 'links' field can either be a
  # reference to another link list in this file, or a literal list.
  - text: Section title
    links: <links>
```

This scheme allows you to define navigational elements that can be
shared by different components, such as the [header](#header) and
[footer](#footer). See the documentation for those components for
more info.

#### Search

We do not use the federal government's [Search.gov](https://search.gov/). It can be configured in `_config.yml,` but it's not going to work unless you are a member of the federal government can create a search.gov account and set up your website with search.gov.

#### Analytics

You can add Google Analytics to your site by uncommenting the `google_analytics_ua` line and replacing `UA-????????-??` with your Google analytics UA code.

```
# Configuration for Google Analytics, add your UA code here:
# google_analytics_ua: UA-????????-??
```

#### Anchor JS

You can show an anchor link next to header tags by uncommenting this section from the `_config.yml` data file.
This will add an anchor link after the header tag on the page and post layouts making each header linkable.
See https://github.com/bryanbraun/anchorjs for more information.

```yml
# anchor_js_targets: [h1, h2, h3, h4, h5, h6]
```

## Pages

Once you have a skeleton of a Jekyll site set up, you will be able to start creating site content in the form of pages written with markdown. 

You can create a page by saving a markdown file (a text file with the `.md` extension) in the main directory of your site. For more details on pages, such as saving pages to sub-directories and determining permalinks, see the [official jekyll page documentation](https://jekyllrb.com/docs/pages/). 

A jekyll page has two sectons: the **front matter** and the **body**.

### Front Matter

The **front matter** of a page contains the page metadata and global variables, including the title, layout, permalink, and date. Custom graphic elements, such as a hero image or tagline, are also contained in the front matter. For more details on front matter and a full list of predefined front matter variables, see the [official jekyll front matter documentation](https://jekyllrb.com/docs/front-matter/).

Front matter is contained between two triple dashes:

```md
---
title: My Page
permalink: /my-page/
layout: page
---
```

#### Page title

Set each page's title in its front matter:

```md
---
title: About us
---
```

#### Page subnavigation

If you're using the [page layout](#layout-page), each page may declare its own
side navigation and/or subnavigation in its [front matter](#front-matter):

```md
---
sidenav: documentation
subnav:
  - text: Section one
    href: '#section-one'
  - text: Section two
    href: '#section-two
---
## Section one

## Section two
```

As with the [header](#header) and [footer](#footer), the `sidenav` field may
either reference a common [navigation list](#navigation) from
`_data/navigation.yml` (recommended) or be a literal list of links.

The `subnav` field should be used to link to sections _within_ the current
page, because links to other pages will cause the linking page's side
navigation to collapse when visited.


A page's "current" or "active" state in the sidenav is
determined by whether a link's `href` matches `page.url` or
`page.permalink` for each page being rendered.

`subnav` is a list of links to display on this page under its own link in the side navigation.

**Note that subnav link hrefs are not prefixed with
`site.baseurl`** because this breaks hash links prefixed with
`#`.

**Pro tip:** Unless your Jekyll configuration specifies otherwise, the default
Markdown formatter (Kramdown) will automatically generate predictable `id`
attributes for your page headings and convert markdown like this:

```md
## Section one
```

into:

```html
<h2 id="section-one">Section one</h2>
```

**Pro tip:** If you're like us and prefer your navigation sticky, you can add `sticky_sidenav: true` on [page](#layout-page), [project](#layout-project), and [team member](#layout-team-member) layouts to have the sidenav follow as you scroll.

#### Hero

```yml
hero: # optional
  image: /path/to/image.jpg # optional
  callout:
    alt: Callout white text! # optional
    text: The rest of the callout in light blue text
  button: # optional
    text: The button text
    href: /button-href/
```

#### Tagline intro

```yml
# optional, but must be used in conjunction with 'intro', below
tagline: A tagline for your page
# also optional, but must be used with 'tagline', above
intro: |
  Some introductory text content.

  This will be processed as **Markdown**.
```

#### Graphics list
```yml
# an optional list of graphics to display before or after the content
graphics:
  - image:
      # note the indentation here: graphics[n].image.src
      src: /path/to/image.ext
      alt: optional alt text
    title: Optional graphic title, rendered as an <h3>
    description: Graphic description text, processed as _Markdown_.

# optional
graphics_position: (before|after)
```

### Body
Body content starts after the front matter and is written in markdown, which is converted to HTML at build. Here's a great [starting point for markdown help](https://www.markdownguide.org/). Global variables set in the front matter can be accessed in the body of the page using [liquid](https://jekyllrb.com/docs/liquid/) syntax. You can also add raw HTML to a markdown file, which may be necessary to include certain page elements.




## Assets

The [stylesheet](_includes/styles.html) and [script](_includes/scripts.html)
includes each incorporate the USWDS CSS and JS files if the corresponding
`styles` and `scripts` lists aren't defined in your `_config.yml`. So unless
you add one or both of those manually, your HTML will include the following:

```html
<!-- in the <head> -->
<link rel="stylesheet" href="/assets/uswds/css/uswds.min.css" media="screen">
<!-- before </body> -->
<script src="/assets/uswds/js/uswds.min.js" async>
```

Read more about customizing [stylesheets](#stylesheets) and [scripts](#scripts)
below.


### Stylesheets

As a general rule, all stylesheets are inserted in a layouts'
`<head>`, which qualifies them as "render-blocking". Site
stylesheets can be specified in `_config.yml` or a layout or page's
[front matter] YAML in the following form:

```yml
styles:
  - /path/to/sheet.css
  - href: /path/to/sheet.css
    media: (screen|print|all) # optional
```

Stylesheets specified as objects (in the latter item above) must
have an `href` property. The `media` defaults to `screen`.


### Scripts

As a general rule, all scripts are inserted before a layouts'
`</body>`, which prevents them from blocking the rendering of your
page's content. Scripts can be specified in `_config.yml` or a
layout or page's [front matter] YAML in the following form:

```yml
scripts:
  - /path/to/script.js
  - src: /path/to/script.js
    async: true # optional
```

Scripts specified as objects (in the latter item above) must have a `src`
property. Scripts with `async: true` will get an `async` attribute, which tells
the browser _not_ to let this script's loading block the execution of
subsequent scripts. If the execution order of your scripts is **not**
important, setting `async: true` may provide performance benefits to your
users. (Conversely, if you don't know whether your scripts need to execute in a
particular order, then you should not set `async: true` because it may prevent
your scripts from running propertly.)


### Asset load order

Both [stylesheets](#stylesheets) and [scripts](#scripts) can be configured

1. Assets configured at the `site` level (in your `_config.yml`) will be loaded
   in all pages that use the USWDS [layouts](#layouts).
1. Those configured at the layout level (in that layout's [front
   matter]) will be loaded on all pages that use that layout, after
   site assets.
1. Those configured at the page level (in the page's [front matter])
   will be loaded last.


## Customization

You have two options for customizing the CSS: [Sass](#customizing-with-sass) or
[CSS overrides](#customizing-with-css-overrides). Individual sites can also
[selectively override](#overriding-includes-and-layouts) individual includes
and layouts.

The CDS includes a built in overrides.scss file to quickly change the site's colors and fonts.
Just put in your organization's brand colors, and the site will automatically update.
The included Chicago styling (relatively similar to the original site) is WCAG 2.0 tested.


### Customizing with Sass

1. Create a [Sass][] (or SCSS) entry point that sets variables and then imports
   the USWDS source files:

    ```scss
    ---
    # assets/main.scss
    ---
    // set your variables or @import them here.

    // at the very least, you should set the USWDS font and image paths
    // to the correct paths relative to assets/main.css, like so:
    $font-path: 'uswds/fonts';
    $image-path: 'uswds/img';

    @import 'uswds/all';
    ```

1. Change the path to your site's default stylesheet in your `_config.yml`:

    ```yml
    styles:
      - /assets/main.css
    ```

All of the USWDS [SCSS source files](https://github.com/uswds/uswds/tree/master/src/stylesheets)
are placed in the [_sass/uswds](_sass/uswds) directory and are available as
Sass imports via `@import 'uswds/<path>';`. See the [Jekyll docs][Jekyll Sass]
for more information about its Sass/SCSS support, and configuring its Sass
renderer in your site's config.

### Customizing with CSS overrides

1. Create a new CSS or Sass file that defines your customizations,
   e.g.

    ```scss
    ---
    # assets/uswds-overrides.scss
    ---
    .usa-header {
      // overrides here
    }
    ```

1. Add the new stylesheet's path to your `_config.yml` _after_
   `uswds.min.css`:

    ```yml
    styles:
      - /assets/uswds/css/uswds.min.css
      - /assets/uswds-overrides.css
    ```

### Overriding includes and layouts

Any [include](_includes) or [layout](_layouts) can be overridden by
your site by placing a file with the same name into your site's
`_includes` or `_layouts` directory. For instance:

- To change how [stylesheets](#stylesheets) are loaded or
  referenced, you can create your own `_includes/styles.html`,
  which will subsequently change how stylesheets are loaded in all
  layouts that inherit from the USWDS [default layout](#layout-default).

- You can change how the side navigation is rendered (but not which
  data it receives) in the [page layout](#layout-page) by creating
  your own `_includes/sidenav.html`.

- You can change how and whether the side navigation is displayed
  at all in the [page layout](#layout-page) by overriding
  `_layouts/page.html`.

## Components

For some [USWDS components](https://designsystem.digital.gov/components/),
there are two different files that control how data is passed to
the template:

1. `components/{component}.html` is the low-level template that
   assumes a similarly named global template variable. For
   instance, the header component operates on the `header` template
   variable.
1. `{component}.html` is the "concrete" implementation of the
   component that sets the appropriate global variable then
   includes the low-level template.

This separation allows you to override either of the component
includes in your own Jekyll site without having to re-implement
either the high- or low-level logic. For instance, if you want your
header data to come directly from the Jekyll configuration file
(`_config.yml`) rather than `_data/header.yml`, you can override
`_includes/header.html` to look like this:

```html
{% assign header = site.header %}
{% include components/header--basic.html %}
```


### Header

The [header.html include](_includes/header.html) sets the `header`
template variable to `site.data.header`, the value of which is set
in your Jekyll project's `_data/header.yml` file. Then it includes
[components/header.html](_includes/components/header.html) to
render the header's markup.

See this repo's [header.yml](_data/header.yml) for more info.


### Footer

The [footer.html include](_includes/footer.html) sets the `header`
template variable to `site.data.footer`, the value of which is set
in your Jekyll project's `_data/footer.yml` file. Then it includes
[components/footer.html](_includes/components/footer.html) to
render the footer's markup.

See this repo's [footer.yml](_data/footer.yml) for more info.


### Cards

Cards are tiles that represent the pages or in a collection, such as a list of team member bios or a list of projects. A card deck is embedded in a page ("card page"), and is generated from a collection. A collection corresponds to a project folder, which contains project files. One card is generated for each project file, and clicking on a card brings you to the corresponding project.

To implement a card deck on your website:

1. Make a collection folder in the main directory of your jekyll site. The folder must be prefaced with an underscore, e.g. `_collection-name`. 
1. Include the new collection in a `collections` section of your `_config.yml` file. Note that `collection-name` is the same name as the folder but *without* a preceding underscore. 
    ```yml
      collections:
        collection-name: 
          output: true
          permalink: /:path/
    ```
1. Create a series of project files in your collection folder. These will be normal markdown files of type "project." Some additional front matter (below) should be included that will be reflected on the card. 

    ```md
      ---
      layout: project
      title: Project Title
      permalink: /card-page/project
      description: Project description.
      large_image: /assets/img/aerial-northside-water.png
      small_image: /assets/img/city-seal-blue.png
      image_alt: The image alt text
      ---
    ```
1. Add a card deck to a page (`card-page` in this example) by adding the HTML code below to body to the markdown file for that page. Make sure to replace `collection-name` with the name of your collection with no underscore.
    ```html
    <div class="card-deck">
      {% for item in site.collection-name %}
        <div class="card">
          <img class="card-img-top" src="{{ site.baseurl }}{{ item.small_image }}" alt="{{ item.image_alt }} ">
          <div class="card-body">
            <h3 class="card-title">{{ item.title }}</h3>
            <p class="card-text">{{ item.description }}</p>
          </div>
          <div class="card-footer">
            <a href="{{ site.baseurl }}{{ item.url }}" class="card-read-more-link">Read more <svg xmlns="http://www.w3.org/2000/svg" width="444.819" height="444.819" viewBox="0 0 444.819 444.819"><path d="M352.025 196.712L165.885 10.848C159.028 3.615 150.468 0 140.185 0s-18.84 3.62-25.696 10.848l-21.7 21.416c-7.045 7.043-10.567 15.604-10.567 25.692 0 9.897 3.52 18.56 10.566 25.98L231.544 222.41 92.785 361.168c-7.04 7.043-10.563 15.604-10.563 25.693 0 9.9 3.52 18.566 10.564 25.98l21.7 21.417c7.043 7.043 15.612 10.564 25.697 10.564 10.09 0 18.656-3.52 25.697-10.564L352.025 248.39c7.046-7.423 10.57-16.084 10.57-25.98.002-10.09-3.524-18.655-10.57-25.698z"/></svg></a>
          </div>
        </div>
      {% endfor %}
    </div>
    ```
1. Build the site. The cards will render based on what pages are in the collections folder.

This repo contains an example HTML for a collection called `projects`. Using this default include, you can simply add the liquid line `{% include project-list.html %}` to show all projects in the `projects` collection. This pattern can also be followed to move HTML components to outside documents. 

## Layouts

This theme provides the following layouts, which you can use by
setting the `layout` [front matter] on each page, like so:

```yml
---
layout: name
---
```
Supported (optional) front matter for page layouts.

- [page navigation](#page-subnavigation)
- [hero](#hero)
- [tagline intro](#tagline-intro)
- [graphics list](#graphics-list)

### `layout: default`

This is the bare-bones USWDS layout, which does all of the
basic page scaffolding then drops the page content into the
`<main>` element. All of the other layouts "inherit" this one and
provide other features in the content block.

The default layout provides a layout [front matter] hook to add
attributes to the `<main>` element. You can see how this works in
the [page layout](_layouts/page.html#L3-L4).

### `layout: home`

This layout implements the [home page
template](https://designsystem.digital.gov/page-templates/landing/), which
accommodates the following [front matter]:

```yml
title: Home
permalink: /

layout: home

hero:
  image: /assets/uswds/img/hero.png
  callout:
    alt: "Hero callout:"
    text: Call attention to a current priority
  button:
    href: /callout/
    text: This is a call to all my
  link:
    text: Link to more about that priority
    href: /link/
  content: Support the callout with some short explanatory text. You don't need more than a couple of sentences.

tagline: A tagline highlights your approach.
intro: |
  The tagline should inspire confidence and interest, [focusing on the value](javascript:void(0);) that your overall approach offers to your audience. Use a heading typeface and keep your tagline to just a few words, and don’t confuse or mystify.

  Use the right side of the grid to explain the tagline a bit more. What are your goals? How do you do your work? Write in the present tense, and stay brief here. People who are interested can find details on internal pages.

graphics:
  - image:
      src: /assets/uswds/img/circle-124.png
      alt: ''
    title: Graphic headings can vary.
    description: Graphic headings can be used a few [different ways](javascript:void(0);), depending on what your landing page is for. Highlight your values, specific program areas, or results.
  - image:
      src: /assets/uswds/img/circle-124.png
      alt: ''
    title: Stick to 6 or fewer words.
    description: Keep body text to about 30. They can be shorter, but try to be somewhat balanced across all four. It creates a clean appearance with good spacing.
  - image:
      src: /assets/uswds/img/circle-124.png
      alt: ''
    title: Never highlight anything without a goal.
    description: For anything you want to highlight here, understand what your users know now, and what activity or impression you want from them after they see it.
  - image:
      src: /assets/uswds/img/circle-124.png
      alt: ''
    title: Could also have 2 or 6.
    description: In addition to your goal, find out your users’ goals. [What do they want to know](https://18f.gsa.gov/) or do that supports your mission? Use these headings to show those.
```

Check out the YAML front matter in the [home demo
page](demo/home.html) for an example of how to structure it.

### `layout: page`

This layout implements the [document page
template](https://designsystem.digital.gov/page-templates/docs/).

See the [page demo page](demo/page.md) for an example of how this
works, and see [_data/navigation.yml](_data/navigation.yml) for how
to structure named navigation data for your site.

### `layout: post`

This layout is identical to the layout `page` and is included to allow for easier site creation using  `Jekyll new`.

### `layout: project`

This layout is used to show details for an individual project and uses the following front matter.

```yml
layout: project
title: Title of project
permalink: /projects/link-to-project/
description: Project description.
large_image: /path/to/image.ext
small_image: /path/to/image.ext
image_alt: The image alt text
```

To show a listing of projects on a page add `{% include project-list.html %} to the page`

### `layout: splash`

This layout is used to create a custom layout for a landing page or new product launch.

```yml
layout: splash
permalink: /
title: Title of splash page
headline: Headline/lead of splash
```


### `layout: team-member`

This layout is used to show details for an individual team member and uses the following front matter.

```yml
layout: team-member
permalink: /team/link-to-team-member/
name: Team member name
image: /path/to/image.ext
job_title: Team member job title
phone: 123-456-7890
email: email@address.gov
```

To show a listing of team members on a page add `{% include team-list.html %} to the page`

[Sass]: http://sass-lang.com/guide
[Jekyll Sass]: https://jekyllrb.com/docs/assets/#sassscss
[front matter]: https://jekyllrb.com/docs/frontmatter/
