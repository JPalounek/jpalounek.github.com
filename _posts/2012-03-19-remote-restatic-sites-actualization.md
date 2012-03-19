---
layout: post
category : posts
tags : [restatic, binaryage, static-sites]
author_name: Jan Palounek
author_uri: http://palounek.com/
---
{% include JB/setup %}

## Problem
If you are - and I hope you are - deploying Restatic powered sites and you are using Google Documents as a CMS for your clients then you will probably need to solve some automatization in parsing new content and deploying it.

## Solution
### Remote
We've developed a tool which we call Remote and is placed in restatic tools repository on github - link is in Links section.

### How it works
In Apache or another standart http server - clone the tools repository and put in any directory contents of folder 'Remote'. Setup an vhost which will target this directory as a document root, setup vhost name - eg. restatic-remote.yourdomain.com

### API
Restatic Remote listen to your POST or GET requests and is performing request using standardized APIs. Access is authorized by key - key is '1' by default and you can always change it throught API command. And its stored in file 'key.dat' in folder 'data'

#### How to change key
GET - `restatic-remote.yourdomain.com/index.php?access_key=1&new_key=5` 
This will change current key from '1' to '5' - this feature will help you keep using this tool safety.

For POST its same - only you don't specify command in URL but you send it in POST request (`access_key=current_key`, `new_key=new_key`)

#### Remote restatic performing
Here are four arguments you should specify (in POST or GET)

* `access_key = 1`
* `source = /path/to/source`
* `target = /path/to/target`
* `restatic_path = /path/to/restatic`

if you need specify path to restatic then `restatic_path=path/to/restatic` is what you need. Its optional of course.

Eg.: restatic-remote.yourdomain.com/index.php?access_key=1&source=~/dev/sites/my_blog&target=~/web/myblog/

#### Result
If the output stream contain `Parsing done - enjoy your new site! Its stored in ... ` then everything is Ok.

## Links
* [Github repository](https://github.com/JPalounek/restatic-tools)
* [Restatic Homepage](http://restatic.binaryage.com/)