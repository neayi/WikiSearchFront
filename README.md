
# WSSearchFront

a vue.js frontend for WSSearch

Build version! for 1.31 and 1.35

example
```
{{#WSSearchFrontend:
|size=10
|clear=term
|sort options=Title, Version
|title=Version
    #label=Label for table
    #highlight=true
    #urlstring=search
|layout=table
|@Title
    #display=ask combobox
    #query=[[Class::+]]
    #data=Title
    #text=name
    #search=true
|@Service
    #translation=Name
    #query=[[Class::Service]]
|@Version
    #display=combobox
|@Dictum
    #logic=or
    #sort=alphabetically
|@Modification date
  	#display=datepicker
    #label=Date
|@Rating
  	#display=range
	  #max=5
  	#step=1
|@Year
  #display=range
  #max=20
  #type=date
|?Version
|?Class
    #label=Page type
    #display=pill
    #highlight=true
    #logic=or
|?Users
    #display=link
|?Image
    #display=image
    #label=Page image
|?Rating
    #display=template
    #template=Special rating
}}
```



**settings :**

size=`<number>`      // amount of results per page
title=`<property>`   // property to use as link title

optional title setting:
 `#label=<text>`
 `#highlight=true`          //adds highlights to result title
 `#urlstring=<urlparam>`    //adds search terms to result href

layout=table                  //optional, show results in table layout
clear=term                    //optional, remove search term when clearing filters
sort=`<property>`             //optional, property to sort results by
sort options=Title, Version   //optional, shows a dropdown with sort options
size options=<number>, <number> //optional , shows a dropdown with size options

**settings for result output:**

    ?<property>
    `#display=<option>`  // optional, options: image, link, pill or template
    `#label=<text>`      // optional
    `#highlight=true`    // optional

   for display template add `#template=<template>`  template, passes {{{Page|}}} and {{{Value|}}} to the template


**settings for facets:**

    @<property>
    `#display=<option>`    // optional
    options: datepicker, search, combobox, ask combobox or range
    `#label=<text>`        // optional
    `#logic=or`            // optional
    `#sort=alphabetically` // optional    

   for display range add `#max=<number>`  and `#step=<number>`

   for display ask combobox add
       `#query=<ask>`      // the ask query example [[Class::Page]]
       `#data=<property>`  // property for data
       `#text=<property>`  // optional, property for display
       `#search=true`      // optional, search on enter key

  facet translations

     `#translation=<property>` // optional, translate property of type page
     `#query=<ask>`      // required for translation, the ask query example [[Class::Page]]
