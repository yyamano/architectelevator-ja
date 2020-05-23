# About the repository

This is a Japanese translation of Gregor Hohpe's [Architect Elevator Blog](https://architectelevator.com/). It is published at https://yyamano.github.io/architectelevator-ja/ with [GitHub Pages](https://pages.github.com/).

# Installation

## Requirements

Install the followings with [pkgsrc](http://pkgsrc.org/).

* devel/git
* www/curl
* security/mozilla-rootcerts-openssl
* lang/ruby27

## Setup the repo

~~~
% git clone https://github.com/yyamano/architectelevator-ja.git
% cd architectelevator-ja
% bundle27 install vendor/bundle
~~~

# Build the site locally

~~~
% bundle27 exec jekyll serve
~~~

You can access the site locally on macOS:

~~~
% open http://127.0.0.1:4000
~~~

# How to add the new article

~~~
% cd architectelevator-ja
% mkdir -p _original_htmls/PATH/TO/THE/ARTICLE
% curl https://architectelevator.com/PATH/TO/THE/ARTICLE/ > _original_htmls/PATH/TO/THE/ARTICLE/index.html
% mkdir -p PATH/TO/THE/ARTICLE
% cp _original_htmls/PATH/TO/THE/ARTICLE/index.html PATH/TO/THE/ARTICLE/index.md
~~~

Add the follwoing [YAML front matter](https://jekyllrb.com/docs/front-matter/) block to the top of the markdown file. The description is used for generating [SEO headers](https://github.com/jekyll/jekyll-seo-tag/blob/master/docs/usage.md).

~~~
description: blah, blah, blah
original:
  url: https://architectelevator.com/PATH/TO/THE/ARTICLE/
~~~

## TODO

* branch strategy
  * develop branch is periodically rebased.
* more explanation for the future me
* variables like original.something
* how to validate?
  * HTML
  * https://search.google.com/structured-data/testing-tool/u/0/
* Replace link to the original article with JP translation
  * Sync title.

# Directory hierarchy

TODO: describe basic directory hierarchy including jekyll stuff.
