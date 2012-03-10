---
layout: page
title: Blog about my work
---
{% include JB/setup %}

<ul class="posts">
  {% for post in site.posts %}
    <li><span>{{ post.date | date_to_string }}</span> &raquo; <a href="{{ BASE_PATH }}{{ post.url }}">{{ post.title }}</a></li>
  {% endfor %}
</ul>

# Restatic
## Tool for parsing google spreadsheet content to your static site

### Brief introduction
Restatic is my first bigger project in BinaryAge. Its developed for an injection of given google documents spreadsheet data to your stati site. You just put a marks - such as /-Posts-B2-/ (What means sheet Posts cell B2)- in your html files of your web and provide the sharing key of your spreadsheet using the configuration file in the root of your web's directory and run "restatic -d" in your web's root directory. And its all - your site is prepaired in the _site directory (which is placed in directory you ran this command).

### How to install it

`sudo bash < <(curl -s https://raw.github.com/JPalounek/restatic/master/install.sh)`

You will need a Unix system (Linux or Mac OS X). Its developed on the Mac OS X, but it runs on the linux as well (contact me if you have troubles with instllation). I use it on my mac and on my servers where I have Ubuntu or Debian and it works perfectly.

### How to configure it
It's as simple as is possible. 
You just should create a file name it restatic.yml in the root directory of the web you want to parse with restatic and put there

`googleSpreadSheetKey: 0AtkoCAIRJ7BPdGM2Y2tYdV9XRXNsNVVrVnFPeFIwb0E`

Of course with your own key :) from the document which you want use as a data source.

If you want use another delimiters of the marks - (Eg. ~Posts-B2~ instead /-Posts-B2-/) you can specify the delimiter in config file too.

`delimiter: /-, -/`

### How to use it
Anywhere you want to have your spreadsheet data put the mark which will specify cell with data. For example /-Posts-B2-/ to import data from sheet Posts cell B2.

If you want to parse the data to your site run in the Terminal:
`"restatic -d"`

You should be in the root directory of your site, it will create the folder "_site" and fill it with parsed page. If you want to specify a target directory then run:

`"restatic /path/to/source /path/to/target"`

### Where to use it
Its task for you!

### Links
* [Github repository](https://github.com/JPalounek/restatic)
* [Homepage](http://restatic.binaryage.com/)