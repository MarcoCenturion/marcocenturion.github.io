# feature-blog-jekyll [![Code Climate](https://codeclimate.com/github/lavkumarv/feature-blog-jekyll/badges/gpa.svg)](https://codeclimate.com/github/lavkumarv/feature-blog-jekyll) <a href="https://codeclimate.com/github/lavkumarv/feature-blog-jekyll"><img src="https://codeclimate.com/github/lavkumarv/feature-blog-jekyll/badges/issue_count.svg" /></a>

Feature Blog is a minimalist, beautiful, responsive theme for Jekyll. It is built using the Bootstrap 3.

Home Page:

![home](home.jpg "home")

## Features

* Twitter Bootstrap 3
* Option to set featured image & video in post
* Pagination support
* Disqus comments if you choose to enable
* MailChip Integration for subscription
* Tags for [Open Graph](https://developers.facebook.com/docs/opengraph/), [Twitter Cards](https://dev.twitter.com/docs/cards) and Schema.org for a better social sharing experience
* Support for recent post
* SEO Enabled theme
* Beautifully crafted 404 page
* Custom categories and tags pages
* Ajax based search
* Sitemap for search engines
* Google Fonts
* Font awesome icons
* Easy to configure and customize

## Basic Setup for a new Jekyll site

1. [Install Jekyll](http://jekyllrb.com) if you haven't already.
2. Fork the [Feature Blog Theme](https://github.com/lavkumarv/feature-blog-jekyll/fork)
3. Clone the repo you just forked.
4. Edit `_config.yml` to personalize your site.
5. Check out the sample posts in `_posts` to see examples for pulling in large feature images, assigning categories and tags, and other YAML data.
6. Read the documentation below for further customization pointers and documentation.

---

## Setup for an Existing Jekyll site

`_config.yml` file:

``` yaml
# Basic settings
description: Un pequeño blog personal.
baseurl: "/"
url: "https://MarcoCenturion.github.io"
twitter_username: Odiseo_Torres
github_username:  MarcoCenturion
include: ['_pages']

# Build settings
markdown:    kramdown
highlighter: pygments
lsi:         false
excerpt_separator: "\n\n"
gems:
  - jekyll-feed
  - jekyll-paginate
exclude:
  - Gemfile
  - Gemfile.lock

# pagination
gems: [jekyll-paginate]
paginate: 5
paginate_path: "/page:num/"

# Enable comments
comments: true

# Markdown settings
kramdown:
  auto_ids:       true
  footnote_nr:    1
  entity_output:  as_char
  toc_levels:     1..6
  smart_quotes:   lsquo,rsquo,ldquo,rdquo
  enable_coderay: false

  coderay:
    coderay_wrap:              div
    coderay_line_numbers:      inline
    coderay_line_number_start: 1
    coderay_tab_width:         4
    coderay_bold_every:        10
    coderay_css:               style
---
```
---
Global Configuration( global.yml):
``` yaml
# Site Settings
title: 'Marco Centurión'
description: 'Blog de estupideces varias'
url: 'https://MarcoCenturion.github.io'

# Admin Settings
admin_name: 'Marco Centurion'
admin_email: 'aulavirtualturismo@gmail.com'

#####################################################################
#About Page
author_name: 'Marco Centurion'
author_profession: 'Sci Fi Writter and amateur developer'
author_description: 'Desarrollador de Módulos Odoo, estudiante de Data Science y Machine Learning.</br></br>
35 años de experiencia en Turismo, los últimos 15 liderando equipos de desarrollo de Software para la industria.</br></br>
author_image: '/images/author.jpg'

# social proiles
facebook: 'https://www.facebook.com/marco.centurion8'
twitter: 'https://twitter.com/Odiseo_Torres'
linkedin: 'https://www.linkedin.com/in/Marco-Adrian-Centurion/'
#instagram: 'https://www.instagram.com/vishwakarmalav/'
github: 'https://github.com/MarcoCenturion'
#google-plus: 'https://plus.google.com/+LAVKUMARVISHWAKARMAdev'
#stackoverflow: 'http://stackoverflow.com/users/4703818/lav-kumar-vishwakarma'
#####################################################################
---
```
Navigation Bar(nav.yml):
``` yaml
main:
    - { url: '/about', text: 'About' }
---
```

## Post Formate:

Image Post:
``` json
layout: blog
title: 'Sample post to check the functionality'
date: 2017-01-24 12:11:34
categories: blog
tags: code
image: '/images/default.jpg'
lead_text: 'Lorem ipsum dolor sit amet, consectetur adipisicing elit.'
```
Video Post:
``` json
layout: blog
title: 'Sample post to check the functionality'
date: 2017-01-24 12:11:34
categories: blog
tags: code
image: '/images/default.jpg'
lead_text: 'Lorem ipsum dolor sit amet, consectetur adipisicing elit.'
```
## Built With

* [Bootstrap](http://getbootstrap.com/) - The css framework used

## Contributing

Contributions are welcome!. Feel free to add a new feature or fix a bug.

## Authors

* **Lav Kumar Vishwakarma** - *Initial work* - [lavkumarv](https://github.com/lavkumarv)

## License

This project is licensed under the MIT License - see the [LICENSE.md](LICENSE.md) file for details
