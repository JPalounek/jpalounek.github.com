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
We've developed a tool which we call Remote and is placed in restatic repository on github in folder tools/Remote - link is in Links section.

### How it works
For Apache or another standart http server - clone the tools repository and put in any directory contents of folder 'tools/Remote'. Setup an vhost which will target this directory as a document root, setup vhost name - eg. restatic-remote.yourdomain.com

### API
Restatic Remote listen to your POST or GET requests and is performing request using standardized APIs. Access is authorized by key - key is '1' by default and you can always change it throught API command. And its stored in file 'key.dat' in folder 'data'

#### How to change key
GET - `restatic-remote.yourdomain.com/index.php?access_key=1&new_key=5` 
This will change current key from '1' to '5' - this feature will help you keep using this tool safety.

For POST its same - only you don't specify command in URL but you send it in POST request (`access_key=current_key`, `new_key=new_key`)

#### Remote restatic performing
Tool has its own JSON storage in folder data in file sites.dat. You can store new site information and use it to restatic a site deployed on your server. Or you can edit existing record.

##### Storing
To store new site you should specify these arguments and send it via POST or GET.

* `access_key = key`
* `action = add`
* `source = /path/to/source`
* `target = /path/to/target`
* `restatic_path = /path/to/restatic`

##### Editing
To edit existing record you should specify these arguments.

* `access_key = key`
* `action = edit`
* `id = record-id`
* `field = source or target`
* `value = new value`

Remote will automatically check if given data are valid and store it.

#### Restatic
To restatic a site just specify arguments

* `access_key = key`
* `action = restatic`
* `id = site-id`

If the output stream contain `Parsing done - enjoy your new site! Its stored in ... ` then everything is Ok.

## Links
* [Github repository](https://github.com/JPalounek/restatic)
* [Restatic Homepage](http://restatic.binaryage.com/)