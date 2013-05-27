---
layout: page
title: "Getting started with RWC"
date: 2013-05-22 15:53
comments: true
sharing: true
footer: true
author: Justin Hume
---

<a id="simple-rwc-demo"></a>
### SimpleRWC.js & Demo application
The easiest way to get familiar with Readium Web Components is to use SimpleRWC.js, a javascript module that wires together all the RWC modules in one object and exposes a simplified API. 

This module is included with a small web application that embeds SimpleRWC.js and wires a few controls, such as page-next and page-previous, to the SimpleRWC API. 

SimpleRWC.js should help you get started using and understanding Readium Web Components. 

#### Instructions for setting up the demo
To use this demo, you need to have a web server. 

1. Download the SimpleRWC demo application: 

[SimpleRWC_Demo.zip]()

2. Unzip the demo file in the folder you intend to serve the application files

3. Start your server

4. Point your browser to url/to/demo/example_reader.html

<a id="simple-rwc-description"></a>
### Description of the demo application

#### Demo app structure
The demo application contains four important pieces: 

1. example_reader.html: The application HTML
2. modules_and_dependencies: A folder that contains RWC javascript [dependencies]() and SimpleRWC.js
3. assets/css: Styling for the demo
4. assets/images: Images for the demo

#### Important parts of the code
Most of the demo application is application-specific code; that is, application layout and styling. There are four important parts of the application that leverage SimpleRWC:

##### _Create an HTML element in which to embed an EPUB publication_

{% codeblock Embedding element lang:HTML %}
    <div id="epub-reader-container">
        <div id="reader" style="height:100%; width:100%">
        </div>
    </div>
{% endcodeblock %}

##### _Initialize the SimpleRWC object_
The SimpleRWC object requires a reference to the HTML element to bind to, an object of viewer preferences, a URL to the EPUB publication package document, and the package document XML. 

{% codeblock Initialize SimpleRWC object lang:javascript %}

    // Get the HTML element to bind the module reader to
    var elementToBindReaderTo = $("#reader");

    // Create an object of viewer preferences
    var viewerPreferences = {
        fontSize : 12,
        syntheticLayout : false,
        currentMargin : 3,
        tocVisible : false,
        currentTheme : "default"
    };

    ...

    // THE MOST IMPORTANT PART - INITIALIZING THE SIMPLE RWC MODEL
    RWCDemoApp.epubViewer = new SimpleRWC(elementToBindReaderTo, viewerPreferences, packageDocumentURL, result);

{% endcodeblock %}

##### _Wire the application to the SimpleRWC API_
Once the SimpleRWC object has been instantiated, the application developer can wire their application to the API provided by RWC. In the case of the demo application, buttons that control next page, previous page etc. have been wired to object. 

{% codeblock Wire HTML to SimpleRWC object lang:javascript %}

    // These are application specific handlers that wire the HTML to the SimpleRWC module API

    // Set handlers for click events

    ...

    $("#prev-page").on("click", function () {
        RWCDemoApp.epubViewer.previousPage();
    });

    ...

    $("#next-page").on("click", function () {
        RWCDemoApp.epubViewer.nextPage();
    });

    ...

    $("#set-margin").on("click", function () {
        var marginVal = RWCDemoApp.getInputValue("margin-val");
        RWCDemoApp.epubViewer.setMargin(parseInt(marginVal));
    }); 

    ...

    $("#set-font-size").on("click", function () {
        var fontVal = RWCDemoApp.getInputValue("font-size-val");
        RWCDemoApp.epubViewer.setFontSize(parseInt(fontVal));
    });

    ...

    $("#set-one-page").on("click", function () {
        RWCDemoApp.epubViewer.setSyntheticLayout(false);
    });

    ...

    $("#set-two-pages").on("click", function () {
        RWCDemoApp.epubViewer.setSyntheticLayout(true);
    });

{% endcodeblock %}

{% codeblock Render and show EPUB publication lang:javascript %}

    // Render the reader. This will load all the viewable resources of the EPUB and fire 
    //   an event when they've all loaded. Once the resources of the epub have been loaded, 
    //   the second spine item will be shown.
    RWCDemoApp.epubViewer.on("epubLoaded", function () { 
        RWCDemoApp.epubViewer.showSpineItem(2);
    }, that);
    RWCDemoApp.epubViewer.render();

{% endcodeblock %}

<a id="simple-rwc-alt-demo"></a>
### Alternative demo app
If you're familiar with the Ruby-ish stack (Rake, bundler, rvm etc.) and git, you can get started with the following demo:

.....

<a id="rwc-ror-demo"></a>
### Ruby on Rails demo application
