---
layout: post
title: "Changes to the Readium.js API"
date: 2013-06-27 14:45
comments: true
categories: 
author: <a href="http://github.com/justinHume">Justin Hume</a>
---

With some recent additions to Readium.js, the "structure" of the API has been framed out. Since the next step in the evolution of the API will be to elicit feedback, I think it's a good time to talk about the structure of the Readium.js API, recent changes, and future directions.

<!--more-->

## The Readium.js API

### API Structure
Readium.js enables the embedding of an EPUB content viewer in a variety of different web applications. As you might expect, the surrounding application will need to call methods on the viewer directly, listen for interesting events triggered by changes in the viewer's state, and customize visual aspects of the viewer and EPUB content.

When I talk about the _structure_ of the API, I mean that the API has three major structural components that allow users to: 

* Listen for events and bind callbacks to them (Event API)
* Customize visual elements (Custom Style API)
* Call methods to interact with the EPUB viewer (Method API)

As I'll describe shortly, the structure of the API should - and is - designed to evolve as functionality, events, and customizability are added to the Readium.js feature set. 

## Recent Changes
The previous version (0.0.1) of Readium.js implemented the method API, provided two events, and did not implement the Custom Style API. Version 0.0.2 of Readium.js now provides a more complete API structure. There have been major changes to the Event API and the Custom Style API has been added.

### Event API

Readium.js now provides a set of events that users can bind callbacks to, using the "on" method: 

{% codeblock Event API lang:javascript %}
    readiumJs.on("atNextPage", function () {

        // Do something when the viewer has rendered the next page 
        //  in the reading order
    }, this);

    readiumJs.on("atLastPage", function () {

        // Do something when the viewer has rendered the last page 
        //  in the EPUB publication
    }, this);
{% endcodeblock %}

Check out the [API documentation](http://readium.github.io/Readium-Web-Components/get-started/api.html) for the set of events currently provided by different Readium.js modules. 

My expectation is that as Readium.js evolves, more and more events can and will be provided. For example:

* Events that are triggered before and after Readium.js fetches EPUB content from the web
* Events for style changes etc. 
* Events for specific content being displayed (images etc.)
* Many more..

Feedback on the types of events you'd like to see is encouraged (justinh@evidentpoint.com). 

### Custom Style API

Readium.js now provides a method to set the visual characteristics of the EPUB viewer and content. This part of the API also provides a set of defaults that can be used out of the box. The "customize" method provides the mechanism for setting styles: 

{% codeblock Custom Style API lang:javascript %}

    // Set a custom style with a default
    readiumJs.customize("page-border", "box-shadow");

    // Set a custom style with your own CSS
    readiumJs.customize("page-border", {
        "border-style" : "solid",
        "border-color" : "red",
        "border-width" : "10px"
    });

    // Chain custom styles
    readiumJs
        .customize("page-border", "box-shadow")
        .customize("spine-divider", "box-shadow")
        ...;

{% endcodeblock %}

Check out the [API documentation](http://readium.github.io/Readium-Web-Components/get-started/api.html) for the set of customizable elements and defaults provided by Readium.js modules. The customize method, like the "on" method, is implemented such that new custom styles can be added in the future, without disrupting current users of the API. 

For example, page transitions and loading animations will likely be provided at some point: 

{% codeblock add a page transition lang:javascript %}
    readiumJs
        .customize("page-transition", "slide")
        .customize("loading-animation", "spinning-wheel");
{% endcodeblock %}

## Evolution of the API

Now that the structure of the API has now been established, I think it's time to get some feedback on how the API should evolve. The project is very open to changes in the API at the moment. To get you started, I think there are a number of things to consider in this regard. 

### Methods, events, custom style defaults
First, suggestions for additional methods and events are welcome. This is fairly straightforward. Also, if you have some design chops, helping out with some custom style defaults would be great.

### Experiment with the Custom Style API
The Custom Style API is fairly experimental at the moment. In particular, the API allows users to provide their own CSS to style specific elements in the viewer. While I feel fairly certain that providing a set of defaults is going to be useful, I'm not sure that the ability to set custom CSS will work. 

There are few restrictions on the CSS that you can provide to the "customize" method, but I'm sure there are lot of ways to break the viewer. It may also be difficult for users to reason about their own custom styles, given that the elements they're styling in Readium.js are in somewhat of a black box. 

That being said, it may make sense to drop the ability to provide custom CSS, provide a white-list or black-list of CSS that can be applied, or just leave it as a free-for-all. Once again, feedback would be greatly appreciated. 

If you'd like to provide feedback of any kind, either email me (justinh@evidentpoint.com) or add an issue to the Github [issue tracker](https://github.com/readium/Readium-Web-Components/issues?state=open).
