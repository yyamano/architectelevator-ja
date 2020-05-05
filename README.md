# Installation

## Requirements

Install the followings with pkgsrc.

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

~~~
% open http://127.0.0.1:4000
~~~

# How to add the new article

* _original_htmls
* directory hier